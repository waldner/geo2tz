<a name="unreleased"></a>
## [3.0.0](https://github.com/waldner/geo2tz/compare/v2.1.4...v3.0.0) (2024-06-09)


### ⚠ BREAKING CHANGES

* the boltdb options are not available anymore, only the in-memory db is supported

### Features

* add authorization support ([4a9c0b0](https://github.com/waldner/geo2tz/commit/4a9c0b06161af9bf4ed7fb1c38840966f192cb8a))
* add script to update tzdata ([67d34db](https://github.com/waldner/geo2tz/commit/67d34dbc7f78910530ae3a9c354b8f527ee259da))
* add support for memory shapefile ([56aa7b1](https://github.com/waldner/geo2tz/commit/56aa7b18288778cbb7357c97554ae29695fad2aa))
* add support for memory shapefile ([30468a9](https://github.com/waldner/geo2tz/commit/30468a914a9c8ef634806e6e6626dbe2158e7982))
* **data:** update tz source to 2021c version ([7610d7e](https://github.com/waldner/geo2tz/commit/7610d7e53b45a639de41211f50d0755b2d897622))
* first commit ([9fe6d03](https://github.com/waldner/geo2tz/commit/9fe6d03f0ad1fc8d3bda822456a50d8c20018e0c))
* remove support for boltdb ([efa6545](https://github.com/waldner/geo2tz/commit/efa6545a72aa600acf8f95dbd5fd5c881efba31b))
* update tzdata to 2023b ([43f9260](https://github.com/waldner/geo2tz/commit/43f9260affdd4a9c1907f68592b4138d3e665fc3))
* update tzdata to v2020d ([009ffd5](https://github.com/waldner/geo2tz/commit/009ffd5c6445f24042774e97f7e82766b69806f3))


### Bug Fixes

* **build:** the docker image is broken ([4cf592b](https://github.com/waldner/geo2tz/commit/4cf592bd09b85f69248b2e5b1f04af1ee53cca83))
* **ci:** install linter in CI ([5106c41](https://github.com/waldner/geo2tz/commit/5106c413f36b31264e2c56b371321a739003a08f))
* **deepsource:** add error handling ([e97a79e](https://github.com/waldner/geo2tz/commit/e97a79e2deabb4d419f85877b5e2b7db6c15ec07))
* **deepsource:** simplify comparison ([1d0b067](https://github.com/waldner/geo2tz/commit/1d0b067a8d991ef1cfb017861d559714695a5284))
* docker image won't build ([f13e809](https://github.com/waldner/geo2tz/commit/f13e80991a92ea5e1208ae2466c39272446f348b))
* docker-image and release process fix ([ae3e690](https://github.com/waldner/geo2tz/commit/ae3e6908c5593e428bf071b581318a27ab1b4546))
* error detecting non-existing files ([992a2ea](https://github.com/waldner/geo2tz/commit/992a2ea6966b0a93761a48c3b99c3388909e01a4))
* go mod tidy ([e05128e](https://github.com/waldner/geo2tz/commit/e05128ee1ad916d393ee8e3e0f5d6bbdd2041b35))
* invalid docker build ([12d5d0d](https://github.com/waldner/geo2tz/commit/12d5d0d2790ee8dc64b0c4b9901ca9b04b25795b))
* linter warnings ([23ef1ca](https://github.com/waldner/geo2tz/commit/23ef1caa4c61d7994af3e1850f678d9899943843))
* release workflow ([3658395](https://github.com/waldner/geo2tz/commit/3658395c33531db79404eb87ee59515433b22458))
* **security:** update dependencies ([33fed50](https://github.com/waldner/geo2tz/commit/33fed50b189893d7d06bbba5cd442f58afa93813))

## [2.1.4](https://github.com/noandrea/geo2tz/compare/v2.1.3...v2.1.4) (2023-06-23)


### Bug Fixes

* invalid docker build ([12d5d0d](https://github.com/noandrea/geo2tz/commit/12d5d0d2790ee8dc64b0c4b9901ca9b04b25795b))

## [2.1.3](https://github.com/noandrea/geo2tz/compare/v2.1.2...v2.1.3) (2023-06-23)


### Bug Fixes

* docker image won't build ([f13e809](https://github.com/noandrea/geo2tz/commit/f13e80991a92ea5e1208ae2466c39272446f348b))

## [2.1.2](https://github.com/noandrea/geo2tz/compare/v2.1.1...v2.1.2) (2023-06-23)


### Bug Fixes

* **build:** the docker image is broken ([4cf592b](https://github.com/noandrea/geo2tz/commit/4cf592bd09b85f69248b2e5b1f04af1ee53cca83))

## [2.1.1](https://github.com/noandrea/geo2tz/compare/v2.1.0...v2.1.1) (2023-06-23)


### Bug Fixes

* release workflow ([3658395](https://github.com/noandrea/geo2tz/commit/3658395c33531db79404eb87ee59515433b22458))

## [2.1.0](https://github.com/noandrea/geo2tz/compare/v2.0.0...v2.1.0) (2023-06-23)


### Features

* add script to update tzdata ([67d34db](https://github.com/noandrea/geo2tz/commit/67d34dbc7f78910530ae3a9c354b8f527ee259da))
* update tzdata to 2023b ([43f9260](https://github.com/noandrea/geo2tz/commit/43f9260affdd4a9c1907f68592b4138d3e665fc3))


### Bug Fixes

* error detecting non-existing files ([992a2ea](https://github.com/noandrea/geo2tz/commit/992a2ea6966b0a93761a48c3b99c3388909e01a4))
* **security:** update dependencies ([33fed50](https://github.com/noandrea/geo2tz/commit/33fed50b189893d7d06bbba5cd442f58afa93813))

## [Unreleased]


<a name="v2.0.0"></a>
## [v2.0.0] - 2022-07-31
### Chore
- improve readme, remove unused deps, improve logging
- update dependencies and go to v1.18

### Feat
- remove support for boltdb
- **data:** update tz source to 2021c version

### Test
- improve test coverage

### BREAKING CHANGE

the boltdb options are not available anymore, only the
in-memory db is supported


<a name="v1.0.0"></a>
## [v1.0.0] - 2021-11-28
### Chore
- upgrade go version and dependencies

### Docs
- update docs

### Feat
- use in memory db instead of bolt
- add server request rate limit


<a name="v0.4.2"></a>
## [v0.4.2] - 2021-09-13
### Build
- add multiple automated build options for docker


<a name="0.4.1"></a>
## [0.4.1] - 2021-09-13
### Build
- publish image on release

### Docs
- update docker image url

### Fix
- go mod tidy


<a name="0.4.0"></a>
## [0.4.0] - 2021-09-13
### Feat
- add support for memory shapefile
- add support for memory shapefile

### Fix
- **ci:** install linter in CI


<a name="0.3.1"></a>
## [0.3.1] - 2020-11-16
### Fix
- docker-image and release process fix


<a name="0.3.0"></a>
## [0.3.0] - 2020-11-16
### Chore
- move to github packages (from docker hub)
- set go version to 1.15

### Feat
- update tzdata to v2020d

### Fix
- linter warnings

### Misc
- hide echo startup banner


<a name="0.2.2"></a>
## [0.2.2] - 2020-06-29
### Build
- add deepsource, move to noandrea org on docker hub

### Fix
- **deepsource:** add error handling
- **deepsource:** simplify comparison


<a name="0.2.1"></a>
## [0.2.1] - 2020-05-17
### Doc
- fix README


<a name="0.2.0"></a>
## [0.2.0] - 2020-05-17
### Feat
- add authorization support


<a name="0.1.0"></a>
## [0.1.0] - 2020-05-06

<a name="0.0.0"></a>
## 0.0.0 - 2020-05-06
### Build
- add changelog support
- better integration with docker-hub
- fix issue with linting
- add travis config
- add dockeringore and gitignore

### Doc
- minor fixes in documentation
- add details in readme
- fix badges URLs
- add readme

### Feat
- first commit

### Test
- add tests for coordinate parsing


[Unreleased]: https://github.com/noandrea/geo2tz/compare/v2.0.0...HEAD
[v2.0.0]: https://github.com/noandrea/geo2tz/compare/v1.0.0...v2.0.0
[v1.0.0]: https://github.com/noandrea/geo2tz/compare/v0.4.2...v1.0.0
[v0.4.2]: https://github.com/noandrea/geo2tz/compare/0.4.1...v0.4.2
[0.4.1]: https://github.com/noandrea/geo2tz/compare/0.4.0...0.4.1
[0.4.0]: https://github.com/noandrea/geo2tz/compare/0.3.1...0.4.0
[0.3.1]: https://github.com/noandrea/geo2tz/compare/0.3.0...0.3.1
[0.3.0]: https://github.com/noandrea/geo2tz/compare/0.2.2...0.3.0
[0.2.2]: https://github.com/noandrea/geo2tz/compare/0.2.1...0.2.2
[0.2.1]: https://github.com/noandrea/geo2tz/compare/0.2.0...0.2.1
[0.2.0]: https://github.com/noandrea/geo2tz/compare/0.1.0...0.2.0
[0.1.0]: https://github.com/noandrea/geo2tz/compare/0.0.0...0.1.0
