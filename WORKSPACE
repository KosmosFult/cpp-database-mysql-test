workspace(
    name = "mysql_test",
)

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "trpc_cpp",
    remote = "https://github.com/KosmosFult/trpc-cpp.git",
    branch = "mysql-main-repo",
)

load("@trpc_cpp//trpc:workspace.bzl", "trpc_workspace")
trpc_workspace()


git_repository(
    name = "trpc_cpp_database_mysql",
    remote = "https://github.com/KosmosFult/cpp-database-mysql.git",
    branch = "main",
)

load("@trpc_cpp_database_mysql//trpc:workspace.bzl", "trpc_database_mysql_workspace")
trpc_database_mysql_workspace()

