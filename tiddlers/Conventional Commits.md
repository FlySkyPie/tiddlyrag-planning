> This document still in draft stage.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](<#RFC 2119>).

1.  Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, etc., followed by an OPTIONAL scope, and a REQUIRED terminal colon and space.
2.  The type `feat` MUST be used when a commit adds a new feature to your application or library.
3.  The type `fix` MUST be used when a commit represents a bug fix for your application.
4.  A scope MAY be provided after a type. A scope MUST consist of a noun describing a section of the codebase surrounded by parenthesis, e.g., `fix(parser):`
5.  A description MUST immediately follow the space after the type/scope prefix. The description is a short summary of the code changes, e.g., *fix: array parsing issue when multiple spaces were contained in string.*
6.  A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
7.  A footer of one or more lines MAY be provided one blank line after the body. The footer MUST contain meta-information about the commit, e.g., related pull-requests, reviewers, breaking changes, with one piece of meta-information per-line.
8.  Breaking changes MUST be indicated at the very beginning of the body section, or at the beginning of a line in the footer section. A breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon and a space.
9.  A description MUST be provided after the `BREAKING CHANGE:` , describing what has changed about the API, e.g., *BREAKING CHANGE: environment variables now take precedence over config files.*
10. Types other than `feat` and `fix` MAY be used in your commit messages.
11. The units of information that make up conventional commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
12. A `!` MAY be appended prior to the `:` in the type/scope prefix, to further draw attention to breaking changes. `BREAKING CHANGE: description` MUST also be included in the body or footer, along with the `!` in the prefix.