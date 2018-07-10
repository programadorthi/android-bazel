# Recommended create a name for workspace
workspace(name = "sample")

# Use the Android SDK to build the project
# ANDROID_HOME is required to use the declaration below
android_sdk_repository(
    name = "androidsdk",
)

# Bazel rules for Kotlin
# git_repository(
#     name = "org_pubref_rules_kotlin",
#     remote = "https://github.com/pubref/rules_kotlin.git",
#     tag = "v0.5.0", # update as needed
# )
# load("@org_pubref_rules_kotlin//kotlin:rules.bzl", "kotlin_repositories")
load("//rules:rules.bzl", "kotlin_repositories")
kotlin_repositories(
    com_github_jetbrains_kotlin_url = "https://github.com/JetBrains/kotlin/releases/download/v1.2.51/kotlin-compiler-1.2.51.zip",
    com_github_jetbrains_kotlin_sha256 = "8a74711c805d3d265b93c13d8c40af5b4dad324591450d2eef0eafc1c9a6f92c",
)

# Google Maven Repository
GMAVEN_TAG = "20180625-1"
http_archive(
    name = "gmaven_rules",
    strip_prefix = "gmaven_rules-%s" % GMAVEN_TAG,
    url = "https://github.com/bazelbuild/gmaven_rules/archive/%s.tar.gz" % GMAVEN_TAG,
)
load("@gmaven_rules//:gmaven.bzl", "gmaven_rules")
gmaven_rules()
