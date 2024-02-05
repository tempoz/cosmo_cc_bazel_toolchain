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
    name = "rules_cc",
    sha256 = "2037875b9a4456dce4a79d112a8ae885bbc4aad968e6587dca6e64f3a0900cdf",
    strip_prefix = "rules_cc-0.0.9",
    urls = ["https://github.com/bazelbuild/rules_cc/releases/download/0.0.9/rules_cc-0.0.9.tar.gz"],
)

load("@rules_cc//cc:repositories.bzl", "rules_cc_dependencies", "rules_cc_toolchains")

rules_cc_dependencies()

http_archive(
    name = "cosmocc",
    workspace_file_content = "workspace(name=\"cosmocc\")",
    build_file_content = """
package(default_visibility = ["//visibility:public"])

filegroup(
    name = "x86_64-full",
    srcs = [
        "//:x86_64-bin",
        "//:libexec/gcc/x86_64-linux-cosmo/11.2.0",
        "//:include",
        "//:x86_64-lib",
    ],
)

# include

filegroup(
    name = "include",
    srcs = glob(["include/**/*"]),
)

# bin

filegroup(
    name = "x86_64-bin",
    srcs = [
        "x86_64-ar",
        "x86_64-gcc",
        "x86_64-g++",
        "x86_64-strip",
        "x86_64-objcopy",
        "x86_64-objdump",
        "x86_64-addr2line",
        "x86_64-elfedit",
        "x86_64-nm",
        "x86_64-ranlib",
        "x86_64-readelf",
        "x86_64-size",
        "x86_64-c++filt",
    ],
)

filegroup(name = "x86_64-ar", srcs = ["bin/x86_64-linux-cosmo-ar"])
filegroup(name = "x86_64-gcc", srcs = ["bin/x86_64-linux-cosmo-gcc"])
filegroup(name = "x86_64-g++", srcs = ["bin/x86_64-linux-cosmo-g++"])
filegroup(name = "x86_64-strip", srcs = ["bin/x86_64-linux-cosmo-strip"])
filegroup(name = "x86_64-objcopy", srcs = ["bin/x86_64-linux-cosmo-objcopy"])
filegroup(name = "x86_64-objdump", srcs = ["bin/x86_64-linux-cosmo-objdump"])
filegroup(name = "x86_64-addr2line", srcs = ["bin/x86_64-linux-cosmo-addr2line"])
filegroup(name = "x86_64-elfedit", srcs = ["bin/x86_64-linux-cosmo-elfedit"])
filegroup(name = "x86_64-nm", srcs = ["bin/x86_64-linux-cosmo-nm"])
filegroup(name = "x86_64-ranlib", srcs = ["bin/x86_64-linux-cosmo-ranlib"])
filegroup(name = "x86_64-readelf", srcs = ["bin/x86_64-linux-cosmo-readelf"])
filegroup(name = "x86_64-size", srcs = ["bin/x86_64-linux-cosmo-size"])
filegroup(name = "x86_64-c++filt", srcs = ["bin/x86_64-linux-cosmo-c++filt"])

alias(name = "x86_64-c++", actual = ":x86_64-g++")
alias(name = "x86_64-cc", actual = ":x86_64-gcc")
alias(name = "x86_64-cpp", actual = ":x86_64-gcc")

# libexec

filegroup(
    name = "libexec/gcc/x86_64-linux-cosmo/11.2.0",
    srcs = [
        "x86_64-as",
        "x86_64-cc1",
        "x86_64-cc1plus",
        "x86_64-collect2",
        "x86_64-ld.bfd",
    ],
)

filegroup(name = "x86_64-as", srcs = ["libexec/gcc/x86_64-linux-cosmo/11.2.0/as"])
filegroup(name = "x86_64-cc1", srcs = ["libexec/gcc/x86_64-linux-cosmo/11.2.0/cc1"])
filegroup(name = "x86_64-cc1plus", srcs = ["libexec/gcc/x86_64-linux-cosmo/11.2.0/cc1plus"])
filegroup(name = "x86_64-collect2", srcs = ["libexec/gcc/x86_64-linux-cosmo/11.2.0/collect2"])
filegroup(name = "x86_64-ld.bfd", srcs = ["libexec/gcc/x86_64-linux-cosmo/11.2.0/ld.bfd"])

alias(name = "x86_64-ld", actual = ":x86_64-ld.bfd")

# lib

filegroup(
    name = "x86_64-lib",
    srcs = [
        ":x86_64-ape-no-modify-self.o",
        ":x86_64-ape.lds",
        ":x86_64-ape.o",
        ":x86_64-crt.o",
        ":x86_64-libc.a",
        ":x86_64-libcosmo.a",
        ":x86_64-libcxx.a",
        ":x86_64-libdl.a",
        ":x86_64-libgcc_s.a",
        ":x86_64-libm.a",
        ":x86_64-libpthread.a",
        ":x86_64-libresolv.a",
        ":x86_64-librt.a",
        ":x86_64-libstdc++.a",
        ":x86_64-libz.a",
    ],
)

filegroup(name = "x86_64-ape-no-modify-self.o", srcs = ["x86_64-linux-cosmo/lib/ape-no-modify-self.o"])
filegroup(name = "x86_64-ape.lds", srcs = ["x86_64-linux-cosmo/lib/ape.lds"])
filegroup(name = "x86_64-ape.o", srcs = ["x86_64-linux-cosmo/lib/ape.o"])
filegroup(name = "x86_64-crt.o", srcs = ["x86_64-linux-cosmo/lib/crt.o"])
filegroup(name = "x86_64-libc.a", srcs = ["x86_64-linux-cosmo/lib/libc.a"])
filegroup(name = "x86_64-libcosmo.a", srcs = ["x86_64-linux-cosmo/lib/libcosmo.a"])
filegroup(name = "x86_64-libcxx.a", srcs = ["x86_64-linux-cosmo/lib/libcxx.a"])
filegroup(name = "x86_64-libdl.a", srcs = ["x86_64-linux-cosmo/lib/libdl.a"])
filegroup(name = "x86_64-libgcc_s.a", srcs = ["x86_64-linux-cosmo/lib/libgcc_s.a"])
filegroup(name = "x86_64-libm.a", srcs = ["x86_64-linux-cosmo/lib/libm.a"])
filegroup(name = "x86_64-libpthread.a", srcs = ["x86_64-linux-cosmo/lib/libpthread.a"])
filegroup(name = "x86_64-libresolv.a", srcs = ["x86_64-linux-cosmo/lib/libresolv.a"])
filegroup(name = "x86_64-librt.a", srcs = ["x86_64-linux-cosmo/lib/librt.a"])
filegroup(name = "x86_64-libstdc++.a", srcs = ["x86_64-linux-cosmo/lib/libstdc++.a"])
filegroup(name = "x86_64-libz.a", srcs = ["x86_64-linux-cosmo/lib/libz.a"])
    """,
    sha256 = "d2fa6dbf6f987310494581deff5b915dbdc5ca701f20f7613bb0dcf1de2ee511",
    url = "https://github.com/jart/cosmopolitan/releases/download/3.2.4/cosmocc-3.2.4.zip",
)
