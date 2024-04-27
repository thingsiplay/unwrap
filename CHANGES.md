# Changelog

Keep track of changes for [unwrap](https://github.com/thingsiplay/unwrap) .

## [0.6] - April 27, 2024

- changed: a list of supported file extensions are added, and script will
  default to process only those files, list can be looked up in the -H long help
- new: option -A to process all files regardless of file extension

## [0.5] - April 26, 2024

- bug: directory in -o DIR containing spaces was not working due to expansion
  of special placeholders by parallel

## [0.4] - April 25, 2024

- new: option -l to list all processed files that were extracted from the
  archive

## [0.3] - April 25, 2024

- new: option -r to disable automatic creation of archive subdirs
- changed: default output directory for -o is original location of input file,
  and no longer the current working directory
- changed: ignore directories as input, process files only

## [0.2] - April 25, 2024

- changed: renamed option -m to -q for quiet

## [0.1] - April 24, 2024

- initial upload
