load("@io_bazel_rules_go//go:def.bzl", "go_library")

go_library(
    name = "go_default_library",
    srcs = [
        "cmt.go",
        "intelrdt.go",
        "mbm.go",
        "monitoring.go",
        "stats.go",
    ],
    importmap = "k8s.io/kubernetes/vendor/github.com/opencontainers/runc/libcontainer/intelrdt",
    importpath = "github.com/opencontainers/runc/libcontainer/intelrdt",
    visibility = ["//visibility:public"],
    deps = [
        "//vendor/github.com/sirupsen/logrus:go_default_library",
    ] + select({
        "@io_bazel_rules_go//go/platform:android": [
            "//vendor/github.com/opencontainers/runc/libcontainer/configs:go_default_library",
        ],
        "@io_bazel_rules_go//go/platform:linux": [
            "//vendor/github.com/opencontainers/runc/libcontainer/configs:go_default_library",
        ],
        "//conditions:default": [],
    }),
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
    visibility = ["//visibility:public"],
)
