# Database Answers model images

This branch contains 1,884 model-related images selected from the `data_models`
directory of [`pranamg/databaseanswers`](https://github.com/pranamg/databaseanswers),
branch `main`, at source commit `b9b981b0912790e323d71a92d2f677c45ad645f7`.

Images are stored in `model_images/`. The output filename is based on the
directory immediately above the nearest `images/` directory:

```text
{normalized-scenario}_model.{original-extension}
```

If a scenario has multiple matching images, every image is retained with a
stable numbered suffix, such as `_01`, `_02`, and so on. The numbering follows
the sorted source paths. No source image is overwritten. The full list of the
408 collision groups and their source-to-output mappings is in
[`COLLISIONS.md`](COLLISIONS.md).

## Selection rules

Only image files beneath a directory named `images` are considered. Matching
is case-insensitive and ignores punctuation and separators in image filenames.
The filename is selected if it contains `model` or `erd`, if it contains both
`data` and `mart`, or if it contains at least two of `data`, `model`, and
`warehouse` in any order or combination. A lone `data` or `warehouse` term is
not sufficient.

Scenario names are lowercased and runs of non-alphanumeric characters become
underscores. Original image formats are preserved.

## Refreshing this branch

Use a separate, clean clone of the repository. Update `main`, sparse-check out
`data_models`, and run the extraction script with a new, empty staging output
directory. Review its complete source-to-destination report and collision
groups before changing this branch. On `model-images-only`, verify the working
tree is clean and update only the generated `model_images/` directory and this
report. Review `git status` and the diff, commit the refresh, and push normally.
Do not force-push this branch or merge it into `main`.
