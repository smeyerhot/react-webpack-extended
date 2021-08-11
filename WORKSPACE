workspace(
    name = "react-webpack-extended",
    managed_directories = {
        "@npm": ["node_modules"],

    },
)
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "8f5f192ba02319254aaf2cdcca00ec12eaafeb979a80a1e946773c520ae0a2c9",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/3.7.0/rules_nodejs-3.7.0.tar.gz"],
)
load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")
yarn_install(
    # Name this npm so that Bazel Label references look like @npm//package
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

###############################
# DOCKER                      #
###############################

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "59d5b42ac315e7eadffa944e86e90c2990110a1c8075f1cd145f487e999d22b3",
    strip_prefix = "rules_docker-0.17.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.17.0/rules_docker-v0.17.0.tar.gz"],
)
load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load(
    "@io_bazel_rules_docker//nodejs:image.bzl",
    _nodejs_image_repos = "repositories",
)

_nodejs_image_repos()