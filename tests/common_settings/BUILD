load("@rules_shell//shell:sh_test.bzl", "sh_test")
load("//rules:common_settings.bzl", "int_flag", "string_flag")

package(
    default_applicable_licenses = ["//:license"],
    default_testonly = 1,
)

licenses(["notice"])

int_flag(
    name = "my_int_flag",
    build_setting_default = 42,
    make_variable = "MY_INT_FLAG",
)

string_flag(
    name = "my_string_flag",
    build_setting_default = "foo",
    make_variable = "MY_STRING_FLAG",
)

sh_test(
    name = "make_variable_test",
    srcs = ["make_variable_test.sh"],
    env = {
        "MESSAGE": "Hello, $(MY_STRING_FLAG)! My name is $(MY_INT_FLAG).",
    },
    toolchains = [
        ":my_int_flag",
        ":my_string_flag",
    ],
)
