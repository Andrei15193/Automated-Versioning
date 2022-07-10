This project aims to test a way of generating automated versions for projects and create releases for dependent projects when the base project has a new release.

Each release has a unique version and each project has its own version which is tracked, and changed, independently of one another. This is particularly useful for releases in dependent projects without having a release in the base project. For instance, `Project 2` can get to version `1.0.5` while `Project 3` is at `1.3.2` and `Project 1` is at `1.1.0`.

The major and minor versions are generally manually managed as it is hard to determine whether a series of commits include a new feature that is released and even more so to determine if it is a breaking change automatically. It is far more easier to modify these versions manually. What we need to be generated automatically is the build version and in case of prereleases, the increment for that particular prerelease.

### Structure

Project 1
- Project 2 (depends on Project 1)
- Project 3 (depends on Project 1)

Releases of `Project 1` generate releases for `Project 2` and `Project 3` for version bumps. Releases for `Project 2` or `Project 3` do not generate any other releases. Versions are tracked independently for each project.

All of this is done using GitHub Actions.