package(
    default_visibility = ["//tensorflow:internal"],
    features = [
        "-layering_check",
        "-parse_headers",
    ],
)

licenses(["notice"])  # Apache 2.0

load("//tensorflow:tensorflow.bzl", "tf_cc_test")
load("//tensorflow:tensorflow.bzl", "if_not_windows")

cc_library(
    name = "tfprof_stats",
    srcs = ["tfprof_stats.cc"],
    hdrs = ["tfprof_stats.h"],
    deps = [
        ":tfprof_code",
        ":tfprof_graph",
        ":tfprof_node",
        ":tfprof_op",
        ":tfprof_options",
        ":tfprof_scope",
        ":tfprof_show",
        ":tfprof_timeline",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_timeline",
    srcs = ["tfprof_timeline.cc"],
    hdrs = ["tfprof_timeline.h"],
    deps = [
        ":tfprof_node_show",
        ":tfprof_utils",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "@jsoncpp_git//:jsoncpp",
    ],
)

cc_library(
    name = "tfprof_node",
    srcs = ["tfprof_node.cc"],
    hdrs = ["tfprof_node.h"],
    deps = [
        ":tfprof_options",
        ":tfprof_utils",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_scope",
    srcs = ["tfprof_scope.cc"],
    hdrs = ["tfprof_scope.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_options",
        ":tfprof_show",
        ":tfprof_tensor",
        ":tfprof_utils",
        "//tensorflow/c:c_api",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:framework",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_op",
    srcs = ["tfprof_op.cc"],
    hdrs = ["tfprof_op.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_options",
        ":tfprof_show_multi",
        ":tfprof_tensor",
        ":tfprof_utils",
        "//tensorflow/c:c_api",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:framework",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_code",
    srcs = ["tfprof_code.cc"],
    hdrs = ["tfprof_code.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_options",
        ":tfprof_show_multi",
        ":tfprof_timeline",
        ":tfprof_utils",
        "//tensorflow/c:c_api",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:framework",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_graph",
    srcs = ["tfprof_graph.cc"],
    hdrs = ["tfprof_graph.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_options",
        ":tfprof_show",
        ":tfprof_tensor",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_node_show",
    srcs = ["tfprof_node_show.cc"],
    hdrs = ["tfprof_node_show.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_options",
        ":tfprof_utils",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_show",
    srcs = ["tfprof_show.cc"],
    hdrs = ["tfprof_show.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_node_show",
        ":tfprof_options",
        ":tfprof_tensor",
        ":tfprof_timeline",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_show_multi",
    srcs = ["tfprof_show_multi.cc"],
    hdrs = ["tfprof_show_multi.h"],
    deps = [
        ":tfprof_constants",
        ":tfprof_node",
        ":tfprof_node_show",
        ":tfprof_options",
        ":tfprof_scope",
        ":tfprof_show",
        ":tfprof_tensor",
        ":tfprof_timeline",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

tf_cc_test(
    name = "tfprof_show_test",
    size = "small",
    srcs = ["tfprof_show_test.cc"],
    data = [
        "testdata/ckpt.data-00000-of-00001",
        "testdata/ckpt.index",
        "testdata/ckpt.meta",
        "testdata/graph.pbtxt",
        "testdata/run_meta",
        "testdata/tfprof_log",
    ],
    deps = [
        ":tfprof_constants",
        ":tfprof_options",
        ":tfprof_stats",
        ":tfprof_tf_testlib",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

tf_cc_test(
    name = "tfprof_timeline_test",
    size = "small",
    srcs = ["tfprof_timeline_test.cc"],
    data = [
        "testdata/graph.pbtxt",
        "testdata/run_meta",
    ],
    deps = [
        ":tfprof_constants",
        ":tfprof_options",
        ":tfprof_stats",
        ":tfprof_tf_testlib",
        ":tfprof_utils",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_utils",
    srcs = ["tfprof_utils.cc"],
    hdrs = ["tfprof_utils.h"],
    copts = if_not_windows(["-Wno-sign-compare"]),
    deps = [
        ":tfprof_options",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
    ],
)

cc_library(
    name = "tfprof_options",
    srcs = ["tfprof_options.cc"],
    hdrs = ["tfprof_options.h"],
    deps = [
        "//tensorflow/core:framework_headers_lib",
        "//tensorflow/core:lib",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "print_model_analysis_hdr",
    hdrs = ["print_model_analysis.h"],
    deps = [
        "//tensorflow/core:framework_lite",
        "//tensorflow/core:protos_all_cc",
    ],
)

cc_library(
    name = "print_model_analysis",
    srcs = ["print_model_analysis.cc"],
    hdrs = ["print_model_analysis.h"],
    deps = [
        ":tfprof_options",
        ":tfprof_stats",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core/profiler:protos_all_cc",
        "//tensorflow/core/profiler/internal/advisor:tfprof_advisor",
    ],
    alwayslink = 1,
)

tf_cc_test(
    name = "tfprof_stats_test",
    size = "small",
    srcs = ["tfprof_stats_test.cc"],
    data = [
        "testdata/ckpt.data-00000-of-00001",
        "testdata/ckpt.index",
        "testdata/ckpt.meta",
        "testdata/graph.pbtxt",
        "testdata/run_meta",
        "testdata/tfprof_log",
    ],
    deps = [
        ":tfprof_constants",
        ":tfprof_options",
        ":tfprof_stats",
        ":tfprof_tf_testlib",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_tensor",
    srcs = ["tfprof_tensor.cc"],
    hdrs = ["tfprof_tensor.h"],
    copts = if_not_windows(["-Wno-sign-compare"]),
    deps = [
        "//tensorflow/core:framework",
        "//tensorflow/core:lib",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

tf_cc_test(
    name = "tfprof_tensor_test",
    size = "small",
    srcs = ["tfprof_tensor_test.cc"],
    data = [
        "testdata/ckpt.data-00000-of-00001",
        "testdata/ckpt.index",
        "testdata/ckpt.meta",
        "testdata/graph.pbtxt",
    ],
    deps = [
        ":tfprof_options",
        ":tfprof_stats",
        ":tfprof_tf_testlib",
        ":tfprof_utils",
        "//tensorflow/c:checkpoint_reader",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "tfprof_constants",
    hdrs = ["tfprof_constants.h"],
    deps = [
    ],
)

cc_library(
    name = "tfprof_tf_testlib",
    testonly = 1,
    deps = [
        ":tfprof_tf_lib",
        "//tensorflow/core:test",
        "//tensorflow/core:test_main",
        "//tensorflow/core:testlib",
    ],
)

cc_library(
    name = "tfprof_tf_lib",
    deps = [
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:regexp_internal",
    ],
)
# -----------------------------------------------------------------------------
# Google-internal targets.  These must be at the end for syncrepo.

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)
