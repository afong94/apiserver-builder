package(default_visibility = ["//visibility:public"])

load(
    "@io_bazel_rules_go//go:def.bzl",
    "go_binary",
    "go_library",
)
load("//pkg/version:def.bzl", "version_x_defs")

go_binary(
    name = "cloud-controller-manager",
    gc_linkopts = [
        "-linkmode",
        "external",
        "-extldflags",
        "-static",
    ],
    importpath = "k8s.io/kubernetes/cmd/cloud-controller-manager",
    library = ":go_default_library",
    x_defs = version_x_defs(),
)

go_library(
    name = "go_default_library",
    srcs = ["controller-manager.go"],
    importpath = "k8s.io/kubernetes/cmd/cloud-controller-manager",
    deps = [
        "//vendor/github.com/golang/glog:go_default_library",
        "//vendor/github.com/spf13/pflag:go_default_library",
        "//vendor/k8s.io/apiserver/pkg/server/healthz:go_default_library",
        "//vendor/k8s.io/apiserver/pkg/util/flag:go_default_library",
        "//vendor/k8s.io/apiserver/pkg/util/logs:go_default_library",
        "//vendor/k8s.io/kubernetes/cmd/cloud-controller-manager/app:go_default_library",
        "//vendor/k8s.io/kubernetes/cmd/cloud-controller-manager/app/options:go_default_library",
        "//vendor/k8s.io/kubernetes/pkg/client/metrics/prometheus:go_default_library",
        "//vendor/k8s.io/kubernetes/pkg/cloudprovider:go_default_library",
        "//vendor/k8s.io/kubernetes/pkg/cloudprovider/providers:go_default_library",
        "//vendor/k8s.io/kubernetes/pkg/version/prometheus:go_default_library",
        "//vendor/k8s.io/kubernetes/pkg/version/verflag:go_default_library",
    ],
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [
        ":package-srcs",
        "//cmd/cloud-controller-manager/app:all-srcs",
    ],
    tags = ["automanaged"],
)
