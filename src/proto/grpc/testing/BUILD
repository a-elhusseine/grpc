# Copyright 2017 gRPC authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

licenses(["notice"])  # Apache v2

load("//bazel:grpc_build_system.bzl", "grpc_package", "grpc_proto_library")
load("@grpc_python_dependencies//:requirements.bzl", "requirement")
load("@org_pubref_rules_protobuf//python:rules.bzl", "py_proto_library")

grpc_package(
    name = "testing",
    visibility = "public",
)

exports_files([
    "echo.proto",
    "echo_messages.proto",
])

grpc_proto_library(
    name = "compiler_test_proto",
    srcs = ["compiler_test.proto"],
    generate_mocks = True,
)

grpc_proto_library(
    name = "control_proto",
    srcs = ["control.proto"],
    has_services = False,
    deps = [
        "payloads_proto",
        "stats_proto",
    ],
)

grpc_proto_library(
    name = "echo_messages_proto",
    srcs = ["echo_messages.proto"],
    has_services = False,
)

grpc_proto_library(
    name = "echo_proto",
    srcs = ["echo.proto"],
    generate_mocks = True,
    deps = [
        "echo_messages_proto",
        "simple_messages_proto",
    ],
)

grpc_proto_library(
    name = "empty_proto",
    srcs = ["empty.proto"],
    has_services = False,
)

py_proto_library(
    name = "py_empty_proto",
    protos = ["empty.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

grpc_proto_library(
    name = "messages_proto",
    srcs = ["messages.proto"],
    has_services = False,
)

py_proto_library(
    name = "py_messages_proto",
    protos = ["messages.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

grpc_proto_library(
    name = "metrics_proto",
    srcs = ["metrics.proto"],
)

grpc_proto_library(
    name = "payloads_proto",
    srcs = ["payloads.proto"],
    has_services = False,
)

grpc_proto_library(
    name = "benchmark_service_proto",
    srcs = ["benchmark_service.proto"],
    deps = [
        "messages_proto",
    ],
)

grpc_proto_library(
    name = "report_qps_scenario_service_proto",
    srcs = ["report_qps_scenario_service.proto"],
    deps = [
        "control_proto",
    ],
)

grpc_proto_library(
    name = "worker_service_proto",
    srcs = ["worker_service.proto"],
    deps = [
        "control_proto",
    ],
)

grpc_proto_library(
    name = "simple_messages_proto",
    srcs = ["simple_messages.proto"],
    has_services = False,
)

grpc_proto_library(
    name = "stats_proto",
    srcs = ["stats.proto"],
    has_services = False,
    deps = [
        "//src/proto/grpc/core:stats_proto",
    ],
)

grpc_proto_library(
    name = "test_proto",
    srcs = ["test.proto"],
    deps = [
        "empty_proto",
        "messages_proto",
    ],
)

py_proto_library(
    name = "py_test_proto",
    proto_deps = [
        ":py_empty_proto",
        ":py_messages_proto",
    ],
    protos = ["test.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

py_proto_library(
    name = "py_benchmark_service_proto",
    proto_deps = [
        ":py_messages_proto",
    ],
    protos = ["benchmark_service.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

py_proto_library(
    name = "py_payloads_proto",
    protos = ["payloads.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

py_proto_library(
    name = "py_stats_proto",
    proto_deps = [
        "//src/proto/grpc/core:py_stats_proto",
    ],
    protos = ["stats.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

py_proto_library(
    name = "py_control_proto",
    proto_deps = [
        ":py_payloads_proto",
        ":py_stats_proto",
    ],
    protos = ["control.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)

py_proto_library(
    name = "py_worker_service_proto",
    proto_deps = [
        ":py_control_proto",
    ],
    protos = ["worker_service.proto"],
    with_grpc = True,
    deps = [
        requirement("protobuf"),
    ],
)
