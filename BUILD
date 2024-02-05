load("@rules_cc//cc:defs.bzl", "cc_toolchain")

load(":cc_toolchain_config.bzl", "cc_toolchain_config")

toolchain(
    name = "cosmo_toolchain",
    toolchain = ":cosmo_cc_toolchain",
    toolchain_type = "@bazel_tools//tools/cpp:toolchain_type",
)

cc_toolchain(
    name = "cosmo_cc_toolchain",
    all_files = "@cosmocc//:x86_64-full",
    ar_files = "@cosmocc//:x86_64-full",
    as_files = "@cosmocc//:x86_64-full",
    compiler_files = "@cosmocc//:x86_64-full",
    dwp_files = ":empty",
    linker_files = "@cosmocc//:x86_64-full",
    objcopy_files = "@cosmocc//:x86_64-full",
    static_runtime_lib = "@cosmocc//:x86_64-libstdc++.a",
    strip_files = "@cosmocc//:x86_64-full",
    supports_param_files = 0,
    toolchain_config = ":cosmo_cc_toolchain_config",
)

cc_toolchain_config(
    name = "cosmo_cc_toolchain_config",
    abi_libc_version = "unknown",
    abi_version = "unknown",
    builtin_sysroot = "",
    compile_flags = [
        # "--strace",
        "-isystem",
        "external/cosmocc/include",
        "-include",
        "external/cosmocc/include/libc/integral/normalize.inc",
    ] + [
        "-U_FORTIFY_SOURCE",
        "-fstack-protector",
        "-Wall",
        "-Wunused-but-set-parameter",
        "-Wno-free-nonheap-object",
        "-pass-exit-codes",
    ] + [
        "-fno-pie",
        "-nostdinc",
        "-fno-math-errno",
        "-fportcosmo",
        "-fno-dwarf2-cfi-asm",
        "-fno-unwind-tables",
        "-fno-asynchronous-unwind-tables",
        "-fno-semantic-interposition",
        "-fno-optimize-sibling-calls",
        "-mno-omit-leaf-frame-pointer",
        "-fno-exceptions",
        "-mno-red-zone",
        "-D__COSMOPOLITAN__",
        "-D__COSMOCC__",
        "-D__FATCOSMOCC__",
        "-mno-tls-direct-seg-refs",
        # "-ffixed-x18", # platform-specific
        # "-ffixed-x28", # platform-specific
        # "-mno-outline-atomics", # platform-specific
        "-fno-omit-frame-pointer",
    ],
    compiler = "cosmo_cc-11.2.0",
    coverage_compile_flags = ["--coverage"],
    coverage_link_flags = ["--coverage"],
    cpu = "k8",
    cxx_flags = [
        # "-std=c++17",
        "-fno-rtti",
        "-fuse-cxa-atexit",
    ],
    dbg_compile_flags = ["-g"],
    host_system_name = "local",
    link_flags = [
        "-Lexternal/cosmocc/x86_64-linux-cosmo/lib",
        "-Texternal/cosmocc/x86_64-linux-cosmo/lib/ape.lds",
        "-zcommon-page-size=4096",
        "-zmax-page-size=16384",
        "-no-as-needed",
        "-znorelro",
        "-znow",
    ],
    link_libs = [
        "-lc",
        "-lcosmo",
        "-lcxx",
        "-ldl",
        "-lgcc_s",
        "-lm",
        "-lresolv",
        "-lrt",
        "-lstdc++",
        # "external/cosmocc/x86_64-linux-cosmo/lib/ape-no-modify-self.o",
        "external/cosmocc/x86_64-linux-cosmo/lib/ape.o",
        "external/cosmocc/x86_64-linux-cosmo/lib/crt.o",
    ],
    opt_compile_flags = [
        "-O2",
        "-D_FORTIFY_SOURCE=1",
        "-DNDEBUG",
        "-ffunction-sections",
        "-fdata-sections",
    ],
    opt_link_flags = ["--gc-sections"],
    target_libc = "cosmo_cc",
    target_system_name = "local",
    toolchain_identifier = "cosmo_cc",
    unfiltered_compile_flags = [
        "-fno-canonical-system-headers",
        "-Wno-builtin-macro-redefined",
        "-D__DATE__=\"redacted\"",
        "-D__TIMESTAMP__=\"redacted\"",
        "-D__TIME__=\"redacted\"",
    ],
)
