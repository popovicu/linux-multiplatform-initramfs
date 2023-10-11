load("@io_bazel_rules_go//go:def.bzl", "go_binary")

go_binary(
    name = "init",
    srcs = ["init.go"] +
           select({
               "//platforms:is_arm_linux": ["hello_arm.go"],
               "//platforms:is_x86_64_linux": ["hello_x86_64.go"],
           }),
)

genrule(
    name = "initramfs",
    srcs = [
        ":init",
    ],
    outs = ["initramfs.cpio"],
    cmd = "echo init > file_list.txt && cp $(location :init) . && cpio -o -H newc < file_list.txt > $@",
)
