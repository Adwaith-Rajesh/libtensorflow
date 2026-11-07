# libtensorflow mirror
> TensorFlow 2.18.0 GPU

Mirror of `libtensorflow-gpu-linux-x86_64.tar.gz`, because the original can't be used with `zig fetch`.

## THE ISSUE

Google's server serves a GZIPPED tarball with `content-type: application/x-tar`, which means UNCOMPRESSED tar.

Zig believes the header, skips decompression, and dies with:

```
error: unable to unpack tarball to temporary directory: TarHeader
```
[Check GH Issue](https://github.com/ziglang/zig/issues/19636)

## WTF

A COMPRESSED FILE. Labeled as UNCOMPRESSED.

FIX THE HEADER GOOGLE. It is supposed to be `application/gzip`.

## Usage

```sh
zig fetch --save=libtensorflow https://github.com/Adwaith-Rajesh/libtensorflow/releases/download/v2.18.0/libtensorflow-gpu-linux-x86_64.tar.gz
```
