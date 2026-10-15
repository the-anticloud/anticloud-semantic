# SEMANTIC

> Anticloud offline package — upstream: github/semantic @ `main`.

## What This Project Does

Parsing, analyzing, and comparing source code across many languages

**Topics:** keep

## Upstream README

**NOTE**: _This repository is no longer supported or updated by GitHub. If you wish to continue to develop this code yourself, we recommend you fork it._

# Semantic

`semantic` is a Haskell library and command line tool for parsing, analyzing, and comparing source code.

In a hurry? Check out our documentation of [example uses for the `semantic` command line tool](docs/examples.md).

| Table of Contents |
| :------------- |
| [Usage](#usage) |
| [Language support](#language-support) |
| [Development](#development) |
| [Technology and architecture](#technology-and-architecture) |
| [Licensing](#licensing) |

## Usage

Run `semantic --help` for complete list of up-to-date options.

#### Parse
```
Usage: semantic parse [--sexpression | (--json-symbols|--symbols) |
                        --proto-symbols | --show | --quiet] [FILES...]
  Generate parse trees for path(s)

Available options:
  --sexpression            Output s-expression parse trees (default)
  --json-symbols,--symbols Output JSON symbol list
  --proto-symbols          Output protobufs symbol list
  --show                   Output using the Show instance (debug only, format
                           subject to change without notice)
  --quiet                  Don't produce output, but show timing stats
  -h,--help                Show this help text
   ```

## Language support

| Language       | Parse | AST Symbols† | Stack graphs |
| :------------- | :---: | :---:        | :---:        |
| Ruby           | ✅    | ✅           | |
| JavaScript     | ✅    | ✅           | |
| TypeScript     | ✅    | ✅           | 🚧 |
| Python         | ✅    | ✅           | 🚧 |
| Go             | ✅    | ✅           | |
| PHP            | ✅    | ✅           | |
| Java           | 🚧    | ✅           | |
| JSON           | ✅    | ⬜️           | ⬜️ |
| JSX            | ✅    | ✅           | |
| TSX            | ✅    | ✅           | |
| CodeQL         | ✅    | ✅           | |
| Haskell        | 🚧    | 🚧           | |

† Used for [code navigation](https://help.github.com/en/github/managing-files-in-a-repository/navigating-code-on-github) on github.com.
* ✅ — Supported
* 🔶 — Partial support
* 🚧 — Under development
* ⬜ - N/A ️


## Development

`semantic` requires at least GHC 8.10.1 and Cabal 3.0. We strongly recommend using [`ghcup`][ghcup] to sandbox GHC versions, as GHC packages installed through your OS's package manager may not install statically-linked versions of the GHC boot libraries. `semantic` currently builds only on Unix systems; users of other operating systems may wish to use the [Docker images](https://github.com/github/semantic/packages/11609).

We use `cabal's` [Nix-style local builds][nix] for development. To get started quickly:

```bash
git clone git@github.com:github/semantic.git
cd semantic
script/bootstrap
cabal v2-build all
cabal v2-run semantic:test
cabal v2-run semantic:semantic -- --help
```

You can also use the [Bazel](https://bazel.build) build system for development. To learn more 

## License

Upstream terms preserved in `THIRD_PARTY_LICENSES/`. Overlay licensed under Anticommons 0.1.0.

## Verification

Recompute the SHA3-256 of `BENCH.json` and compare to this package’s register. Any drift = invalid package.
