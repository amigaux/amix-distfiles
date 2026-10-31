# amix-distfiles

Fallback copies of upstream source archives that the
[amix](https://github.com/amigaux/amix) build fetches.

The build recipes fetch every source from its original upstream location
first. A recipe falls back to this repository only when that fetch fails:
the upstream is gone, has moved, or serves different bytes. Every recipe
pins the SHA-256 of its archive, and that check applies to a copy from
here exactly as to one from upstream.

Only sources at risk are mirrored here: old or archived releases,
SourceForge-only downloads, and GitHub-generated archives, which GitHub
does not guarantee to stay byte-identical. Sources from stable upstreams
are not copied.

## Layout

Each source is a release asset under a tag named `<name>-<version>`:

    https://github.com/amigaux/amix-distfiles/releases/download/<name>-<version>/<file>

For example `releases/download/ncurses-6.6/ncurses-6.6.tar.gz`.
A tag can hold more than one file (`xorg-x11r6.3` holds `xc-1.tar.gz`,
`xc-2.tar.gz` and `xc-3.tar.gz`).

## What the files are

Each file is the upstream's own archive, byte for byte, unmodified. Before
upload each was downloaded again from its original URL and compared by
SHA-256, and where the upstream publishes checksums or signatures they were
checked as well.

[MANIFEST.tsv](MANIFEST.tsv) lists for every file: the tag, file name,
size, SHA-256, original URL, the result of the fresh download, the result
of the upstream's published checksum or signature, and the licence.

Each file stays under its upstream's licence; see MANIFEST.tsv and the
licence files inside each archive. This repository holds no project code
and no patches: those live in amix.
