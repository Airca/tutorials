### 编译bazel时，如果报这种错
```
ERROR: /root/.cache/bazel/_bazel_root/266a621d658e480269db4afbd63d6ed1/external/jpeg/BUILD:122:12: Illegal ambiguous match on configurable attribute "deps" in @jpeg//:jpeg:
@jpeg//:k8
@jpeg//:armeabi-v7a
Multiple matches are not allowed unless one is unambiguously more specialized.
ERROR: Analysis of target '//tensorflow/examples/label_image:label_image' failed; build aborted: 

/root/.cache/bazel/_bazel_root/266a621d658e480269db4afbd63d6ed1/external/jpeg/BUILD:122:12: Illegal ambiguous match on configurable attribute "deps" in @jpeg//:jpeg:
@jpeg//:k8
@jpeg//:armeabi-v7a
Multiple matches are not allowed unless one is unambiguously more specialized.
INFO: Elapsed time: 9.406s
INFO: 0 processes.
FAILED: Build did NOT complete successfully (37 packages loaded, 2355 targets \
configured)
    currently loading: tensorflow/core/kernels
    Fetching @eigen_archive; fetching
```
### 就需要重新安装0.11.1版本的bazel
```
$ sudo apt-get install -y --no-install-recommends bash-completion g++ zlib1g-dev
$ curl -LO "https://github.com/bazelbuild/bazel/releases/download/0.11.1/bazel_0.11.1-linux-x86_64.deb" 
$ sudo dpkg -i bazel_*.deb
```
