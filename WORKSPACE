workspace(name = "halo_containers")

load(
    "@bazel_tools//tools/build_defs/repo:http.bzl",
    "http_archive",
    "http_file",
)

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "b1e80761a8a8243d03ebca8845e9cc1ba6c82ce7c5179ce2b295cd36f7e394bf",
    urls = [
        "https://github.com/bazelbuild/rules_docker/releases/download/v0.25.0/rules_docker-v0.25.0.tar.gz",
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
    digest = "sha256:b795f8e0caaaacad9859a9a38fe1c78154f8301fdaf0872eaf1520d66d9c0b98",
    registry = "docker.io",
    repository = "library/ubuntu",
)

# bazel
http_file(
    name = "bazelisk",
    downloaded_file_path = "bazelisk",
    executable = True,
    sha256 = "61699e22abb2a26304edfa1376f65ad24191f94a4ffed68a58d42b6fee01e124",
    urls = ["https://github.com/bazelbuild/bazelisk/releases/download/v1.17.0/bazelisk-linux-amd64"],
)

# CUE
http_file(
    name = "cue",
    downloaded_file_path = "cue.tar.gz",
    sha256 = "38c9a2f484076aeafd9f522efdee40538c31337539bd8c80a29f5c4077314e53",
    urls = ["https://github.com/cue-lang/cue/releases/download/v0.5.0/cue_v0.5.0_linux_amd64.tar.gz"],
)

# Google Cloud SDK
# See https://cloud.google.com/sdk/docs/install#deb
http_file(
    name = "cloud_sdk_apt_key",
    downloaded_file_path = "cloud-sdk-apt-key.gpg",
    sha256 = "aa26cfdf2640ea1e02e8959b77957491cf5fb78964f06a5921e2c79607872797",
    urls = ["https://packages.cloud.google.com/apt/doc/apt-key.gpg"],
)
