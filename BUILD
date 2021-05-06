load("@rules_jvm_external//:defs.bzl", "java_export")
load("@bazel_sonatype//:defs.bzl", "sonatype_java_export")

exports_files([
    "pom.xml",
])

java_export(
    name = "dummy",
    maven_coordinates = "org.jetbrains.bsp:dummy:0.1.0",
    runtime_deps = [
        "//src/main/org/jetbrains/dummy",
    ],
)

sonatype_java_export(
    name = "dummy-sonatype",
    maven_coordinates = "org.jetbrains:dummy:0.1.1",
    maven_profile = "org.jetbrains",
    pom_template = "//:pom.xml",
    runtime_deps = [
        "//src/main/org/jetbrains/dummy",
    ],
)
