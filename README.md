Set up MinGW-w64
================

This is a GitHub action that sets up MinGW-w64 in your workflow run.

1. Installs MinGW-w64 on either Ubuntu or Windows.
2. Fixes the infamous libwinpthread-1.dll [static linking issue].

[static linking issue]: https://stackoverflow.com/q/13768515/514684

Use it in your workflow like this:

    - name: Set up MinGW
      uses: egor-tensin/setup-mingw@v1
      with:
        platform: x64

`x64` is the default value for the `platform` parameter and can be omitted.
Use `x86` if you want to build 32-bit binaries.

Set the `cygwin` parameter to `1` to set up MinGW inside an existing Cygwin
installation (installing Cygwin itself is as simple as `choco install cygwin`).

API
---

| Input    | Value   | Default | Description
| -------- | ------- | ------- | -----------
| platform | x64     | Yes     | Install the x86_64 toolchain.
|          | *Other* | No      | Install the i686 toolchain.
| cygwin   | 1       | No      | Install Cygwin packages.
|          | *Other* | Yes     | Install native binaries.
| static   | 1       | Yes     | Enable the static-linking workaround.
|          | *Other* | No      | Disable the static-linking workaround.

| Output  | Example                  | Description
| ------- | ------------------------ | -----------
| prefix  | x86_64-w64-mingw32       | Cross-compilation toolchain prefix
| gcc     | x86_64-w64-mingw32-gcc   | gcc binary name
| gxx     | i686-w64-mingw32-g++     | g++ binary name
| windres | i686-w64-mingw32-windres | windres binary name

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

[LICENSE.txt]: LICENSE.txt
