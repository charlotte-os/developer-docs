# Conventions

## GitHub

If you are reading this file, it is likely that you know we are using GitHub as our version control. There are some conventions and practices that we as a group use to keep our GitHub space clean.

### Repository naming

Use concise and descriptive names. Please use hyphens instead of spaces when naming a new repository. Every repository should be always lower case.

Examples:

- `developer-docs`
- `module-development-kit`

#### Codenames

Codenames that are not descriptive have to be accepted by a `Maintainer` first.

### Branch naming

Main branches are always called `main`. Please make sure you always keep that as your default branch for the repository.

### Commits

Commits should be concise. They should start with capital letters and be imperative.

Examples:

- `Add framebuffer`
- `Enhance memory allocator`

### Merging

We use GitHub's rebase. Please ensure that each branch is only merged once this way. After merge, the branch should be deleted. This way we can keep our linear history clean. If you have trouble with rebasing, please let us know.

## Special files

- Every single repository should have a `README.md` in its root.
- There should also be a `LICESNE.md` as well. Our default license is `Mozilla Public License 2.0`.

## Linting

### Markdown

Please use the `markdownlint_cli2` linting engine or any linting tool built on it to ensure consistency in Markdown files. Using the default setting should suffice.

### Rust

Please ensure that you are using our special `Clippy` configuration made to automatically follow some of our Rust conventions.

### Bashscripts

Bashscript is not really a cross-platform solution. Don't use it if you don't have to. If it does make sense to use a bashscript, please make sure it doesn't have bashism and is POSIX compatible. You can use [ShellCheck](https://www.shellcheck.net/) to verify these properties.
