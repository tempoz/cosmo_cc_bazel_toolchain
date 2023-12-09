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
    supports_param_files = 1,
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
        "-L external/cosmocc/x86_64-linux-cosmo/lib",
        "-static",
        "-no-stdlib",
        "-no-pie",
        "-fuse-ld=bfd",
        "-Wl,-z,norelro",
        "-Wl,--gc-sections",
        "-Wl,-T,external/cosmocc/x86_64-linux-cosmo/lib/ape.lds",
        "-Wl,-z,common-page-size=4096",
        "-Wl,-z,max-page-size=16384",
        "-Wl,-no-as-needed",
        "external/cosmocc/x86_64-linux-cosmo/lib/ape.o",
        "external/cosmocc/x86_64-linux-cosmo/lib/crt.o",
        "-lcosmo",
        "-lcxx",
    ],
    link_libs = [],
    opt_compile_flags = [],
    opt_link_flags = ["-Wl,--gc-sections"],
    supports_start_end_lib = True,
    target_libc = "cosmo_cc",
    target_system_name = "local",
    toolchain_identifier = "cosmo_cc",
    unfiltered_compile_flags = [],
)
