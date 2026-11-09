# daffin

daffin is nebul.'s games frontend: every game of the home in one library, played from any screen. This repository
holds its downloads only: the Android app on the [releases](https://github.com/moukrea/daffin/releases) page, and the
page at [moukrea.github.io/daffin](https://moukrea.github.io/daffin/) that the app reads to update itself. The source
code is private for now and will be published under the same license. Each release keeps, next to its APK, the
sources that the licences of the third-party code it contains ask for (`.crate` files and the built-in player's source
archives), for as long as that APK is distributed. daffin's checks also run here, on GitHub Actions
(`.github/workflows/ci.yml`): started by hand on a commit of the private source, which never leaves the runner.
Releases are kept unless a licence problem forces their withdrawal,
as on 7 November 2026, when the first two releases were withdrawn because they contained a font whose licence did not
allow publishing it.

daffin is a preview for invited testers: there is no warranty and no support, and issues and pull requests are not
accepted here. See [SECURITY.md](SECURITY.md) for the security model and for checking a download. daffin is licensed
under the GNU Affero General Public License v3.0 only ([LICENSE](LICENSE)).
