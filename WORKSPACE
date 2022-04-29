workspace(name = "halo_containers")

load(
    "@bazel_tools//tools/build_defs/repo:http.bzl",
    "http_archive",
    "http_file",
)

RULES_DOCKER_VERSION = "0.24.0"

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "27d53c1d646fc9537a70427ad7b034734d08a9c38924cc6357cc973fed300820",
    strip_prefix = "rules_docker-{version}".format(
        version = RULES_DOCKER_VERSION,
    ),
    urls = [
        "https://github.com/bazelbuild/rules_docker/releases/download/v{version}/rules_docker-v{version}.tar.gz".format(
            version = RULES_DOCKER_VERSION,
        ),
    ],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

# docker.io/library/ubuntu:20.04
container_pull(
    name = "ubuntu_20_04",
    digest = "sha256:dcc176d1ab45d154b767be03c703a35fe0df16cfb1cc7ea5dd3b6f9af99b6718",
    registry = "docker.io",
    repository = "library/ubuntu",
)

# bazel
http_file(
    name = "bazelisk",
    downloaded_file_path = "bazelisk",
    executable = True,
    sha256 = "4cb534c52cdd47a6223d4596d530e7c9c785438ab3b0a49ff347e991c210b2cd",
    urls = ["https://github.com/bazelbuild/bazelisk/releases/download/v1.10.1/bazelisk-linux-amd64"],
)

# CUE
http_file(
    name = "cue",
    downloaded_file_path = "cue.tar.gz",
    sha256 = "810851e0e7d38192a6d0e09a6fa89ab5ff526ce29c9741f697995601edccb134",
    urls = ["https://github.com/cuelang/cue/releases/download/v0.2.2/cue_0.2.2_Linux_x86_64.tar.gz"],
)

# Google Cloud SDK
# See https://cloud.google.com/sdk/docs/install#deb
http_file(
    name = "cloud_sdk_apt_key",
    downloaded_file_path = "cloud-sdk-apt-key.gpg",
    sha256 = "ff834d1e179c3727d9cd3d0c8dad763b0710241f1b64539a200fbac68aebff3e",
    urls = ["https://packages.cloud.google.com/apt/doc/apt-key.gpg"],
)

container_pull(
    name = "liquibase",
    digest = "sha256:6ddadbf89160e8f1e690cf52267703cf7279268f31e8d95781402270367c9e82",
    registry = "docker.io",
    repository = "liquibase/liquibase",
)
