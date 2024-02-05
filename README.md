# cosmo_cc_bazel_toolchain
Bazel toolchain that is backed by [cosmopolitan](https://github.com/jart/cosmopolitan).

Still largely untested, but now functional in at least some cases!

Add the following to your `WORKSPACE` file:
```
http_archive(
    name = "cosmo_cc_bazel_toolchain",
    url = "https://github.com/tempoz/cosmo_cc_bazel_toolchain/archive/refs/heads/main.zip",
)
```

Add the following to your `.bazelrc`:
```
build:cosmo --incompatible_enable_cc_toolchain_resolution
build:cosmo --extra_toolchains=@cosmo_cc_bazel_toolchain//:cosmo_toolchain
```

To make sure your `cosmo` bazel config now uses the `cosmo_cc` toolchain, run:

```
bazel cquery "@bazel_tools//tools/cpp:current_cc_toolchain" --config=cosmo --output starlark --starlark:expr 'providers(target)["CcToolchainInfo"].toolchain_id'
```

It should print `cosmo_cc`.

If you clone this repo, you can run the example build in `internal/examples` with:


```
bazel run //internal/examples:main
```
