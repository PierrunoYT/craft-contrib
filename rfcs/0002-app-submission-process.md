# RFC-0001: Proposing a new app

Builds on [RFC-0000](https://github.com/storytold/craft-contrib/pull/1), under
which adding or removing an app is an RFC with a 7-day comment period. This
RFC says what such an RFC contains, how maintainers judge it, and what
happens once it merges.

## Why

New-app ideas arrive as feature requests scattered across repos
(storytold/artcraft#2193, storytold/artcraft#2214, storytold/craft-launcher#348),
and there is an open argument for adding no apps for now
(storytold/artcraft#1999). There is no single place to propose an app, no
shared bar for accepting one, and so no clear answer for the people asking.

## Ideas

Anyone can open an issue here with the `app-idea` label to gauge interest.
An idea is not a commitment; it becomes a proposal when someone writes the RFC.
App requests filed in other repos can be pointed here.

## The RFC

A PR adding `rfcs/NNNN-app-<id>.md` with these sections:

- **Name and id.** Display name (`ExampleCraft`) and machine id (`examplecraft`),
  used as repo, binary, package and asset stem, and in `ai.storyteller.<id>`.
- **What it is.** Who it is for, and the familiar app it is like, if any.
- **Fit.** Why it is its own app and not a feature or mode of an existing one.
  Say how it overlaps the current apps.
- **First release.** The smallest version worth shipping, and what is left out.
- **Shared code.** Which `craft-libs` crates it would use, and what it would
  add or need there.
- **Clean room.** How it stays clean-room: no code, assets or documentation
  copied from the product it resembles, and its trademarks used only to
  describe what the app is like.
- **Maintainers.** At least one named person who will triage issues and review
  PRs for it. An app without a maintainer is not added.
- **Prototype** (optional, encouraged). A link to a working repo.

## How maintainers judge it

- It fits the suite: a desktop creative or productivity app in Rust that can
  ship on the platforms the launcher supports.
- It does not overlap an existing app so much that it belongs inside it.
- It has a maintainer.
- It does not take review time the existing apps need. A maintainer may object
  on capacity grounds alone, and says what would resolve the objection
  (for example: after a named app reaches a release, or with a second maintainer).

## After it merges

An owner creates `storytold/<id>`, or transfers the prototype repo there. Then:

- CI and releases use `craft-common-actions`, with release assets named by `<id>`.
- The app joins the `craft-launcher` catalog as a `New` app, with its colours,
  icon and screenshots in `craft-launcher-assets`.
- The repo gets a README and the shared contributor and agent guidelines,
  once those are decided.
- Releases are marked preview until a maintainer says otherwise on the repo.

## Open questions

- Should ideas live as issues here, as GitHub Discussions, or stay where they are filed?
- Should a working prototype be required before an RFC?
- How long a commitment should a maintainer make, and what happens when
  an app loses its last maintainer? (That would also be a 7-day RFC under RFC-0000.)
- Should new apps pause until the existing ones reach some bar (storytold/artcraft#1999)?
- Where is the line between a new app and an extension of an existing one
  (storytold/artcraft#2214)?
