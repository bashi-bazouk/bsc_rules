## bsc_rules

# Use

Refer to `bsc_sources.bzl` and etc in your tree.

Add a clause to your `MODULE.bazel`, adjusting `BSC_ROOT` to reflect your `bsc`'s install location.

```python
BSC_ROOT="/opt/homebrew/Cellar/bsc/2026.01/"

local_repository(
    name = "bsc_local",
    path = BSC_ROOT,
    build_file_content = """
exports_files(["bin/bsc"])

filegroup(
    name="bsc_runfiles",
    srcs=glob([
        "libexec/lib/Libraries/*"
    ]),
    visibility=["//visibility:public"]
)
""",
)
```

