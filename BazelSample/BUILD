#load("@bazel_tools//tools/build_defs/repo:maven_rules.bzl", "maven_aar")
#load("@org_pubref_rules_kotlin//kotlin:rules.bzl", "kotlin_android_library")
load("//rules:rules.bzl", "kotlin_android_library")
load("@gmaven_rules//:defs.bzl", "gmaven_artifact")

BASE_MANIFEST = "app/src/main/AndroidManifest.xml"
BASE_PACKAGE = "io.moneyex.bazelsample"
BASE_RES = "app/src/main/res/**"

# Compile only res folder
android_library(
    name = "res",
    custom_package = BASE_PACKAGE,
    manifest = BASE_MANIFEST,
    resource_files = glob([BASE_RES]),
    deps = [
        gmaven_artifact("com.android.support:appcompat-v7:aar:27.1.1"),
        gmaven_artifact("com.android.support.constraint:constraint-layout:aar:1.1.2"),
    ],
)

# Compile only kotlin files
kotlin_android_library(
    name = "kotlin",
    srcs = glob(["app/src/main/**/*.kt"]),
    aar_deps = [
        ":res",
        gmaven_artifact("android.arch.core:common:jar:1.1.1"),
        gmaven_artifact("android.arch.lifecycle:common:jar:1.1.1"),
        gmaven_artifact("android.arch.lifecycle:runtime:aar:1.1.1"),
        gmaven_artifact("android.arch.lifecycle:viewmodel:aar:1.1.1"),
        gmaven_artifact("com.android.support:appcompat-v7:aar:27.1.1"),
        gmaven_artifact("com.android.support:support-compat:aar:27.1.1"),
        gmaven_artifact("com.android.support:support-core-ui:aar:27.1.1"),
        gmaven_artifact("com.android.support:support-core-utils:aar:27.1.1"),
        gmaven_artifact("com.android.support:support-fragment:aar:27.1.1"),
    ],
)

# Build APK
android_binary(
    name = "app",
    custom_package = BASE_PACKAGE,
    manifest = BASE_MANIFEST,
    manifest_values = {
        "applicationId": "io.moneyex.bazelsample",
        "minSdkVersion": "19",
        "targetSdkVersion": "27",
        "versionCode": "1",
        "versionName": "1.0.0",
    },
    deps = [
        ":kotlin",
        ":res",
    ]
)
