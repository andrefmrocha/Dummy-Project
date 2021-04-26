workspace(name = "dummy_project")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

skylib_version = "1.0.3"

http_archive(
    name = "bazel_skylib",
    sha256 = "1c531376ac7e5a180e0237938a2536de0c54d93f5c278634818e0efc952dd56c",
    type = "tar.gz",
    url = "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib-{}.tar.gz".format(skylib_version, skylib_version),
)

rules_scala_version = "9bd9ffd3e52ab9e92b4f7b43051d83231743f231"

http_archive(
    name = "io_bazel_rules_scala",
    sha256 = "438bc03bbb971c45385fde5762ab368a3321e9db5aa78b96252736d86396a9da",
    strip_prefix = "rules_scala-%s" % rules_scala_version,
    type = "zip",
    url = "https://github.com/bazelbuild/rules_scala/archive/%s.zip" % rules_scala_version,
)

# Stores Scala version and other configuration
# 2.12 is a default version, other versions can be use by passing them explicitly:
# scala_config(scala_version = "2.11.12")
load("@io_bazel_rules_scala//:scala_config.bzl", "scala_config")

scala_config("2.12.6")

load("@io_bazel_rules_scala//scala:scala.bzl", "scala_repositories")

scala_repositories()

load("@io_bazel_rules_scala//scala:toolchains.bzl", "scala_register_toolchains")

scala_register_toolchains()

RULES_JVM_EXTERNAL_TAG = "3bb065efc666579fc2eb4e154f9b7b6bf334af27"

BAZEL_SONATYPE_TAG = "8d67d3b029185c030fe8b6057346f6450c57496c"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "org.sonatype.spice.zapper:spice-zapper:1.3",
        "org.wvlet.airframe:airframe-http_2.12:20.12.1",
        "org.scala-lang.modules:scala-java8-compat_2.12:0.9.1",
        "org.wvlet.airframe:airspec_2.12:20.12.1",
        "org.backuity.clist:clist-core_2.12:3.5.1",
        "org.backuity.clist:clist-macros_2.12:3.5.1",
    ],
    generate_compat_repositories = True,
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

http_archive(
    name = "bazel_sonatype",
    strip_prefix = "sbt-sonatype-%s" % BAZEL_SONATYPE_TAG,
    url = "https://github.com/andrefmrocha/sbt-sonatype/archive/%s.zip" % BAZEL_SONATYPE_TAG,
)

#local_repository(
#    name = "bazel_sonatype",
#    path = "/home/andre/Projects/sbt-sonatype",
#)
