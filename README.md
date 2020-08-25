# java_multiple_files - proto libraries must be used to autocomplete 

When using a `java_proto_library`, its classes will only appear in autocompletion if they are
included as a dependency of a `java_library` rule and the proto jars have been built already.

## Reproduction steps

### 1. No autocomplete if not added as a dependency

1. Build all targets: `bazel build //...`
2. Open/restart VSCode
3. Open *C.Java* and type `My` in the main method. The `MyMsg` proto will not appear in the autocompletion menu.

### 2. Autocompletes if added as a dependency

1. Uncomment line 15 of *BUILD.bazel*
2. Open/restart VSCode
3. Open *C.Java* and type `My` in the main method. The `MyMsg` proto appears as an autocomplete option.