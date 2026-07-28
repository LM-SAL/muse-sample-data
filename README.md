# muse-sample-data

Sample data files for the [`muse`](https://github.com/LM-SAL/muse) documentation gallery.

The files are **not** stored in the git tree — they are attached as release assets and downloaded on demand by `muse.data.fetch_example_data`, which caches them locally with [pooch](https://www.fatiando.org/pooch/).

Download URL pattern:

```
https://github.com/LM-SAL/muse-sample-data/releases/download/<tag>/<filename>
```

## Adding or updating files

Use `upload_data.sh` (requires the [`gh` CLI](https://cli.github.com/), authenticated):

```bash
./upload_data.sh path/to/file1.nc path/to/file2.nc
```

Always upload to the `v1` tag (the default) and let it clobber same-named assets, one release holds the current copy of everything.
The script prints the URL + SHA-256 entries to paste into `_REGISTRY` in `muse/data/__init__.py`; a changed file changes its hash, so update `_REGISTRY` in the same PR.

Notes:

- Per-file limit is 2 GB (GitHub release asset limit).
- Zarr stores must be uploaded as a single `.tar.gz` (assets are flat files).
