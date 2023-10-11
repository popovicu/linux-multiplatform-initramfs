platform(
    name = "arm_linux",
    constraint_values = [
        "@platforms//os:linux",
        "@platforms//cpu:arm",
        "@io_bazel_rules_go//go/toolchain:cgo_off",
    ],
)

platform(
    name = "x86_64_linux",
    constraint_values = [
        "@platforms//os:linux",
        "@platforms//cpu:x86_64",
        "@io_bazel_rules_go//go/toolchain:cgo_off",
    ],
)

# Config settings are used below to select the platform-specific files in our build accurately.
# For rationale why not reuse the platform targets from above, please check:
# https://bazel.build/docs/configurable-attributes#faq-select-platforms
# The section is called "Why doesn't select() work with platforms?"

config_setting(
    name = "is_x86_64_linux",
    constraint_values = [
        "@platforms//cpu:x86_64",
        "@platforms//os:linux",
    ],
)

config_setting(
    name = "is_arm_linux",
    constraint_values = [
        "@platforms//cpu:arm",
        "@platforms//os:linux",
    ],
)
