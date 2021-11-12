workspace(name = "halo_containers")

load(
    "@bazel_tools//tools/build_defs/repo:http.bzl",
    "http_archive",
    "http_file",
)

RULES_DOCKER_VERSION = "0.19.0"

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "1f4e59843b61981a96835dc4ac377ad4da9f8c334ebe5e0bb3f58f80c09735f4",
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

# docker.io/library/ubuntu:18.04
container_pull(
    name = "ubuntu_18_04",
    digest = "sha256:b9caadbf898c50ce67da0ab5bafc4680997b010c3e17d2bb73d2ae5fe056e52b",
    registry = "docker.io",
    repository = "library/ubuntu",
)

# docker.io/library/debian:bullseye-slim
container_pull(
    name = "debian_bullseye",
    digest = "sha256:8ab4e348f60ebd18b891593a531ded31cbbc3878f6e476116f3b49b15c199110",
    registry = "docker.io",
    repository = "library/debian",
)

# Custom Java base image.
# See //base:push_java_base
container_pull(
    name = "debian_java_base",
    digest = "sha256:c6746729103a1a306a1ed572012562496512a691b3b23c3abacd64ad503cebc2",
    registry = "index.docker.io",
    repository = "wfameasurement/java-base",
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
