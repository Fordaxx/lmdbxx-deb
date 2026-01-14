# liblmdbxx-dev — Debian Package

Debian packaging for lmdb++ — a comprehensive C++17 header-only wrapper for LMDB (Lightning Memory-Mapped Database).

## About lmdb++

- **Header-only C++17** wrapper for the LMDB embedded database
- **Modern C++ idioms**: RAII, std::string_view support, exception handling
- **Zero overhead**: thin wrapper around the C API
- **Fork of**: original lmdbxx by Arto Bendiken, maintained by Doug Hoyte
- **Public Domain** (Unlicense)

**Upstream**: [https://github.com/hoytech/lmdbxx](https://github.com/hoytech/lmdbxx)

## Quick Start

### Installing

```bash
sudo dpkg -i liblmdbxx-dev_*.deb
sudo apt-get install -f
```

### Building from source

```bash
sudo apt-get install debhelper-compat build-essential dpkg-dev liblmdb-dev
dpkg-source -x liblmdbxx_*.dsc
cd liblmdbxx-*/
dpkg-buildpackage -b -us -uc
sudo dpkg -i ../liblmdbxx-dev_*.deb
```

## Package Information

| Field | Value |
|-------|-------|
| **Package** | liblmdbxx-dev |
| **Version** | 1.0.0-1 |
| **Section** | libdevel |
| **Architecture** | all (header-only) |
| **Multi-Arch** | foreign |
| **Maintainer** | Ruslan Dautov |
| **Build-Depends** | debhelper-compat (= 13) |
| **Depends** | liblmdb-dev (>= 0.9.18) |

## Debian Packaging Files

```
debian/
├── changelog          # Version history (1.0.0-1)
├── control            # Package metadata and dependencies
├── copyright          # Unlicense + Apache-2.0 for debian/
├── rules              # Build instructions
├── source/format      # 3.0 (quilt)
├── watch              # GitHub upstream release tracking
└── tests/
    ├── control              # Autopkgtest configuration
    ├── installation-test    # Verify header installed
    ├── compilation-test     # Test compilation with liblmdb
    └── string-view-test     # std::string_view functionality test
```

## Autopkgtest

Package includes comprehensive test suite:

```bash
autopkgtest liblmdbxx-dev_*.deb -- null
```

Tests verify:
- Header file installation (`installation-test`)
- Compilation with liblmdb (`compilation-test`)
- std::string_view support (`string-view-test`)


## Contributing

1. Fork repository
2. Modify `debian/` directory
3. Update `debian/changelog` with `dch`
4. Test with `dpkg-buildpackage -b -us -uc`
5. Run `lintian` on resulting `.changes` file
6. Submit pull request

## License

- **Upstream**: Unlicense (Public Domain)
- **Debian packaging**: Apache License 2.0
- See `debian/copyright` for full details

## Support

- **Packaging issues**: [https://github.com/Fordaxx/lmdbxx-deb/issues](https://github.com/Fordaxx/lmdbxx-deb/issues)
- **Library issues**: [https://github.com/hoytech/lmdbxx/issues](https://github.com/hoytech/lmdbxx/issues)

---

**Maintainer**: Ruslan Dautov <r.dautoff2016@yandex.ru>
