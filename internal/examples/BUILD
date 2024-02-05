load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")

cc_binary(
    name = "main",
    visibility = ["//visibility:public"],
    deps = [":main_lib"],
)

cc_library(
    name = "main_lib",
    srcs = [
        "main.cpp",
    ],
    visibility = ["//visibility:public"],
)
