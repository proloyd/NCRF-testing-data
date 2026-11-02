NCRF-testing-data
=================
Data for neuro-currentRF testing

Add or change files in the repo for use with NCRF
-------------------------------------------------
1. Ensure your only option is to add files here. Alternatives would be e.g.:
  
   - See if you can make use of existing files
   - Synthesize the necessary testing files using e.g. RawArray and NumPy directly
    
2. If new files are needed, make a PR to this repo to add your files.

3. Update the `version.txt` of the repo in your PR to the next increment.

4. Once your PR is merged, ask a maintainer to cut a new release of the testing data, e.g. 0.53.

5. In NCRF, update `ncrf/tests/fetch.py` to:
   
   1. Change the `RELEASE` in `ncrf/tests/fetch.py` to the new version.

   2. Set `known_hash` to the new SHA-256 hash, as `"sha256:<hash>"`. This can be easily done by either:
   
      1. Downloading and running `shasum -a 256` (or `sha256sum`) on this (with the proper version number):

         https://codeload.github.com/proloyd/NCRF-testing-data/tar.gz/0.3

         or

      2. Force-updating the repo and looking at the error message (as it gives the new true hash), e.g.:

             $ python -c "from ncrf.tests.fetch import fetch_dataset; fetch_dataset(force_download=True)"

Source space
------------
The source space of `fwd_sol` stores its `subjects_dir` relative to the dataset (`subjects`).
NCRF resolves it against the download directory, and on first use of the source coordinates
fetches fsaverage there and generates the `vol-7` source space; it is not part of this repo.

