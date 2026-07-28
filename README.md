# muse-sample-data

Sample data files for the [`muse`](https://github.com/LM-SAL/muse) documentation gallery.

The files are **not** stored in the git tree — they are attached as release
assets and downloaded on demand by `muse.data.fetch_example_data`, which
caches them locally with [pooch](https://www.fatiando.org/pooch/).

Download URL pattern:

```
https://github.com/LM-SAL/muse-sample-data/releases/download/<tag>/<filename>
```

## Adding or updating files

Use `upload_data.sh` (requires the [`gh` CLI](https://cli.github.com/), authenticated):

```bash
TAG=v1 ./upload_data.sh path/to/file1.nc path/to/file2.nc
```

It creates the release if needed, uploads the files (overwriting same-named
assets), and prints the URL + SHA-256 entries to paste into `_REGISTRY` in
`muse/data/__init__.py`.

Notes:

- Re-uploading a changed file under the same name changes its hash — update
  `_REGISTRY` in the same PR, or upload under a new tag to keep old muse
  versions working.
- Per-file limit is 2 GB (GitHub release asset limit).
- Zarr stores must be uploaded as a single `.tar.gz` (assets are flat files).
