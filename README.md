# cosmo_cc_bazel_toolchain
Bazel toolchain that is backed by [cosmopolitan](https://github.com/jart/cosmopolitan).

Work in progress; not currently functional.

Add the following to your `WORKSPACE` file:
```
http_archive(
    name = "cosmo_cc_bazel_toolchain",
    url = "https://github.com/tempoz/cosmo_cc_bazel_toolchain/archive/refs/heads/main.zip",
)
```

Add the following to your `.bazelrc`:
```
build:cosmo --repo_env BAZEL_DO_NOT_DETECT_CPP_TOOLCHAIN=1
build:cosmo --extra_toolchains=@cosmo_cc_bazel_toolchain//:cosmo_toolchain
build:cosmo --dynamic_mode=off
build:cosmo --linkopt="-static"
```
