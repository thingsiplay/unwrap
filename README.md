# Unwrap

Wrapper to marry GNU Parallel and 7-Zip for archive extraction.

- Author: [Tuncay D.](https://github.com/thingsiplay)
- Source: [Github](https://github.com/thingsiplay/unwrap)
- License: [MIT](LICENSE)

## What is this script for?

It uses 7z to extract files from archives. By also utilizing GNU Parallel,
multiple files can be processed at the same time.

The purpose is to streamline option handling and usability of both programs
into an unified command line interface, by only incorporating functionality
which I need. 7z option and argument handling is a bit confusing and does
things in unique and unfamiliar ways. On the other side, we have Parallel,
which is extremely complex and has ton of functionality; also confusing. So I
picked up my favorite options and bundled them into a manageable script.

Name of the script is inspired by `unwrap()` functionality from Rust
programming language. It's purpose is to provide the content of certain type
of variables by looking inside of it and taking it out.

## Installation

This is a Bash script. It does not need an installation. Just download and give
it the executable bit.

### Requirements

Linux only. 2 programs are required as a dependency:

- `parallel`: [GNU Parallel](https://www.gnu.org/software/parallel/)
- `7z`: [p7zip](https://github.com/p7zip-project/p7zip) (fork from [7z](https://7-zip.org/))

These applications are provided by packages that may have been packaged
differently, depending on the distribution or package manager. Here is a list
of commands with known setups to install:

#### Arch (includes Manjaro, EndeavourOS)

```bash
pacman -S parallel p7zip
```

### Download

There is no release or build version of the script. Just get the source, make
the script executable and put the file in a folder that is found in the $PATH
variable.

```bash
git clone https://github.com/thingsiplay/unwrap
cd unwrap
chmod +x unwrap
```

## How to use

I won't go too much into detail here, as the script has a descriptive help
page: `unwrap -h` , or more explanation with `unwrap -H`

In case of most basic usage without options, folders are created automatically
for each input file in current working directory. The following command will
create a folder named `my_1/` and unpack everything from the file `my_1.zip`
into it. Existing files in that directory will not be overwritten by files with
same name from archive content.

```bash
unwrap my_1.zip
```

When multiple files are given, then 2 files will be processed at the same time
with `parallel`:

```bash
unwrap *.zip
```

Use option `-a` to overwrite existing files:

```bash
unwrap -a *.zip
```

With `-i GLOB` a file name or path with wildcards can be specified, to extract
only files that match the GLOB pattern. Option `-f` will extract files without
a folder structure, meaning all files are output flat without creating sub
folders. `-o DIR` will specify a directory to channel all extracted files and
folders into. Let's combine all these three options to extract .txt files into
current working dir:

```bash
unwrap -f -i '*.txt' -o . *.zip
```

Or same as above, but shorter:

```bash
unwrap -fi'*.txt' -o. *.zip
```

There are a few more options available. You can also instruct the script to not
execute any `7z` command, but instead list them for inspection. Just add `-X`
to it and watch:

```bash
unwrap -X -fi'*.txt' -o. *.zip
```

Have a great rest of your day.
