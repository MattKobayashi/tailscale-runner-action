# Changelog

## [1.2.2](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.2.1...v1.2.2) (2024-11-12)


### Bug Fixes

* **tailscale:** Improve connectivity check ([#37](https://github.com/MattKobayashi/tailscale-runner-action/issues/37)) ([530ed85](https://github.com/MattKobayashi/tailscale-runner-action/commit/530ed856312eccb58a417893bdfb4665aaf7eed2))

## [1.2.1](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.2.0...v1.2.1) (2024-11-12)


### Bug Fixes

* **tailscale:** Configurable check timeout ([#35](https://github.com/MattKobayashi/tailscale-runner-action/issues/35)) ([b771a39](https://github.com/MattKobayashi/tailscale-runner-action/commit/b771a393a87253f39b2f69abfb71b3214cc1f5d3))

## [1.2.0](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.6...v1.2.0) (2024-11-12)


### Features

* **action:** Add connectivity check ([#33](https://github.com/MattKobayashi/tailscale-runner-action/issues/33)) ([afb0d6c](https://github.com/MattKobayashi/tailscale-runner-action/commit/afb0d6c417b2c9e6b29ab7babb0206237d258c22))

## [1.1.6](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.5...v1.1.6) (2024-11-12)


### Bug Fixes

* **tailscale:** Bump to 1.76.6 ([#31](https://github.com/MattKobayashi/tailscale-runner-action/issues/31)) ([2d53000](https://github.com/MattKobayashi/tailscale-runner-action/commit/2d5300012c5adc5136fad76740a1bd81c5399606))

## [1.1.5](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.4...v1.1.5) (2024-10-15)


### Bug Fixes

* Bump default Tailscale version to 1.76.0 ([#25](https://github.com/MattKobayashi/tailscale-runner-action/issues/25)) ([a28f0b9](https://github.com/MattKobayashi/tailscale-runner-action/commit/a28f0b9d48bdd1fa221247aa18e87af154c218b0))

## [1.1.4](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.3...v1.1.4) (2024-10-15)


### Bug Fixes

* Don't error when ~/.ssh directory exists ([#23](https://github.com/MattKobayashi/tailscale-runner-action/issues/23)) ([b312c64](https://github.com/MattKobayashi/tailscale-runner-action/commit/b312c6452f8930293dfc7a310ae8a72ee56dab1d))

## [1.1.3](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.2...v1.1.3) (2024-10-08)


### Bug Fixes

* Add `ssh-keyscan-timeout` to README ([#22](https://github.com/MattKobayashi/tailscale-runner-action/issues/22)) ([a566824](https://github.com/MattKobayashi/tailscale-runner-action/commit/a56682459cb80c26eaa7e3b7b75926de36257fa9))
* Make `ssh-keyscan` timeout value configurable ([#20](https://github.com/MattKobayashi/tailscale-runner-action/issues/20)) ([32b77f1](https://github.com/MattKobayashi/tailscale-runner-action/commit/32b77f16912718f98c5f87c2d549ddc639d07cee))

## [1.1.2](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.1...v1.1.2) (2024-10-08)


### Bug Fixes

* Increase `ssh-keyscan` timeout ([#16](https://github.com/MattKobayashi/tailscale-runner-action/issues/16)) ([03df381](https://github.com/MattKobayashi/tailscale-runner-action/commit/03df381b4e63be556f079739e1889ef6861d0481))

## [1.1.1](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.1.0...v1.1.1) (2024-10-04)


### Bug Fixes

* Pin `docker-github-actions-runner`container version ([d1e1546](https://github.com/MattKobayashi/tailscale-runner-action/commit/d1e1546ebbb76fb9e255d28f71c54750527b5e6c))

## [1.1.0](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.0.2...v1.1.0) (2024-09-29)


### Features

* Use `ssh-keyscan` ([#13](https://github.com/MattKobayashi/tailscale-runner-action/issues/13)) ([64677ed](https://github.com/MattKobayashi/tailscale-runner-action/commit/64677edd1e06094de35e38ddc2ba0f22d94148b1))

## [1.0.2](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.0.1...v1.0.2) (2024-09-28)


### Bug Fixes

* Make Tailscale node tag configurable ([#7](https://github.com/MattKobayashi/tailscale-runner-action/issues/7)) ([2d03511](https://github.com/MattKobayashi/tailscale-runner-action/commit/2d035113e1388d2968258bd519fa29d32a17ec9b))

## [1.0.1](https://github.com/MattKobayashi/tailscale-runner-action/compare/v1.0.0...v1.0.1) (2024-09-28)


### Bug Fixes

* Add color label ([#5](https://github.com/MattKobayashi/tailscale-runner-action/issues/5)) ([9d0b8af](https://github.com/MattKobayashi/tailscale-runner-action/commit/9d0b8af39ccfa2b4a253f6c56beeb37f91c8317a))

## 1.0.0 (2024-09-28)


### ⚠ BREAKING CHANGES

* Initial commit

### Features

* Initial commit ([82b021a](https://github.com/MattKobayashi/tailscale-runner-action/commit/82b021abd08c046522087d7e1af3eb7c95168058))


### Bug Fixes

* Define action as composite ([#4](https://github.com/MattKobayashi/tailscale-runner-action/issues/4)) ([48c622b](https://github.com/MattKobayashi/tailscale-runner-action/commit/48c622b9ebc9a4ba0e5b94d7a78c267a64dcad72))
* YAML error ([#3](https://github.com/MattKobayashi/tailscale-runner-action/issues/3)) ([d95ceeb](https://github.com/MattKobayashi/tailscale-runner-action/commit/d95ceeb8333d71afebff957c6d6b462476492cfd))
