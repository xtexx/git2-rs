# Changelog

## 0.20.2 - 2025-05-05
[0.20.1...0.20.2](https://github.com/rust-lang/git2-rs/compare/git2-0.20.1...git2-0.20.2)

### Added

- Added `Status::WT_UNREADABLE`.
  [#1151](https://github.com/rust-lang/git2-rs/pull/1151)

### Fixed

- Added missing codes for `GIT_EDIRECTORY`, `GIT_EMERGECONFLICT`, `GIT_EUNCHANGED`, `GIT_ENOTSUPPORTED`, and `GIT_EREADONLY` to `Error::raw_code`.
  [#1153](https://github.com/rust-lang/git2-rs/pull/1153)
- Fixed missing initialization in `Indexer::new`.
  [#1160](https://github.com/rust-lang/git2-rs/pull/1160)

## 0.20.1 - 2025-03-17
[0.20.0...0.20.1](https://github.com/rust-lang/git2-rs/compare/git2-0.20.0...git2-0.20.1)

### Added

- Added `Repository::branch_upstream_merge()`
  [#1131](https://github.com/rust-lang/git2-rs/pull/1131)
- Added `Index::conflict_get()`
  [#1134](https://github.com/rust-lang/git2-rs/pull/1134)
- Added `Index::conflict_remove()`
  [#1133](https://github.com/rust-lang/git2-rs/pull/1133)
- Added `opts::set_cache_object_limit()`
  [#1118](https://github.com/rust-lang/git2-rs/pull/1118)
- Added `Repo::merge_file_from_index()` and associated `MergeFileOptions` and `MergeFileResult`.
  [#1062](https://github.com/rust-lang/git2-rs/pull/1062)

### Changed

- The `url` dependency minimum raised to 2.5.4
  [#1128](https://github.com/rust-lang/git2-rs/pull/1128)
- Changed the tracing callback to abort the process if the callback panics instead of randomly detecting the panic in some other function.
  [#1121](https://github.com/rust-lang/git2-rs/pull/1121)
- Credential helper config (loaded with `CredentialHelper::config`) now checks for helpers that start with something that looks like an absolute path, rather than checking for a `/` or `\` anywhere in the helper string (which resolves an issue if the helper had arguments with `/` or `\`).
  [#1137](https://github.com/rust-lang/git2-rs/pull/1137)

### Fixed

- Fixed panic in `Remote::url_bytes` if the url is empty.
  [#1120](https://github.com/rust-lang/git2-rs/pull/1120)
- Fixed incorrect lifetimes on `Patch::delta`, `Patch::hunk`, and `Patch::line_in_hunk`. The return values must not outlive the `Patch`.
  [#1141](https://github.com/rust-lang/git2-rs/pull/1141)
- Bumped requirement to libgit2-sys 0.18.1, which fixes linking of advapi32 on Windows.
  [#1143](https://github.com/rust-lang/git2-rs/pull/1143)


## 0.20.0 - 2025-01-04
[0.19.0...0.20.0](https://github.com/rust-lang/git2-rs/compare/git2-0.19.0...git2-0.20.0)

### Added

- `Debug` is now implemented for `transport::Service`
  [#1074](https://github.com/rust-lang/git2-rs/pull/1074)
- Added `Repository::commondir`
  [#1079](https://github.com/rust-lang/git2-rs/pull/1079)
- Added `Repository::merge_base_octopus`
  [#1088](https://github.com/rust-lang/git2-rs/pull/1088)
- Restored impls for `PartialOrd`, `Ord`, and `Hash` for bitflags types that were inadvertently removed in a prior release.
  [#1096](https://github.com/rust-lang/git2-rs/pull/1096)
- Added `CheckoutBuilder::disable_pathspec_match`
  [#1107](https://github.com/rust-lang/git2-rs/pull/1107)
- Added `PackBuilder::write`
  [#1110](https://github.com/rust-lang/git2-rs/pull/1110)

### Changed

- ❗ Updated to libgit2 [1.9.0](https://github.com/libgit2/libgit2/releases/tag/v1.9.0)
  [#1111](https://github.com/rust-lang/git2-rs/pull/1111)
- ❗ Removed the `ssh_key_from_memory` Cargo feature, it was unused.
  [#1087](https://github.com/rust-lang/git2-rs/pull/1087)
- ❗ Errors from `Tree::walk` are now correctly reported to the caller.
  [#1098](https://github.com/rust-lang/git2-rs/pull/1098)
- ❗ The `trace_set` callback now takes a `&[u8]` instead of a `&str`.
  [#1071](https://github.com/rust-lang/git2-rs/pull/1071)
- ❗ `Error::last_error` now returns `Error` instead of `Option<Error>`.
  [#1072](https://github.com/rust-lang/git2-rs/pull/1072)

### Fixed

- Fixed `OdbReader::read` return value.
  [#1061](https://github.com/rust-lang/git2-rs/pull/1061)
- When a credential helper executes a shell command, don't pop open a console window on Windows.
  [#1075](https://github.com/rust-lang/git2-rs/pull/1075)

## 0.19.0 - 2024-06-13
[0.18.3...0.19.0](https://github.com/rust-lang/git2-rs/compare/git2-0.18.3...git2-0.19.0)

### Added

- Added `opts` functions to control server timeouts (`get_server_connect_timeout_in_milliseconds`, `set_server_connect_timeout_in_milliseconds`, `get_server_timeout_in_milliseconds`, `set_server_timeout_in_milliseconds`), and add `ErrorCode::Timeout`.
  [#1052](https://github.com/rust-lang/git2-rs/pull/1052)

### Changed

- ❗ Updated to libgit2 [1.8.1](https://github.com/libgit2/libgit2/releases/tag/v1.8.1)
  [#1032](https://github.com/rust-lang/git2-rs/pull/1032)
- Reduced size of the `Error` struct.
  [#1053](https://github.com/rust-lang/git2-rs/pull/1053)

### Fixed

- Fixed some callbacks to relay the error from the callback to libgit2.
  [#1043](https://github.com/rust-lang/git2-rs/pull/1043)

## 0.18.3 - 2024-03-18
[0.18.2...0.18.3](https://github.com/rust-lang/git2-rs/compare/git2-0.18.2...git2-0.18.3)

### Added

- Added `opts::` functions to get / set libgit2 mwindow options
  [#1035](https://github.com/rust-lang/git2-rs/pull/1035)


### Changed

- Updated examples to use clap instead of structopt
  [#1007](https://github.com/rust-lang/git2-rs/pull/1007)

## 0.18.2 - 2024-02-06
[0.18.1...0.18.2](https://github.com/rust-lang/git2-rs/compare/git2-0.18.1...git2-0.18.2)

### Added

- Added `opts::set_ssl_cert_file` and `opts::set_ssl_cert_dir` for setting Certificate Authority file locations.
  [#997](https://github.com/rust-lang/git2-rs/pull/997)
- Added `TreeIter::nth` which makes jumping ahead in the iterator more efficient.
  [#1004](https://github.com/rust-lang/git2-rs/pull/1004)
- Added `Repository::find_commit_by_prefix` to find a commit by a shortened hash.
  [#1011](https://github.com/rust-lang/git2-rs/pull/1011)
- Added `Repository::find_tag_by_prefix` to find a tag by a shortened hash.
  [#1015](https://github.com/rust-lang/git2-rs/pull/1015)
- Added `Repository::find_object_by_prefix` to find an object by a shortened hash.
  [#1014](https://github.com/rust-lang/git2-rs/pull/1014)

### Changed

- ❗ Updated to libgit2 [1.7.2](https://github.com/libgit2/libgit2/releases/tag/v1.7.2).
  This fixes [CVE-2024-24575](https://github.com/libgit2/libgit2/security/advisories/GHSA-54mf-x2rh-hq9v) and [CVE-2024-24577](https://github.com/libgit2/libgit2/security/advisories/GHSA-j2v7-4f6v-gpg8).
  [#1017](https://github.com/rust-lang/git2-rs/pull/1017)

## 0.18.1 - 2023-09-20
[0.18.0...0.18.1](https://github.com/rust-lang/git2-rs/compare/git2-0.18.0...git2-0.18.1)

### Added

- Added `FetchOptions::depth` to set the depth of a fetch or clone, adding support for shallow clones.
  [#979](https://github.com/rust-lang/git2-rs/pull/979)

### Fixed

- Fixed an internal data type (`TreeWalkCbData`) to not assume it is a transparent type while casting.
  [#989](https://github.com/rust-lang/git2-rs/pull/989)
- Fixed so that `DiffPatchidOptions` and `StashSaveOptions` are publicly exported allowing the corresponding APIs to actually be used.
  [#988](https://github.com/rust-lang/git2-rs/pull/988)

## 0.18.0 - 2023-08-28
[0.17.2...0.18.0](https://github.com/rust-lang/git2-rs/compare/0.17.2...git2-0.18.0)

### Added

- Added `Blame::blame_buffer` for getting blame data for a file that has been modified in memory.
  [#981](https://github.com/rust-lang/git2-rs/pull/981)

### Changed

- Updated to libgit2 [1.7.0](https://github.com/libgit2/libgit2/releases/tag/v1.7.0).
  [#968](https://github.com/rust-lang/git2-rs/pull/968)
- Updated to libgit2 [1.7.1](https://github.com/libgit2/libgit2/releases/tag/v1.7.1).
  [#982](https://github.com/rust-lang/git2-rs/pull/982)
- Switched from bitflags 1.x to 2.1. This brings some small changes to types generated by bitflags.
  [#973](https://github.com/rust-lang/git2-rs/pull/973)
- Changed `Revwalk::with_hide_callback` to take a mutable reference to its callback to enforce type safety.
  [#970](https://github.com/rust-lang/git2-rs/pull/970)
- Implemented `FusedIterator` for many iterators that can support it.
  [#955](https://github.com/rust-lang/git2-rs/pull/955)

### Fixed

- Fixed builds with cargo's `-Zminimal-versions`.
  [#960](https://github.com/rust-lang/git2-rs/pull/960)

## 0.17.2 - 2023-05-27
[0.17.1...0.17.2](https://github.com/rust-lang/git2-rs/compare/0.17.1...0.17.2)

### Added
- Added support for stashing with options (which can support partial stashing).
  [#930](https://github.com/rust-lang/git2-rs/pull/930)

## 0.17.1 - 2023-04-13
[0.17.0...0.17.1](https://github.com/rust-lang/git2-rs/compare/0.17.0...0.17.1)

### Changed

- Updated to libgit2 [1.6.4](https://github.com/libgit2/libgit2/releases/tag/v1.6.4).
  [#948](https://github.com/rust-lang/git2-rs/pull/948)

## 0.17.0 - 2023-04-02
[0.16.1...0.17.0](https://github.com/rust-lang/git2-rs/compare/0.16.1...0.17.0)

### Added

- Added `IntoIterator` implementation for `Statuses`.
  [#880](https://github.com/rust-lang/git2-rs/pull/880)
- Added `Reference::symbolic_set_target`
  [#893](https://github.com/rust-lang/git2-rs/pull/893)
- Added `Copy`, `Clone`, `Debug`, `PartialEq`, and `Eq` implementations for `AutotagOption` and `FetchPrune`.
  [#889](https://github.com/rust-lang/git2-rs/pull/889)
- Added `Eq` and `PartialEq` implementations for `Signature`.
  [#890](https://github.com/rust-lang/git2-rs/pull/890)
- Added `Repository::discover_path`.
  [#883](https://github.com/rust-lang/git2-rs/pull/883)
- Added `Submodule::repo_init`.
  [#914](https://github.com/rust-lang/git2-rs/pull/914)
- Added `Tag::is_valid_name`.
  [#882](https://github.com/rust-lang/git2-rs/pull/882)
- Added `Repository::set_head_bytes`.
  [#931](https://github.com/rust-lang/git2-rs/pull/931)
- Added the `Indexer` type which is a low-level API for storing and indexing pack files.
  [#911](https://github.com/rust-lang/git2-rs/pull/911)
- Added `Index::find_prefix`.
  [#903](https://github.com/rust-lang/git2-rs/pull/903)
- Added support for the deprecated group-writeable blob mode. This adds a new variant to `FileMode`.
  [#887](https://github.com/rust-lang/git2-rs/pull/887)
- Added `PushCallbacks::push_negotiation` callback and the corresponding `PushUpdate` type for getting receiving information about the updates to perform.
  [#926](https://github.com/rust-lang/git2-rs/pull/926)

### Changed

- Updated to libgit2 [1.6.3](https://github.com/libgit2/libgit2/blob/main/docs/changelog.md#v163).
  This brings in many changes, including better SSH host key support on Windows and better SSH host key algorithm negotiation.
  1.6.3 is now the minimum supported version.
  [#935](https://github.com/rust-lang/git2-rs/pull/935)
- Updated libssh2-sys from 0.2 to 0.3.
  This brings in numerous changes, including SHA2 algorithm support with RSA.
  [#919](https://github.com/rust-lang/git2-rs/pull/919)
- Changed `RemoteCallbacks::credentials` callback error handler to correctly set the libgit2 error class.
  [#918](https://github.com/rust-lang/git2-rs/pull/918)
- `DiffOptions::flag` now takes a `git_diff_option_t` type.
  [#935](https://github.com/rust-lang/git2-rs/pull/935)


## 0.16.1 - 2023-01-20
[0.16.0...0.16.1](https://github.com/rust-lang/git2-rs/compare/0.16.0...0.16.1)

### Changed
- Updated to [libgit2-sys 0.14.2+1.5.1](libgit2-sys/CHANGELOG.md#0142151---2023-01-20)

## 0.16.0 - 2023-01-10
[0.15.0...0.16.0](https://github.com/rust-lang/git2-rs/compare/0.15.0...0.16.0)

### Changed
- Added ability to get the SSH host key and its type.
  This includes an API breaking change to the `certificate_check` callback.
  [#909](https://github.com/rust-lang/git2-rs/pull/909)
- Updated to [libgit2-sys 0.14.1+1.5.0](libgit2-sys/CHANGELOG.md#0141150---2023-01-10)

## 0.15.0 - 2022-07-28
[0.14.4...0.15.0](https://github.com/rust-lang/git2-rs/compare/0.14.4...0.15.0)

### Added
- Added `Repository::tag_annotation_create` binding `git_tag_annotation_create`.
  [#845](https://github.com/rust-lang/git2-rs/pull/845)
- Added the `Email` type which represents a patch in mbox format for sending via email.
  Added the `EmailCreateOptions` struct to control formatting of the email.
  Deprecates `Diff::format_email`, use `Email::from_diff` instead.
  [#847](https://github.com/rust-lang/git2-rs/pull/847)
- Added `ErrorCode::Owner` to map to the new `GIT_EOWNER` errors.
  [#839](https://github.com/rust-lang/git2-rs/pull/839)
- Added `opts::set_verify_owner_validation` to set whether or not ownership validation is performed.
  [#839](https://github.com/rust-lang/git2-rs/pull/839)

### Changed
- Updated to [libgit2-sys 0.14.0+1.5.0](libgit2-sys/CHANGELOG.md#0140150---2022-07-28)
- Removed the `Iterator` implementation for `ConfigEntries` due to the unsound usage of the API which allowed values to be used after free.
  Added `ConfigEntries::next` and `ConfigEntries::for_each` for iterating over all entries in a safe manor.
  [#854](https://github.com/rust-lang/git2-rs/pull/854)

## 0.14.4 - 2022-05-19
[0.14.3...0.14.4](https://github.com/rust-lang/git2-rs/compare/0.14.3...0.14.4)

### Added
- Added `Commit::body` and `Commit::body_bytes` for retrieving the commit message body.
  [#835](https://github.com/rust-lang/git2-rs/pull/835)
- Added `Tree::get_name_bytes` to handle non-UTF-8 entry names.
  [#841](https://github.com/rust-lang/git2-rs/pull/841)

### Changed
- Updated to [libgit2-sys 0.13.4+1.4.2](libgit2-sys/CHANGELOG.md#0134142---2022-05-10)

## 0.14.3 - 2022-04-27
[0.14.2...0.14.3](https://github.com/rust-lang/git2-rs/compare/0.14.2...0.14.3)

### Changed
- Updated to [libgit2-sys 0.13.3+1.4.2](libgit2-sys/CHANGELOG.md#0133142---2022-04-27)

### Fixed
- Fixed the lifetime of `Remote::create_detached`.
  [#825](https://github.com/rust-lang/git2-rs/pull/825)

## 0.14.2 - 2022-03-10
[0.14.1...0.14.2](https://github.com/rust-lang/git2-rs/compare/0.14.1...0.14.2)

### Added
- Added `Odb::exists_ext` to checks if an object database has an object, with extended flags.
  [#818](https://github.com/rust-lang/git2-rs/pull/818)

### Changed
- Updated to [libgit2-sys 0.13.2+1.4.2](libgit2-sys/CHANGELOG.md#0132142---2022-03-10)

## 0.14.1 - 2022-02-28
[0.14.0...0.14.1](https://github.com/rust-lang/git2-rs/compare/0.14.0...0.14.1)

### Changed
- Updated to [libgit2-sys 0.13.1+1.4.2](libgit2-sys/CHANGELOG.md#0131142---2022-02-28)

## 0.14.0 - 2022-02-24
[0.13.25...0.14.0](https://github.com/rust-lang/git2-rs/compare/0.13.25...0.14.0)

### Added
- Added `opts::get_extensions` and `opts::set_extensions` to support git extensions.
  [#791](https://github.com/rust-lang/git2-rs/pull/791)
- Added `PackBuilder::name` and `PackBuilder::name_bytes`.
  [#806](https://github.com/rust-lang/git2-rs/pull/806)
    - Deprecated `PackBuilder::hash`, use `PackBuilder::name` instead.
- Added `FetchOptions::follow_redirects` and `PushOptions::follow_redirects`.
  [#806](https://github.com/rust-lang/git2-rs/pull/806)
- Added `StatusOptions::rename_threshold`.
  [#806](https://github.com/rust-lang/git2-rs/pull/806)

### Changed
- Updated to [libgit2-sys 0.13.0+1.4.1](libgit2-sys/CHANGELOG.md#0130141---2022-02-24)
  [#806](https://github.com/rust-lang/git2-rs/pull/806)
  [#811](https://github.com/rust-lang/git2-rs/pull/811)
