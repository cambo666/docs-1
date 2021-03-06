# Changelog

Ark Core (`v2.0.X`) is a complete redesign, deprecating all APIs and internal structure. The official changelog of `v2.1` is hosted in the [core repository](https://github.com/ArkEcosystem/core/blob/develop/CHANGELOG.md#changelog).

## [2.0.19] - 2019-01-31

### Fixed

-   https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-009.md
-   https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-010.md

## [2.0.18] - 2019-01-28

### Fixed

-   https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-011.md

## [2.0.17] - 2019-01-15

### Fixed

-   https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-008.md
-   https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-007.md

## [2.0.16] - 2018-12-17

### Fixed

-   Prevent the list of peers from becoming too short. This is related to the nodes running behind a firewall.

Closed security vulnerabilities:

-   [CORE-SV-004](https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-004.md)
-   [CORE-SV-003](https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-003.md)
-   [CORE-SV-002](https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-002.md)
-   [CORE-SV-001](https://github.com/ArkEcosystem/security-vulnerabilities/blob/master/core/core-sv-001.md)

## [2.0.15] - 2018-12-11

### Fixed

-   Ensure no local peers are enlisted and that the IP of the TCP connection is used ([#1695])

## [2.0.14] - 2018-12-10

### Fixed

-   Reset last downloaded block when the block is discarded ([#1692])

## [2.0.13] - 2018-12-07

### Fixed

-   Ensure safe integer range for block height lookups via API ([#1673])

## [2.0.12] - 2018-12-06

### Fixed

-   Perform second-signature checks in the `canApply` logic of multi-signatures ([#1658])
-   return the encoded WIF for BIP38 wallets instead of the encrypted WIF ([#1653])

## [2.0.11] - 2018-12-05

### Added

-   Store executed migrations in the database ([#1648])

### Changed

-   Increase cache generation timeout and make it configurable ([#1645], [#1646])

## [2.0.1] - 2018-12-05

### Added

-   Retrieve blocks via height or ID per public API ([#1626])

### Changed

-   Improved performance for block and transaction queries by adding more indices on critical columns ([#1636], [#1638], [#1634])

### Fixed

-   Take milestones into account for supply calculations ([#1640])
-   Use the raw transaction data in `acceptChainedBlock` to avoid timestamp mismatches and second signature double spend errors ([#1564])
-   Return the correct peer count for the v2 public API ([#1563])

## [2.0.0] - 2018-12-03

-   Initial Release

[unreleased]: https://github.com/ArkEcosystem/core/compare/2.0.19...develop
[2.1.0]: https://github.com/ArkEcosystem/core/compare/2.0.19...2.1.0
[2.0.19]: https://github.com/ArkEcosystem/core/compare/2.0.18...2.0.19
[2.0.18]: https://github.com/ArkEcosystem/core/compare/2.0.17...2.0.18
[2.0.17]: https://github.com/ArkEcosystem/core/compare/2.0.16...2.0.17
[2.0.16]: https://github.com/ArkEcosystem/core/compare/2.0.15...2.0.16
[2.0.15]: https://github.com/ArkEcosystem/core/compare/2.0.14...2.0.15
[2.0.14]: https://github.com/ArkEcosystem/core/compare/2.0.13...2.0.14
[2.0.13]: https://github.com/ArkEcosystem/core/compare/2.0.12...2.0.13
[2.0.12]: https://github.com/ArkEcosystem/core/compare/2.0.11...2.0.12
[2.0.11]: https://github.com/ArkEcosystem/core/compare/2.0.1...2.0.11
[2.0.1]: https://github.com/ArkEcosystem/core/compare/2.0.0...2.0.1
[2.0.0]: https://github.com/ArkEcosystem/core/compare/0.1.1...2.0.0
[#1563]: https://github.com/ArkEcosystem/core/pull/1563
[#1564]: https://github.com/ArkEcosystem/core/pull/1564
[#1625]: https://github.com/ArkEcosystem/core/pull/1625
[#1626]: https://github.com/ArkEcosystem/core/pull/1626
[#1634]: https://github.com/ArkEcosystem/core/pull/1634
[#1636]: https://github.com/ArkEcosystem/core/pull/1636
[#1638]: https://github.com/ArkEcosystem/core/pull/1638
[#1638]: https://github.com/ArkEcosystem/core/pull/1638
[#1640]: https://github.com/ArkEcosystem/core/pull/1640
[#1645]: https://github.com/ArkEcosystem/core/pull/1645
[#1646]: https://github.com/ArkEcosystem/core/pull/1646
[#1648]: https://github.com/ArkEcosystem/core/pull/1648
[#1653]: https://github.com/ArkEcosystem/core/pull/1653
[#1655]: https://github.com/ArkEcosystem/core/pull/1655
[#1658]: https://github.com/ArkEcosystem/core/pull/1658
[#1673]: https://github.com/ArkEcosystem/core/pull/1673
[#1689]: https://github.com/ArkEcosystem/core/pull/1689
[#1692]: https://github.com/ArkEcosystem/core/pull/1692
[#1695]: https://github.com/ArkEcosystem/core/pull/1695
[#1717]: https://github.com/ArkEcosystem/core/pull/1717
[#1730]: https://github.com/ArkEcosystem/core/pull/1730
[#1731]: https://github.com/ArkEcosystem/core/pull/1731
[#1732]: https://github.com/ArkEcosystem/core/pull/1732
[#1733]: https://github.com/ArkEcosystem/core/pull/1733
[#1738]: https://github.com/ArkEcosystem/core/pull/1738
[#1831]: https://github.com/ArkEcosystem/core/pull/1831
[#1833]: https://github.com/ArkEcosystem/core/pull/1833
[#1836]: https://github.com/ArkEcosystem/core/pull/1836
[#1837]: https://github.com/ArkEcosystem/core/pull/1837
[#1853]: https://github.com/ArkEcosystem/core/pull/1853
[#1869]: https://github.com/ArkEcosystem/core/pull/1869
[#1873]: https://github.com/ArkEcosystem/core/pull/1873
[#1887]: https://github.com/ArkEcosystem/core/pull/1887
[#1891]: https://github.com/ArkEcosystem/core/pull/1891
[#1898]: https://github.com/ArkEcosystem/core/pull/1898
[#1901]: https://github.com/ArkEcosystem/core/pull/1901
[#1905]: https://github.com/ArkEcosystem/core/pull/1905
[#1906]: https://github.com/ArkEcosystem/core/pull/1906
[#1911]: https://github.com/ArkEcosystem/core/pull/1911
[#1917]: https://github.com/ArkEcosystem/core/pull/1917
[#1919]: https://github.com/ArkEcosystem/core/pull/1919
[#1924]: https://github.com/ArkEcosystem/core/pull/1924
[#1926]: https://github.com/ArkEcosystem/core/pull/1926
[#1927]: https://github.com/ArkEcosystem/core/pull/1927
[#1930]: https://github.com/ArkEcosystem/core/pull/1930
[#1931]: https://github.com/ArkEcosystem/core/pull/1931
[#1939]: https://github.com/ArkEcosystem/core/pull/1939
[#1940]: https://github.com/ArkEcosystem/core/pull/1940
[#1941]: https://github.com/ArkEcosystem/core/pull/1941
[#1943]: https://github.com/ArkEcosystem/core/pull/1943
[#1947]: https://github.com/ArkEcosystem/core/pull/1947
[#1948]: https://github.com/ArkEcosystem/core/pull/1948
[#1953]: https://github.com/ArkEcosystem/core/pull/1953
[#1954]: https://github.com/ArkEcosystem/core/pull/1954
[#1955]: https://github.com/ArkEcosystem/core/pull/1955
[#1957]: https://github.com/ArkEcosystem/core/pull/1957
[#1969]: https://github.com/ArkEcosystem/core/pull/1969
[#1970]: https://github.com/ArkEcosystem/core/pull/1970
[#1985]: https://github.com/ArkEcosystem/core/pull/1985
[#1987]: https://github.com/ArkEcosystem/core/pull/1987
[#1996]: https://github.com/ArkEcosystem/core/pull/1996
[#1999]: https://github.com/ArkEcosystem/core/pull/1999
[#2009]: https://github.com/ArkEcosystem/core/pull/2009
[#2016]: https://github.com/ArkEcosystem/core/pull/2016
[#2021]: https://github.com/ArkEcosystem/core/pull/2021
[#2038]: https://github.com/ArkEcosystem/core/pull/2038
[#2044]: https://github.com/ArkEcosystem/core/pull/2044
[#2045]: https://github.com/ArkEcosystem/core/pull/2045
[#2046]: https://github.com/ArkEcosystem/core/pull/2046
[#2047]: https://github.com/ArkEcosystem/core/pull/2047
[#2049]: https://github.com/ArkEcosystem/core/pull/2049
[#2050]: https://github.com/ArkEcosystem/core/pull/2050
[#2051]: https://github.com/ArkEcosystem/core/pull/2051
[#2052]: https://github.com/ArkEcosystem/core/pull/2052
[#2053]: https://github.com/ArkEcosystem/core/pull/2053
[#2057]: https://github.com/ArkEcosystem/core/pull/2057
[#2058]: https://github.com/ArkEcosystem/core/pull/2058
[#2061]: https://github.com/ArkEcosystem/core/pull/2061
