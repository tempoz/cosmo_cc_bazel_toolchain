workspace(
    name = "cosmo_cc_bazel_toolchain",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

http_archive(
    name = "platforms",
    sha256 = "5308fc1d8865406a49427ba24a9ab53087f17f5266a7aabbfc28823f3916e1ca",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/platforms/releases/download/0.0.6/platforms-0.0.6.tar.gz",
        "https://github.com/bazelbuild/platforms/releases/download/0.0.6/platforms-0.0.6.tar.gz",
    ],
)

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "f6f5ede97567d1c61d6d5227848bb13f419e4ea195b81ba4ca451f20bcd03d66",
    strip_prefix = "rules_go-4706a513acc1f6e5125b476936060ff71bfb8723",
    urls = [
        "https://github.com/bazelbuild/rules_go/archive/4706a513acc1f6e5125b476936060ff71bfb8723.zip",
    ],
)

http_archive(
    name = "rules_cc",
    sha256 = "2037875b9a4456dce4a79d112a8ae885bbc4aad968e6587dca6e64f3a0900cdf",
    strip_prefix = "rules_cc-0.0.9",
    urls = ["https://github.com/bazelbuild/rules_cc/releases/download/0.0.9/rules_cc-0.0.9.tar.gz"],
)

load("@rules_cc//cc:repositories.bzl", "rules_cc_dependencies", "rules_cc_toolchains")

rules_cc_dependencies()

http_archive(
    name = "cosmocc",
    patch_args = ["-p1"],
    patches = ["//buildpatches:cosmocc.patch"],
    sha256 = "7470f05ef28f1941eb655c0359de08118023ba75767c2c47b398569a16397504",
    urls = [
        "https://github.com/jart/cosmopolitan/releases/download/3.1.3/cosmocc-3.1.3.zip",
        "https://cosmo.zip/pub/cosmocc/cosmocc-3.1.3.zip",
    ],
)
