# bazel-issues - aquery has no output for java_proto_library

When using `bazel aquery` against a `java_proto_library` rule, no action information is returned.

```console
$ bazel version
Build label: 3.4.1-homebrew
Build target: bazel-out/darwin-opt/bin/src/main/java/com/google/devtools/build/lib/bazel/BazelServer_deploy.jar
Build time: Tue Jul 14 20:30:00 2020 (1594758600)
Build timestamp: 1594758600
Build timestamp as int: 1594758600

# Action information returned for proto_library as expected.
$ bazel aquery //:example_proto
INFO: Analyzed target //:example_proto (0 packages loaded, 0 targets configured).
INFO: Found 1 target...
action 'Generating Descriptor Set proto_library //:example_proto'
  Mnemonic: GenProtoDescriptorSet
  Target: //:example_proto
  Configuration: darwin-fastbuild
  ActionKey: fb235fab0c250947673444fb1dd28931c565ae479aa02adf966997d8e9c65978
  Inputs: [bazel-out/host/bin/external/com_google_protobuf/protoc, bazel-out/host/internal/_middlemen/external_Scom_Ugoogle_Uprotobuf_Sprotoc-runfiles, example.proto]
  Outputs: [bazel-out/darwin-fastbuild/bin/example_proto-descriptor-set.proto.bin]
  Command Line: (exec bazel-out/host/bin/external/com_google_protobuf/protoc \
    '--descriptor_set_out=bazel-out/darwin-fastbuild/bin/example_proto-descriptor-set.proto.bin' \
    '-Iexample.proto=example.proto' \
    --direct_dependencies \
    example.proto \
    '--direct_dependencies_violation_msg=%s is imported, but //:example_proto doesn'\''t directly depend on a proto_library that '\''srcs'\'' it.' \
    example.proto)

INFO: Elapsed time: 0.168s
INFO: 0 processes.
INFO: Build completed successfully, 0 total actions

# No information for java_proto_library
$ bazel aquery //:example_java_proto
INFO: Analyzed target //:example_java_proto (0 packages loaded, 15 targets configured).
INFO: Found 1 target...
INFO: Elapsed time: 0.151s
INFO: 0 processes.
INFO: Build completed successfully, 0 total actions
```
