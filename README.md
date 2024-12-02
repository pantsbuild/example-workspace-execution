# Pantsbuild - Workspace Execution Example

This example project demonstrates the "in-workspace" execution support in Pants which allows running processes directly in a project's repository instead of the usual execution sandbox. The workspace execution support is accessible via the new [`experimental_workspace_environment` target type](https://www.pantsbuild.org/stable/docs/using-pants/environments#in-workspace-execution-experimental_workspace_environment).

## Overview

This example project integrates Pants with Bazel to build a small Java program. (Pants has Java support so this example is very much contrived, but the point is demonstrate integration with a third party build tool, not to focus too much on details of this particular example.)

Some items to be aware of:

- _Bazel sources_. The Bazel workspace is under the `bazel-jvm` directory.

- _Pants configuration_. Pants has been configured to only look in `BUILD.pants` for targets so that Pants does not try to read any `BUILD.bazel` files.

## Running

1. Ensure you have Bazel and Docker both installed somewhere on the `PATH`.

2. Run `pants package //:project_image`. This will produce a Docker image with the jar file produced by Bazel.

3. Execute the Docker image: `docker run project_image:latest`. You should see the output: `Hello!`

## Additional Reading

For futher context, see the original ["In-Workspace Process Execution" design document](https://docs.google.com/document/d/1jUZTQHmUBr-Ij0nXOO0QX2Bq6XNANJg4-GNzhiOL4Xs/edit?usp=sharing).
