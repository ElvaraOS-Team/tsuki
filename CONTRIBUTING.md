# Contributing to tsuki

## Formatting

Please format the code using `cargo fmt`

## Building

Tsuki is built with cargo.

To build tsuki use:

```
cargo build
```

To run tsuki use:

```
cargo run -- <args>
```

Tsuki has a couple of feature flags which you may want to enable:

- backtrace: does nothing, kept around for backwards compatibility
- git: target the libalpm-git API
- generate: generate the libalpm bindings at build time (requires clang)

### Building Against a Custom libalpm

If you wish to build against a custom libalpm you can specify **ALPM_LIB_DIR** while using the generate
feature. Then running with **LD_LIBRARY_PATH** pointed at the custom libalpm.so.

## Testing

Tsuki's test suite can be run by running:

```
cargo test --features mock
```

## Translating

See https://github.com/Morganamilo/paru/discussions/433 for discussion on localization.
You probably want to subscribe to this to be notified when translations need to be updated.

### New Languages

When translating to a new language try to stick to languages pacman already supports:
https://gitlab.archlinux.org/pacman/pacman/-/tree/master/src/pacman/po. For example using
`es` over `es_ES`.

To translate tsuki to a new language, copy the the template .pot file to the locale you
are translating to.

For example, to translate tsuki to Japanese you would do:

```
cp po/tsuki.pot po/jp.po
```

Then fill out the template file with your information and translation.

Alternatively, you can use programs like `poedit` to write the translations.

### Updating existing translations

To update existing translations against new code you must first update the .po
files.

Do this as its own commit.

```
./scripts/updpo
git commit po
```

Then fill in new strings.

### Testing Translations

To test the translations you first must build the translation then run tsuki
pointing it at the generated files.

```
./scripts/mkmo locale/
LOCALE_DIR=locale/ cargo run -- <args>
```
