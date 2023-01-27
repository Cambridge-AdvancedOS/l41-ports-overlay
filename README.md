# L41 Ports Overlay

This repository includes ports for packages used in L41 that do not have ports available in upstream yet.

## Package building

In order to build a package, you need a FreeBSD ports branch corresponding to a FreeBSD version used in [l41-freebsd](https://github.com/Cambridge-AdvancedOS/l41-freebsd) and [l41-image](https://github.com/Cambridge-AdvancedOS/l41-image), and this repository.

As of the 2022-2023 L41 course edition, the [release/13.1.0](https://github.com/freebsd/freebsd-ports/tree/release/13.1.0) FreeBSD port tag should be used that corresponds to the [l41-2021-2022-stable/13](https://github.com/Cambridge-AdvancedOS/l41-freebsd/tree/l41-2021-2022-stable/13) l41-freebsd branch (based on [stable/13](https://github.com/freebsd/freebsd-src/tree/0b12cc411b46d5fa9569b46c8ff512f316d1b8a1) that also was used for [releng/13.1](https://github.com/freebsd/freebsd-src/tree/releng/13.1)).

The following commands can be used to build a package. After the build, the package should be available in `l41-ports-overlay/path/to/port/work*/pkg/`.

```
$ git clone --branch release/13.1.0 https://github.com/freebsd/freebsd-ports.git
$ git clone https://github.com/Cambridge-AdvancedOS/l41-ports-overlay.git
$ env PORTSIDR=`realpath freebsd-ports` make -C l41-ports-overlay/path/to/port package
```

The package should be added to the [advopsys-packages](https://github.com/Cambridge-AdvancedOS/advopsys-packages/) repository in a directory `packages/All/` within a branch corresponding to the current course edition. Additionally, `packagify.sh` must be modified to install an additional package if it's not a dependency of a package that is already listed in that file.
