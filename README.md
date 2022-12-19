# Fork of protoc-gen-validate

## Background

- [Source](https://github.com/bufbuild/protoc-gen-validate)
- While implementing my own envoy als server, the use of go_control_plane requires protoc_gen_validate, which leads to issues on Bazel build:
  - The repository '@com_google_protobuf' could not be resolved (need to manually import).
  - The source project has its own BUILD files which force the compilation of non-go library that I don't need.
- Currently pushing a minimal fork to workaround the issue.

## Possible solution

- Find a way to override BUILD file. (tried with gazelle build_file_generation = "on" + build_file_name = "BUILD.minimal" + build_extra_args = ["-exclude=**/BUILD"] but original BUILD file was still evaluated.)
- Try to use 1.18 workspace features, replace original one with a forked version in the same monorepo.
- TODO: something that can be done on upstream?
