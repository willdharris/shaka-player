# Changelog

## [5.0.0](https://github.com/willdharris/shaka-player/compare/v4.3.0...v5.0.0) (2023-02-23)


### ⚠ BREAKING CHANGES

* Remove small/large gap config, always jump gaps ([#4125](https://github.com/willdharris/shaka-player/issues/4125))
* **config:** `manifest.dash.defaultPresentationDelay` has been replaced by `manifest.defaultPresentationDelay` (deprecated in v3.0.0)
* **config:** Configuration of factories should be plain factory functions, not constructors; these will not be invoked with `new` (deprecated in v3.1.0)
* **player:** `shaka.Player.prototype.addTextTrack()` has been replaced by `addTextTrackAsync()`, which returns a `Promise` (deprecated in v3.1.0)
* **ui:** `shaka.ui.TrackLabelFormat` has been renamed to `shaka.ui.Overlay.TrackLabelFormat` (deprecated in v3.1.0)
* **ui:** `shaka.ui.FailReasonCode` has been renamed to `shaka.ui.Overlay.FailReasonCode` (deprecated in v3.1.0)
* **offline:** `shaka.offline.Storage.prototype.store()` returns `AbortableOperation` instead of `Promise` (deprecated in v3.0.0)
* **offline:** `shaka.offline.Storage.prototype.getStoreInProgress()` has been removed; concurrent operations are supported, so callers don't need to check this (deprecated in v3.0.0)
* `shaka.util.Uint8ArrayUtils.equal` has been replaced by `shaka.util.BufferUtils.equal`, which can handle multiple types of buffers (deprecated in v3.0.0)
* **manifest:** `shaka.media.SegmentIndex.prototype.destroy()` has been replaced by `release()`, which is synchronous (deprecated in v3.0.0)
* **manifest:** `shaka.media.SegmentIterator.prototype.seek()`, which mutates the iterator, has been replaced by `shaka.media.SegmentIndex.getIteratorForTime()` (deprecated in v3.1.0)
* **manifest:** `shaka.media.SegmentIndex.prototype.merge()` has become private; use `mergeAndEvict()` instead (deprecated in v3.2.0)
* **plugin:** `AbrManager` plugins must implement the `playbackRateChanged()` method (deprecated in v3.0.0)
* **plugin:** `shaka.extern.Cue.prototype.spacer` has been replaced by the more clearly-named `lineBreak` (deprecated in v3.1.0)
* **plugin:** `IUIElement` plugins must have a `release()` method (not `destroy()`) (deprecated in v3.0.0)
* Remove deprecated features, update upgrade guides ([#4089](https://github.com/willdharris/shaka-player/issues/4089))
* Remove support for Safari 12 and iOS 12 ([#4112](https://github.com/willdharris/shaka-player/issues/4112))
* **hls:** HLS disabled in old browsers/platforms due to incompatibilities ([#3964](https://github.com/willdharris/shaka-player/issues/3964))

### Features

* `shaka.util.Uint8ArrayUtils.equal` has been replaced by `shaka.util.BufferUtils.equal`, which can handle multiple types of buffers (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Add AAC transmuxer ([#4632](https://github.com/willdharris/shaka-player/issues/4632)) ([8623a5d](https://github.com/willdharris/shaka-player/commit/8623a5d0304dd3e65c613b176b4afa38a6dc96b5))
* Add AC-3 detection in TS ([#4931](https://github.com/willdharris/shaka-player/issues/4931)) ([48c30bc](https://github.com/willdharris/shaka-player/commit/48c30bcd036060a09175badadeeacdff4d8f3728))
* add Amazon Fire TV platform support ([#4375](https://github.com/willdharris/shaka-player/issues/4375)) ([5102dac](https://github.com/willdharris/shaka-player/commit/5102dac96cb1a749fefeb1f6b7a24c13f6b1077b))
* Add config for sequenceMode in DASH ([#4607](https://github.com/willdharris/shaka-player/issues/4607)) ([aff2a5d](https://github.com/willdharris/shaka-player/commit/aff2a5d9e81e5fdfaeb91275aaa0821aa189d34f))
* Add Dockerfile and docker build instructions ([925de19](https://github.com/willdharris/shaka-player/commit/925de1995eeb22863e8d4e92d720465834619288))
* Add ExpressPlay FairPlay util ([#4926](https://github.com/willdharris/shaka-player/issues/4926)) ([7fa40fd](https://github.com/willdharris/shaka-player/commit/7fa40fdb483e155099d0141ee110ac1a791d88ae))
* Add external thumbnails support ([#4497](https://github.com/willdharris/shaka-player/issues/4497)) ([3582f0a](https://github.com/willdharris/shaka-player/commit/3582f0a7274d6bb6f0bbfdf2ad51c5ecfb6f974b))
* Add external thumbnails with sprites support ([#4584](https://github.com/willdharris/shaka-player/issues/4584)) ([86cb3e7](https://github.com/willdharris/shaka-player/commit/86cb3e714cc3f59cff8f0b33adb291e128c32609))
* Add getManifestType method ([#5021](https://github.com/willdharris/shaka-player/issues/5021)) ([c7c5e94](https://github.com/willdharris/shaka-player/commit/c7c5e94a32f402edc1ab8dd2b492139bb5079e49))
* Add Id to chapters ([#4184](https://github.com/willdharris/shaka-player/issues/4184)) ([5ca3271](https://github.com/willdharris/shaka-player/commit/5ca32712e375ba875be86827ea1efaaa5e3c0035))
* Add keySystemsMapping to drm config ([#4254](https://github.com/willdharris/shaka-player/issues/4254)) ([5e107d5](https://github.com/willdharris/shaka-player/commit/5e107d584f824e66ab3e5e07f9d833f6dc456d14)), closes [#4243](https://github.com/willdharris/shaka-player/issues/4243)
* Add limited support for HLS "identity" key format ([#4451](https://github.com/willdharris/shaka-player/issues/4451)) ([b1e81a6](https://github.com/willdharris/shaka-player/commit/b1e81a684afe086b7a37ea29bbbfc972575ba332)), closes [#2146](https://github.com/willdharris/shaka-player/issues/2146)
* add listenable events for playback stall detection and gap jumping ([#4249](https://github.com/willdharris/shaka-player/issues/4249)) ([5987458](https://github.com/willdharris/shaka-player/commit/5987458e445cf21f91bf4833396edd63d5f69765))
* add modern EME support for FairPlay ([#3776](https://github.com/willdharris/shaka-player/issues/3776)) ([6d76a13](https://github.com/willdharris/shaka-player/commit/6d76a135e5128dfd47653acea025d0a264d121d5))
* add new methods to FairPlayUtils ([#4029](https://github.com/willdharris/shaka-player/issues/4029)) ([f1eeac1](https://github.com/willdharris/shaka-player/commit/f1eeac1efb618aa7202b17b67c43056714f8da2f))
* add Occitan locale ([#4900](https://github.com/willdharris/shaka-player/issues/4900)) ([68486a3](https://github.com/willdharris/shaka-player/commit/68486a3f3743946188827aa0ebf6ef0e321153be))
* add option for segment-relative VTT timings ([#4083](https://github.com/willdharris/shaka-player/issues/4083)) ([f382cc7](https://github.com/willdharris/shaka-player/commit/f382cc702be6cc28266fe61a33e43573cb22be57))
* Add preferredAudioLabel to PlayerConfiguration ([#4763](https://github.com/willdharris/shaka-player/issues/4763)) ([aadecd6](https://github.com/willdharris/shaka-player/commit/aadecd6401c00af56eccc26bd710d96d41be76ce))
* Add separate audio and video MIME types to Track API ([#3892](https://github.com/willdharris/shaka-player/issues/3892)) ([74c491d](https://github.com/willdharris/shaka-player/commit/74c491d2e0042f62385813f04e74517cf00fcade)), closes [#3888](https://github.com/willdharris/shaka-player/issues/3888)
* Add support for Document Picture-in-Picture ([#4969](https://github.com/willdharris/shaka-player/issues/4969)) ([3828fd6](https://github.com/willdharris/shaka-player/commit/3828fd6849fba98218ed934279d5d8a23183dc06))
* Add support for Modern EME and legacy Apple Media Keys for FairPlay ([#4309](https://github.com/willdharris/shaka-player/issues/4309)) ([5441f93](https://github.com/willdharris/shaka-player/commit/5441f932fd3da20f26da162cc0d49d0470689b41))
* Add support to text-shadow in VTT parser ([#4257](https://github.com/willdharris/shaka-player/issues/4257)) ([62bda2c](https://github.com/willdharris/shaka-player/commit/62bda2cd36c6d49d08c10757bfe5869b5be54b88))
* Adds ChannelCount as a filter to the Player Select Audio Track Method ([#4552](https://github.com/willdharris/shaka-player/issues/4552)) ([9dd945c](https://github.com/willdharris/shaka-player/commit/9dd945c3df7364b90a9c3cb3150021492ebb7d81)), closes [#4550](https://github.com/willdharris/shaka-player/issues/4550)
* **ads:** Add getDescription to CS and SS ads ([#4526](https://github.com/willdharris/shaka-player/issues/4526)) ([7d2a170](https://github.com/willdharris/shaka-player/commit/7d2a170336b828e8aac871ff276dbb8b42c384a4))
* **ads:** Add getTitle to CS and SS ads ([#4513](https://github.com/willdharris/shaka-player/issues/4513)) ([a019065](https://github.com/willdharris/shaka-player/commit/a019065d5d19598c9d0ba6ce5d4d79070f3e3cba))
* **ads:** Ignore ad events with no associated ad ([#4488](https://github.com/willdharris/shaka-player/issues/4488)) ([e826eb8](https://github.com/willdharris/shaka-player/commit/e826eb8eec207dd2ebd4d4ee1e44510ebff22b71)), closes [#4481](https://github.com/willdharris/shaka-player/issues/4481)
* Allow add extra features to MediaSource.addSourceBuffer ([#4527](https://github.com/willdharris/shaka-player/issues/4527)) ([4033be7](https://github.com/willdharris/shaka-player/commit/4033be7c5b1d1c397d5a4840ef7333a26ca93983))
* Allow clearKey configuration in base64 or hex ([#4627](https://github.com/willdharris/shaka-player/issues/4627)) ([29ffc89](https://github.com/willdharris/shaka-player/commit/29ffc89a117e6f4285c0133dce555e44a1414228))
* Allow custom plugins for transmuxing ([#4854](https://github.com/willdharris/shaka-player/issues/4854)) ([fac721d](https://github.com/willdharris/shaka-player/commit/fac721df868af2a4a53f5454b1838a60da3cee83))
* Allow customization of HLS Live behavior ([#4578](https://github.com/willdharris/shaka-player/issues/4578)) ([4914201](https://github.com/willdharris/shaka-player/commit/4914201f86f6e683b64c7cc3338cdf67cee544cf))
* Allow playback of HLS Media Playlist with AAC by default ([#4564](https://github.com/willdharris/shaka-player/issues/4564)) ([757b34e](https://github.com/willdharris/shaka-player/commit/757b34e5959f14c9a5b5aed173cc99d98a794a40))
* Allow playback of HLS Media Playlist with RAW formats by default and support ID3 ([#4591](https://github.com/willdharris/shaka-player/issues/4591)) ([18d8367](https://github.com/willdharris/shaka-player/commit/18d836746e20164409c070c787e08b8bcf4da180))
* Allow VTT files with erroneous linebreaks ([#2394](https://github.com/willdharris/shaka-player/issues/2394)) ([9b1c614](https://github.com/willdharris/shaka-player/commit/9b1c614815d4963e03dec41a155e58cb5eefb94f)), closes [#2358](https://github.com/willdharris/shaka-player/issues/2358)
* Allow WebP and AVIF image streams ([#3856](https://github.com/willdharris/shaka-player/issues/3856)) ([9f3fb46](https://github.com/willdharris/shaka-player/commit/9f3fb46d371d52f58bc9a7fc5beefe51890879ed)), closes [#3845](https://github.com/willdharris/shaka-player/issues/3845)
* Automatic ABR quality restrictions based on screen size ([#4515](https://github.com/willdharris/shaka-player/issues/4515)) ([b5935a8](https://github.com/willdharris/shaka-player/commit/b5935a8a6b3b05c0c4cd10774a9625b0bbaf1cf6))
* Automatic ABR quality restrictions based on size ([#4404](https://github.com/willdharris/shaka-player/issues/4404)) ([cfe8af5](https://github.com/willdharris/shaka-player/commit/cfe8af5ff928fe7466b103429a6325917579ce70)), closes [#2333](https://github.com/willdharris/shaka-player/issues/2333)
* Cache mediaCapabilities.decodingInfo results ([#4789](https://github.com/willdharris/shaka-player/issues/4789)) ([b7781f0](https://github.com/willdharris/shaka-player/commit/b7781f04468c0e25502679a7bc740cc024551adf)), closes [#4775](https://github.com/willdharris/shaka-player/issues/4775)
* Caching and other efficiency improvements for mcap polyfill ([#4708](https://github.com/willdharris/shaka-player/issues/4708)) ([884c4ca](https://github.com/willdharris/shaka-player/commit/884c4ca4f8ed94457e7eabce68d4e476811739d5)), closes [#4574](https://github.com/willdharris/shaka-player/issues/4574)
* **cast:** Add Android receiver support ([#4183](https://github.com/willdharris/shaka-player/issues/4183)) ([dbba571](https://github.com/willdharris/shaka-player/commit/dbba571c6bb7e99a99469ffb695f59a590d44118))
* **cea:** Add CEA parser for TS ([#4697](https://github.com/willdharris/shaka-player/issues/4697)) ([70fad8d](https://github.com/willdharris/shaka-player/commit/70fad8de8fc18cdd186ee431bbd433bbd4d440cc))
* Config to require a minimum HDCP version ([#4883](https://github.com/willdharris/shaka-player/issues/4883)) ([61613cf](https://github.com/willdharris/shaka-player/commit/61613cf0ee8bdbcbf7bfee209bba4fe052f8857c))
* **config:** `manifest.dash.defaultPresentationDelay` has been replaced by `manifest.defaultPresentationDelay` (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **config:** Configuration of factories should be plain factory functions, not constructors; these will not be invoked with `new` (deprecated in v3.1.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **DASH:** Add support for &lt;dashif:Laurl&gt; ([#4849](https://github.com/willdharris/shaka-player/issues/4849)) ([b441518](https://github.com/willdharris/shaka-player/commit/b441518943241693fa2df03196be6ee707c8511e)), closes [#4748](https://github.com/willdharris/shaka-player/issues/4748)
* **dash:** Construct ClearKey PSSH based on MPD ContentProtection ([#4104](https://github.com/willdharris/shaka-player/issues/4104)) ([b83b412](https://github.com/willdharris/shaka-player/commit/b83b4120f46ae94e3ce194f43b13517b7a736f07))
* **dash:** Parse ClearKey license URL in MPD ([#4066](https://github.com/willdharris/shaka-player/issues/4066)) ([19e24b1](https://github.com/willdharris/shaka-player/commit/19e24b1d741b4ba6946011748be8b759b4b71773))
* **demo:** Add Apple Advanced HLS Stream (TS) with raw AAC ([#3933](https://github.com/willdharris/shaka-player/issues/3933)) ([1becadf](https://github.com/willdharris/shaka-player/commit/1becadfc93ca06d64d0c9ace37c80213268a1675))
* **demo:** Added demo asset with raw AAC. ([014c7b3](https://github.com/willdharris/shaka-player/commit/014c7b302b292a22f62d4e01230b927b33bc51da)), closes [#2337](https://github.com/willdharris/shaka-player/issues/2337)
* **demo:** Demo visualizer for buffered ranges. ([#4417](https://github.com/willdharris/shaka-player/issues/4417)) ([55d0a15](https://github.com/willdharris/shaka-player/commit/55d0a1556a273b6af0da16197b424796a175adf8))
* **DRM:** add drmInfo to license requests ([#4030](https://github.com/willdharris/shaka-player/issues/4030)) ([abe846e](https://github.com/willdharris/shaka-player/commit/abe846e1a3456b029822ea42eb0520dec547fda6))
* **DRM:** add initData and initDataType to license requests ([#4039](https://github.com/willdharris/shaka-player/issues/4039)) ([bdc5ea7](https://github.com/willdharris/shaka-player/commit/bdc5ea767ebe55bb0b18dd106e269ab3fecd6d00))
* enable uninstalling PatchedMediaKeysApple ([#4471](https://github.com/willdharris/shaka-player/issues/4471)) ([7166f0c](https://github.com/willdharris/shaka-player/commit/7166f0c1d09ad458abf0ee18e961c88f415afefc)), closes [#4469](https://github.com/willdharris/shaka-player/issues/4469)
* Enable variant failover for BAD_HTTP_STATUS and TIMEOUT ([#4769](https://github.com/willdharris/shaka-player/issues/4769)) ([b46012d](https://github.com/willdharris/shaka-player/commit/b46012df647d0fd6f1b6209a324171ab86f9fa80))
* **HLS:** Add HLS support for non-sequence mode ([#4623](https://github.com/willdharris/shaka-player/issues/4623)) ([2b50b88](https://github.com/willdharris/shaka-player/commit/2b50b88030d44c841daea8f67a3c51eb9b2284a4))
* **hls:** Add support for EXT-X-GAP ([#4208](https://github.com/willdharris/shaka-player/issues/4208)) ([14e61a7](https://github.com/willdharris/shaka-player/commit/14e61a7368ddbd66c4b10f3b0475840cc50512bd)), closes [#1308](https://github.com/willdharris/shaka-player/issues/1308)
* **HLS:** Add support for EXT-X-SESSION-KEY tag ([#4655](https://github.com/willdharris/shaka-player/issues/4655)) ([172c9f8](https://github.com/willdharris/shaka-player/commit/172c9f834ab6575cf9cdb2f825abd9961b9ad7fb)), closes [#917](https://github.com/willdharris/shaka-player/issues/917)
* **HLS:** Add support to HLS-AES128 low latency ([#4982](https://github.com/willdharris/shaka-player/issues/4982)) ([07787a8](https://github.com/willdharris/shaka-player/commit/07787a8874f8448df66e487a5485155a00e39b0c))
* **HLS:** allow customize live segments delay ([#4585](https://github.com/willdharris/shaka-player/issues/4585)) ([1f558a8](https://github.com/willdharris/shaka-player/commit/1f558a82c14e3d68a3a67cbb58879f2ab12549d0))
* **HLS:** Allow mp3 playback with mp4a.40.34 ([#4592](https://github.com/willdharris/shaka-player/issues/4592)) ([8f892b1](https://github.com/willdharris/shaka-player/commit/8f892b136f4cadce6a4d0585f88d4eccaf065f1b))
* **HLS:** Containerless format support ([36d0b54](https://github.com/willdharris/shaka-player/commit/36d0b5484fad68dc1d640fbddf2fae3e1eb7169b)), closes [#2337](https://github.com/willdharris/shaka-player/issues/2337)
* **hls:** HLS disabled in old browsers/platforms due to incompatibilities ([#3964](https://github.com/willdharris/shaka-player/issues/3964)) ([0daa00f](https://github.com/willdharris/shaka-player/commit/0daa00fc7f074c1c86968ed0fcd84bc30254ee6d))
* **HLS:** Improve detection of basic info from Media Playlist ([#4809](https://github.com/willdharris/shaka-player/issues/4809)) ([d465942](https://github.com/willdharris/shaka-player/commit/d465942c4393e6c891d6a230bea90a44d90cc70b))
* **HLS:** Improve Low Latency performance in HLS ([#4952](https://github.com/willdharris/shaka-player/issues/4952)) ([5514385](https://github.com/willdharris/shaka-player/commit/5514385c87440b4e77ae772f533b30927dcdb303))
* **HLS:** Lazy-load HLS media playlists ([#4511](https://github.com/willdharris/shaka-player/issues/4511)) ([b2f279d](https://github.com/willdharris/shaka-player/commit/b2f279db1b111e3c8a02706551f466468621cd97)), closes [#1936](https://github.com/willdharris/shaka-player/issues/1936)
* **hls:** make a head request if hls subtitles have no extension ([#4140](https://github.com/willdharris/shaka-player/issues/4140)) ([19e12b5](https://github.com/willdharris/shaka-player/commit/19e12b5e282e661a9a17a6bfbb87c565faf2bc6e))
* **hls:** parse EXT-X-GAP ([#4134](https://github.com/willdharris/shaka-player/issues/4134)) ([42eecc8](https://github.com/willdharris/shaka-player/commit/42eecc84f992ca6a680c3a5fd46d1c300fe92a72))
* **HLS:** Poll HLS playlists using last segment duration ([#4779](https://github.com/willdharris/shaka-player/issues/4779)) ([1ba3806](https://github.com/willdharris/shaka-player/commit/1ba38067759654b5e53573c41db65d9d748af003)), closes [#4771](https://github.com/willdharris/shaka-player/issues/4771)
* **HLS:** Re-add TS support to Safari ([#4097](https://github.com/willdharris/shaka-player/issues/4097)) ([8a3bed7](https://github.com/willdharris/shaka-player/commit/8a3bed710c104c9729fec2072318e50f9fe15ab2))
* **hls:** Read EXT-X-PROGRAM-DATE-TIME ([#4034](https://github.com/willdharris/shaka-player/issues/4034)) ([89409ce](https://github.com/willdharris/shaka-player/commit/89409cee3eaeb6764dbc191b7408bf45eecdced3)), closes [#2337](https://github.com/willdharris/shaka-player/issues/2337)
* **hls:** Support AES-128 in HLS ([#4386](https://github.com/willdharris/shaka-player/issues/4386)) ([6194021](https://github.com/willdharris/shaka-player/commit/6194021a3d4ea5dae22ade6713bb077875a4ee9d)), closes [#850](https://github.com/willdharris/shaka-player/issues/850)
* **HLS:** Support for HLS key rotation ([#4568](https://github.com/willdharris/shaka-player/issues/4568)) ([3846eea](https://github.com/willdharris/shaka-player/commit/3846eeac3f3777c35e61f479958015062f4275af)), closes [#741](https://github.com/willdharris/shaka-player/issues/741)
* Improve gap-detection robustness ([#4399](https://github.com/willdharris/shaka-player/issues/4399)) ([4293a14](https://github.com/willdharris/shaka-player/commit/4293a1421ada4b189d64b8c3f87a7599bc7b1a8f))
* Improved LCEVC integration ([#4560](https://github.com/willdharris/shaka-player/issues/4560)) ([50062f5](https://github.com/willdharris/shaka-player/commit/50062f58adea248a403461b50b65c3a585de31b4))
* LCEVC Integration ([#4050](https://github.com/willdharris/shaka-player/issues/4050)) ([284ea63](https://github.com/willdharris/shaka-player/commit/284ea63a60178cbc87ce2fde769eb06bdb8fb8ea))
* **logs:** Add extra logging for 3015 errors ([#4932](https://github.com/willdharris/shaka-player/issues/4932)) ([67a2451](https://github.com/willdharris/shaka-player/commit/67a245129f53d99cce89aff3ea194b1098d65ee6))
* **manifest:** `shaka.media.SegmentIndex.prototype.destroy()` has been replaced by `release()`, which is synchronous (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **manifest:** `shaka.media.SegmentIndex.prototype.merge()` has become private; use `mergeAndEvict()` instead (deprecated in v3.2.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **manifest:** `shaka.media.SegmentIterator.prototype.seek()`, which mutates the iterator, has been replaced by `shaka.media.SegmentIndex.getIteratorForTime()` (deprecated in v3.1.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Move forceTransmux from streaming to mediasource config ([#4783](https://github.com/willdharris/shaka-player/issues/4783)) ([b491a6b](https://github.com/willdharris/shaka-player/commit/b491a6b7caa5d4a8167adf18cf90b23c30a5a1be))
* **net:** Added advanced type to filters ([#5006](https://github.com/willdharris/shaka-player/issues/5006)) ([fbce38a](https://github.com/willdharris/shaka-player/commit/fbce38af1cc7f05a30992907103af4a82f180520)), closes [#4966](https://github.com/willdharris/shaka-player/issues/4966)
* New autoShowText config to change initial text visibility behavior ([#3421](https://github.com/willdharris/shaka-player/issues/3421)) ([5c24410](https://github.com/willdharris/shaka-player/commit/5c24410560d8afa13e6f2492590f13506419b59e))
* **offline:** `shaka.offline.Storage.prototype.getStoreInProgress()` has been removed; concurrent operations are supported, so callers don't need to check this (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **offline:** `shaka.offline.Storage.prototype.store()` returns `AbortableOperation` instead of `Promise` (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **offline:** improve the speed of offline downloads ([#4168](https://github.com/willdharris/shaka-player/issues/4168)) ([73f6de3](https://github.com/willdharris/shaka-player/commit/73f6de3e01ae4ed3b86302add7ee16c86c3b9b78))
* only polyfill MCap for non Android-based Cast devices. ([#4170](https://github.com/willdharris/shaka-player/issues/4170)) ([11321d8](https://github.com/willdharris/shaka-player/commit/11321d8f26b01412fa5173aa6efcf777186fa7a0))
* Parse and surface "prft" boxes as events ([#4389](https://github.com/willdharris/shaka-player/issues/4389)) ([89777dd](https://github.com/willdharris/shaka-player/commit/89777dd7043ae2b5fa213ab73e43f93482bb86d0)), closes [#4382](https://github.com/willdharris/shaka-player/issues/4382)
* Parse ID3 metadata ([#4409](https://github.com/willdharris/shaka-player/issues/4409)) ([95bbf72](https://github.com/willdharris/shaka-player/commit/95bbf72f426f9df899193f6083197a77191c0c4f))
* **player:** `shaka.Player.prototype.addTextTrack()` has been replaced by `addTextTrackAsync()`, which returns a `Promise` (deprecated in v3.1.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **plugin:** `AbrManager` plugins must implement the `playbackRateChanged()` method (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **plugin:** `IUIElement` plugins must have a `release()` method (not `destroy()`) (deprecated in v3.0.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **plugin:** `shaka.extern.Cue.prototype.spacer` has been replaced by the more clearly-named `lineBreak` (deprecated in v3.1.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Public release of Sindarin (sjn) translation easter egg ([#4033](https://github.com/willdharris/shaka-player/issues/4033)) ([9029d06](https://github.com/willdharris/shaka-player/commit/9029d0677e0e0325e0dbe939907ba60ecec74c92))
* Remove deprecated features, update upgrade guides ([#4089](https://github.com/willdharris/shaka-player/issues/4089)) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Remove small/large gap config, always jump gaps ([#4125](https://github.com/willdharris/shaka-player/issues/4125)) ([0fd1999](https://github.com/willdharris/shaka-player/commit/0fd19997dde7b03bad7464a82dc86d7b2cd8a304))
* Remove support for Safari 12 and iOS 12 ([#4112](https://github.com/willdharris/shaka-player/issues/4112)) ([8bb7044](https://github.com/willdharris/shaka-player/commit/8bb70449d33c31a0e7fc312260dc001cc9e3a792))
* Support customizing clearBuffers and safeMargin when select variants by label ([#4770](https://github.com/willdharris/shaka-player/issues/4770)) ([c724625](https://github.com/willdharris/shaka-player/commit/c7246250323c3c97a2d30f9f66880e914e5c2344))
* Support HTML-escaped cues in VTT ([#4660](https://github.com/willdharris/shaka-player/issues/4660)) ([2b8b387](https://github.com/willdharris/shaka-player/commit/2b8b38788ab5b6fc297eaa3537e97bc348d2b389))
* Support Parallel Segment Fetching ([#4784](https://github.com/willdharris/shaka-player/issues/4784)) ([de6abde](https://github.com/willdharris/shaka-player/commit/de6abde06f38d802f1f9fb297c284283ca8e4751))
* Temporarily disable the active variant from NETWORK HTTP_ERROR ([#4189](https://github.com/willdharris/shaka-player/issues/4189)) ([b57279d](https://github.com/willdharris/shaka-player/commit/b57279d39c24d3b2568c4b62338524ecc23423ad)), closes [#4121](https://github.com/willdharris/shaka-player/issues/4121) [#1542](https://github.com/willdharris/shaka-player/issues/1542) [#2541](https://github.com/willdharris/shaka-player/issues/2541)
* TS parser improvements ([#4612](https://github.com/willdharris/shaka-player/issues/4612)) ([5157b44](https://github.com/willdharris/shaka-player/commit/5157b44b2d644ec9cdc13b03b4ac762ed8e0f183))
* **ui:** `shaka.ui.FailReasonCode` has been renamed to `shaka.ui.Overlay.FailReasonCode` (deprecated in v3.1.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **ui:** `shaka.ui.TrackLabelFormat` has been renamed to `shaka.ui.Overlay.TrackLabelFormat` (deprecated in v3.1.0) ([ac5acc8](https://github.com/willdharris/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **ui:** Add quality selection for audio-only content ([#3649](https://github.com/willdharris/shaka-player/issues/3649)) ([adc3502](https://github.com/willdharris/shaka-player/commit/adc3502d55f39eaca30f3c42e17961ec7d681c80)), closes [#2071](https://github.com/willdharris/shaka-player/issues/2071)
* **UI:** Add video fullscreen support for iOS ([#3853](https://github.com/willdharris/shaka-player/issues/3853)) ([8d1b5e6](https://github.com/willdharris/shaka-player/commit/8d1b5e6b07e979bd641da0b2b53c5f8e872422ad)), closes [#3832](https://github.com/willdharris/shaka-player/issues/3832)
* **UI:** Added keyboardSeekDistance config to UI ([#4246](https://github.com/willdharris/shaka-player/issues/4246)) ([6084ca6](https://github.com/willdharris/shaka-player/commit/6084ca6395fbe3d5a97fa92137b8bb51f15c89f8))
* **UI:** Allow customizing FullScreen element ([#4963](https://github.com/willdharris/shaka-player/issues/4963)) ([c471d23](https://github.com/willdharris/shaka-player/commit/c471d23bc25db11dda85a18870ebd3fe37971848))
* Upgrade eme-encryption-scheme-polyfill to support ChromeCast version of PlayReady ([#4378](https://github.com/willdharris/shaka-player/issues/4378)) ([e6b6d7c](https://github.com/willdharris/shaka-player/commit/e6b6d7c24bee4138b6bb2735e3c9a4dc885a6cf6))
* **webvtt:** add support for karaoke style text in WebVTT ([#4274](https://github.com/willdharris/shaka-player/issues/4274)) ([60af516](https://github.com/willdharris/shaka-player/commit/60af5165207d39ebe26d536b009521192ab8cad9))
* **webvtt:** webvtt colors output ([#4954](https://github.com/willdharris/shaka-player/issues/4954)) ([ed7a736](https://github.com/willdharris/shaka-player/commit/ed7a736ca22bb768672135ad0d468c00be4c5dac))


### Bug Fixes

* **abr:** use Network Info API in ABR getBandwidthEstimate ([#4263](https://github.com/willdharris/shaka-player/issues/4263)) ([4fc7a48](https://github.com/willdharris/shaka-player/commit/4fc7a4893fd081d4dafa26a2034361afd7b7e6ed))
* Add explicit release() for FakeEventTarget ([#3950](https://github.com/willdharris/shaka-player/issues/3950)) ([f1c1585](https://github.com/willdharris/shaka-player/commit/f1c1585afb2cfa3eb6b7465c8b32c9bad8e62d15))
* Add fallback to TextDecoder and TextEncoder [#4324](https://github.com/willdharris/shaka-player/issues/4324) ([5b18069](https://github.com/willdharris/shaka-player/commit/5b180694309f1cc01b2997cd0366154135f8acd8))
* Add missing module export in generated typescript defs ([feefd7b](https://github.com/willdharris/shaka-player/commit/feefd7b7d1cc318800c8d83de8cce81c57939f7d))
* Add mux.js to support.html ([#4923](https://github.com/willdharris/shaka-player/issues/4923)) ([d9fa4eb](https://github.com/willdharris/shaka-player/commit/d9fa4ebdec49b609690b4d028a0fa1318b83f179))
* add strictMissingProperties suppressions to unblock strict missing properties on union types. ([#4371](https://github.com/willdharris/shaka-player/issues/4371)) ([b361948](https://github.com/willdharris/shaka-player/commit/b36194878e26a22b522a6cf1dba07e9fc5cd341d))
* **Ads:** Fix CS volume ad ([#5016](https://github.com/willdharris/shaka-player/issues/5016)) ([492b5f3](https://github.com/willdharris/shaka-player/commit/492b5f3ac83c801bc3f50a0aaa8a5382dd8f0936))
* **ads:** Fix IMA crash when autoplay is rejected ([#4518](https://github.com/willdharris/shaka-player/issues/4518)) ([d27f7d2](https://github.com/willdharris/shaka-player/commit/d27f7d24bb3e1000fc489a6aa125fca359dd77e1)), closes [#4179](https://github.com/willdharris/shaka-player/issues/4179)
* **Ads:** Fix usage of EventManager on CS ([#5017](https://github.com/willdharris/shaka-player/issues/5017)) ([541badc](https://github.com/willdharris/shaka-player/commit/541badcfca7226ac77f9f6073e5542889b3fb104))
* **ads:** Fix VMAP ads stay muted on muted autoplay ([#4995](https://github.com/willdharris/shaka-player/issues/4995)) ([d074afc](https://github.com/willdharris/shaka-player/commit/d074afc1fc1a675aaee7059df860a160004871fc))
* allow build without text ([#4506](https://github.com/willdharris/shaka-player/issues/4506)) ([340b04a](https://github.com/willdharris/shaka-player/commit/340b04ad4798c9b68ed9510ae71912192a61348b))
* Allow overriding special handling of 404s ([#4635](https://github.com/willdharris/shaka-player/issues/4635)) ([427f126](https://github.com/willdharris/shaka-player/commit/427f126ea3958541d69474505e1af0eb892d8dde)), closes [#4548](https://github.com/willdharris/shaka-player/issues/4548)
* allow the playback on platforms when low latency APIs are not supported ([#4485](https://github.com/willdharris/shaka-player/issues/4485)) ([c1753e1](https://github.com/willdharris/shaka-player/commit/c1753e1a02881cfbbafd863eeb582411c45df92c))
* Caption can not turn off at iOS Safari ([#4978](https://github.com/willdharris/shaka-player/issues/4978)) ([9d2c325](https://github.com/willdharris/shaka-player/commit/9d2c325cdf431664d33bca31626f73d5c6f7a608))
* **cast:** Added existence checks for MediaDecodingConfig.{audio|video} in decodingInfo(). ([#4796](https://github.com/willdharris/shaka-player/issues/4796)) ([36db83d](https://github.com/willdharris/shaka-player/commit/36db83dc992bf86e08c610f31ef39ae2c41d0130))
* **cast:** Reduce size of Cast update messages ([#4644](https://github.com/willdharris/shaka-player/issues/4644)) ([4e75ec6](https://github.com/willdharris/shaka-player/commit/4e75ec64be76414b1d4945cbfbf7bc52b5ff3b01))
* **cast:** Use cast platform APIs in MediaCapabilties polyfill ([#4727](https://github.com/willdharris/shaka-player/issues/4727)) ([5d6f56a](https://github.com/willdharris/shaka-player/commit/5d6f56adf33557ca3ff70a0c459d400b2eae6f79))
* **cea:** Fix MAX_ROWS in CEA-708 window ([#4757](https://github.com/willdharris/shaka-player/issues/4757)) ([e89eeb6](https://github.com/willdharris/shaka-player/commit/e89eeb69fab877ee6b330f12c4ff67b3eeac8839))
* **cea:** Fix not rendering CEA-608 Closed Captions ([#4683](https://github.com/willdharris/shaka-player/issues/4683)) ([a489282](https://github.com/willdharris/shaka-player/commit/a489282ff26796a55f96e035b55d331abfc14142)), closes [#4605](https://github.com/willdharris/shaka-player/issues/4605) [#3659](https://github.com/willdharris/shaka-player/issues/3659)
* **cea:** Fix not rendering CEA-608 on encrypted mp4 segments ([#4756](https://github.com/willdharris/shaka-player/issues/4756)) ([d600109](https://github.com/willdharris/shaka-player/commit/d6001097a9751bd9211eb52f940e282ead026a32))
* **cea:** make a more robust CEA MP4 parser ([#3965](https://github.com/willdharris/shaka-player/issues/3965)) ([2687b95](https://github.com/willdharris/shaka-player/commit/2687b95d5830179c53914a7e903ecfbaced429cc))
* **chapters:** removed duplicate chapters by id ([#4810](https://github.com/willdharris/shaka-player/issues/4810)) ([151bdda](https://github.com/willdharris/shaka-player/commit/151bdda36d60499f5cfdd4d5c6ebbe088025cd2a))
* check for negative rows before moving ([#4510](https://github.com/willdharris/shaka-player/issues/4510)) ([b3621c2](https://github.com/willdharris/shaka-player/commit/b3621c26a86897ba80c17b68f316e22aba61b30b)), closes [#4508](https://github.com/willdharris/shaka-player/issues/4508)
* Clear buffer on seek if mediaState is updating ([#3795](https://github.com/willdharris/shaka-player/issues/3795)) ([9705639](https://github.com/willdharris/shaka-player/commit/9705639f4514d8d2dbfe5d81a31388f99e6be507)), closes [#3299](https://github.com/willdharris/shaka-player/issues/3299)
* **cmcd:** Fix Symbol usage in CMCD on Xbox One ([#4073](https://github.com/willdharris/shaka-player/issues/4073)) ([4005754](https://github.com/willdharris/shaka-player/commit/400575498f34cf252aaba0bc1367953b8cf44537)), closes [#4072](https://github.com/willdharris/shaka-player/issues/4072)
* Content reload starttime with HLS on iOS ([#4575](https://github.com/willdharris/shaka-player/issues/4575)) ([59d4360](https://github.com/willdharris/shaka-player/commit/59d4360b686421f07aa0d7f28eb944f0c51ff5a2)), closes [#4244](https://github.com/willdharris/shaka-player/issues/4244)
* Correct default initDataTransform for legacy Apple Media Keys ([#4797](https://github.com/willdharris/shaka-player/issues/4797)) ([67a5d56](https://github.com/willdharris/shaka-player/commit/67a5d56e8606c58cef6ff969aca6010e6db2dd16))
* **css:** Fix missing % in calculation ([#4157](https://github.com/willdharris/shaka-player/issues/4157)) ([1c86195](https://github.com/willdharris/shaka-player/commit/1c8619582319c46c524807aa4bdff1191b2efc91))
* DAI ID3 metadata parsing ([#4616](https://github.com/willdharris/shaka-player/issues/4616)) ([0d67ecd](https://github.com/willdharris/shaka-player/commit/0d67ecd7cba253eb1919ae6e15a80f34e08fc132))
* **dash:** Account for bandwidth before filtering text stream ([#3765](https://github.com/willdharris/shaka-player/issues/3765)) ([0b04aec](https://github.com/willdharris/shaka-player/commit/0b04aecdd7ad4184a72b8cf562318b28128344bf)), closes [#3724](https://github.com/willdharris/shaka-player/issues/3724)
* **DASH:** Fix dynamic manifests from edgeware ([#4914](https://github.com/willdharris/shaka-player/issues/4914)) ([056588b](https://github.com/willdharris/shaka-player/commit/056588b2e1eaf2e627cb8878735f4db5d0d04087))
* **dash:** Fix performance regression ([#4064](https://github.com/willdharris/shaka-player/issues/4064)) ([298b604](https://github.com/willdharris/shaka-player/commit/298b60481d34bd9d776874fe1b9a8eea05b533d9))
* **dash:** Fix playback of Dolby Atmos ([#4173](https://github.com/willdharris/shaka-player/issues/4173)) ([d51fe23](https://github.com/willdharris/shaka-player/commit/d51fe23b7fab99501818c18cc76586e1ec4abcdd)), closes [#4171](https://github.com/willdharris/shaka-player/issues/4171)
* Debug buffer placement ([#4345](https://github.com/willdharris/shaka-player/issues/4345)) ([47fa309](https://github.com/willdharris/shaka-player/commit/47fa3093e1462d0bcca87238dc4886b9e2c1f8f4))
* **Demo:** Allow manifest type for DAI custom assets ([#4977](https://github.com/willdharris/shaka-player/issues/4977)) ([1e50630](https://github.com/willdharris/shaka-player/commit/1e50630ad4631cd2455f0e8a179012de34935a80))
* **demo:** allow switch between UITextDisplayer and SimpleTextDisplayer ([#4275](https://github.com/willdharris/shaka-player/issues/4275)) ([28689f3](https://github.com/willdharris/shaka-player/commit/28689f38fb7cc8f3b85b6b1eb2337a1779e8ee95))
* **demo:** erroneous FairPlay keysystem in demo ([#4276](https://github.com/willdharris/shaka-player/issues/4276)) ([8719bdc](https://github.com/willdharris/shaka-player/commit/8719bdc0defd7956ec9fad934525477a603744a0))
* Do not report MANIFEST RESTRICTIONS_CANNOT_BE_MET error twice ([#4194](https://github.com/willdharris/shaka-player/issues/4194)) ([08589e8](https://github.com/willdharris/shaka-player/commit/08589e8fb27f3f73f64204e7d3a2387f3c197d84)), closes [#4190](https://github.com/willdharris/shaka-player/issues/4190)
* Don't send drmsessionupdate after unload ([#4248](https://github.com/willdharris/shaka-player/issues/4248)) ([60af9ad](https://github.com/willdharris/shaka-player/commit/60af9ad596e5c2cb31d1e7bb616e415cf46ca761))
* DrmEngine exception thrown when using FairPlay ([#4971](https://github.com/willdharris/shaka-player/issues/4971)) ([eebf18c](https://github.com/willdharris/shaka-player/commit/eebf18cabdcee3c62daee9bed9ceb2958f30f9f5))
* embed cc not shown when seeking back ([#4643](https://github.com/willdharris/shaka-player/issues/4643)) ([2a6b0d0](https://github.com/willdharris/shaka-player/commit/2a6b0d02e550cfa5749b838f5915b8b6cf7b2099)), closes [#4641](https://github.com/willdharris/shaka-player/issues/4641)
* exception if on early adError ([#4362](https://github.com/willdharris/shaka-player/issues/4362)) ([3c92f05](https://github.com/willdharris/shaka-player/commit/3c92f0598e6c1628ff50d980a842dd40b2b56813)), closes [#4004](https://github.com/willdharris/shaka-player/issues/4004)
* Explicitly specify [@externs](https://github.com/externs) in transmuxer externs. ([#4999](https://github.com/willdharris/shaka-player/issues/4999)) ([ef8078a](https://github.com/willdharris/shaka-player/commit/ef8078a05f5b56cc4cabe7e6b78e14a5d26b89ce))
* Failed to set 'currentTime' property on 'HTMLMediaElement' on a Hisense TV ([#4962](https://github.com/willdharris/shaka-player/issues/4962)) ([5d93b8f](https://github.com/willdharris/shaka-player/commit/5d93b8f9a71214b984db45db3cda7ba40d86ff87))
* **fairplay:** Re-add initDataTransform config ([#4231](https://github.com/willdharris/shaka-player/issues/4231)) ([ff310e9](https://github.com/willdharris/shaka-player/commit/ff310e91e564bcc4be340c47bf1be81a5323765a))
* Filter unsupported H.264 streams in Xbox ([#4493](https://github.com/willdharris/shaka-player/issues/4493)) ([8475214](https://github.com/willdharris/shaka-player/commit/8475214bc46e8321f7b60a6fc7fabee484a40800))
* Fix audio mime type in multiplexed HLS stream ([#4241](https://github.com/willdharris/shaka-player/issues/4241)) ([4e4e92e](https://github.com/willdharris/shaka-player/commit/4e4e92e98da357285547859a98e6b3fe75d1904f))
* Fix bitmap-based cue size ([#4453](https://github.com/willdharris/shaka-player/issues/4453)) ([4a197e1](https://github.com/willdharris/shaka-player/commit/4a197e1288c8f20a950cf491041eca9dde7033cb))
* Fix broken deps file generation on Windows ([#4086](https://github.com/willdharris/shaka-player/issues/4086)) ([9660ce8](https://github.com/willdharris/shaka-player/commit/9660ce85df48856b964eebc330c28beba2e3068a)), closes [#4085](https://github.com/willdharris/shaka-player/issues/4085)
* Fix bufferBehind setting broken by image segments ([#4718](https://github.com/willdharris/shaka-player/issues/4718)) ([cd1b7c0](https://github.com/willdharris/shaka-player/commit/cd1b7c09429f9d13361a5ab1fdfb79940673f941)), closes [#4717](https://github.com/willdharris/shaka-player/issues/4717)
* Fix choppy HLS startup ([#4553](https://github.com/willdharris/shaka-player/issues/4553)) ([59ef54a](https://github.com/willdharris/shaka-player/commit/59ef54a158e14da2f7c6ab04e1fd9409bf63c6f0)), closes [#4516](https://github.com/willdharris/shaka-player/issues/4516)
* Fix CMCD top bitrate reporting ([#3852](https://github.com/willdharris/shaka-player/issues/3852)) ([922778a](https://github.com/willdharris/shaka-player/commit/922778a5ebd2d58ca0c1e804745ca40cda1228bc)), closes [#3851](https://github.com/willdharris/shaka-player/issues/3851)
* Fix compiler error introduced in [#3864](https://github.com/willdharris/shaka-player/issues/3864) ([#3906](https://github.com/willdharris/shaka-player/issues/3906)) ([0635e2c](https://github.com/willdharris/shaka-player/commit/0635e2c055c13a405048c7696389c1dfc039902f))
* Fix compiler error on static use of "this" ([#4699](https://github.com/willdharris/shaka-player/issues/4699)) ([b06fd6a](https://github.com/willdharris/shaka-player/commit/b06fd6ad27b38238c401867971ce6b0ac1e53882))
* Fix detection of ac4, dts, and dolby h265 ([#4657](https://github.com/willdharris/shaka-player/issues/4657)) ([319a358](https://github.com/willdharris/shaka-player/commit/319a358b8dc1838a89d8977109cab4296a558841))
* Fix dispatch ID3 metadata when transmuxing AAC ([#4639](https://github.com/willdharris/shaka-player/issues/4639)) ([bf813f2](https://github.com/willdharris/shaka-player/commit/bf813f2553dfc56efa79b708c54cbddee0f3ee2e))
* Fix download of some HLS assets ([#3934](https://github.com/willdharris/shaka-player/issues/3934)) ([36ca820](https://github.com/willdharris/shaka-player/commit/36ca820877965db8bcc8b9c4b2a428317301bb95))
* Fix DRM workaround for Tizen and Xbox with hvc1/hev1 boxes ([#4743](https://github.com/willdharris/shaka-player/issues/4743)) ([a61c084](https://github.com/willdharris/shaka-player/commit/a61c08433dab654edd224b2dc930c6d257460ec9)), closes [#4742](https://github.com/willdharris/shaka-player/issues/4742)
* Fix drm.keySystemsMapping config ([#4425](https://github.com/willdharris/shaka-player/issues/4425)) ([d945084](https://github.com/willdharris/shaka-player/commit/d9450846e11224e0b1add6cc20a64844d6c09fcf)), closes [#4422](https://github.com/willdharris/shaka-player/issues/4422)
* Fix duplicate CMCD parameters in HLS live content ([#3875](https://github.com/willdharris/shaka-player/issues/3875)) ([f27401c](https://github.com/willdharris/shaka-player/commit/f27401cc151a435ae8fb12be4e86d672c331e1e5)), closes [#3862](https://github.com/willdharris/shaka-player/issues/3862)
* Fix duplicate updates in StreamingEngine ([#4840](https://github.com/willdharris/shaka-player/issues/4840)) ([224207b](https://github.com/willdharris/shaka-player/commit/224207ba6caf49b2cdb7434a0534df8210bc4be9)), closes [#4831](https://github.com/willdharris/shaka-player/issues/4831)
* Fix duration error when HLS goes from LIVE to VOD ([#5001](https://github.com/willdharris/shaka-player/issues/5001)) ([1aee989](https://github.com/willdharris/shaka-player/commit/1aee98944f020427d081e9c7d1474675dac8b745))
* Fix encryption detection to work around broken platforms ([#4169](https://github.com/willdharris/shaka-player/issues/4169)) ([c5f474e](https://github.com/willdharris/shaka-player/commit/c5f474ef983169e6ff29f1594d15a9b50b12d316))
* Fix EOS set-top box being identified as Apple. ([#4310](https://github.com/willdharris/shaka-player/issues/4310)) ([7c2c4be](https://github.com/willdharris/shaka-player/commit/7c2c4be2ae946c4cf270717f852b0d95b498266e))
* Fix errors with TS segments on Chromecast ([#4543](https://github.com/willdharris/shaka-player/issues/4543)) ([593c280](https://github.com/willdharris/shaka-player/commit/593c280dd578ee19cbb6a47f22962ff7fdd2cb45))
* Fix event listener leaks in Player ([#4229](https://github.com/willdharris/shaka-player/issues/4229)) ([a5d3568](https://github.com/willdharris/shaka-player/commit/a5d356874ba90069ca5a86be1979a5904a1150e8))
* Fix exception enabling captions on HLS ([#4894](https://github.com/willdharris/shaka-player/issues/4894)) ([b7b2a7c](https://github.com/willdharris/shaka-player/commit/b7b2a7cbe9f1b23ca184617a2c51f26cc85bf0a3)), closes [#4889](https://github.com/willdharris/shaka-player/issues/4889)
* Fix exception in StreamingEngine for EMSG with HLS ([#3887](https://github.com/willdharris/shaka-player/issues/3887)) ([48433ab](https://github.com/willdharris/shaka-player/commit/48433abe74c5f603cf06097e391ffdfa22d64256)), closes [#3886](https://github.com/willdharris/shaka-player/issues/3886)
* Fix exception with streaming.startAtSegmentBoundary ([#4216](https://github.com/willdharris/shaka-player/issues/4216)) ([426a19c](https://github.com/willdharris/shaka-player/commit/426a19c8e7ff188390e7430fb02f3cfcb79cc017)), closes [#4188](https://github.com/willdharris/shaka-player/issues/4188)
* Fix exceptions when quickly shutting down src= on Safari ([#4088](https://github.com/willdharris/shaka-player/issues/4088)) ([ca08230](https://github.com/willdharris/shaka-player/commit/ca08230fbe85d66176c7fa1fb4f9782d0ab364fc)), closes [#4087](https://github.com/willdharris/shaka-player/issues/4087)
* Fix flattenedCues in WebVttGenerator ([#4867](https://github.com/willdharris/shaka-player/issues/4867)) ([15232dd](https://github.com/willdharris/shaka-player/commit/15232ddf06294f7f932b2a97f619e6ff87514a6c))
* Fix getVideoPlaybackQuality in WebOS 3 ([#4316](https://github.com/willdharris/shaka-player/issues/4316)) ([5561111](https://github.com/willdharris/shaka-player/commit/556111143dfccbc7348fc15792df75bc35fea465))
* Fix hang when seeking to the last segment ([#4537](https://github.com/willdharris/shaka-player/issues/4537)) ([19a4842](https://github.com/willdharris/shaka-player/commit/19a48422901440ff88fbbedfea5803c6dda07127))
* Fix HLS dynamic to static transition ([a16b1ac](https://github.com/willdharris/shaka-player/commit/a16b1ac8a4c8f367f65747fc789a7d8c160e29e3))
* Fix HLS dynamic to static transition ([#4483](https://github.com/willdharris/shaka-player/issues/4483)) ([a16b1ac](https://github.com/willdharris/shaka-player/commit/a16b1ac8a4c8f367f65747fc789a7d8c160e29e3)), closes [#4431](https://github.com/willdharris/shaka-player/issues/4431)
* Fix HLS lazy-loading exception during update ([#4648](https://github.com/willdharris/shaka-player/issues/4648)) ([777c27e](https://github.com/willdharris/shaka-player/commit/777c27ee558d803b3f166a0ac8b9778b08196654)), closes [#4647](https://github.com/willdharris/shaka-player/issues/4647)
* Fix HLS lazy-loading exception on switch ([#4645](https://github.com/willdharris/shaka-player/issues/4645)) ([941ed4e](https://github.com/willdharris/shaka-player/commit/941ed4ed286e4463d4973e994d322250678cfdcb)), closes [#4621](https://github.com/willdharris/shaka-player/issues/4621)
* Fix HLS lazy-loading with DRM ([#4646](https://github.com/willdharris/shaka-player/issues/4646)) ([a7f0be7](https://github.com/willdharris/shaka-player/commit/a7f0be726d5b801ac2365bb0c9b6db9e576c964f)), closes [#4622](https://github.com/willdharris/shaka-player/issues/4622)
* Fix HLS live stream subtitle offsets ([#4586](https://github.com/willdharris/shaka-player/issues/4586)) ([3b9af2e](https://github.com/willdharris/shaka-player/commit/3b9af2efa6be06c8c8a13e5d715828e2875d75d7))
* Fix ID3 parsing in TS segments ([#4609](https://github.com/willdharris/shaka-player/issues/4609)) ([3b534fd](https://github.com/willdharris/shaka-player/commit/3b534fd405ad3254d37a86fd1895ceeb96dc8094))
* Fix in-band key rotation on Xbox One ([#4478](https://github.com/willdharris/shaka-player/issues/4478)) ([4e93311](https://github.com/willdharris/shaka-player/commit/4e933116984beb630d31ce7a0b8c9bc6f8b48c06)), closes [#4401](https://github.com/willdharris/shaka-player/issues/4401)
* Fix key ID byteswapping for PlayReady on PS4 ([#4377](https://github.com/willdharris/shaka-player/issues/4377)) ([25fd4f4](https://github.com/willdharris/shaka-player/commit/25fd4f4af6ddd8953c4bc2da4a2d9eb1144c3fb9))
* Fix legacy codec support by rewriting codec metadata ([#4858](https://github.com/willdharris/shaka-player/issues/4858)) ([e351395](https://github.com/willdharris/shaka-player/commit/e351395c4a78ccc9e3ceafaa0288cbd06489a927))
* Fix media source duration when using sequence mode ([#4848](https://github.com/willdharris/shaka-player/issues/4848)) ([1762267](https://github.com/willdharris/shaka-player/commit/1762267d356a04217340ec792c51ceadb842cd6a))
* Fix MediaCapabilities polyfill on Hisense ([#4927](https://github.com/willdharris/shaka-player/issues/4927)) ([6a48cfe](https://github.com/willdharris/shaka-player/commit/6a48cfe64da49c49aeaabeb646b0233537a2ae3e))
* Fix MediaCapabilities polyfill on Playstation 4 ([#4320](https://github.com/willdharris/shaka-player/issues/4320)) ([0335b2a](https://github.com/willdharris/shaka-player/commit/0335b2af2efea6ceda83e536e12094e4cc942a25))
* Fix MediaCapabilities polyfill on Safari ([0201f2b](https://github.com/willdharris/shaka-player/commit/0201f2b7604e76062b68b8b1acbf098faf71d019)), closes [#3696](https://github.com/willdharris/shaka-player/issues/3696) [#3530](https://github.com/willdharris/shaka-player/issues/3530)
* Fix MediaCapabilities polyfill on Tizen and WebOS ([#4396](https://github.com/willdharris/shaka-player/issues/4396)) ([eb2aed8](https://github.com/willdharris/shaka-player/commit/eb2aed825e84142f9fb9ddb3e69ebc333127c295)), closes [#4383](https://github.com/willdharris/shaka-player/issues/4383) [#4357](https://github.com/willdharris/shaka-player/issues/4357)
* Fix memory leak in DASH live streams with inband EventStream ([#3957](https://github.com/willdharris/shaka-player/issues/3957)) ([b7f04cb](https://github.com/willdharris/shaka-player/commit/b7f04cb36bda664ec9cf23a081d237793907eaae))
* Fix metadata assert when the ID3 is future (coming in a previous segment) ([#4640](https://github.com/willdharris/shaka-player/issues/4640)) ([216bdd7](https://github.com/willdharris/shaka-player/commit/216bdd7657d7be8bb33f71c3a62f649ecc25ace5))
* Fix misdetection of HEVC support on MS Edge ([#3897](https://github.com/willdharris/shaka-player/issues/3897)) ([dfb3699](https://github.com/willdharris/shaka-player/commit/dfb369935b9e84fe69a7d38c7904fb0e00dc064a)), closes [#3860](https://github.com/willdharris/shaka-player/issues/3860)
* Fix missing throughput in CMCD for HLS live ([#3874](https://github.com/willdharris/shaka-player/issues/3874)) ([df55944](https://github.com/willdharris/shaka-player/commit/df55944e8f49bdf8e34a679219cd6596ba46c777)), closes [#3873](https://github.com/willdharris/shaka-player/issues/3873)
* Fix multi-period DASH with descriptive audio ([#4629](https://github.com/willdharris/shaka-player/issues/4629)) ([81ccd5c](https://github.com/willdharris/shaka-player/commit/81ccd5c73ba5e021466b82c05f8b607b0c345849)), closes [#4500](https://github.com/willdharris/shaka-player/issues/4500)
* Fix parsing error on Chromecast when resyncing HLS ([#4869](https://github.com/willdharris/shaka-player/issues/4869)) ([afca6af](https://github.com/willdharris/shaka-player/commit/afca6af230685a0c9b556fddb46341380b611923)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* Fix PERIOD_FLATTENING_FAILED error when periods have different base sample types ([#4206](https://github.com/willdharris/shaka-player/issues/4206)) ([b757a81](https://github.com/willdharris/shaka-player/commit/b757a81902a2159b217e7cb6a1445ab6d4d69bf4)), closes [#4202](https://github.com/willdharris/shaka-player/issues/4202)
* Fix playRangeEnd for certain content ([#4068](https://github.com/willdharris/shaka-player/issues/4068)) ([5c81f3b](https://github.com/willdharris/shaka-player/commit/5c81f3bddb9e48431556f4d622364043fee4ea80)), closes [#4026](https://github.com/willdharris/shaka-player/issues/4026)
* Fix potential AV sync issues after seek or adaptation ([#4886](https://github.com/willdharris/shaka-player/issues/4886)) ([c42565c](https://github.com/willdharris/shaka-player/commit/c42565ccb9c69455307742e1f5c3c763892ec1c6)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* Fix potential duplicate segments, AV sync issues ([#4884](https://github.com/willdharris/shaka-player/issues/4884)) ([52f4b63](https://github.com/willdharris/shaka-player/commit/52f4b638b155b4b7f7f6a0bd14e6e9661d5cceba)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* Fix rare exception after StreamingEngine teardown ([#4830](https://github.com/willdharris/shaka-player/issues/4830)) ([234beef](https://github.com/willdharris/shaka-player/commit/234beefb73ea7f8a7442112eb2efb78d619a13cb)), closes [#4813](https://github.com/willdharris/shaka-player/issues/4813)
* Fix segment index assertions with DAI ([#4348](https://github.com/willdharris/shaka-player/issues/4348)) ([c2b3853](https://github.com/willdharris/shaka-player/commit/c2b3853a56e816c97fab57f961f295b7272e410e))
* Fix subtitles not added to DOM region ([#4733](https://github.com/willdharris/shaka-player/issues/4733)) ([4081434](https://github.com/willdharris/shaka-player/commit/4081434eba7f90ea7fe8544665baf99f59ec5863)), closes [#4680](https://github.com/willdharris/shaka-player/issues/4680)
* fix support clear and encrypted periods ([#4606](https://github.com/willdharris/shaka-player/issues/4606)) ([6256db3](https://github.com/willdharris/shaka-player/commit/6256db3af5065ea1db1951ea7583d4608ce5e28d))
* Fix support for TTAF1 namespace (old version of TTML) ([#3864](https://github.com/willdharris/shaka-player/issues/3864)) ([771619f](https://github.com/willdharris/shaka-player/commit/771619ff0ef8ba0e3da9569ded3894b428d03c58)), closes [#3009](https://github.com/willdharris/shaka-player/issues/3009)
* Fix TextDecoder fallback and browser support check ([#4403](https://github.com/willdharris/shaka-player/issues/4403)) ([04fc0d4](https://github.com/willdharris/shaka-player/commit/04fc0d47c3895f294401b588ed49cc4360f31be1))
* Fix timestamp offset for ID3 on DAI-HLS ([#4696](https://github.com/willdharris/shaka-player/issues/4696)) ([386a28a](https://github.com/willdharris/shaka-player/commit/386a28a8eb0cd995e7eee9f95c97b7f8e7542774))
* Fix UI captions icon state ([#4384](https://github.com/willdharris/shaka-player/issues/4384)) ([d462633](https://github.com/willdharris/shaka-player/commit/d46263333ba3de68707d521b997c40c5ba492fda)), closes [#4358](https://github.com/willdharris/shaka-player/issues/4358)
* Fix usage of WebCrypto in old browsers ([#4711](https://github.com/willdharris/shaka-player/issues/4711)) ([9afce3b](https://github.com/willdharris/shaka-player/commit/9afce3b423406aae0cd2841bb39071c90196c792))
* Fix vanishing tracks while offline ([#4426](https://github.com/willdharris/shaka-player/issues/4426)) ([c935cc1](https://github.com/willdharris/shaka-player/commit/c935cc17703297a44b3ce3bda75d8f2ea37f4147)), closes [#4408](https://github.com/willdharris/shaka-player/issues/4408)
* Fix VP9 codec checks on Mac Firefox ([#4391](https://github.com/willdharris/shaka-player/issues/4391)) ([b6ab769](https://github.com/willdharris/shaka-player/commit/b6ab76976211852e96b2883562166a5e1e4dd0f2))
* Fix VTT cue timing in HLS ([#4217](https://github.com/willdharris/shaka-player/issues/4217)) ([5818260](https://github.com/willdharris/shaka-player/commit/58182605a7da3c18a7331828c319c88446a13d52)), closes [#4191](https://github.com/willdharris/shaka-player/issues/4191)
* Fix WebVTT parser failure on REGION blocks ([#4915](https://github.com/willdharris/shaka-player/issues/4915)) ([da84a2c](https://github.com/willdharris/shaka-player/commit/da84a2c86b7d7e6968472ce9d2bbe09e0608dbef))
* Fixed LCEVC decode breaking dependencies issue and read me addition ([#4565](https://github.com/willdharris/shaka-player/issues/4565)) ([3c75d1a](https://github.com/willdharris/shaka-player/commit/3c75d1a71aea039c802555031fffbf3cad77f6fc))
* focus on first element when back to the settings menu ([#4653](https://github.com/willdharris/shaka-player/issues/4653)) ([b40b6e7](https://github.com/willdharris/shaka-player/commit/b40b6e7669d4ccf8677a6d262767f3e155eb02e6)), closes [#4652](https://github.com/willdharris/shaka-player/issues/4652)
* Force using mcap polyfill on EOS browsers ([#4630](https://github.com/willdharris/shaka-player/issues/4630)) ([6191d58](https://github.com/willdharris/shaka-player/commit/6191d5894deb679ed68da54357dc1f6831edeb23))
* **HLS:** Add a guard on closeSegmentIndex ([#4615](https://github.com/willdharris/shaka-player/issues/4615)) ([57ce56b](https://github.com/willdharris/shaka-player/commit/57ce56b8d2bd5d2b1626b38594e6d54defd10255))
* **hls:** Fix AV sync issues, fallback to sequence numbers if PROGRAM-DATE-TIME ignored ([#4289](https://github.com/willdharris/shaka-player/issues/4289)) ([314a987](https://github.com/willdharris/shaka-player/commit/314a987ecf85b47cc8a6cef08f390ef817e11c49)), closes [#4287](https://github.com/willdharris/shaka-player/issues/4287)
* **HLS:** Fix AV sync over ad boundaries ([#4824](https://github.com/willdharris/shaka-player/issues/4824)) ([35033bb](https://github.com/willdharris/shaka-player/commit/35033bb2db1ca630f4f7895e7678bd0ee6cfd9ef)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* **hls:** Fix av1 codec selection in HLS. ([#4203](https://github.com/willdharris/shaka-player/issues/4203)) ([5e13495](https://github.com/willdharris/shaka-player/commit/5e1349570d64c17e6ca1fcdc5ffde1076ea9a999))
* **HLS:** Fix detection of Media Playlist for audio and video only in MP4 ([#4803](https://github.com/willdharris/shaka-player/issues/4803)) ([76f96b9](https://github.com/willdharris/shaka-player/commit/76f96b9fee2dc43b03f6803dd80c51fdc5b73a9e))
* **HLS:** Fix detection of WebVTT subtitles in HLS by extension ([#4663](https://github.com/willdharris/shaka-player/issues/4663)) ([8f698c6](https://github.com/willdharris/shaka-player/commit/8f698c6eaad6e1019f388e2d36f28883a142ddfb))
* **HLS:** Fix detection of WebVTT subtitles in HLS by extension ([#4928](https://github.com/willdharris/shaka-player/issues/4928)) ([15b0388](https://github.com/willdharris/shaka-player/commit/15b03884bb61542f451f7854a8562aa3d759ed0f)), closes [#4929](https://github.com/willdharris/shaka-player/issues/4929)
* **HLS:** Fix discontinuity tracking ([#4881](https://github.com/willdharris/shaka-player/issues/4881)) ([fc3d5c1](https://github.com/willdharris/shaka-player/commit/fc3d5c144708c748d90f25de34c436495db2a816)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* **HLS:** Fix duplicate hinted segments ([#4258](https://github.com/willdharris/shaka-player/issues/4258)) ([9171f73](https://github.com/willdharris/shaka-player/commit/9171f733e8de0b811ebac71d5ddbe0cb1ff7c75b)), closes [#4223](https://github.com/willdharris/shaka-player/issues/4223)
* **HLS:** fix lazy load with multiple raw audio tracks ([#4715](https://github.com/willdharris/shaka-player/issues/4715)) ([76149ae](https://github.com/willdharris/shaka-player/commit/76149ae7453ccff852483b437c9de72cb6ebfbf5))
* **HLS:** Fix lazy-loading of TS content ([#4601](https://github.com/willdharris/shaka-player/issues/4601)) ([dd7356d](https://github.com/willdharris/shaka-player/commit/dd7356d0e0655f59792b3f992841d4c0c8d5540a))
* **HLS:** Fix lowLatencyPresentationDelay when using autoLowLatencyMode ([#4712](https://github.com/willdharris/shaka-player/issues/4712)) ([877e954](https://github.com/willdharris/shaka-player/commit/877e9542170aa0467d28b5edb5a4b1b29dd4452e))
* **HLS:** Fix missing roles ([#4760](https://github.com/willdharris/shaka-player/issues/4760)) ([2bc481d](https://github.com/willdharris/shaka-player/commit/2bc481decd11ec1db93e3bb5ca0db4a644b13269)), closes [#4759](https://github.com/willdharris/shaka-player/issues/4759)
* **hls:** Fix raw format detection when the main playlist hasn't type ([#4583](https://github.com/willdharris/shaka-player/issues/4583)) ([d319718](https://github.com/willdharris/shaka-player/commit/d319718eded6e36f4fc705588de84a301a428d49))
* **hls:** Fix single-variant HLS streams ([#4573](https://github.com/willdharris/shaka-player/issues/4573)) ([62906bd](https://github.com/willdharris/shaka-player/commit/62906bdc9a26456d213a0c5d33f00b4454cdfb5b)), closes [#1936](https://github.com/willdharris/shaka-player/issues/1936) [#3536](https://github.com/willdharris/shaka-player/issues/3536)
* **HLS:** Fix support for mixed AES-128/NONE decryption ([#4847](https://github.com/willdharris/shaka-player/issues/4847)) ([452694d](https://github.com/willdharris/shaka-player/commit/452694d59785f2e88cab607618f10ba980851805))
* **HLS:** Fix support legacy AVC1 codec used in HLS ([#4716](https://github.com/willdharris/shaka-player/issues/4716)) ([c3ff8e5](https://github.com/willdharris/shaka-player/commit/c3ff8e5e5f6ad5867ed0650e153627dafcb1bcf7))
* **hls:** Fix type error in lazy-loading ([#4687](https://github.com/willdharris/shaka-player/issues/4687)) ([28b73b9](https://github.com/willdharris/shaka-player/commit/28b73b921d1dbdc6d7e016aa8e0a000e62318ed3))
* **hls:** Fix X-PRELOAD-HINT failure with LL mode off ([#4212](https://github.com/willdharris/shaka-player/issues/4212)) ([86497a5](https://github.com/willdharris/shaka-player/commit/86497a5089e272ed682f017f5ed9135108be5a65)), closes [#4185](https://github.com/willdharris/shaka-player/issues/4185)
* **hls:** Fixed buffering issue with live HLS ([#4002](https://github.com/willdharris/shaka-player/issues/4002)) ([c438e85](https://github.com/willdharris/shaka-player/commit/c438e857f2f122eb45899148e067d68ffec3477c))
* **HLS:** IMSC1 subtitles not working in a HLS stream ([#4942](https://github.com/willdharris/shaka-player/issues/4942)) ([974f5dc](https://github.com/willdharris/shaka-player/commit/974f5dcb630977fcdb8ac67d1af001919cf40f7f))
* **HLS:** Infer missing codecs from config ([#4656](https://github.com/willdharris/shaka-player/issues/4656)) ([08fc7dd](https://github.com/willdharris/shaka-player/commit/08fc7dd717390c61dcc3304c58bfff5c87c77833))
* **HLS:** Return 0-0 seek range until fully loaded ([#4590](https://github.com/willdharris/shaka-player/issues/4590)) ([bf50ada](https://github.com/willdharris/shaka-player/commit/bf50ada6874879b33ac1acd34ec7e5375eb4c45d))
* **HLS:** Single alternative video renditions not working ([#4785](https://github.com/willdharris/shaka-player/issues/4785)) ([6915a97](https://github.com/willdharris/shaka-player/commit/6915a970efead95d41dbe05a824f699e7c68a3a5))
* **HLS:** skip whitespace in attributes ([#3884](https://github.com/willdharris/shaka-player/issues/3884)) ([ea6c02a](https://github.com/willdharris/shaka-player/commit/ea6c02aece1510598a898c235e66335d20eabedb))
* **hls:** Support playing media playlists directly ([#4080](https://github.com/willdharris/shaka-player/issues/4080)) ([48dd205](https://github.com/willdharris/shaka-player/commit/48dd20562c2226f61cc753a922629e44c1866f6d)), closes [#3536](https://github.com/willdharris/shaka-player/issues/3536)
* **image:** Fix thumbnails issues ([#3858](https://github.com/willdharris/shaka-player/issues/3858)) ([087a9b4](https://github.com/willdharris/shaka-player/commit/087a9b489b030aa0dc80011ca4e0a0c7a4124ecd))
* Increase IndexedDB timeout ([#4984](https://github.com/willdharris/shaka-player/issues/4984)) ([ea290ab](https://github.com/willdharris/shaka-player/commit/ea290ab958385f81ef8ad4ce855100dc21d26667))
* Limit key ids to 32 characters ([#4614](https://github.com/willdharris/shaka-player/issues/4614)) ([9531b07](https://github.com/willdharris/shaka-player/commit/9531b07296163d8cc5c8416f0baa4ffd29c0a90d))
* Make encoding problem detection more robust ([#4885](https://github.com/willdharris/shaka-player/issues/4885)) ([0e3621c](https://github.com/willdharris/shaka-player/commit/0e3621c21e914b38640e0c2c8cf9bece6158efad)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* Make XML parsing secure ([#4598](https://github.com/willdharris/shaka-player/issues/4598)) ([a731eba](https://github.com/willdharris/shaka-player/commit/a731eba804ae1a3f3ee3061550fa43ea82e06313))
* Manually order key for decodingInfo cache ([#4795](https://github.com/willdharris/shaka-player/issues/4795)) ([806a9a8](https://github.com/willdharris/shaka-player/commit/806a9a81c4e6d16d8affa46010665479bfa5bdff))
* **MCap:** Remove robustness when robustness value is default ([#4953](https://github.com/willdharris/shaka-player/issues/4953)) ([7439a26](https://github.com/willdharris/shaka-player/commit/7439a264d63ff5b68b0411098939eb19708d7134))
* Missing AES-128 key of last HLS segment ([#4519](https://github.com/willdharris/shaka-player/issues/4519)) ([3d0f752](https://github.com/willdharris/shaka-player/commit/3d0f752c7d0677f750dbbd9bcd2895358358628f)), closes [#4517](https://github.com/willdharris/shaka-player/issues/4517)
* New EME polyfill fixes EME/MCap issues on some smart TVs ([#4279](https://github.com/willdharris/shaka-player/issues/4279)) ([db1b20e](https://github.com/willdharris/shaka-player/commit/db1b20ec77f74472dd24f493f2a26c02b17927bc))
* **offline:** Add storage muxer init timeout ([#4566](https://github.com/willdharris/shaka-player/issues/4566)) ([d4d3740](https://github.com/willdharris/shaka-player/commit/d4d37407c87b7c032a16679e96b318146bbdee22))
* **offline:** Clean up orphaned segments on abort ([#4177](https://github.com/willdharris/shaka-player/issues/4177)) ([c07447f](https://github.com/willdharris/shaka-player/commit/c07447f00e9095020890366695561b71b045e55a))
* **offline:** Speed up offline storage by ~87% ([#4176](https://github.com/willdharris/shaka-player/issues/4176)) ([c1c9613](https://github.com/willdharris/shaka-player/commit/c1c96135120480afc9615713812eecc4a51f153b)), closes [#4166](https://github.com/willdharris/shaka-player/issues/4166)
* **performance:** Eliminate use of ES6 generators ([#4092](https://github.com/willdharris/shaka-player/issues/4092)) ([57c7324](https://github.com/willdharris/shaka-player/commit/57c73241a0e8ce1615f7b3aca4c3ad8f69b7e8c2)), closes [#4062](https://github.com/willdharris/shaka-player/issues/4062)
* **playhead:** Safeguard getStallsDetected as stallDetector can be null ([#4581](https://github.com/willdharris/shaka-player/issues/4581)) ([21ceaca](https://github.com/willdharris/shaka-player/commit/21ceacab9e9577c18cef7f6c76f57f39eca3dca9))
* Polyfill missing AbortController on Tizen ([#4707](https://github.com/willdharris/shaka-player/issues/4707)) ([75ef975](https://github.com/willdharris/shaka-player/commit/75ef9752a4c7d618a934da773e35ed4d27a9bdf5))
* Populate track's spatialAudio property ([#4291](https://github.com/willdharris/shaka-player/issues/4291)) ([713f461](https://github.com/willdharris/shaka-player/commit/713f461c62b23680557f8d6c4b9c3126bb604f9e))
* Prevent content from being restarted after Postroll ads ([#4979](https://github.com/willdharris/shaka-player/issues/4979)) ([64e94f1](https://github.com/willdharris/shaka-player/commit/64e94f1c79f3eda75e762474502ba2fc70fb9ee2)), closes [#4445](https://github.com/willdharris/shaka-player/issues/4445)
* Release region timeline when unloading ([#4871](https://github.com/willdharris/shaka-player/issues/4871)) ([a236180](https://github.com/willdharris/shaka-player/commit/a2361806ce3b2eab60024cdca81ecb1ea5a0ed8a)), closes [#4850](https://github.com/willdharris/shaka-player/issues/4850)
* Remove IE 11 from default browsers for Windows ([#4272](https://github.com/willdharris/shaka-player/issues/4272)) ([490b06c](https://github.com/willdharris/shaka-player/commit/490b06cd45d09c7567056535f4b8dc6f3e2e5733)), closes [#4271](https://github.com/willdharris/shaka-player/issues/4271)
* Resolve load failures for TS-based content on Android-based Cast devices ([#4569](https://github.com/willdharris/shaka-player/issues/4569)). ([#4570](https://github.com/willdharris/shaka-player/issues/4570)) ([65903aa](https://github.com/willdharris/shaka-player/commit/65903aa27b5723632ff16a92059cb20c4879fc59))
* Respect existing app usage of Cast SDK ([#4523](https://github.com/willdharris/shaka-player/issues/4523)) ([8d3d556](https://github.com/willdharris/shaka-player/commit/8d3d556edaa817af686e1577f0a0bad92d0c74d4)), closes [#4521](https://github.com/willdharris/shaka-player/issues/4521)
* return width and height in the stats when we are using src= ([#4435](https://github.com/willdharris/shaka-player/issues/4435)) ([9bbfb57](https://github.com/willdharris/shaka-player/commit/9bbfb57cb4e2c0653e6eb5681e10714cb939bad9))
* Revert "Add missing module export in generated typescript defs" ([#4175](https://github.com/willdharris/shaka-player/issues/4175)) ([fe4f5c6](https://github.com/willdharris/shaka-player/commit/fe4f5c6e19214d6cf4d42da9430de03040532bab)), closes [#4167](https://github.com/willdharris/shaka-player/issues/4167)
* Select first of identical audio streams ([#3869](https://github.com/willdharris/shaka-player/issues/3869)) ([a6d8610](https://github.com/willdharris/shaka-player/commit/a6d8610241dc7c8abd56cf7f0d48993d6139dcae))
* Simplify transmuxer to allow more mimetypes in the future ([#4642](https://github.com/willdharris/shaka-player/issues/4642)) ([a14e84b](https://github.com/willdharris/shaka-player/commit/a14e84b5c9a6feb8f7f2efcbae52fe9691d48412))
* Support multiple chapter tracks with same language ([#3868](https://github.com/willdharris/shaka-player/issues/3868)) ([8c626ae](https://github.com/willdharris/shaka-player/commit/8c626aec238c01ebad7ccd06c9313e4f2e99d383)), closes [#3597](https://github.com/willdharris/shaka-player/issues/3597)
* Sync each segment against EXT-X-PROGRAM-DATE-TIME ([#4870](https://github.com/willdharris/shaka-player/issues/4870)) ([50c9df4](https://github.com/willdharris/shaka-player/commit/50c9df49a70e17b8b2973ae7a7d47d7856cd09f8)), closes [#4589](https://github.com/willdharris/shaka-player/issues/4589)
* **text:** Fix caption overlap. ([bf67d87](https://github.com/willdharris/shaka-player/commit/bf67d87387b1dfc4d3d8e0661bfe4efb1e4083b2)), closes [#3850](https://github.com/willdharris/shaka-player/issues/3850) [#3741](https://github.com/willdharris/shaka-player/issues/3741)
* **text:** Fix cue region rendering in UI ([#4412](https://github.com/willdharris/shaka-player/issues/4412)) ([b1f46db](https://github.com/willdharris/shaka-player/commit/b1f46dbc3a685b0216600835e24fd13c504e1b62)), closes [#4381](https://github.com/willdharris/shaka-player/issues/4381)
* **text:** Fix TTML render timing and line break issues for native display ([122f223](https://github.com/willdharris/shaka-player/commit/122f223d19732bf5977ab8a5c93bbc4d934da1d7))
* **text:** Fix webvtt offset in sequence mode ([#3955](https://github.com/willdharris/shaka-player/issues/3955)) ([a4e9267](https://github.com/willdharris/shaka-player/commit/a4e926772e1b754fe968ee6f97490f08a40fe535)), closes [#2337](https://github.com/willdharris/shaka-player/issues/2337)
* **text:** Inherit alignment from regions. ([e9df8fb](https://github.com/willdharris/shaka-player/commit/e9df8fb10c3752cb833e89c8ac793241497e29b6))
* **text:** Made nested cues inherit region ([#3837](https://github.com/willdharris/shaka-player/issues/3837)) ([3ff48cb](https://github.com/willdharris/shaka-player/commit/3ff48cba9b28a29e8decc11898e326d7918bc8f4)), closes [#3743](https://github.com/willdharris/shaka-player/issues/3743)
* Treat regions uniquely ([#4841](https://github.com/willdharris/shaka-player/issues/4841)) ([5681efe](https://github.com/willdharris/shaka-player/commit/5681efe95cb7e32e2eddd6fcae1b44d265407939)), closes [#4839](https://github.com/willdharris/shaka-player/issues/4839)
* **TTML:** Add font-family mapping ([#4801](https://github.com/willdharris/shaka-player/issues/4801)) ([db8987d](https://github.com/willdharris/shaka-player/commit/db8987d6dfdb59b9f6d187051d47edf6d846a9ed))
* **ttml:** Center subtitles by default ([#4023](https://github.com/willdharris/shaka-player/issues/4023)) ([f2f24d5](https://github.com/willdharris/shaka-player/commit/f2f24d528f71e59c81d6172c24da2f412ca18d70))
* **ttml:** Default TTML background color to transparent if unspecified ([#4496](https://github.com/willdharris/shaka-player/issues/4496)) ([32b0a90](https://github.com/willdharris/shaka-player/commit/32b0a90a8c583bba03a3d7b035a1244d325e3da6)), closes [#4468](https://github.com/willdharris/shaka-player/issues/4468)
* **TTML:** Fix duplicate cues overlapping segment boundaries ([#4798](https://github.com/willdharris/shaka-player/issues/4798)) ([bd75032](https://github.com/willdharris/shaka-player/commit/bd75032d63755044d2d78ca109e2e9f132e36a00)), closes [#4631](https://github.com/willdharris/shaka-player/issues/4631)
* **UI:** Ad position and ad counter are too close to each other ([#4416](https://github.com/willdharris/shaka-player/issues/4416)) ([8376410](https://github.com/willdharris/shaka-player/commit/83764104277363b6ce0e05d8e53449ff454c6f0e))
* **UI:** Add cursor pointer to range elements ([#4059](https://github.com/willdharris/shaka-player/issues/4059)) ([33e8400](https://github.com/willdharris/shaka-player/commit/33e84009dc9f6d48884ecfc2f66eeb285f60d05a)), closes [#3220](https://github.com/willdharris/shaka-player/issues/3220)
* **ui:** Avoid submitting form if player is inside form ([#4866](https://github.com/willdharris/shaka-player/issues/4866)) ([da21850](https://github.com/willdharris/shaka-player/commit/da21850f21ac94fc06349b528a2bf7c17487b681)), closes [#4861](https://github.com/willdharris/shaka-player/issues/4861)
* **ui:** Check event cancelable before event.preventDefault ([#4690](https://github.com/willdharris/shaka-player/issues/4690)) ([6d8de72](https://github.com/willdharris/shaka-player/commit/6d8de72dafa757ac7d00ef7c4acbfab6529b15c2))
* **ui:** Fix exception on screen rotation if fullscreen is not supported ([#4669](https://github.com/willdharris/shaka-player/issues/4669)) ([fd93f6a](https://github.com/willdharris/shaka-player/commit/fd93f6ae1bc917061c035abcfb835855e336bb06))
* **ui:** Fix iOS fullscreen on rotation ([#4679](https://github.com/willdharris/shaka-player/issues/4679)) ([86256f4](https://github.com/willdharris/shaka-player/commit/86256f49202e64d15f53c7d29e5cac150f018d5c))
* **UI:** Fix text UI not updating when text is disabled ([#3867](https://github.com/willdharris/shaka-player/issues/3867)) ([9f53d39](https://github.com/willdharris/shaka-player/commit/9f53d394279066f29a2d391b6964cba11c4a3e1e)), closes [#3728](https://github.com/willdharris/shaka-player/issues/3728)
* **UI:** Suppress error log from fullscreen button on desktop ([#4823](https://github.com/willdharris/shaka-player/issues/4823)) ([99da4ce](https://github.com/willdharris/shaka-player/commit/99da4ce7dea43ae67870acbcf708ed6479efa7cc)), closes [#4822](https://github.com/willdharris/shaka-player/issues/4822)
* **ui:** Widen touchable button area ([#3249](https://github.com/willdharris/shaka-player/issues/3249)) ([6c0283e](https://github.com/willdharris/shaka-player/commit/6c0283e7d040fd0df9383454b174a7ceb2678c89))
* Update main branch Cast receiver ID ([#4364](https://github.com/willdharris/shaka-player/issues/4364)) ([46b27f1](https://github.com/willdharris/shaka-player/commit/46b27f19e099d44ab3929222da7a3bcb41bdb230))
* Upgrade mux.js to version that emits partial ID3 when malformed ([#4259](https://github.com/willdharris/shaka-player/issues/4259)) ([dc88fe0](https://github.com/willdharris/shaka-player/commit/dc88fe0814f82aa447a3fa8f7098c85621faf9c6)), closes [#3761](https://github.com/willdharris/shaka-player/issues/3761)
* Use middle segment when guessing MIME type on HLS ([#4269](https://github.com/willdharris/shaka-player/issues/4269)) ([#4270](https://github.com/willdharris/shaka-player/issues/4270)) ([3d27d2a](https://github.com/willdharris/shaka-player/commit/3d27d2a2cfeb8fa21f3415baaf013567dcccf480))
* Virgin Media set top box is incorrectly categorized as Apple/Safari ([df79470](https://github.com/willdharris/shaka-player/commit/df79470af088089f8beba2f44a236593820d655a))
* VTT Cue Parsing On PlayStation 4 ([#4340](https://github.com/willdharris/shaka-player/issues/4340)) ([b5da41e](https://github.com/willdharris/shaka-player/commit/b5da41ed80b96e8edae970c39dd5fac7348a9a55)), closes [#4321](https://github.com/willdharris/shaka-player/issues/4321)
* **VTT:** Fix combining style selectors ([#4934](https://github.com/willdharris/shaka-player/issues/4934)) ([128562d](https://github.com/willdharris/shaka-player/commit/128562d93e90ba406c8cbde1af730052fcfc5175))
* **VTT:** Fix spacing between text lines ([#4961](https://github.com/willdharris/shaka-player/issues/4961)) ([2d0469f](https://github.com/willdharris/shaka-player/commit/2d0469fb4a2ee62d67fb9f0dbac8009b667156f2))
* Wait for chapters track to be loaded ([#4228](https://github.com/willdharris/shaka-player/issues/4228)) ([80e81f1](https://github.com/willdharris/shaka-player/commit/80e81f139129dbe1c797ee07fedc1217b8790b53)), closes [#4186](https://github.com/willdharris/shaka-player/issues/4186)
* WebVTT line not correctly positioned in UITextDisplayer ([#4567](https://github.com/willdharris/shaka-player/issues/4567)) ([#4682](https://github.com/willdharris/shaka-player/issues/4682)) ([140aefe](https://github.com/willdharris/shaka-player/commit/140aefee04718faa631ba090d6313e372b608fc1))
* **WebVTT:** Add support to &nbsp;, &lrm; and &rlm; ([#4920](https://github.com/willdharris/shaka-player/issues/4920)) ([726ef42](https://github.com/willdharris/shaka-player/commit/726ef425b095543a216ba8fed0dfe6d1657e2e95))
* **WebVTT:** Fix horizontal positioning with cue box size ([#4949](https://github.com/willdharris/shaka-player/issues/4949)) ([f456318](https://github.com/willdharris/shaka-player/commit/f45631834d363b23eb8897b03bce9b3b1b50ca9a))
* **WebVTT:** Fix voice tag styles ([a5f8b43](https://github.com/willdharris/shaka-player/commit/a5f8b4361e38973c74d0180b5ba7769f636c651d))
* **WebVTT:** Fix voices with styles and support to multiple styles ([#4922](https://github.com/willdharris/shaka-player/issues/4922)) ([68968c1](https://github.com/willdharris/shaka-player/commit/68968c17d8ad1eaca6afa6d86bb4f8b1baa69d10))
* **WebVTT:** Tags in the WebVTT subtitle are not parsed ([#4960](https://github.com/willdharris/shaka-player/issues/4960)) ([d4fc54f](https://github.com/willdharris/shaka-player/commit/d4fc54f8dc68668244b72405b9f972c711b9a868))


### Performance Improvements

* Caching mediaSource support for browser engine ([#4778](https://github.com/willdharris/shaka-player/issues/4778)) ([ad6c085](https://github.com/willdharris/shaka-player/commit/ad6c08561d509cd0cf0e7f4736ba4473774577d9))

## [4.3.0](https://github.com/shaka-project/shaka-player/compare/v4.2.0...v4.3.0) (2022-11-10)


### Features

* Add AAC transmuxer ([#4632](https://github.com/shaka-project/shaka-player/issues/4632)) ([8623a5d](https://github.com/shaka-project/shaka-player/commit/8623a5d0304dd3e65c613b176b4afa38a6dc96b5))
* Add config for sequenceMode in DASH ([#4607](https://github.com/shaka-project/shaka-player/issues/4607)) ([aff2a5d](https://github.com/shaka-project/shaka-player/commit/aff2a5d9e81e5fdfaeb91275aaa0821aa189d34f))
* Add external thumbnails support ([#4497](https://github.com/shaka-project/shaka-player/issues/4497)) ([3582f0a](https://github.com/shaka-project/shaka-player/commit/3582f0a7274d6bb6f0bbfdf2ad51c5ecfb6f974b))
* Add external thumbnails with sprites support ([#4584](https://github.com/shaka-project/shaka-player/issues/4584)) ([86cb3e7](https://github.com/shaka-project/shaka-player/commit/86cb3e714cc3f59cff8f0b33adb291e128c32609))
* Add limited support for HLS "identity" key format ([#4451](https://github.com/shaka-project/shaka-player/issues/4451)) ([b1e81a6](https://github.com/shaka-project/shaka-player/commit/b1e81a684afe086b7a37ea29bbbfc972575ba332)), closes [#2146](https://github.com/shaka-project/shaka-player/issues/2146)
* Adds ChannelCount as a filter to the Player Select Audio Track Method ([#4552](https://github.com/shaka-project/shaka-player/issues/4552)) ([9dd945c](https://github.com/shaka-project/shaka-player/commit/9dd945c3df7364b90a9c3cb3150021492ebb7d81)), closes [#4550](https://github.com/shaka-project/shaka-player/issues/4550)
* **ads:** Add getDescription to CS and SS ads ([#4526](https://github.com/shaka-project/shaka-player/issues/4526)) ([7d2a170](https://github.com/shaka-project/shaka-player/commit/7d2a170336b828e8aac871ff276dbb8b42c384a4))
* **ads:** Add getTitle to CS and SS ads ([#4513](https://github.com/shaka-project/shaka-player/issues/4513)) ([a019065](https://github.com/shaka-project/shaka-player/commit/a019065d5d19598c9d0ba6ce5d4d79070f3e3cba))
* **ads:** Ignore ad events with no associated ad ([#4488](https://github.com/shaka-project/shaka-player/issues/4488)) ([e826eb8](https://github.com/shaka-project/shaka-player/commit/e826eb8eec207dd2ebd4d4ee1e44510ebff22b71)), closes [#4481](https://github.com/shaka-project/shaka-player/issues/4481)
* Allow add extra features to MediaSource.addSourceBuffer ([#4527](https://github.com/shaka-project/shaka-player/issues/4527)) ([4033be7](https://github.com/shaka-project/shaka-player/commit/4033be7c5b1d1c397d5a4840ef7333a26ca93983))
* Allow clearKey configuration in base64 or hex ([#4627](https://github.com/shaka-project/shaka-player/issues/4627)) ([29ffc89](https://github.com/shaka-project/shaka-player/commit/29ffc89a117e6f4285c0133dce555e44a1414228))
* Allow customization of HLS Live behavior ([#4578](https://github.com/shaka-project/shaka-player/issues/4578)) ([4914201](https://github.com/shaka-project/shaka-player/commit/4914201f86f6e683b64c7cc3338cdf67cee544cf))
* Allow playback of HLS Media Playlist with AAC by default ([#4564](https://github.com/shaka-project/shaka-player/issues/4564)) ([757b34e](https://github.com/shaka-project/shaka-player/commit/757b34e5959f14c9a5b5aed173cc99d98a794a40))
* Allow playback of HLS Media Playlist with RAW formats by default and support ID3 ([#4591](https://github.com/shaka-project/shaka-player/issues/4591)) ([18d8367](https://github.com/shaka-project/shaka-player/commit/18d836746e20164409c070c787e08b8bcf4da180))
* Automatic ABR quality restrictions based on screen size ([#4515](https://github.com/shaka-project/shaka-player/issues/4515)) ([b5935a8](https://github.com/shaka-project/shaka-player/commit/b5935a8a6b3b05c0c4cd10774a9625b0bbaf1cf6))
* **demo:** Demo visualizer for buffered ranges. ([#4417](https://github.com/shaka-project/shaka-player/issues/4417)) ([55d0a15](https://github.com/shaka-project/shaka-player/commit/55d0a1556a273b6af0da16197b424796a175adf8))
* enable uninstalling PatchedMediaKeysApple ([#4471](https://github.com/shaka-project/shaka-player/issues/4471)) ([7166f0c](https://github.com/shaka-project/shaka-player/commit/7166f0c1d09ad458abf0ee18e961c88f415afefc)), closes [#4469](https://github.com/shaka-project/shaka-player/issues/4469)
* **HLS:** Add support for EXT-X-SESSION-KEY tag ([#4655](https://github.com/shaka-project/shaka-player/issues/4655)) ([172c9f8](https://github.com/shaka-project/shaka-player/commit/172c9f834ab6575cf9cdb2f825abd9961b9ad7fb)), closes [#917](https://github.com/shaka-project/shaka-player/issues/917)
* **HLS:** allow customize live segments delay ([#4585](https://github.com/shaka-project/shaka-player/issues/4585)) ([1f558a8](https://github.com/shaka-project/shaka-player/commit/1f558a82c14e3d68a3a67cbb58879f2ab12549d0))
* **HLS:** Allow mp3 playback with mp4a.40.34 ([#4592](https://github.com/shaka-project/shaka-player/issues/4592)) ([8f892b1](https://github.com/shaka-project/shaka-player/commit/8f892b136f4cadce6a4d0585f88d4eccaf065f1b))
* **HLS:** Lazy-load HLS media playlists ([#4511](https://github.com/shaka-project/shaka-player/issues/4511)) ([b2f279d](https://github.com/shaka-project/shaka-player/commit/b2f279db1b111e3c8a02706551f466468621cd97)), closes [#1936](https://github.com/shaka-project/shaka-player/issues/1936)
* **HLS:** Support for HLS key rotation ([#4568](https://github.com/shaka-project/shaka-player/issues/4568)) ([3846eea](https://github.com/shaka-project/shaka-player/commit/3846eeac3f3777c35e61f479958015062f4275af)), closes [#741](https://github.com/shaka-project/shaka-player/issues/741)
* Improved LCEVC integration ([#4560](https://github.com/shaka-project/shaka-player/issues/4560)) ([50062f5](https://github.com/shaka-project/shaka-player/commit/50062f58adea248a403461b50b65c3a585de31b4))
* LCEVC Integration ([#4050](https://github.com/shaka-project/shaka-player/issues/4050)) ([284ea63](https://github.com/shaka-project/shaka-player/commit/284ea63a60178cbc87ce2fde769eb06bdb8fb8ea))
* New autoShowText config to change initial text visibility behavior ([#3421](https://github.com/shaka-project/shaka-player/issues/3421)) ([5c24410](https://github.com/shaka-project/shaka-player/commit/5c24410560d8afa13e6f2492590f13506419b59e))
* Parse and surface "prft" boxes as events ([#4389](https://github.com/shaka-project/shaka-player/issues/4389)) ([89777dd](https://github.com/shaka-project/shaka-player/commit/89777dd7043ae2b5fa213ab73e43f93482bb86d0)), closes [#4382](https://github.com/shaka-project/shaka-player/issues/4382)
* Parse ID3 metadata ([#4409](https://github.com/shaka-project/shaka-player/issues/4409)) ([95bbf72](https://github.com/shaka-project/shaka-player/commit/95bbf72f426f9df899193f6083197a77191c0c4f))
* Support HTML-escaped cues in VTT ([#4660](https://github.com/shaka-project/shaka-player/issues/4660)) ([2b8b387](https://github.com/shaka-project/shaka-player/commit/2b8b38788ab5b6fc297eaa3537e97bc348d2b389))
* TS parser improvements ([#4612](https://github.com/shaka-project/shaka-player/issues/4612)) ([5157b44](https://github.com/shaka-project/shaka-player/commit/5157b44b2d644ec9cdc13b03b4ac762ed8e0f183))


### Bug Fixes

* **ads:** Fix IMA crash when autoplay is rejected ([#4518](https://github.com/shaka-project/shaka-player/issues/4518)) ([d27f7d2](https://github.com/shaka-project/shaka-player/commit/d27f7d24bb3e1000fc489a6aa125fca359dd77e1)), closes [#4179](https://github.com/shaka-project/shaka-player/issues/4179)
* allow build without text ([#4506](https://github.com/shaka-project/shaka-player/issues/4506)) ([340b04a](https://github.com/shaka-project/shaka-player/commit/340b04ad4798c9b68ed9510ae71912192a61348b))
* Allow overriding special handling of 404s ([#4635](https://github.com/shaka-project/shaka-player/issues/4635)) ([427f126](https://github.com/shaka-project/shaka-player/commit/427f126ea3958541d69474505e1af0eb892d8dde)), closes [#4548](https://github.com/shaka-project/shaka-player/issues/4548)
* allow the playback on platforms when low latency APIs are not supported ([#4485](https://github.com/shaka-project/shaka-player/issues/4485)) ([c1753e1](https://github.com/shaka-project/shaka-player/commit/c1753e1a02881cfbbafd863eeb582411c45df92c))
* **cast:** Reduce size of Cast update messages ([#4644](https://github.com/shaka-project/shaka-player/issues/4644)) ([4e75ec6](https://github.com/shaka-project/shaka-player/commit/4e75ec64be76414b1d4945cbfbf7bc52b5ff3b01))
* **cea:** Fix not rendering CEA-608 Closed Captions ([#4683](https://github.com/shaka-project/shaka-player/issues/4683)) ([a489282](https://github.com/shaka-project/shaka-player/commit/a489282ff26796a55f96e035b55d331abfc14142)), closes [#4605](https://github.com/shaka-project/shaka-player/issues/4605) [#3659](https://github.com/shaka-project/shaka-player/issues/3659)
* check for negative rows before moving ([#4510](https://github.com/shaka-project/shaka-player/issues/4510)) ([b3621c2](https://github.com/shaka-project/shaka-player/commit/b3621c26a86897ba80c17b68f316e22aba61b30b)), closes [#4508](https://github.com/shaka-project/shaka-player/issues/4508)
* Content reload starttime with HLS on iOS ([#4575](https://github.com/shaka-project/shaka-player/issues/4575)) ([59d4360](https://github.com/shaka-project/shaka-player/commit/59d4360b686421f07aa0d7f28eb944f0c51ff5a2)), closes [#4244](https://github.com/shaka-project/shaka-player/issues/4244)
* DAI ID3 metadata parsing ([#4616](https://github.com/shaka-project/shaka-player/issues/4616)) ([0d67ecd](https://github.com/shaka-project/shaka-player/commit/0d67ecd7cba253eb1919ae6e15a80f34e08fc132))
* embed cc not shown when seeking back ([#4643](https://github.com/shaka-project/shaka-player/issues/4643)) ([2a6b0d0](https://github.com/shaka-project/shaka-player/commit/2a6b0d02e550cfa5749b838f5915b8b6cf7b2099)), closes [#4641](https://github.com/shaka-project/shaka-player/issues/4641)
* Filter unsupported H.264 streams in Xbox ([#4493](https://github.com/shaka-project/shaka-player/issues/4493)) ([8475214](https://github.com/shaka-project/shaka-player/commit/8475214bc46e8321f7b60a6fc7fabee484a40800))
* Fix bitmap-based cue size ([#4453](https://github.com/shaka-project/shaka-player/issues/4453)) ([4a197e1](https://github.com/shaka-project/shaka-player/commit/4a197e1288c8f20a950cf491041eca9dde7033cb))
* Fix choppy HLS startup ([#4553](https://github.com/shaka-project/shaka-player/issues/4553)) ([59ef54a](https://github.com/shaka-project/shaka-player/commit/59ef54a158e14da2f7c6ab04e1fd9409bf63c6f0)), closes [#4516](https://github.com/shaka-project/shaka-player/issues/4516)
* Fix detection of ac4, dts, and dolby h265 ([#4657](https://github.com/shaka-project/shaka-player/issues/4657)) ([319a358](https://github.com/shaka-project/shaka-player/commit/319a358b8dc1838a89d8977109cab4296a558841))
* Fix dispatch ID3 metadata when transmuxing AAC ([#4639](https://github.com/shaka-project/shaka-player/issues/4639)) ([bf813f2](https://github.com/shaka-project/shaka-player/commit/bf813f2553dfc56efa79b708c54cbddee0f3ee2e))
* Fix drm.keySystemsMapping config ([#4425](https://github.com/shaka-project/shaka-player/issues/4425)) ([d945084](https://github.com/shaka-project/shaka-player/commit/d9450846e11224e0b1add6cc20a64844d6c09fcf)), closes [#4422](https://github.com/shaka-project/shaka-player/issues/4422)
* Fix errors with TS segments on Chromecast ([#4543](https://github.com/shaka-project/shaka-player/issues/4543)) ([593c280](https://github.com/shaka-project/shaka-player/commit/593c280dd578ee19cbb6a47f22962ff7fdd2cb45))
* Fix hang when seeking to the last segment ([#4537](https://github.com/shaka-project/shaka-player/issues/4537)) ([19a4842](https://github.com/shaka-project/shaka-player/commit/19a48422901440ff88fbbedfea5803c6dda07127))
* Fix HLS dynamic to static transition ([a16b1ac](https://github.com/shaka-project/shaka-player/commit/a16b1ac8a4c8f367f65747fc789a7d8c160e29e3))
* Fix HLS dynamic to static transition ([#4483](https://github.com/shaka-project/shaka-player/issues/4483)) ([a16b1ac](https://github.com/shaka-project/shaka-player/commit/a16b1ac8a4c8f367f65747fc789a7d8c160e29e3)), closes [#4431](https://github.com/shaka-project/shaka-player/issues/4431)
* Fix HLS lazy-loading exception during update ([#4648](https://github.com/shaka-project/shaka-player/issues/4648)) ([777c27e](https://github.com/shaka-project/shaka-player/commit/777c27ee558d803b3f166a0ac8b9778b08196654)), closes [#4647](https://github.com/shaka-project/shaka-player/issues/4647)
* Fix HLS lazy-loading exception on switch ([#4645](https://github.com/shaka-project/shaka-player/issues/4645)) ([941ed4e](https://github.com/shaka-project/shaka-player/commit/941ed4ed286e4463d4973e994d322250678cfdcb)), closes [#4621](https://github.com/shaka-project/shaka-player/issues/4621)
* Fix HLS lazy-loading with DRM ([#4646](https://github.com/shaka-project/shaka-player/issues/4646)) ([a7f0be7](https://github.com/shaka-project/shaka-player/commit/a7f0be726d5b801ac2365bb0c9b6db9e576c964f)), closes [#4622](https://github.com/shaka-project/shaka-player/issues/4622)
* Fix HLS live stream subtitle offsets ([#4586](https://github.com/shaka-project/shaka-player/issues/4586)) ([3b9af2e](https://github.com/shaka-project/shaka-player/commit/3b9af2efa6be06c8c8a13e5d715828e2875d75d7))
* Fix ID3 parsing in TS segments ([#4609](https://github.com/shaka-project/shaka-player/issues/4609)) ([3b534fd](https://github.com/shaka-project/shaka-player/commit/3b534fd405ad3254d37a86fd1895ceeb96dc8094))
* Fix in-band key rotation on Xbox One ([#4478](https://github.com/shaka-project/shaka-player/issues/4478)) ([4e93311](https://github.com/shaka-project/shaka-player/commit/4e933116984beb630d31ce7a0b8c9bc6f8b48c06)), closes [#4401](https://github.com/shaka-project/shaka-player/issues/4401)
* Fix metadata assert when the ID3 is future (coming in a previous segment) ([#4640](https://github.com/shaka-project/shaka-player/issues/4640)) ([216bdd7](https://github.com/shaka-project/shaka-player/commit/216bdd7657d7be8bb33f71c3a62f649ecc25ace5))
* Fix multi-period DASH with descriptive audio ([#4629](https://github.com/shaka-project/shaka-player/issues/4629)) ([81ccd5c](https://github.com/shaka-project/shaka-player/commit/81ccd5c73ba5e021466b82c05f8b607b0c345849)), closes [#4500](https://github.com/shaka-project/shaka-player/issues/4500)
* fix support clear and encrypted periods ([#4606](https://github.com/shaka-project/shaka-player/issues/4606)) ([6256db3](https://github.com/shaka-project/shaka-player/commit/6256db3af5065ea1db1951ea7583d4608ce5e28d))
* Fix vanishing tracks while offline ([#4426](https://github.com/shaka-project/shaka-player/issues/4426)) ([c935cc1](https://github.com/shaka-project/shaka-player/commit/c935cc17703297a44b3ce3bda75d8f2ea37f4147)), closes [#4408](https://github.com/shaka-project/shaka-player/issues/4408)
* Fixed LCEVC decode breaking dependencies issue and read me addition ([#4565](https://github.com/shaka-project/shaka-player/issues/4565)) ([3c75d1a](https://github.com/shaka-project/shaka-player/commit/3c75d1a71aea039c802555031fffbf3cad77f6fc))
* focus on first element when back to the settings menu ([#4653](https://github.com/shaka-project/shaka-player/issues/4653)) ([b40b6e7](https://github.com/shaka-project/shaka-player/commit/b40b6e7669d4ccf8677a6d262767f3e155eb02e6)), closes [#4652](https://github.com/shaka-project/shaka-player/issues/4652)
* Force using mcap polyfill on EOS browsers ([#4630](https://github.com/shaka-project/shaka-player/issues/4630)) ([6191d58](https://github.com/shaka-project/shaka-player/commit/6191d5894deb679ed68da54357dc1f6831edeb23))
* **HLS:** Add a guard on closeSegmentIndex ([#4615](https://github.com/shaka-project/shaka-player/issues/4615)) ([57ce56b](https://github.com/shaka-project/shaka-player/commit/57ce56b8d2bd5d2b1626b38594e6d54defd10255))
* **HLS:** Fix detection of WebVTT subtitles in HLS by extension ([#4663](https://github.com/shaka-project/shaka-player/issues/4663)) ([8f698c6](https://github.com/shaka-project/shaka-player/commit/8f698c6eaad6e1019f388e2d36f28883a142ddfb))
* **HLS:** Fix lazy-loading of TS content ([#4601](https://github.com/shaka-project/shaka-player/issues/4601)) ([dd7356d](https://github.com/shaka-project/shaka-player/commit/dd7356d0e0655f59792b3f992841d4c0c8d5540a))
* **hls:** Fix raw format detection when the main playlist hasn't type ([#4583](https://github.com/shaka-project/shaka-player/issues/4583)) ([d319718](https://github.com/shaka-project/shaka-player/commit/d319718eded6e36f4fc705588de84a301a428d49))
* **hls:** Fix single-variant HLS streams ([#4573](https://github.com/shaka-project/shaka-player/issues/4573)) ([62906bd](https://github.com/shaka-project/shaka-player/commit/62906bdc9a26456d213a0c5d33f00b4454cdfb5b)), closes [#1936](https://github.com/shaka-project/shaka-player/issues/1936) [#3536](https://github.com/shaka-project/shaka-player/issues/3536)
* **HLS:** Infer missing codecs from config ([#4656](https://github.com/shaka-project/shaka-player/issues/4656)) ([08fc7dd](https://github.com/shaka-project/shaka-player/commit/08fc7dd717390c61dcc3304c58bfff5c87c77833))
* **HLS:** Return 0-0 seek range until fully loaded ([#4590](https://github.com/shaka-project/shaka-player/issues/4590)) ([bf50ada](https://github.com/shaka-project/shaka-player/commit/bf50ada6874879b33ac1acd34ec7e5375eb4c45d))
* Limit key ids to 32 characters ([#4614](https://github.com/shaka-project/shaka-player/issues/4614)) ([9531b07](https://github.com/shaka-project/shaka-player/commit/9531b07296163d8cc5c8416f0baa4ffd29c0a90d))
* Make XML parsing secure ([#4598](https://github.com/shaka-project/shaka-player/issues/4598)) ([a731eba](https://github.com/shaka-project/shaka-player/commit/a731eba804ae1a3f3ee3061550fa43ea82e06313))
* Missing AES-128 key of last HLS segment ([#4519](https://github.com/shaka-project/shaka-player/issues/4519)) ([3d0f752](https://github.com/shaka-project/shaka-player/commit/3d0f752c7d0677f750dbbd9bcd2895358358628f)), closes [#4517](https://github.com/shaka-project/shaka-player/issues/4517)
* **offline:** Add storage muxer init timeout ([#4566](https://github.com/shaka-project/shaka-player/issues/4566)) ([d4d3740](https://github.com/shaka-project/shaka-player/commit/d4d37407c87b7c032a16679e96b318146bbdee22))
* **playhead:** Safeguard getStallsDetected as stallDetector can be null ([#4581](https://github.com/shaka-project/shaka-player/issues/4581)) ([21ceaca](https://github.com/shaka-project/shaka-player/commit/21ceacab9e9577c18cef7f6c76f57f39eca3dca9))
* Resolve load failures for TS-based content on Android-based Cast devices ([#4569](https://github.com/shaka-project/shaka-player/issues/4569)). ([#4570](https://github.com/shaka-project/shaka-player/issues/4570)) ([65903aa](https://github.com/shaka-project/shaka-player/commit/65903aa27b5723632ff16a92059cb20c4879fc59))
* Respect existing app usage of Cast SDK ([#4523](https://github.com/shaka-project/shaka-player/issues/4523)) ([8d3d556](https://github.com/shaka-project/shaka-player/commit/8d3d556edaa817af686e1577f0a0bad92d0c74d4)), closes [#4521](https://github.com/shaka-project/shaka-player/issues/4521)
* return width and height in the stats when we are using src= ([#4435](https://github.com/shaka-project/shaka-player/issues/4435)) ([9bbfb57](https://github.com/shaka-project/shaka-player/commit/9bbfb57cb4e2c0653e6eb5681e10714cb939bad9))
* Simplify transmuxer to allow more mimetypes in the future ([#4642](https://github.com/shaka-project/shaka-player/issues/4642)) ([a14e84b](https://github.com/shaka-project/shaka-player/commit/a14e84b5c9a6feb8f7f2efcbae52fe9691d48412))
* **ttml:** Default TTML background color to transparent if unspecified ([#4496](https://github.com/shaka-project/shaka-player/issues/4496)) ([32b0a90](https://github.com/shaka-project/shaka-player/commit/32b0a90a8c583bba03a3d7b035a1244d325e3da6)), closes [#4468](https://github.com/shaka-project/shaka-player/issues/4468)
* **UI:** Ad position and ad counter are too close to each other ([#4416](https://github.com/shaka-project/shaka-player/issues/4416)) ([8376410](https://github.com/shaka-project/shaka-player/commit/83764104277363b6ce0e05d8e53449ff454c6f0e))
* **ui:** Fix exception on screen rotation if fullscreen is not supported ([#4669](https://github.com/shaka-project/shaka-player/issues/4669)) ([fd93f6a](https://github.com/shaka-project/shaka-player/commit/fd93f6ae1bc917061c035abcfb835855e336bb06))
* Virgin Media set top box is incorrectly categorized as Apple/Safari ([df79470](https://github.com/shaka-project/shaka-player/commit/df79470af088089f8beba2f44a236593820d655a))
* WebVTT line not correctly positioned in UITextDisplayer ([#4567](https://github.com/shaka-project/shaka-player/issues/4567)) ([#4682](https://github.com/shaka-project/shaka-player/issues/4682)) ([140aefe](https://github.com/shaka-project/shaka-player/commit/140aefee04718faa631ba090d6313e372b608fc1))

## [4.2.0](https://github.com/shaka-project/shaka-player/compare/v4.1.0...v4.2.0) (2022-08-16)


### Features

* add Amazon Fire TV platform support ([#4375](https://github.com/shaka-project/shaka-player/issues/4375)) ([5102dac](https://github.com/shaka-project/shaka-player/commit/5102dac96cb1a749fefeb1f6b7a24c13f6b1077b))
* Add support for Modern EME and legacy Apple Media Keys for FairPlay ([#4309](https://github.com/shaka-project/shaka-player/issues/4309)) ([5441f93](https://github.com/shaka-project/shaka-player/commit/5441f932fd3da20f26da162cc0d49d0470689b41))
* Automatic ABR quality restrictions based on size ([#4404](https://github.com/shaka-project/shaka-player/issues/4404)) ([cfe8af5](https://github.com/shaka-project/shaka-player/commit/cfe8af5ff928fe7466b103429a6325917579ce70)), closes [#2333](https://github.com/shaka-project/shaka-player/issues/2333)
* **hls:** Support AES-128 in HLS ([#4386](https://github.com/shaka-project/shaka-player/issues/4386)) ([6194021](https://github.com/shaka-project/shaka-player/commit/6194021a3d4ea5dae22ade6713bb077875a4ee9d)), closes [#850](https://github.com/shaka-project/shaka-player/issues/850)
* Improve gap-detection robustness ([#4399](https://github.com/shaka-project/shaka-player/issues/4399)) ([4293a14](https://github.com/shaka-project/shaka-player/commit/4293a1421ada4b189d64b8c3f87a7599bc7b1a8f))
* Upgrade eme-encryption-scheme-polyfill to support ChromeCast version of PlayReady ([#4378](https://github.com/shaka-project/shaka-player/issues/4378)) ([e6b6d7c](https://github.com/shaka-project/shaka-player/commit/e6b6d7c24bee4138b6bb2735e3c9a4dc885a6cf6))
* **webvtt:** add support for karaoke style text in WebVTT ([#4274](https://github.com/shaka-project/shaka-player/issues/4274)) ([60af516](https://github.com/shaka-project/shaka-player/commit/60af5165207d39ebe26d536b009521192ab8cad9))


### Bug Fixes

* Add fallback to TextDecoder and TextEncoder [#4324](https://github.com/shaka-project/shaka-player/issues/4324) ([5b18069](https://github.com/shaka-project/shaka-player/commit/5b180694309f1cc01b2997cd0366154135f8acd8))
* add strictMissingProperties suppressions to unblock strict missing properties on union types. ([#4371](https://github.com/shaka-project/shaka-player/issues/4371)) ([b361948](https://github.com/shaka-project/shaka-player/commit/b36194878e26a22b522a6cf1dba07e9fc5cd341d))
* Debug buffer placement ([#4345](https://github.com/shaka-project/shaka-player/issues/4345)) ([47fa309](https://github.com/shaka-project/shaka-player/commit/47fa3093e1462d0bcca87238dc4886b9e2c1f8f4))
* **demo:** allow switch between UITextDisplayer and SimpleTextDisplayer ([#4275](https://github.com/shaka-project/shaka-player/issues/4275)) ([28689f3](https://github.com/shaka-project/shaka-player/commit/28689f38fb7cc8f3b85b6b1eb2337a1779e8ee95))
* **demo:** erroneous FairPlay keysystem in demo ([#4276](https://github.com/shaka-project/shaka-player/issues/4276)) ([8719bdc](https://github.com/shaka-project/shaka-player/commit/8719bdc0defd7956ec9fad934525477a603744a0))
* exception if on early adError ([#4362](https://github.com/shaka-project/shaka-player/issues/4362)) ([3c92f05](https://github.com/shaka-project/shaka-player/commit/3c92f0598e6c1628ff50d980a842dd40b2b56813)), closes [#4004](https://github.com/shaka-project/shaka-player/issues/4004)
* Fix EOS set-top box being identified as Apple. ([#4310](https://github.com/shaka-project/shaka-player/issues/4310)) ([7c2c4be](https://github.com/shaka-project/shaka-player/commit/7c2c4be2ae946c4cf270717f852b0d95b498266e))
* Fix getVideoPlaybackQuality in WebOS 3 ([#4316](https://github.com/shaka-project/shaka-player/issues/4316)) ([5561111](https://github.com/shaka-project/shaka-player/commit/556111143dfccbc7348fc15792df75bc35fea465))
* Fix key ID byteswapping for PlayReady on PS4 ([#4377](https://github.com/shaka-project/shaka-player/issues/4377)) ([25fd4f4](https://github.com/shaka-project/shaka-player/commit/25fd4f4af6ddd8953c4bc2da4a2d9eb1144c3fb9))
* Fix MediaCapabilities polyfill on Playstation 4 ([#4320](https://github.com/shaka-project/shaka-player/issues/4320)) ([0335b2a](https://github.com/shaka-project/shaka-player/commit/0335b2af2efea6ceda83e536e12094e4cc942a25))
* Fix MediaCapabilities polyfill on Tizen and WebOS ([#4396](https://github.com/shaka-project/shaka-player/issues/4396)) ([eb2aed8](https://github.com/shaka-project/shaka-player/commit/eb2aed825e84142f9fb9ddb3e69ebc333127c295)), closes [#4383](https://github.com/shaka-project/shaka-player/issues/4383) [#4357](https://github.com/shaka-project/shaka-player/issues/4357)
* Fix segment index assertions with DAI ([#4348](https://github.com/shaka-project/shaka-player/issues/4348)) ([c2b3853](https://github.com/shaka-project/shaka-player/commit/c2b3853a56e816c97fab57f961f295b7272e410e))
* Fix TextDecoder fallback and browser support check ([#4403](https://github.com/shaka-project/shaka-player/issues/4403)) ([04fc0d4](https://github.com/shaka-project/shaka-player/commit/04fc0d47c3895f294401b588ed49cc4360f31be1))
* Fix UI captions icon state ([#4384](https://github.com/shaka-project/shaka-player/issues/4384)) ([d462633](https://github.com/shaka-project/shaka-player/commit/d46263333ba3de68707d521b997c40c5ba492fda)), closes [#4358](https://github.com/shaka-project/shaka-player/issues/4358)
* Fix VP9 codec checks on Mac Firefox ([#4391](https://github.com/shaka-project/shaka-player/issues/4391)) ([b6ab769](https://github.com/shaka-project/shaka-player/commit/b6ab76976211852e96b2883562166a5e1e4dd0f2))
* **hls:** Fix AV sync issues, fallback to sequence numbers if PROGRAM-DATE-TIME ignored ([#4289](https://github.com/shaka-project/shaka-player/issues/4289)) ([314a987](https://github.com/shaka-project/shaka-player/commit/314a987ecf85b47cc8a6cef08f390ef817e11c49)), closes [#4287](https://github.com/shaka-project/shaka-player/issues/4287)
* New EME polyfill fixes EME/MCap issues on some smart TVs ([#4279](https://github.com/shaka-project/shaka-player/issues/4279)) ([db1b20e](https://github.com/shaka-project/shaka-player/commit/db1b20ec77f74472dd24f493f2a26c02b17927bc))
* Populate track's spatialAudio property ([#4291](https://github.com/shaka-project/shaka-player/issues/4291)) ([713f461](https://github.com/shaka-project/shaka-player/commit/713f461c62b23680557f8d6c4b9c3126bb604f9e))
* Remove IE 11 from default browsers for Windows ([#4272](https://github.com/shaka-project/shaka-player/issues/4272)) ([490b06c](https://github.com/shaka-project/shaka-player/commit/490b06cd45d09c7567056535f4b8dc6f3e2e5733)), closes [#4271](https://github.com/shaka-project/shaka-player/issues/4271)
* **text:** Fix cue region rendering in UI ([#4412](https://github.com/shaka-project/shaka-player/issues/4412)) ([b1f46db](https://github.com/shaka-project/shaka-player/commit/b1f46dbc3a685b0216600835e24fd13c504e1b62)), closes [#4381](https://github.com/shaka-project/shaka-player/issues/4381)
* **text:** Fix TTML render timing and line break issues for native display ([122f223](https://github.com/shaka-project/shaka-player/commit/122f223d19732bf5977ab8a5c93bbc4d934da1d7))
* Update main branch Cast receiver ID ([#4364](https://github.com/shaka-project/shaka-player/issues/4364)) ([46b27f1](https://github.com/shaka-project/shaka-player/commit/46b27f19e099d44ab3929222da7a3bcb41bdb230))
* Use middle segment when guessing MIME type on HLS ([#4269](https://github.com/shaka-project/shaka-player/issues/4269)) ([#4270](https://github.com/shaka-project/shaka-player/issues/4270)) ([3d27d2a](https://github.com/shaka-project/shaka-player/commit/3d27d2a2cfeb8fa21f3415baaf013567dcccf480))
* VTT Cue Parsing On PlayStation 4 ([#4340](https://github.com/shaka-project/shaka-player/issues/4340)) ([b5da41e](https://github.com/shaka-project/shaka-player/commit/b5da41ed80b96e8edae970c39dd5fac7348a9a55)), closes [#4321](https://github.com/shaka-project/shaka-player/issues/4321)

## [4.1.0](https://github.com/shaka-project/shaka-player/compare/v4.0.0...v4.1.0) (2022-06-02)


### Features

* Add Id to chapters ([#4184](https://github.com/shaka-project/shaka-player/issues/4184)) ([5ca3271](https://github.com/shaka-project/shaka-player/commit/5ca32712e375ba875be86827ea1efaaa5e3c0035))
* Add keySystemsMapping to drm config ([#4254](https://github.com/shaka-project/shaka-player/issues/4254)) ([5e107d5](https://github.com/shaka-project/shaka-player/commit/5e107d584f824e66ab3e5e07f9d833f6dc456d14)), closes [#4243](https://github.com/shaka-project/shaka-player/issues/4243)
* add listenable events for playback stall detection and gap jumping ([#4249](https://github.com/shaka-project/shaka-player/issues/4249)) ([5987458](https://github.com/shaka-project/shaka-player/commit/5987458e445cf21f91bf4833396edd63d5f69765))
* Add support to text-shadow in VTT parser ([#4257](https://github.com/shaka-project/shaka-player/issues/4257)) ([62bda2c](https://github.com/shaka-project/shaka-player/commit/62bda2cd36c6d49d08c10757bfe5869b5be54b88))
* **cast:** Add Android receiver support ([#4183](https://github.com/shaka-project/shaka-player/issues/4183)) ([dbba571](https://github.com/shaka-project/shaka-player/commit/dbba571c6bb7e99a99469ffb695f59a590d44118))
* **hls:** Add support for EXT-X-GAP ([#4208](https://github.com/shaka-project/shaka-player/issues/4208)) ([14e61a7](https://github.com/shaka-project/shaka-player/commit/14e61a7368ddbd66c4b10f3b0475840cc50512bd)), closes [#1308](https://github.com/shaka-project/shaka-player/issues/1308)
* Temporarily disable the active variant from NETWORK HTTP_ERROR ([#4189](https://github.com/shaka-project/shaka-player/issues/4189)) ([b57279d](https://github.com/shaka-project/shaka-player/commit/b57279d39c24d3b2568c4b62338524ecc23423ad)), closes [#4121](https://github.com/shaka-project/shaka-player/issues/4121) [#1542](https://github.com/shaka-project/shaka-player/issues/1542) [#2541](https://github.com/shaka-project/shaka-player/issues/2541)
* **UI:** Added keyboardSeekDistance config to UI ([#4246](https://github.com/shaka-project/shaka-player/issues/4246)) ([6084ca6](https://github.com/shaka-project/shaka-player/commit/6084ca6395fbe3d5a97fa92137b8bb51f15c89f8))


### Bug Fixes

* **abr:** use Network Info API in ABR getBandwidthEstimate ([#4263](https://github.com/shaka-project/shaka-player/issues/4263)) ([4fc7a48](https://github.com/shaka-project/shaka-player/commit/4fc7a4893fd081d4dafa26a2034361afd7b7e6ed))
* Do not report MANIFEST RESTRICTIONS_CANNOT_BE_MET error twice ([#4194](https://github.com/shaka-project/shaka-player/issues/4194)) ([08589e8](https://github.com/shaka-project/shaka-player/commit/08589e8fb27f3f73f64204e7d3a2387f3c197d84)), closes [#4190](https://github.com/shaka-project/shaka-player/issues/4190)
* Don't send drmsessionupdate after unload ([#4248](https://github.com/shaka-project/shaka-player/issues/4248)) ([60af9ad](https://github.com/shaka-project/shaka-player/commit/60af9ad596e5c2cb31d1e7bb616e415cf46ca761))
* **fairplay:** Re-add initDataTransform config ([#4231](https://github.com/shaka-project/shaka-player/issues/4231)) ([ff310e9](https://github.com/shaka-project/shaka-player/commit/ff310e91e564bcc4be340c47bf1be81a5323765a))
* Fix audio mime type in multiplexed HLS stream ([#4241](https://github.com/shaka-project/shaka-player/issues/4241)) ([4e4e92e](https://github.com/shaka-project/shaka-player/commit/4e4e92e98da357285547859a98e6b3fe75d1904f))
* Fix event listener leaks in Player ([#4229](https://github.com/shaka-project/shaka-player/issues/4229)) ([a5d3568](https://github.com/shaka-project/shaka-player/commit/a5d356874ba90069ca5a86be1979a5904a1150e8))
* Fix exception with streaming.startAtSegmentBoundary ([#4216](https://github.com/shaka-project/shaka-player/issues/4216)) ([426a19c](https://github.com/shaka-project/shaka-player/commit/426a19c8e7ff188390e7430fb02f3cfcb79cc017)), closes [#4188](https://github.com/shaka-project/shaka-player/issues/4188)
* Fix PERIOD_FLATTENING_FAILED error when periods have different base sample types ([#4206](https://github.com/shaka-project/shaka-player/issues/4206)) ([b757a81](https://github.com/shaka-project/shaka-player/commit/b757a81902a2159b217e7cb6a1445ab6d4d69bf4)), closes [#4202](https://github.com/shaka-project/shaka-player/issues/4202)
* Fix VTT cue timing in HLS ([#4217](https://github.com/shaka-project/shaka-player/issues/4217)) ([5818260](https://github.com/shaka-project/shaka-player/commit/58182605a7da3c18a7331828c319c88446a13d52)), closes [#4191](https://github.com/shaka-project/shaka-player/issues/4191)
* **hls:** Fix av1 codec selection in HLS. ([#4203](https://github.com/shaka-project/shaka-player/issues/4203)) ([5e13495](https://github.com/shaka-project/shaka-player/commit/5e1349570d64c17e6ca1fcdc5ffde1076ea9a999))
* **HLS:** Fix duplicate hinted segments ([#4258](https://github.com/shaka-project/shaka-player/issues/4258)) ([9171f73](https://github.com/shaka-project/shaka-player/commit/9171f733e8de0b811ebac71d5ddbe0cb1ff7c75b)), closes [#4223](https://github.com/shaka-project/shaka-player/issues/4223)
* **hls:** Fix X-PRELOAD-HINT failure with LL mode off ([#4212](https://github.com/shaka-project/shaka-player/issues/4212)) ([86497a5](https://github.com/shaka-project/shaka-player/commit/86497a5089e272ed682f017f5ed9135108be5a65)), closes [#4185](https://github.com/shaka-project/shaka-player/issues/4185)
* **ui:** Widen touchable button area ([#3249](https://github.com/shaka-project/shaka-player/issues/3249)) ([6c0283e](https://github.com/shaka-project/shaka-player/commit/6c0283e7d040fd0df9383454b174a7ceb2678c89))
* Upgrade mux.js to version that emits partial ID3 when malformed ([#4259](https://github.com/shaka-project/shaka-player/issues/4259)) ([dc88fe0](https://github.com/shaka-project/shaka-player/commit/dc88fe0814f82aa447a3fa8f7098c85621faf9c6)), closes [#3761](https://github.com/shaka-project/shaka-player/issues/3761)
* Wait for chapters track to be loaded ([#4228](https://github.com/shaka-project/shaka-player/issues/4228)) ([80e81f1](https://github.com/shaka-project/shaka-player/commit/80e81f139129dbe1c797ee07fedc1217b8790b53)), closes [#4186](https://github.com/shaka-project/shaka-player/issues/4186)

## [4.0.0](https://github.com/shaka-project/shaka-player/compare/v3.3.0...v4.0.0) (2022-04-30)


### ⚠ BREAKING CHANGES

* Remove small/large gap config, always jump gaps (#4125)
* **config:** `manifest.dash.defaultPresentationDelay` has been replaced by `manifest.defaultPresentationDelay` (deprecated in v3.0.0)
* **config:** Configuration of factories should be plain factory functions, not constructors; these will not be invoked with `new` (deprecated in v3.1.0)
* **player:** `shaka.Player.prototype.addTextTrack()` has been replaced by `addTextTrackAsync()`, which returns a `Promise` (deprecated in v3.1.0)
* **ui:** `shaka.ui.TrackLabelFormat` has been renamed to `shaka.ui.Overlay.TrackLabelFormat` (deprecated in v3.1.0)
* **ui:** `shaka.ui.FailReasonCode` has been renamed to `shaka.ui.Overlay.FailReasonCode` (deprecated in v3.1.0)
* **offline:** `shaka.offline.Storage.prototype.store()` returns `AbortableOperation` instead of `Promise` (deprecated in v3.0.0)
* **offline:** `shaka.offline.Storage.prototype.getStoreInProgress()` has been removed; concurrent operations are supported, so callers don't need to check this (deprecated in v3.0.0)
* `shaka.util.Uint8ArrayUtils.equal` has been replaced by `shaka.util.BufferUtils.equal`, which can handle multiple types of buffers (deprecated in v3.0.0)
* **manifest:** `shaka.media.SegmentIndex.prototype.destroy()` has been replaced by `release()`, which is synchronous (deprecated in v3.0.0)
* **manifest:** `shaka.media.SegmentIterator.prototype.seek()`, which mutates the iterator, has been replaced by `shaka.media.SegmentIndex.getIteratorForTime()` (deprecated in v3.1.0)
* **manifest:** `shaka.media.SegmentIndex.prototype.merge()` has become private; use `mergeAndEvict()` instead (deprecated in v3.2.0)
* **plugin:** `AbrManager` plugins must implement the `playbackRateChanged()` method (deprecated in v3.0.0)
* **plugin:** `shaka.extern.Cue.prototype.spacer` has been replaced by the more clearly-named `lineBreak` (deprecated in v3.1.0)
* **plugin:** `IUIElement` plugins must have a `release()` method (not `destroy()`) (deprecated in v3.0.0)
* Remove deprecated features, update upgrade guides (#4089)
* Remove support for Safari 12 and iOS 12 (#4112)
* **hls:** HLS disabled in old browsers/platforms due to incompatibilities (#3964)

### Features

* `shaka.util.Uint8ArrayUtils.equal` has been replaced by `shaka.util.BufferUtils.equal`, which can handle multiple types of buffers (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Add Dockerfile and docker build instructions ([925de19](https://github.com/shaka-project/shaka-player/commit/925de1995eeb22863e8d4e92d720465834619288))
* add modern EME support for FairPlay ([#3776](https://github.com/shaka-project/shaka-player/issues/3776)) ([6d76a13](https://github.com/shaka-project/shaka-player/commit/6d76a135e5128dfd47653acea025d0a264d121d5))
* add new methods to FairPlayUtils ([#4029](https://github.com/shaka-project/shaka-player/issues/4029)) ([f1eeac1](https://github.com/shaka-project/shaka-player/commit/f1eeac1efb618aa7202b17b67c43056714f8da2f))
* add option for segment-relative VTT timings ([#4083](https://github.com/shaka-project/shaka-player/issues/4083)) ([f382cc7](https://github.com/shaka-project/shaka-player/commit/f382cc702be6cc28266fe61a33e43573cb22be57))
* Add separate audio and video MIME types to Track API ([#3892](https://github.com/shaka-project/shaka-player/issues/3892)) ([74c491d](https://github.com/shaka-project/shaka-player/commit/74c491d2e0042f62385813f04e74517cf00fcade)), closes [#3888](https://github.com/shaka-project/shaka-player/issues/3888)
* Allow WebP and AVIF image streams ([#3856](https://github.com/shaka-project/shaka-player/issues/3856)) ([9f3fb46](https://github.com/shaka-project/shaka-player/commit/9f3fb46d371d52f58bc9a7fc5beefe51890879ed)), closes [#3845](https://github.com/shaka-project/shaka-player/issues/3845)
* **config:** `manifest.dash.defaultPresentationDelay` has been replaced by `manifest.defaultPresentationDelay` (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **config:** Configuration of factories should be plain factory functions, not constructors; these will not be invoked with `new` (deprecated in v3.1.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **dash:** Construct ClearKey PSSH based on MPD ContentProtection ([#4104](https://github.com/shaka-project/shaka-player/issues/4104)) ([b83b412](https://github.com/shaka-project/shaka-player/commit/b83b4120f46ae94e3ce194f43b13517b7a736f07))
* **dash:** Parse ClearKey license URL in MPD ([#4066](https://github.com/shaka-project/shaka-player/issues/4066)) ([19e24b1](https://github.com/shaka-project/shaka-player/commit/19e24b1d741b4ba6946011748be8b759b4b71773))
* **demo:** Add Apple Advanced HLS Stream (TS) with raw AAC ([#3933](https://github.com/shaka-project/shaka-player/issues/3933)) ([1becadf](https://github.com/shaka-project/shaka-player/commit/1becadfc93ca06d64d0c9ace37c80213268a1675))
* **demo:** Added demo asset with raw AAC. ([014c7b3](https://github.com/shaka-project/shaka-player/commit/014c7b302b292a22f62d4e01230b927b33bc51da)), closes [#2337](https://github.com/shaka-project/shaka-player/issues/2337)
* **DRM:** add drmInfo to license requests ([#4030](https://github.com/shaka-project/shaka-player/issues/4030)) ([abe846e](https://github.com/shaka-project/shaka-player/commit/abe846e1a3456b029822ea42eb0520dec547fda6))
* **DRM:** add initData and initDataType to license requests ([#4039](https://github.com/shaka-project/shaka-player/issues/4039)) ([bdc5ea7](https://github.com/shaka-project/shaka-player/commit/bdc5ea767ebe55bb0b18dd106e269ab3fecd6d00))
* **HLS:** Containerless format support ([36d0b54](https://github.com/shaka-project/shaka-player/commit/36d0b5484fad68dc1d640fbddf2fae3e1eb7169b)), closes [#2337](https://github.com/shaka-project/shaka-player/issues/2337)
* **hls:** HLS disabled in old browsers/platforms due to incompatibilities ([#3964](https://github.com/shaka-project/shaka-player/issues/3964)) ([0daa00f](https://github.com/shaka-project/shaka-player/commit/0daa00fc7f074c1c86968ed0fcd84bc30254ee6d))
* **hls:** make a head request if hls subtitles have no extension ([#4140](https://github.com/shaka-project/shaka-player/issues/4140)) ([19e12b5](https://github.com/shaka-project/shaka-player/commit/19e12b5e282e661a9a17a6bfbb87c565faf2bc6e))
* **hls:** parse EXT-X-GAP ([#4134](https://github.com/shaka-project/shaka-player/issues/4134)) ([42eecc8](https://github.com/shaka-project/shaka-player/commit/42eecc84f992ca6a680c3a5fd46d1c300fe92a72))
* **HLS:** Re-add TS support to Safari ([#4097](https://github.com/shaka-project/shaka-player/issues/4097)) ([8a3bed7](https://github.com/shaka-project/shaka-player/commit/8a3bed710c104c9729fec2072318e50f9fe15ab2))
* **hls:** Read EXT-X-PROGRAM-DATE-TIME ([#4034](https://github.com/shaka-project/shaka-player/issues/4034)) ([89409ce](https://github.com/shaka-project/shaka-player/commit/89409cee3eaeb6764dbc191b7408bf45eecdced3)), closes [#2337](https://github.com/shaka-project/shaka-player/issues/2337)
* **manifest:** `shaka.media.SegmentIndex.prototype.destroy()` has been replaced by `release()`, which is synchronous (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **manifest:** `shaka.media.SegmentIndex.prototype.merge()` has become private; use `mergeAndEvict()` instead (deprecated in v3.2.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **manifest:** `shaka.media.SegmentIterator.prototype.seek()`, which mutates the iterator, has been replaced by `shaka.media.SegmentIndex.getIteratorForTime()` (deprecated in v3.1.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **offline:** `shaka.offline.Storage.prototype.getStoreInProgress()` has been removed; concurrent operations are supported, so callers don't need to check this (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **offline:** `shaka.offline.Storage.prototype.store()` returns `AbortableOperation` instead of `Promise` (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **offline:** improve the speed of offline downloads ([#4168](https://github.com/shaka-project/shaka-player/issues/4168)) ([73f6de3](https://github.com/shaka-project/shaka-player/commit/73f6de3e01ae4ed3b86302add7ee16c86c3b9b78))
* only polyfill MCap for non Android-based Cast devices. ([#4170](https://github.com/shaka-project/shaka-player/issues/4170)) ([11321d8](https://github.com/shaka-project/shaka-player/commit/11321d8f26b01412fa5173aa6efcf777186fa7a0))
* **player:** `shaka.Player.prototype.addTextTrack()` has been replaced by `addTextTrackAsync()`, which returns a `Promise` (deprecated in v3.1.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **plugin:** `AbrManager` plugins must implement the `playbackRateChanged()` method (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **plugin:** `IUIElement` plugins must have a `release()` method (not `destroy()`) (deprecated in v3.0.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **plugin:** `shaka.extern.Cue.prototype.spacer` has been replaced by the more clearly-named `lineBreak` (deprecated in v3.1.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Public release of Sindarin (sjn) translation easter egg ([#4033](https://github.com/shaka-project/shaka-player/issues/4033)) ([9029d06](https://github.com/shaka-project/shaka-player/commit/9029d0677e0e0325e0dbe939907ba60ecec74c92))
* Remove deprecated features, update upgrade guides ([#4089](https://github.com/shaka-project/shaka-player/issues/4089)) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* Remove small/large gap config, always jump gaps ([#4125](https://github.com/shaka-project/shaka-player/issues/4125)) ([0fd1999](https://github.com/shaka-project/shaka-player/commit/0fd19997dde7b03bad7464a82dc86d7b2cd8a304))
* Remove support for Safari 12 and iOS 12 ([#4112](https://github.com/shaka-project/shaka-player/issues/4112)) ([8bb7044](https://github.com/shaka-project/shaka-player/commit/8bb70449d33c31a0e7fc312260dc001cc9e3a792))
* **ui:** `shaka.ui.FailReasonCode` has been renamed to `shaka.ui.Overlay.FailReasonCode` (deprecated in v3.1.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **ui:** `shaka.ui.TrackLabelFormat` has been renamed to `shaka.ui.Overlay.TrackLabelFormat` (deprecated in v3.1.0) ([ac5acc8](https://github.com/shaka-project/shaka-player/commit/ac5acc80cb8d2bcb58455e8f66f7e1c2d18b0a3a))
* **ui:** Add quality selection for audio-only content ([#3649](https://github.com/shaka-project/shaka-player/issues/3649)) ([adc3502](https://github.com/shaka-project/shaka-player/commit/adc3502d55f39eaca30f3c42e17961ec7d681c80)), closes [#2071](https://github.com/shaka-project/shaka-player/issues/2071)
* **UI:** Add video fullscreen support for iOS ([#3853](https://github.com/shaka-project/shaka-player/issues/3853)) ([8d1b5e6](https://github.com/shaka-project/shaka-player/commit/8d1b5e6b07e979bd641da0b2b53c5f8e872422ad)), closes [#3832](https://github.com/shaka-project/shaka-player/issues/3832)


### Bug Fixes

* Add explicit release() for FakeEventTarget ([#3950](https://github.com/shaka-project/shaka-player/issues/3950)) ([f1c1585](https://github.com/shaka-project/shaka-player/commit/f1c1585afb2cfa3eb6b7465c8b32c9bad8e62d15))
* Add missing module export in generated typescript defs ([feefd7b](https://github.com/shaka-project/shaka-player/commit/feefd7b7d1cc318800c8d83de8cce81c57939f7d))
* Avoid WebCrypto randomUUID when CMCD disabled ([4731c76](https://github.com/shaka-project/shaka-player/commit/4731c7677f4f179f19ae647d3bb1edfda40dac53))
* **cea:** make a more robust CEA MP4 parser ([#3965](https://github.com/shaka-project/shaka-player/issues/3965)) ([2687b95](https://github.com/shaka-project/shaka-player/commit/2687b95d5830179c53914a7e903ecfbaced429cc))
* Clear buffer on seek if mediaState is updating ([#3795](https://github.com/shaka-project/shaka-player/issues/3795)) ([9705639](https://github.com/shaka-project/shaka-player/commit/9705639f4514d8d2dbfe5d81a31388f99e6be507)), closes [#3299](https://github.com/shaka-project/shaka-player/issues/3299)
* **cmcd:** Fix Symbol usage in CMCD on Xbox One ([#4073](https://github.com/shaka-project/shaka-player/issues/4073)) ([4005754](https://github.com/shaka-project/shaka-player/commit/400575498f34cf252aaba0bc1367953b8cf44537)), closes [#4072](https://github.com/shaka-project/shaka-player/issues/4072)
* **css:** Fix missing % in calculation ([#4157](https://github.com/shaka-project/shaka-player/issues/4157)) ([1c86195](https://github.com/shaka-project/shaka-player/commit/1c8619582319c46c524807aa4bdff1191b2efc91))
* **dash:** Account for bandwidth before filtering text stream ([#3765](https://github.com/shaka-project/shaka-player/issues/3765)) ([0b04aec](https://github.com/shaka-project/shaka-player/commit/0b04aecdd7ad4184a72b8cf562318b28128344bf)), closes [#3724](https://github.com/shaka-project/shaka-player/issues/3724)
* **dash:** Fix performance regression ([#4064](https://github.com/shaka-project/shaka-player/issues/4064)) ([298b604](https://github.com/shaka-project/shaka-player/commit/298b60481d34bd9d776874fe1b9a8eea05b533d9))
* **dash:** Fix playback of Dolby Atmos ([#4173](https://github.com/shaka-project/shaka-player/issues/4173)) ([d51fe23](https://github.com/shaka-project/shaka-player/commit/d51fe23b7fab99501818c18cc76586e1ec4abcdd)), closes [#4171](https://github.com/shaka-project/shaka-player/issues/4171)
* Fix broken deps file generation on Windows ([#4086](https://github.com/shaka-project/shaka-player/issues/4086)) ([9660ce8](https://github.com/shaka-project/shaka-player/commit/9660ce85df48856b964eebc330c28beba2e3068a)), closes [#4085](https://github.com/shaka-project/shaka-player/issues/4085)
* Fix CMCD property mangling ([#3842](https://github.com/shaka-project/shaka-player/issues/3842)) ([fa5932c](https://github.com/shaka-project/shaka-player/commit/fa5932ca8f604952590734bf8bdc27ad8e69e8d8)), closes [#3839](https://github.com/shaka-project/shaka-player/issues/3839)
* Fix CMCD top bitrate reporting ([#3852](https://github.com/shaka-project/shaka-player/issues/3852)) ([922778a](https://github.com/shaka-project/shaka-player/commit/922778a5ebd2d58ca0c1e804745ca40cda1228bc)), closes [#3851](https://github.com/shaka-project/shaka-player/issues/3851)
* Fix compiler error introduced in [#3864](https://github.com/shaka-project/shaka-player/issues/3864) ([#3906](https://github.com/shaka-project/shaka-player/issues/3906)) ([0635e2c](https://github.com/shaka-project/shaka-player/commit/0635e2c055c13a405048c7696389c1dfc039902f))
* Fix download of some HLS assets ([#3934](https://github.com/shaka-project/shaka-player/issues/3934)) ([36ca820](https://github.com/shaka-project/shaka-player/commit/36ca820877965db8bcc8b9c4b2a428317301bb95))
* Fix duplicate CMCD parameters in HLS live content ([#3875](https://github.com/shaka-project/shaka-player/issues/3875)) ([f27401c](https://github.com/shaka-project/shaka-player/commit/f27401cc151a435ae8fb12be4e86d672c331e1e5)), closes [#3862](https://github.com/shaka-project/shaka-player/issues/3862)
* Fix encryption detection to work around broken platforms ([#4169](https://github.com/shaka-project/shaka-player/issues/4169)) ([c5f474e](https://github.com/shaka-project/shaka-player/commit/c5f474ef983169e6ff29f1594d15a9b50b12d316))
* Fix exception in StreamingEngine for EMSG with HLS ([#3887](https://github.com/shaka-project/shaka-player/issues/3887)) ([48433ab](https://github.com/shaka-project/shaka-player/commit/48433abe74c5f603cf06097e391ffdfa22d64256)), closes [#3886](https://github.com/shaka-project/shaka-player/issues/3886)
* Fix exceptions when quickly shutting down src= on Safari ([#4088](https://github.com/shaka-project/shaka-player/issues/4088)) ([ca08230](https://github.com/shaka-project/shaka-player/commit/ca08230fbe85d66176c7fa1fb4f9782d0ab364fc)), closes [#4087](https://github.com/shaka-project/shaka-player/issues/4087)
* Fix MediaCapabilities polyfill on Safari ([0201f2b](https://github.com/shaka-project/shaka-player/commit/0201f2b7604e76062b68b8b1acbf098faf71d019)), closes [#3696](https://github.com/shaka-project/shaka-player/issues/3696) [#3530](https://github.com/shaka-project/shaka-player/issues/3530)
* Fix memory leak in DASH live streams with inband EventStream ([#3957](https://github.com/shaka-project/shaka-player/issues/3957)) ([b7f04cb](https://github.com/shaka-project/shaka-player/commit/b7f04cb36bda664ec9cf23a081d237793907eaae))
* Fix misdetection of HEVC support on MS Edge ([#3897](https://github.com/shaka-project/shaka-player/issues/3897)) ([dfb3699](https://github.com/shaka-project/shaka-player/commit/dfb369935b9e84fe69a7d38c7904fb0e00dc064a)), closes [#3860](https://github.com/shaka-project/shaka-player/issues/3860)
* Fix missing throughput in CMCD for HLS live ([#3874](https://github.com/shaka-project/shaka-player/issues/3874)) ([df55944](https://github.com/shaka-project/shaka-player/commit/df55944e8f49bdf8e34a679219cd6596ba46c777)), closes [#3873](https://github.com/shaka-project/shaka-player/issues/3873)
* Fix playback failure due to rounding errors ([1cc99c1](https://github.com/shaka-project/shaka-player/commit/1cc99c1241c89b5fb5a989dd52ff0b9a9753b65f)), closes [#3717](https://github.com/shaka-project/shaka-player/issues/3717)
* Fix playRangeEnd for certain content ([#4068](https://github.com/shaka-project/shaka-player/issues/4068)) ([5c81f3b](https://github.com/shaka-project/shaka-player/commit/5c81f3bddb9e48431556f4d622364043fee4ea80)), closes [#4026](https://github.com/shaka-project/shaka-player/issues/4026)
* Fix support for TTAF1 namespace (old version of TTML) ([#3864](https://github.com/shaka-project/shaka-player/issues/3864)) ([771619f](https://github.com/shaka-project/shaka-player/commit/771619ff0ef8ba0e3da9569ded3894b428d03c58)), closes [#3009](https://github.com/shaka-project/shaka-player/issues/3009)
* Fix usage of Shaka without polyfills ([dfc44cb](https://github.com/shaka-project/shaka-player/commit/dfc44cbca6b95eb137882075cb8bf02cfc73a9d3))
* **hls:** Fixed buffering issue with live HLS ([#4002](https://github.com/shaka-project/shaka-player/issues/4002)) ([c438e85](https://github.com/shaka-project/shaka-player/commit/c438e857f2f122eb45899148e067d68ffec3477c))
* **HLS:** skip whitespace in attributes ([#3884](https://github.com/shaka-project/shaka-player/issues/3884)) ([ea6c02a](https://github.com/shaka-project/shaka-player/commit/ea6c02aece1510598a898c235e66335d20eabedb))
* **hls:** Support playing media playlists directly ([#4080](https://github.com/shaka-project/shaka-player/issues/4080)) ([48dd205](https://github.com/shaka-project/shaka-player/commit/48dd20562c2226f61cc753a922629e44c1866f6d)), closes [#3536](https://github.com/shaka-project/shaka-player/issues/3536)
* **image:** Fix HLS image track issues ([264c842](https://github.com/shaka-project/shaka-player/commit/264c84249684ee809f53fd4117f9aab4e0a599ac)), closes [#3840](https://github.com/shaka-project/shaka-player/issues/3840)
* **image:** Fix thumbnails issues ([#3858](https://github.com/shaka-project/shaka-player/issues/3858)) ([087a9b4](https://github.com/shaka-project/shaka-player/commit/087a9b489b030aa0dc80011ca4e0a0c7a4124ecd))
* **offline:** Clean up orphaned segments on abort ([#4177](https://github.com/shaka-project/shaka-player/issues/4177)) ([c07447f](https://github.com/shaka-project/shaka-player/commit/c07447f00e9095020890366695561b71b045e55a))
* **offline:** Speed up offline storage by ~87% ([#4176](https://github.com/shaka-project/shaka-player/issues/4176)) ([c1c9613](https://github.com/shaka-project/shaka-player/commit/c1c96135120480afc9615713812eecc4a51f153b)), closes [#4166](https://github.com/shaka-project/shaka-player/issues/4166)
* **performance:** Eliminate use of ES6 generators ([#4092](https://github.com/shaka-project/shaka-player/issues/4092)) ([57c7324](https://github.com/shaka-project/shaka-player/commit/57c73241a0e8ce1615f7b3aca4c3ad8f69b7e8c2)), closes [#4062](https://github.com/shaka-project/shaka-player/issues/4062)
* Revert "Add missing module export in generated typescript defs" ([#4175](https://github.com/shaka-project/shaka-player/issues/4175)) ([fe4f5c6](https://github.com/shaka-project/shaka-player/commit/fe4f5c6e19214d6cf4d42da9430de03040532bab)), closes [#4167](https://github.com/shaka-project/shaka-player/issues/4167)
* Select first of identical audio streams ([#3869](https://github.com/shaka-project/shaka-player/issues/3869)) ([a6d8610](https://github.com/shaka-project/shaka-player/commit/a6d8610241dc7c8abd56cf7f0d48993d6139dcae))
* Support multiple chapter tracks with same language ([#3868](https://github.com/shaka-project/shaka-player/issues/3868)) ([8c626ae](https://github.com/shaka-project/shaka-player/commit/8c626aec238c01ebad7ccd06c9313e4f2e99d383)), closes [#3597](https://github.com/shaka-project/shaka-player/issues/3597)
* **text:** Fix caption overlap. ([bf67d87](https://github.com/shaka-project/shaka-player/commit/bf67d87387b1dfc4d3d8e0661bfe4efb1e4083b2)), closes [#3850](https://github.com/shaka-project/shaka-player/issues/3850) [#3741](https://github.com/shaka-project/shaka-player/issues/3741)
* **text:** Fix webvtt offset in sequence mode ([#3955](https://github.com/shaka-project/shaka-player/issues/3955)) ([a4e9267](https://github.com/shaka-project/shaka-player/commit/a4e926772e1b754fe968ee6f97490f08a40fe535)), closes [#2337](https://github.com/shaka-project/shaka-player/issues/2337)
* **text:** Inherit alignment from regions. ([e9df8fb](https://github.com/shaka-project/shaka-player/commit/e9df8fb10c3752cb833e89c8ac793241497e29b6))
* **text:** Made nested cues inherit region ([#3837](https://github.com/shaka-project/shaka-player/issues/3837)) ([3ff48cb](https://github.com/shaka-project/shaka-player/commit/3ff48cba9b28a29e8decc11898e326d7918bc8f4)), closes [#3743](https://github.com/shaka-project/shaka-player/issues/3743)
* **text:** Remove caption wrapper bgColor ([#3838](https://github.com/shaka-project/shaka-player/issues/3838)) ([0117441](https://github.com/shaka-project/shaka-player/commit/0117441bb06e0325b84666d2a5a76c0c2de81725)), closes [#3745](https://github.com/shaka-project/shaka-player/issues/3745)
* **ttml:** Center subtitles by default ([#4023](https://github.com/shaka-project/shaka-player/issues/4023)) ([f2f24d5](https://github.com/shaka-project/shaka-player/commit/f2f24d528f71e59c81d6172c24da2f412ca18d70))
* **UI:** Add cursor pointer to range elements ([#4059](https://github.com/shaka-project/shaka-player/issues/4059)) ([33e8400](https://github.com/shaka-project/shaka-player/commit/33e84009dc9f6d48884ecfc2f66eeb285f60d05a)), closes [#3220](https://github.com/shaka-project/shaka-player/issues/3220)
* **UI:** Fix text UI not updating when text is disabled ([#3867](https://github.com/shaka-project/shaka-player/issues/3867)) ([9f53d39](https://github.com/shaka-project/shaka-player/commit/9f53d394279066f29a2d391b6964cba11c4a3e1e)), closes [#3728](https://github.com/shaka-project/shaka-player/issues/3728)

## 3.3.1 (2022-01-28)

Bugfixes:
  - Fix duplicate CMCD parameters in HLS live content
    - https://github.com/shaka-project/shaka-player/issues/3862
    - https://github.com/shaka-project/shaka-player/pull/3875
  - Inherit alignment from regions
  - Fix support for TTAF1 namespace (old version of TTML)
    - https://github.com/shaka-project/shaka-player/issues/3009
    - https://github.com/shaka-project/shaka-player/pull/3864
    - https://github.com/shaka-project/shaka-player/pull/3906
  - Fix misdetection of HEVC support on MS Edge
    - https://github.com/shaka-project/shaka-player/pull/3897
  - Fix caption overlap
    - https://github.com/shaka-project/shaka-player/issues/3850
    - https://github.com/shaka-project/shaka-player/issues/3741
  - Fix missing throughput in CMCD for HLS live
    - https://github.com/shaka-project/shaka-player/issues/3873
    - https://github.com/shaka-project/shaka-player/pull/3874
  - Support multiple chapter tracks with same language
    - https://github.com/shaka-project/shaka-player/issues/3597
    - https://github.com/shaka-project/shaka-player/pull/3868
  - Fix text UI not updating when text is disabled
    - https://github.com/shaka-project/shaka-player/issues/3728
    - https://github.com/shaka-project/shaka-player/pull/3867
  - Clear buffer on seek if mediaState is updating
    - https://github.com/shaka-project/shaka-player/issues/3299
    - https://github.com/shaka-project/shaka-player/pull/3795
  - Fix thumbnails issues
    - https://github.com/shaka-project/shaka-player/pull/3858
  - Made nested cues inherit region
    - https://github.com/shaka-project/shaka-player/issues/3743
    - https://github.com/shaka-project/shaka-player/pull/3837
  - Fix CMCD top bitrate reporting
    - https://github.com/shaka-project/shaka-player/issues/3851
    - https://github.com/shaka-project/shaka-player/pull/3852
  - Fix MediaCapabilities polyfill on Safari
    - https://github.com/shaka-project/shaka-player/issues/3696
    - https://github.com/shaka-project/shaka-player/issues/3530
  - Fix usage of Shaka without polyfills
    - https://github.com/shaka-project/shaka-player/issues/3843
  - Fix playback failure due to rounding errors
    - https://github.com/shaka-project/shaka-player/issues/3717
  - Fix HLS image track issues
    - https://github.com/shaka-project/shaka-player/issues/3840
  - Fix CMCD property mangling
    - https://github.com/shaka-project/shaka-player/issues/3839
    - https://github.com/shaka-project/shaka-player/pull/3842
  - Remove caption wrapper bgColor
    - https://github.com/shaka-project/shaka-player/issues/3745
    - https://github.com/shaka-project/shaka-player/pull/3838
  - Avoid WebCrypto randomUUID when CMCD disabled


## 3.2.3 (2022-01-28)

Bugfixes:
  - Fix support for TTAF1 namespace (old version of TTML)
    - https://github.com/shaka-project/shaka-player/issues/3009
    - https://github.com/shaka-project/shaka-player/pull/3864
    - https://github.com/shaka-project/shaka-player/pull/3906
  - Fix misdetection of HEVC support on MS Edge
    - https://github.com/shaka-project/shaka-player/pull/3897
  - Fix caption overlap
    - https://github.com/shaka-project/shaka-player/issues/3850
    - https://github.com/shaka-project/shaka-player/issues/3741
  - Support multiple chapter tracks with same language
    - https://github.com/shaka-project/shaka-player/issues/3597
    - https://github.com/shaka-project/shaka-player/pull/3868
  - Fix text UI not updating when text is disabled
    - https://github.com/shaka-project/shaka-player/issues/3728
    - https://github.com/shaka-project/shaka-player/pull/3867
  - Clear buffer on seek if mediaState is updating
    - https://github.com/shaka-project/shaka-player/issues/3299
    - https://github.com/shaka-project/shaka-player/pull/3795
  - Fix thumbnails issues
    - https://github.com/shaka-project/shaka-player/pull/3858
  - Made nested cues inherit region
    - https://github.com/shaka-project/shaka-player/issues/3743
    - https://github.com/shaka-project/shaka-player/pull/3837
  - Fix MediaCapabilities polyfill on Safari
    - https://github.com/shaka-project/shaka-player/issues/3696
    - https://github.com/shaka-project/shaka-player/issues/3530
  - Fix usage of Shaka without polyfills
    - https://github.com/shaka-project/shaka-player/issues/3843
  - Fix playback failure due to rounding errors
    - https://github.com/shaka-project/shaka-player/issues/3717
  - Fix HLS image track issues
    - https://github.com/shaka-project/shaka-player/issues/3840
  - Remove caption wrapper bgColor
    - https://github.com/shaka-project/shaka-player/issues/3745
    - https://github.com/shaka-project/shaka-player/pull/3838
  - Support "forced-subtitle" role
    - https://github.com/shaka-project/shaka-player/issues/3767
    - https://github.com/shaka-project/shaka-player/pull/3807
  - Fix time element height on Safari
    - https://github.com/shaka-project/shaka-player/issues/3739
    - https://github.com/shaka-project/shaka-player/pull/3809


## 3.1.5 (2022-01-28)

Bugfixes:
  - Fix support for TTAF1 namespace (old version of TTML)
    - https://github.com/shaka-project/shaka-player/issues/3009
    - https://github.com/shaka-project/shaka-player/pull/3864
    - https://github.com/shaka-project/shaka-player/pull/3906
  - Fix misdetection of HEVC support on MS Edge
    - https://github.com/shaka-project/shaka-player/pull/3897
  - Fix caption overlap
    - https://github.com/shaka-project/shaka-player/issues/3850
    - https://github.com/shaka-project/shaka-player/issues/3741
  - Fix text UI not updating when text is disabled
    - https://github.com/shaka-project/shaka-player/issues/3728
    - https://github.com/shaka-project/shaka-player/pull/3867
  - Clear buffer on seek if mediaState is updating
    - https://github.com/shaka-project/shaka-player/issues/3299
    - https://github.com/shaka-project/shaka-player/pull/3795
  - Made nested cues inherit region
    - https://github.com/shaka-project/shaka-player/issues/3743
    - https://github.com/shaka-project/shaka-player/pull/3837
  - Fix MediaCapabilities polyfill on Safari
    - https://github.com/shaka-project/shaka-player/issues/3696
    - https://github.com/shaka-project/shaka-player/issues/3530
  - Fix usage of Shaka without polyfills
    - https://github.com/shaka-project/shaka-player/issues/3843
  - Fix playback failure due to rounding errors
    - https://github.com/shaka-project/shaka-player/issues/3717
  - Remove caption wrapper bgColor
    - https://github.com/shaka-project/shaka-player/issues/3745
    - https://github.com/shaka-project/shaka-player/pull/3838
  - Support "forced-subtitle" role
    - https://github.com/shaka-project/shaka-player/issues/3767
    - https://github.com/shaka-project/shaka-player/pull/3807
  - Fix time element height on Safari
    - https://github.com/shaka-project/shaka-player/issues/3739
    - https://github.com/shaka-project/shaka-player/pull/3809


## 3.3.0 (2022-01-07)

New Features:
  - Adds singleClickForPlayAndPause config
    - https://github.com/shaka-project/shaka-player/issues/3821
  - Add media quality change events
    - https://github.com/shaka-project/shaka-player/pull/3700
  - Add Common Media Client Data (CMCD) logging support
    - https://github.com/shaka-project/shaka-player/issues/3619
    - https://github.com/shaka-project/shaka-player/pull/3662
  - Adds advanced ABR config options
    - https://github.com/shaka-project/shaka-player/issues/3422
    - https://github.com/shaka-project/shaka-player/pull/3706
  - Integrate with non-linear IMA CS ads
    - https://github.com/shaka-project/shaka-player/pull/3639
  - Add a config to dispatch all emsg boxes
    - https://github.com/shaka-project/shaka-player/issues/3348
    - https://github.com/shaka-project/shaka-player/pull/3653
  - Added Loop and PIP to context menu, and Statistics to overflow menu
    - https://github.com/shaka-project/shaka-player/pull/3578
  - Export LanguageUtils
    - https://github.com/shaka-project/shaka-player/issues/3692
  - Add randomUUID polyfill
    - https://github.com/shaka-project/shaka-player/pull/3669
  - Export individual polyfill install methods
    - https://github.com/shaka-project/shaka-player/pull/3660
  - Make default HLS audio/video codecs configurable
    - https://github.com/shaka-project/shaka-player/pull/3651
  - Add response HTTP status to Networking engine responses
    - https://github.com/shaka-project/shaka-player/issues/3640
    - https://github.com/shaka-project/shaka-player/pull/3641
  - Create segment index only when used
  - Partially support tts:textOutline
    - https://github.com/shaka-project/shaka-player/issues/3612
  - Add tooltips to control panel buttons
    - https://github.com/shaka-project/shaka-player/pull/3572
  - Add configurable rates
    - https://github.com/shaka-project/shaka-player/pull/3579
  - Add blob-url support
    - https://github.com/shaka-project/shaka-player/issues/1481
    - https://github.com/shaka-project/shaka-player/pull/3583
  - Add updateStartTime method to play
    - https://github.com/shaka-project/shaka-player/pull/3491
  - Add right-click context menu, statistics button
    - https://github.com/shaka-project/shaka-player/issues/2607
    - https://github.com/shaka-project/shaka-player/pull/3548
  - Added events for download lifecycle
    - https://github.com/shaka-project/shaka-player/issues/3533
  - Add Quality, Language, Playback, Captions buttons to control panel
    - https://github.com/shaka-project/shaka-player/pull/3465
  - Add goToLive method
    - https://github.com/shaka-project/shaka-player/pull/3527


## 3.2.2 (2022-01-06)

Bugfixes:
  - Allow comments in the TTML parser
    - https://github.com/shaka-project/shaka-player/issues/3766
    - https://github.com/shaka-project/shaka-player/pull/3827
  - Fix HDR signalling via essential or supplemental property
    - https://github.com/shaka-project/shaka-player/issues/3726
    - https://github.com/shaka-project/shaka-player/pull/3727
  - Fix MediaCapabilities polyfill on Playstation 5
    - https://github.com/shaka-project/shaka-player/issues/3582
    - https://github.com/shaka-project/shaka-player/pull/3808
  - Add DASH MIME type mapping for src= playback
    - https://github.com/shaka-project/shaka-player/pull/3805
  - Fix captions not working after a period transition on live DASH streams
    - https://github.com/shaka-project/shaka-player/issues/3783
    - https://github.com/shaka-project/shaka-player/pull/3801
  - Fix timestamp offset of CEA-608 cues
    - https://github.com/shaka-project/shaka-player/issues/3782
  - Force caption update when removing cues
  - Fixes parsing of HLS 'DEFAULT' attribute
    - https://github.com/shaka-project/shaka-player/issues/3769
    - https://github.com/shaka-project/shaka-player/pull/3771
  - support stpp.ttml codec in Mp4TtmlParser
    - https://github.com/shaka-project/shaka-player/pull/3754
  - Fix Russian translation
    - https://github.com/shaka-project/shaka-player/pull/3751
  - Fix HLS VOD duration
    - https://github.com/shaka-project/shaka-player/issues/3733
  - Query HDR transfer function
    - https://github.com/shaka-project/shaka-player/issues/3729
    - https://github.com/shaka-project/shaka-player/pull/3730
  - Fix styling of UI text cues
    - https://github.com/shaka-project/shaka-player/issues/3521
    - https://github.com/shaka-project/shaka-player/issues/3600
    - https://github.com/shaka-project/shaka-player/issues/3713
  - Fix seek range issues on transition from live to VOD
    - https://github.com/shaka-project/shaka-player/issues/3675
  - Enforce string-format of event data keys
    - https://github.com/shaka-project/shaka-player/issues/3710
  - Fix vp09 playback on webOS
    - https://github.com/shaka-project/shaka-player/pull/3566
  - Dedupe DRM init data
    - https://github.com/shaka-project/shaka-player/pull/3695
  - Failover in geo-redundant streams
    - https://github.com/shaka-project/shaka-player/pull/3587
  - Update Cast receiver ID for v3.2

Demo App:
  - Fix 'Tears of Steel (live, DASH, Server Side ads)'
    - https://github.com/shaka-project/shaka-player/pull/3758

Docs:
  - Fix typo in Fairplay tutorial
    - https://github.com/shaka-project/shaka-player/pull/3714


## 3.1.4 (2022-01-06)

Bugfixes:
  - Allow comments in the TTML parser
    - https://github.com/shaka-project/shaka-player/issues/3766
    - https://github.com/shaka-project/shaka-player/pull/3827
  - Fix HDR signalling via essential or supplemental property
    - https://github.com/shaka-project/shaka-player/issues/3726
    - https://github.com/shaka-project/shaka-player/pull/3727
  - Fix MediaCapabilities polyfill on Playstation 5
    - https://github.com/shaka-project/shaka-player/issues/3582
    - https://github.com/shaka-project/shaka-player/pull/3808
  - Add DASH MIME type mapping for src= playback
    - https://github.com/shaka-project/shaka-player/pull/3805
  - Fix captions not working after a period transition on live DASH streams
    - https://github.com/shaka-project/shaka-player/issues/3783
    - https://github.com/shaka-project/shaka-player/pull/3801
  - Fix timestamp offset of CEA-608 cues
    - https://github.com/shaka-project/shaka-player/issues/3782
  - Force caption update when removing cues
  - Fixes parsing of HLS 'DEFAULT' attribute
    - https://github.com/shaka-project/shaka-player/issues/3769
    - https://github.com/shaka-project/shaka-player/pull/3771
  - support stpp.ttml codec in Mp4TtmlParser
    - https://github.com/shaka-project/shaka-player/pull/3754
  - Fix Russian translation
    - https://github.com/shaka-project/shaka-player/pull/3751
  - Fix HLS VOD duration
    - https://github.com/shaka-project/shaka-player/issues/3733
  - Query HDR transfer function
    - https://github.com/shaka-project/shaka-player/issues/3729
    - https://github.com/shaka-project/shaka-player/pull/3730
  - Fix styling of UI text cues
    - https://github.com/shaka-project/shaka-player/issues/3521
    - https://github.com/shaka-project/shaka-player/issues/3600
    - https://github.com/shaka-project/shaka-player/issues/3713
  - Fix seek range issues on transition from live to VOD
    - https://github.com/shaka-project/shaka-player/issues/3675
  - Enforce string-format of event data keys.
    - https://github.com/shaka-project/shaka-player/issues/3710
  - Fix vp09 playback on webOS
    - https://github.com/shaka-project/shaka-player/pull/3566
  - Dedupe DRM init data
    - https://github.com/shaka-project/shaka-player/pull/3695
  - Failover in geo-redundant streams
    - https://github.com/shaka-project/shaka-player/pull/3587

Demo App:
  - Fix 'Tears of Steel (live, DASH, Server Side ads)'
    - https://github.com/shaka-project/shaka-player/pull/3758

Docs:
  - Fix typo in Fairplay tutorial
    - https://github.com/shaka-project/shaka-player/pull/3714


## 3.0.15 (2022-01-06)

Bugfixes:
  - Allow comments in the TTML parser
    - https://github.com/shaka-project/shaka-player/issues/3766
    - https://github.com/shaka-project/shaka-player/pull/3827
  - Add DASH MIME type mapping for src= playback
    - https://github.com/shaka-project/shaka-player/pull/3805
  - Fix captions not working after a period transition on live DASH streams
    - https://github.com/shaka-project/shaka-player/issues/3783
    - https://github.com/shaka-project/shaka-player/pull/3801
  - Force caption update when removing cues
  - Fixes parsing of HLS 'DEFAULT' attribute
    - https://github.com/shaka-project/shaka-player/issues/3769
    - https://github.com/shaka-project/shaka-player/pull/3771
  - support stpp.ttml codec in Mp4TtmlParser
    - https://github.com/shaka-project/shaka-player/pull/3754
  - Fix Russian translation
    - https://github.com/shaka-project/shaka-player/pull/3751
  - Made HLS notify segments after fit
    - https://github.com/shaka-project/shaka-player/issues/3733
  - Fix seek range issues on transition from live to VOD
    - https://github.com/shaka-project/shaka-player/issues/3675
  - Enforce string-format of event data keys
    - https://github.com/shaka-project/shaka-player/issues/3710
  - Dedupe DRM init data
    - https://github.com/shaka-project/shaka-player/pull/3695
  - Failover in geo-redundant streams
    - https://github.com/shaka-project/shaka-player/pull/3587

Demo App:
  - Fix 'Tears of Steel (live, DASH, Server Side ads)'
    - https://github.com/shaka-project/shaka-player/pull/3758

Docs:
  - Fix typo in Fairplay tutorial
    - https://github.com/shaka-project/shaka-player/pull/3714


## 3.2.1 (2021-10-13)

Bugfixes:
  - Work around override of MediaCapabilities polyfill in Apple browsers
    - https://github.com/shaka-project/shaka-player/issues/3530
    - https://github.com/shaka-project/shaka-player/pull/3668
  - Fix video poster when autoplay is disabled
    - https://github.com/shaka-project/shaka-player/pull/3645
  - Fix tracking of active variant track in live streams
  - Fixes updating of nested cues
    - https://github.com/shaka-project/shaka-player/issues/3524
    - https://github.com/shaka-project/shaka-player/issues/3643
  - Fix ttml erroneously dismissing cues
    - https://github.com/shaka-project/shaka-player/issues/3643
  - Fix control panel alignment in UI
    - https://github.com/shaka-project/shaka-player/pull/3650
  - Export missing polyfill install methods
    - https://github.com/shaka-project/shaka-player/pull/3660
  - Dispose of ad manager on player detach
    - https://github.com/shaka-project/shaka-player/pull/3665
  - Add ResizeObserver to CS ad manager
    - https://github.com/shaka-project/shaka-player/pull/3652
  - Avoid seeking on src when start time is 0
    - https://github.com/shaka-project/shaka-player/issues/3518
    - https://github.com/shaka-project/shaka-player/pull/3644
  - Tolerate misaligned TS files
    - https://github.com/shaka-project/shaka-player/issues/3580
  - Account for server-side ad cue points in external text tracks
    - https://github.com/shaka-project/shaka-player/pull/3617
  - Fix stopping of Server Side Ad manager
    - https://github.com/shaka-project/shaka-player/pull/3611
  - Fix DRM workaround for Tizen and Xbox with ac-3 boxes
    - https://github.com/shaka-project/shaka-player/issues/3589
    - https://github.com/shaka-project/shaka-player/pull/3631
  - Fix DRM workaround for Tizen and Xbox with avc3 boxes
    - https://github.com/shaka-project/shaka-player/pull/3625
  - Fix `BUFFER_READ_OUT_OF_BOUNDS` error when CEA caption packets are empty
    - https://github.com/shaka-project/shaka-player/issues/3608
    - https://github.com/shaka-project/shaka-player/pull/3609
  - Fix error when un-storing DRM asset
    - https://github.com/shaka-project/shaka-player/issues/3534
  - Fix CC parsing of EPB and v1 TKHD boxes
    - https://github.com/shaka-project/shaka-player/issues/3502
    - https://github.com/shaka-project/shaka-player/pull/3610
  - Always polyfill MediaCapabilities for Apple browsers
    - https://github.com/shaka-project/shaka-player/pull/3588
  - Add Support to iOS 12 in MediaCapabilities polyfill
    - https://github.com/shaka-project/shaka-player/pull/3573
  - Add support to file type in MediaCapabilities implementation
    - https://github.com/shaka-project/shaka-player/pull/3570
  - Display captions with forward slashes
    - https://github.com/shaka-project/shaka-player/issues/3555
    - https://github.com/shaka-project/shaka-player/pull/3556
  - Add support to file type in MediaCapabilities polyfill
    - https://github.com/shaka-project/shaka-player/pull/3569
  - Use "undetermined" for missing CC language
  - Fix FairPlay playback
    - https://github.com/shaka-project/shaka-player/pull/3531
  - Exit PiP when destroying UI
    - https://github.com/shaka-project/shaka-player/issues/3553

Docs:
  - Add FAQ entry for common Vue problem
    - https://github.com/shaka-project/shaka-player/issues/3155


## 3.1.3 (2021-10-13)

Bugfixes:
  - Work around override of MediaCapabilities polyfill in Apple browsers
    - https://github.com/shaka-project/shaka-player/issues/3530
    - https://github.com/shaka-project/shaka-player/pull/3668
  - Add support to file type in MediaCapabilities implementation
    - https://github.com/shaka-project/shaka-player/pull/3570
  - Fix video poster when autoplay is disabled
    - https://github.com/shaka-project/shaka-player/pull/3645
  - Fix tracking of active variant track in live streams
  - Fixes updating of nested cues
    - https://github.com/shaka-project/shaka-player/issues/3524
    - https://github.com/shaka-project/shaka-player/issues/3643
  - Fix ttml erroneously dismissing cues
    - https://github.com/shaka-project/shaka-player/issues/3643
  - Fix control panel alignment in UI
    - https://github.com/shaka-project/shaka-player/pull/3650
  - Export missing polyfill install methods
    - https://github.com/shaka-project/shaka-player/pull/3660
  - Dispose of ad manager on player detach
    - https://github.com/shaka-project/shaka-player/pull/3665
  - Add ResizeObserver to CS ad manager
    - https://github.com/shaka-project/shaka-player/pull/3652
  - Avoid seeking on src when start time is 0
    - https://github.com/shaka-project/shaka-player/issues/3518
    - https://github.com/shaka-project/shaka-player/pull/3644
  - Tolerate misaligned TS files
    - https://github.com/shaka-project/shaka-player/issues/3580
  - Fix stopping of Server Side Ad manager
    - https://github.com/shaka-project/shaka-player/pull/3611
  - Fix DRM workaround for Tizen and Xbox with ac-3 boxes
    - https://github.com/shaka-project/shaka-player/issues/3589
    - https://github.com/shaka-project/shaka-player/pull/3631
  - Fix DRM workaround for Tizen and Xbox with avc3 boxes
    - https://github.com/shaka-project/shaka-player/pull/3625
  - Fix `BUFFER_READ_OUT_OF_BOUNDS` error when CEA caption packets are empty
    - https://github.com/shaka-project/shaka-player/issues/3608
    - https://github.com/shaka-project/shaka-player/pull/3609
  - Fix error when un-storing DRM asset
    - https://github.com/shaka-project/shaka-player/issues/3534
  - Fix CC parsing of EPB and v1 TKHD boxes
    - https://github.com/shaka-project/shaka-player/issues/3502
    - https://github.com/shaka-project/shaka-player/pull/3610
  - Always polyfill MediaCapabilities for Apple browsers
    - https://github.com/shaka-project/shaka-player/pull/3588
  - Add Support to iOS 12 in MediaCapabilities polyfill
    - https://github.com/shaka-project/shaka-player/pull/3573
  - Display captions with forward slashes
    - https://github.com/shaka-project/shaka-player/issues/3555
    - https://github.com/shaka-project/shaka-player/pull/3556
  - Add support to file type in MediaCapabilities polyfill
    - https://github.com/shaka-project/shaka-player/pull/3569
  - Use "undetermined" for missing CC language
  - Exit PiP when destroying UI
    - https://github.com/shaka-project/shaka-player/issues/3553

Docs:
  - Add FAQ entry for common Vue problem
    - https://github.com/shaka-project/shaka-player/issues/3155


## 3.0.14 (2021-10-13)

Bugfixes:
  - Fix video poster when autoplay is disabled
    - https://github.com/shaka-project/shaka-player/pull/3645
  - Fix tracking of active variant track in live streams
  - Fix control panel alignment in UI
    - https://github.com/shaka-project/shaka-player/pull/3650
  - Export missing polyfill install methods
    - https://github.com/shaka-project/shaka-player/pull/3660
  - Dispose of ad manager on player detach
    - https://github.com/shaka-project/shaka-player/pull/3665
  - Add ResizeObserver to CS ad manager
    - https://github.com/shaka-project/shaka-player/pull/3652
  - Avoid seeking on src when start time is 0
    - https://github.com/shaka-project/shaka-player/issues/3518
    - https://github.com/shaka-project/shaka-player/pull/3644
  - Tolerate misaligned TS files
    - https://github.com/shaka-project/shaka-player/issues/3580
  - Fix stopping of Server Side Ad manager
    - https://github.com/shaka-project/shaka-player/pull/3611
  - Fix DRM workaround for Tizen and Xbox with ac-3 boxes
    - https://github.com/shaka-project/shaka-player/issues/3589
    - https://github.com/shaka-project/shaka-player/pull/3631
  - Fix DRM workaround for Tizen and Xbox with avc3 boxes
    - https://github.com/shaka-project/shaka-player/pull/3625
  - Fix error when un-storing DRM asset
    - https://github.com/shaka-project/shaka-player/issues/3534
  - Exit PiP when destroying UI
    - https://github.com/shaka-project/shaka-player/issues/3553

Docs:
  - Add FAQ entry for common Vue problem
    - https://github.com/shaka-project/shaka-player/issues/3155


## 3.2.0 (2021-07-14)

New Features:
  - MediaCapabilities support: configs for preferred codecs, decoding
    attributes, and key systems
    - https://github.com/shaka-project/shaka-player/pull/3424
    - https://github.com/shaka-project/shaka-player/issues/1391
    - https://github.com/shaka-project/shaka-player/issues/3002
  - Support more frequent segment updates during streaming
    - https://github.com/shaka-project/shaka-player/pull/3483
  - Add callback for apps to pre-process DASH manifests
    - https://github.com/shaka-project/shaka-player/issues/3339
    - https://github.com/shaka-project/shaka-player/pull/3480
  - Add chapters support
    - https://github.com/shaka-project/shaka-player/pull/2972
  - Add support for HLS Image Media Playlists
    - https://github.com/shaka-project/shaka-player/pull/3365
  - Add align and vertical settings to WebVttGenerator
    - https://github.com/shaka-project/shaka-player/pull/3413
  - Add a buffer fullness method
    - https://github.com/shaka-project/shaka-player/issues/3389
    - https://github.com/shaka-project/shaka-player/pull/3392
  - Progress toward FairPlay DRM w/ MSE
    - https://github.com/shaka-project/shaka-player/pull/3347
  - Add serverCertificateUri in DRM advanced config
    - https://github.com/shaka-project/shaka-player/issues/1906
    - https://github.com/shaka-project/shaka-player/pull/3358
  - Add goToLive method
    - https://github.com/shaka-project/shaka-player/pull/3527


## 3.1.2 (2021-07-14)

Bugfixes:
  - Fix choosing tracks from streaming event
    - https://github.com/shaka-project/shaka-player/issues/3448
    - https://github.com/shaka-project/shaka-player/pull/3459
  - Fix multiperiod without consistent thumbnails
    - https://github.com/shaka-project/shaka-player/issues/3383
  - Fix failure with multiple thumbnails per period
    - https://github.com/shaka-project/shaka-player/issues/3383
  - Update Play icon after seeking from end
    - https://github.com/shaka-project/shaka-player/pull/3515
  - Reset forced subs between loads
  - Fix thumbnail position calculation
    - https://github.com/shaka-project/shaka-player/issues/3511
    - https://github.com/shaka-project/shaka-player/pull/3516
  - Fix thumbnail duration, expose start time and duration
    - https://github.com/shaka-project/shaka-player/pull/3517
  - Fix enforcement of cue alignment styles
    - https://github.com/shaka-project/shaka-player/issues/3379
  - Fix DASH transition from dynamic to static
    - https://github.com/shaka-project/shaka-player/pull/3497
  - Fix ARIA label on replay button
    - https://github.com/shaka-project/shaka-player/pull/3513
  - Fix audio language switching while using AirPlay
    - https://github.com/shaka-project/shaka-player/issues/3125
    - https://github.com/shaka-project/shaka-player/pull/3472
  - Show captions with rapid seek when ignoreTextStreamFailures is true
    - https://github.com/shaka-project/shaka-player/pull/3476
  - Fix clearing buffer when requested for already-selected variant
    - https://github.com/shaka-project/shaka-player/pull/3477
  - Fix hung playback on rapid seek
    - https://github.com/shaka-project/shaka-player/pull/3479
  - Don't show AirPlay button if unavailable
    - https://github.com/shaka-project/shaka-player/issues/3471
  - Fix bogus debug logs

Docs:
  - Update upgrade guides
    - https://github.com/shaka-project/shaka-player/issues/3487


## 3.0.13 (2021-07-14)

Bugfixes:
  - Fix choosing tracks from streaming event
    - https://github.com/shaka-project/shaka-player/issues/3448
    - https://github.com/shaka-project/shaka-player/pull/3459
  - Update Play icon after seeking from end
    - https://github.com/shaka-project/shaka-player/pull/3515
  - Fix DASH transition from dynamic to static
    - https://github.com/shaka-project/shaka-player/pull/3497
  - Fix ARIA label on replay button
    - https://github.com/shaka-project/shaka-player/pull/3513
  - Fix audio language switching while using AirPlay
    - https://github.com/shaka-project/shaka-player/issues/3125
    - https://github.com/shaka-project/shaka-player/pull/3472
  - Show captions with rapid seek when ignoreTextStreamFailures is true
    - https://github.com/shaka-project/shaka-player/pull/3476
  - Fix clearing buffer when requested for already-selected variant
    - https://github.com/shaka-project/shaka-player/pull/3477
  - Fix hung playback on rapid seek
    - https://github.com/shaka-project/shaka-player/pull/3479


## 3.1.1 (2021-06-17)

Bugfixes:
  - Fix buffering due to re-fetch in multi-period DASH
    - https://github.com/shaka-project/shaka-player/pull/3419
    - https://github.com/shaka-project/shaka-player/issues/3354
  - Prioritize AVERAGE-BANDWIDTH over BANDWIDTH in HLS
    - https://github.com/shaka-project/shaka-player/pull/3428
  - Fix EC-3 box support in DRM workaround on smart TVs
    - https://github.com/shaka-project/shaka-player/pull/3427
  - Fix exception in UI on devices that do not support fullscreen
    - https://github.com/shaka-project/shaka-player/issues/3441
  - Fix caption positioning and sizing when the container resizes
    - https://github.com/shaka-project/shaka-player/pull/3426
    - https://github.com/shaka-project/shaka-player/pull/3425
    - https://github.com/shaka-project/shaka-player/pull/3414
  - Fix exceptions thrown in content with trick-mode tracks
    - https://github.com/shaka-project/shaka-player/issues/3423
  - Filter unsupported H.264 streams in Xbox
    - https://github.com/shaka-project/shaka-player/pull/3411
  - Fix out-of-bounds exception in LL-DASH
    - https://github.com/shaka-project/shaka-player/issues/3402
    - https://github.com/shaka-project/shaka-player/pull/3403
  - Fix failures and gaps in LL-DASH
    - https://github.com/shaka-project/shaka-player/issues/3404
    - https://github.com/shaka-project/shaka-player/pull/3405
  - Allow muxjs to be loaded after Shaka
    - https://github.com/shaka-project/shaka-player/issues/3407
  - Choose the configured preferred text role at start
    - https://github.com/shaka-project/shaka-player/pull/3399
  - Fix STORAGE_LIMIT_REACHED error masked by DOWNLOAD_SIZE_CALLBACK_ERROR
    - https://github.com/shaka-project/shaka-player/pull/3396
  - Fix "details" field in shaka-ui-load-failed event
    - https://github.com/shaka-project/shaka-player/issues/3388
  - Ignore network changes if ABR is disabled
    - https://github.com/shaka-project/shaka-player/pull/3387
  - Fix ClearKey+WebM+src= playback failure
    - https://github.com/shaka-project/shaka-player/issues/3366

Docs:
  - Document disabling Range header requests in HLS
    - https://github.com/shaka-project/shaka-player/pull/3442
  - Add Angular integration link
    - https://github.com/shaka-project/shaka-player/pull/3409

Demo App:
  - Add MIME type and extra config to custom assets


## 3.0.12 (2021-06-17)

Bugfixes:
  - Fix buffering due to re-fetch in multi-period DASH
    - https://github.com/shaka-project/shaka-player/pull/3419
    - https://github.com/shaka-project/shaka-player/issues/3354
  - Prioritize AVERAGE-BANDWIDTH over BANDWIDTH in HLS
    - https://github.com/shaka-project/shaka-player/pull/3428
  - Fix EC-3 box support in DRM workaround on smart TVs
    - https://github.com/shaka-project/shaka-player/pull/3427
  - Fix exception in UI on devices that do not support fullscreen
    - https://github.com/shaka-project/shaka-player/issues/3441
  - Fix caption positioning and sizing when the container resizes
    - https://github.com/shaka-project/shaka-player/pull/3426
    - https://github.com/shaka-project/shaka-player/pull/3425
    - https://github.com/shaka-project/shaka-player/pull/3414
  - Fix exceptions thrown in content with trick-mode tracks
    - https://github.com/shaka-project/shaka-player/issues/3423
  - Filter unsupported H.264 streams in Xbox
    - https://github.com/shaka-project/shaka-player/pull/3411
  - Choose the configured preferred text role at start
    - https://github.com/shaka-project/shaka-player/pull/3399
  - Fix ClearKey+WebM+src= playback failure
    - https://github.com/shaka-project/shaka-player/issues/3366
  - Fix double-display of embedded and non-embedded captions
    - https://github.com/shaka-project/shaka-player/issues/3199

Docs:
  - Document disabling Range header requests in HLS
    - https://github.com/shaka-project/shaka-player/pull/3442
  - Add Angular integration link
    - https://github.com/shaka-project/shaka-player/pull/3409


## 2.5.23 (2021-06-17)

Bugfixes:
  - Prioritize AVERAGE-BANDWIDTH over BANDWIDTH in HLS
    - https://github.com/shaka-project/shaka-player/pull/3428
  - Fix exception in UI on devices that do not support fullscreen
    - https://github.com/shaka-project/shaka-player/issues/3441
  - Fix caption positioning and sizing when the container resizes
    - https://github.com/shaka-project/shaka-player/pull/3426
    - https://github.com/shaka-project/shaka-player/pull/3425
    - https://github.com/shaka-project/shaka-player/pull/3414
  - Filter unsupported H.264 streams in Xbox
    - https://github.com/shaka-project/shaka-player/pull/3411
  - Choose the configured preferred text role at start
    - https://github.com/shaka-project/shaka-player/pull/3399
  - Fix ClearKey+WebM+src= playback failure
    - https://github.com/shaka-project/shaka-player/issues/3366

Docs:
  - Add Angular integration link
    - https://github.com/shaka-project/shaka-player/pull/3409


## 3.1.0 (2021-04-29)

New Features:
  - Ads APIs are now STABLE (no longer BETA)
  - MediaCapabilities support (BETA)
    - https://github.com/shaka-project/shaka-player/issues/1391
  - Remove support for IE11
    - https://github.com/shaka-project/shaka-player/issues/2339
  - Low-latency HLS (LL-HLS) and DASH (LL-DASH) support
    - https://github.com/shaka-project/shaka-player/issues/1525
  - Make DASH keySystems configurable
    - https://github.com/shaka-project/shaka-player/pull/3276
  - Make DRM sessionType configurable in advanced DRM config
    - https://github.com/shaka-project/shaka-player/pull/3301
  - Add Loop, PIP, Cast, AirPlay buttons to control panel
    - https://github.com/shaka-project/shaka-player/issues/2676
    - https://github.com/shaka-project/shaka-player/pull/3255
  - Network stall detection
    - https://github.com/shaka-project/shaka-player/pull/3227
  - Store thumbnails for offline playback
    - https://github.com/shaka-project/shaka-player/pull/3280
  - Extract HDR metadata from DASH manifests
    - https://github.com/shaka-project/shaka-player/pull/3226
  - Make gap detection threshold configurable
    - https://github.com/shaka-project/shaka-player/pull/3166
  - Support WebVTT default text color and default text background color
    - https://github.com/shaka-project/shaka-player/issues/3182
    - https://github.com/shaka-project/shaka-player/pull/3182
  - Add support for thumbnail tracks
    - https://github.com/shaka-project/shaka-player/pull/3145
  - Add getKeyStatuses to Player
  - Parse spatial audio from manifest
    - https://github.com/shaka-project/shaka-player/pull/3148
  - Add support for WebVTT style blocks
    - https://github.com/shaka-project/shaka-player/pull/3071
  - Add SubViewer (SBV) support
    - https://github.com/shaka-project/shaka-player/pull/3063
    - https://github.com/shaka-project/shaka-player/pull/3266
  - Add SubStation Alpha (SSA) support
    - https://github.com/shaka-project/shaka-player/pull/3060
  - Add downloadSizeCallback before storing offline
    - https://github.com/shaka-project/shaka-player/issues/3049
    - https://github.com/shaka-project/shaka-player/pull/3049
  - Extract HDR metadata from HLS manifests
    - https://github.com/shaka-project/shaka-player/issues/3116
    - https://github.com/shaka-project/shaka-player/pull/3116
  - add ignoreMaxSegmentDuration config for DASH manifest
    - https://github.com/shaka-project/shaka-player/pull/3115
  - Add navigator.storage.estimate polyfill
    - https://github.com/shaka-project/shaka-player/issues/2900
    - https://github.com/shaka-project/shaka-player/pull/3050
  - Prefer unprefixed EME for Safari
    - https://github.com/shaka-project/shaka-player/pull/3021
  - Add config to prefer native HLS playback
    - https://github.com/shaka-project/shaka-player/issues/3077
  - Add LyRiCs (LRC) support
    - https://github.com/shaka-project/shaka-player/pull/3036
  - Add support for SMPTE namespace 2013
    - https://github.com/shaka-project/shaka-player/issues/3061
    - https://github.com/shaka-project/shaka-player/pull/3062
  - Add support for mpegB:cicp:ChannelConfiguration
    - https://github.com/shaka-project/shaka-player/pull/3057
  - Config to prefer forced subtitles
    - https://github.com/shaka-project/shaka-player/pull/3022
  - Change default network request timeout
    - https://github.com/shaka-project/shaka-player/pull/3024
  - Optionally force HTTPS content URIs
    - https://github.com/shaka-project/shaka-player/pull/3025
  - Add parameter to probeSupport to skip DRM tests
    - https://github.com/shaka-project/shaka-player/pull/3047
  - Add autoLowLatencyMode config
    - https://github.com/shaka-project/shaka-player/issues/1525
    - https://github.com/shaka-project/shaka-player/pull/2861
  - Allow apps to register a custom seek bar UI implementation
    - https://github.com/shaka-project/shaka-player/issues/2924
    - https://github.com/shaka-project/shaka-player/pull/2966
  - Parse forced subtitles from manifest
    - https://github.com/shaka-project/shaka-player/issues/2122
    - https://github.com/shaka-project/shaka-player/issues/2916
    - https://github.com/shaka-project/shaka-player/pull/2938
  - Add addTextTrackAsync
    - https://github.com/shaka-project/shaka-player/pull/2932
  - Allow showing track labels in UI
    - https://github.com/shaka-project/shaka-player/issues/2927
  - Allow switching between mono and stereo tracks
    - https://github.com/shaka-project/shaka-player/pull/2911
  - Add support to side-load subtitles in src mode
    - https://github.com/shaka-project/shaka-player/pull/2874
  - Add SubRip (SRT) subtitle support
    - https://github.com/shaka-project/shaka-player/pull/2872
  - CEA-708 Decoder
    - https://github.com/shaka-project/shaka-player/pull/2807
  - Added completionPercent to playback stats
  - Render bold/italics/underline on SimpleTextDisplayer
    - https://github.com/shaka-project/shaka-player/pull/2779
  - Adds VTT tag rendering for bold, italic, and underline
    - https://github.com/shaka-project/shaka-player/issues/2348
    - https://github.com/shaka-project/shaka-player/pull/2776
  - CEA-608 Decoder
    - https://github.com/shaka-project/shaka-player/issues/2648
    - https://github.com/shaka-project/shaka-player/pull/2731
    - https://github.com/shaka-project/shaka-player/pull/2649
    - https://github.com/shaka-project/shaka-player/pull/2660
  - Add dependencies module to allow custom dependency injection
    - https://github.com/shaka-project/shaka-player/issues/2562
    - https://github.com/shaka-project/shaka-player/pull/2683
  - Add HLS PlayReady support
    - https://github.com/shaka-project/shaka-player/pull/2719
  - Add AirPlay button to overflow menu
    - https://github.com/shaka-project/shaka-player/pull/2701
  - Use Network Information API to react to network changes
    - https://github.com/shaka-project/shaka-player/pull/2663
  - Added polyfill for screen.orientation
  - Add support for EXT-X-SESSION-DATA in HLS
    - https://github.com/shaka-project/shaka-player/pull/2642
  - Add forceLandscapeOnFullscreen UI config
    - https://github.com/shaka-project/shaka-player/issues/883
    - https://github.com/shaka-project/shaka-player/issues/2653


## 3.0.11 (2021-04-28)

Bugfixes:
  - Assume MP4 in HLS if MIME type can't be deduced
    - https://github.com/shaka-project/shaka-player/issues/3142
    - https://github.com/shaka-project/shaka-player/pull/3325
  - Fix resolution changes with lang change
    - https://github.com/shaka-project/shaka-player/issues/3262
    - https://github.com/shaka-project/shaka-player/issues/3288
  - Resume previous playback speed after pause
    - https://github.com/shaka-project/shaka-player/issues/3261
  - Fix updating of the mute icon
    - https://github.com/shaka-project/shaka-player/pull/3307
  - Fix text writing-mode support in old versions of Tizen and WebOS
    - https://github.com/shaka-project/shaka-player/pull/3330
  - Show replay icon instead of play when video ends
    - https://github.com/shaka-project/shaka-player/issues/3247
    - https://github.com/shaka-project/shaka-player/pull/3253
  - Fix cross-browser focus outline
    - https://github.com/shaka-project/shaka-player/issues/2863
  - Fix rapid keyboard-based seeking
    - https://github.com/shaka-project/shaka-player/issues/3234
    - https://github.com/shaka-project/shaka-player/pull/3259
  - Fix holding keyboard controls
    - https://github.com/shaka-project/shaka-player/pull/3267
  - Display cursors as pointers on overflow menu buttons
    - https://github.com/shaka-project/shaka-player/pull/3218
  - Fix failed assertion for eviction logic
    - https://github.com/shaka-project/shaka-player/issues/3169
  - Fix stalls on a live dash stream
    - https://github.com/shaka-project/shaka-player/issues/3139
    - https://github.com/shaka-project/shaka-player/issues/3169
  - Fix HLS content type detection with text codecs
    - https://github.com/shaka-project/shaka-player/issues/3184

Ad Features (BETA):
  - Fix the skip ad button not being clickable
    - https://github.com/shaka-project/shaka-player/issues/3284
    - https://github.com/shaka-project/shaka-player/pull/3326
  - Add the original IMA event to the Shaka `AD_CLICKED` event
    - https://github.com/shaka-project/shaka-player/issues/3304
  - Add more info on serving limited ads to the tutorial

Demo App:
  - Fix centering of icons, add hover effect on settings
    - https://github.com/shaka-project/shaka-player/pull/3352

Docs:
  - Update event docs and event links
    - https://github.com/shaka-project/shaka-player/pull/3256
  - Add the UI Theme Gallery link to the docs
    - https://github.com/shaka-project/shaka-player/issues/3246
  - Fixed various grammatical errors and typos
    - https://github.com/shaka-project/shaka-player/pull/3342
    - https://github.com/shaka-project/shaka-player/pull/3340
  - Fix offline tutorial to use the correct config
    - https://github.com/shaka-project/shaka-player/pull/3337

Misc:
  - Allow testing with Chromium-based Edge in Karma
    - https://github.com/shaka-project/shaka-player/pull/3265
  - Official Xbox One support
    - https://github.com/shaka-project/shaka-player/issues/1705


## 2.5.22 (2021-04-28)

Bugfixes:
  - Assume MP4 in HLS if MIME type can't be deduced
    - https://github.com/shaka-project/shaka-player/issues/3142
    - https://github.com/shaka-project/shaka-player/pull/3325
  - Fix resolution changes with lang change
    - https://github.com/shaka-project/shaka-player/issues/3262
    - https://github.com/shaka-project/shaka-player/issues/3288
  - Resume previous playback speed after pause
    - https://github.com/shaka-project/shaka-player/issues/3261
  - Fix updating of the mute icon
    - https://github.com/shaka-project/shaka-player/pull/3307
  - Fix text writing-mode support in old versions of Tizen and WebOS
    - https://github.com/shaka-project/shaka-player/pull/3330
  - Show replay icon instead of play when video ends
    - https://github.com/shaka-project/shaka-player/issues/3247
    - https://github.com/shaka-project/shaka-player/pull/3253
  - Fix cross-browser focus outline
    - https://github.com/shaka-project/shaka-player/issues/2863
  - Fix rapid keyboard-based seeking
    - https://github.com/shaka-project/shaka-player/issues/3234
    - https://github.com/shaka-project/shaka-player/pull/3259
  - Fix holding keyboard controls
    - https://github.com/shaka-project/shaka-player/pull/3267
  - Fix stylelint on Windows
    - https://github.com/shaka-project/shaka-player/issues/2985
    - https://github.com/shaka-project/shaka-player/pull/3214
  - Display cursors as pointers on overflow menu buttons
    - https://github.com/shaka-project/shaka-player/pull/3218

Demo App:
  - Fix centering of icons, add hover effect on settings
    - https://github.com/shaka-project/shaka-player/pull/3352

Docs:
  - Update event docs and event links
  - Add the UI Theme Gallery link to the docs
    - https://github.com/shaka-project/shaka-player/issues/3246
  - Fixed various grammatical errors and typos
    - https://github.com/shaka-project/shaka-player/pull/3342
    - https://github.com/shaka-project/shaka-player/pull/3340

Misc:
  - Allow testing with Chromium-based Edge in Karma
    - https://github.com/shaka-project/shaka-player/pull/3265
  - Official Xbox One support
    - https://github.com/shaka-project/shaka-player/issues/1705


## 3.0.10 (2021-03-18)

Bugfixes:
  - Fix stalls in some multi-Period DASH content
    - https://github.com/shaka-project/shaka-player/issues/3230
  - Fix stylelint errors on Windows
    - https://github.com/shaka-project/shaka-player/issues/2985
    - https://github.com/shaka-project/shaka-player/pull/3214


## 3.0.9 (2021-03-15)

Bugfixes:
  - Fixed build error on Windows
    - https://github.com/shaka-project/shaka-player/issues/3208
    - https://github.com/shaka-project/shaka-player/issues/3204
    - https://github.com/shaka-project/shaka-player/pull/3211
  - Exported SegmentReference.getUris
    - https://github.com/shaka-project/shaka-player/issues/3096
  - Fix giant gaps in SSAI content
    - https://github.com/shaka-project/shaka-player/issues/3191
  - Fix TTML background image attribute case
    - https://github.com/shaka-project/shaka-player/issues/3196
  - Avoid setting global Cast hook
    - https://github.com/shaka-project/shaka-player/issues/3167
  - Fix codec choice when resolutions differ
    - https://github.com/shaka-project/shaka-player/issues/3056
    - https://github.com/shaka-project/shaka-player/pull/3072
  - Fix autoplay for non-zero-start VOD
    - https://github.com/shaka-project/shaka-player/issues/2987
  - Allow playing Periods with missing text
    - https://github.com/shaka-project/shaka-player/issues/2957
  - Support localized whitespace preservation in TTML
    - https://github.com/shaka-project/shaka-player/issues/3011
    - https://github.com/shaka-project/shaka-player/pull/3043
  - Fix offline storage after a failure
    - https://github.com/shaka-project/shaka-player/issues/2781
  - Fix repeated seek on start for some content
    - https://github.com/shaka-project/shaka-player/issues/2831
  - Fix subtitle display in timing edge case
    - https://github.com/shaka-project/shaka-player/issues/3151
    - https://github.com/shaka-project/shaka-player/pull/3152
  - Support version 1 emsg boxes
    - https://github.com/shaka-project/shaka-player/issues/1539
    - https://github.com/shaka-project/shaka-player/pull/3147
    - https://github.com/shaka-project/shaka-player/pull/3198

Ads (BETA):
  - Change the value of the 'mpt' param we set for tracking
  - Expose native IMA stream manager for SS DAI
  - Hide the ad container when ads aren't playing
    - https://github.com/shaka-project/shaka-player/issues/3121
  - Add "limited ads" section to the ads tutorial
  - Expand the IMA integration tutorial
    - https://github.com/shaka-project/shaka-player/issues/3168

Docs:
  - Fixed various typos
    - https://github.com/shaka-project/shaka-player/pull/3222
  - Fixed outdated info and typos
    - https://github.com/shaka-project/shaka-player/pull/3206
  - Document programmatic UI setup
    - https://github.com/shaka-project/shaka-player/issues/2655
  - Update doc for manifest and segment ALR
  - Add vue.js, nuxt.js and video.js integration examples
    - https://github.com/shaka-project/shaka-player/pull/3160

Demo App:
  - Make it possible to add custom ad assets with no manifest uri.
    - https://github.com/shaka-project/shaka-player/issues/3136
  - Add an ADS tab to the custom content page
    - https://github.com/shaka-project/shaka-player/issues/3136
  - Add DAI live DASH example to DEMO app
    - https://github.com/shaka-project/shaka-player/pull/3170


## 2.5.21 (2021-03-12)

Bugfixes:
  - Fix giant gaps in SSAI content
    - https://github.com/shaka-project/shaka-player/issues/3191
  - Fix TTML background image attribute case
    - https://github.com/shaka-project/shaka-player/issues/3196
  - Avoid setting global Cast hook
    - https://github.com/shaka-project/shaka-player/issues/3167
  - Fix codec choice when resolutions differ
    - https://github.com/shaka-project/shaka-player/pull/3072
  - Fix autoplay for non-zero-start VOD
    - https://github.com/shaka-project/shaka-player/issues/2987
  - Support localized whitespace preservation in TTML
    - https://github.com/shaka-project/shaka-player/issues/3011
    - https://github.com/shaka-project/shaka-player/pull/3043
  - Fix repeated seek on start for some content
    - https://github.com/shaka-project/shaka-player/issues/2831
  - Fix subtitle display in timing edge case
    - https://github.com/shaka-project/shaka-player/issues/3151
    - https://github.com/shaka-project/shaka-player/pull/3152
  - Fixed build error on Windows
    - https://github.com/shaka-project/shaka-player/pull/3211
    - https://github.com/shaka-project/shaka-player/issues/3208
    - https://github.com/shaka-project/shaka-player/issues/3204

Docs:
  - Fixed outdated info and typos
    - https://github.com/shaka-project/shaka-player/pull/3206
  - Fixed various typos
    - https://github.com/shaka-project/shaka-player/pull/3222
  - Document programmatic UI setup
    - https://github.com/shaka-project/shaka-player/issues/2655
  - Update doc for manifest and segment ALR


## 3.0.8 (2021-02-08)

Bugfixes:
  - Fix memory leak in Webpack-bundled version
    - https://github.com/shaka-project/shaka-player/issues/3092
    - https://github.com/shaka-project/shaka-player/pull/3098
  - Fix build in Python 3
    - https://github.com/shaka-project/shaka-player/issues/3102
  - Fix broken build in directories with spaces
    - https://github.com/shaka-project/shaka-player/issues/3102
  - Fix mixed clear/encrypted content on Xbox & Tizen
    - https://github.com/shaka-project/shaka-player/issues/2759
  - Fix trick mode tracks in DASH (work around compiler bug)
    - https://github.com/shaka-project/shaka-player/issues/3085
    - https://github.com/shaka-project/shaka-player/pull/3087
  - Fix DRM initialization on WebOS 3.0
    - https://github.com/shaka-project/shaka-player/pull/3109
  - Fix segment refs for "future" DASH periods
  - Recognize "m4f" extension in HLS
    - https://github.com/shaka-project/shaka-player/issues/3099
    - https://github.com/shaka-project/shaka-player/pull/3111
  - Catch unhandled rejection while destroying StreamingEngine
  - Fix header sizes for MP4 boxes with 64-bit size fields
  - Fix load-time exception in nodejs

Ads (BETA):
  - Use the correct AdsLoader `AD_ERROR` event
    - https://github.com/shaka-project/shaka-player/issues/3095
    - https://github.com/shaka-project/shaka-player/pull/3105
  - Expose getMinSuggestedDuration
  - Add setVpaidMode to the IMA externs
    - https://github.com/shaka-project/shaka-player/pull/3135


## 2.5.20 (2021-02-08)

Bugfixes:
  - Fix build in Python 3
    - https://github.com/shaka-project/shaka-player/issues/3102
  - Fix broken build in directories with spaces
    - https://github.com/shaka-project/shaka-player/issues/3102
  - Fix trick mode tracks in DASH (work around compiler bug)
    - https://github.com/shaka-project/shaka-player/issues/3085
    - https://github.com/shaka-project/shaka-player/pull/3087
  - Fix DRM initialization on WebOS 3.0
    - https://github.com/shaka-project/shaka-player/pull/3109
  - Recognize "m4f" extension in HLS
    - https://github.com/shaka-project/shaka-player/issues/3099
    - https://github.com/shaka-project/shaka-player/pull/3111
  - Fix header sizes for MP4 boxes with 64-bit size fields


## 3.0.7 (2021-01-06)

Bugfixes:
  - Fix text failures triggered by rapid stream switches
  - Remove legacy Edge workarounds on new Edge
  - Fix viewport anchor calculations in TTML
    - https://github.com/shaka-project/shaka-player/pull/3065
  - Fix slow memory leak related to MediaSource object URLs
    - https://github.com/shaka-project/shaka-player/issues/2953
  - Fix clicking in interactive client-side ads
    - https://github.com/shaka-project/shaka-player/issues/3053
  - Improve cue comparison performance
    - https://github.com/shaka-project/shaka-player/issues/3018
  - Fix race condition in text stream scheduling
    - https://github.com/shaka-project/shaka-player/issues/2764
  - Fix multiple stream-merging issues with DASH multi-period content
    - https://github.com/shaka-project/shaka-player/issues/2785
    - https://github.com/shaka-project/shaka-player/issues/2884
  - Fix exception when removing content from buffer
    - https://github.com/shaka-project/shaka-player/issues/2982
    - https://github.com/shaka-project/shaka-player/pull/3042
  - Fix memory leak in DASH with SegmentTimeline
    - https://github.com/shaka-project/shaka-player/issues/3038
    - https://github.com/shaka-project/shaka-player/pull/3039
  - Fix trick-mode tracks associated with multiple regular tracks
    - https://github.com/shaka-project/shaka-player/pull/2992
  - Fix TS DRM failures
    - https://github.com/shaka-project/shaka-player/issues/2981
  - Work around misreported AC-3 support on Tizen
    - https://github.com/shaka-project/shaka-player/issues/2989
  - Ignore incompatible TrickMode streams
    - https://github.com/shaka-project/shaka-player/pull/2984
  - Fix rare exception thrown when switching streams
    - https://github.com/shaka-project/shaka-player/issues/2956
    - https://github.com/shaka-project/shaka-player/issues/2970
  - Fix rendering of line breaks in text cues
    - https://github.com/shaka-project/shaka-player/issues/2828

Ads (BETA):
  - Fix ad disappearance when reconfiguring UI during an ad
    - https://github.com/shaka-project/shaka-player/issues/2869
    - https://github.com/shaka-project/shaka-player/issues/2943
  - Fix stopping ad manager after adblock

Build:
  - Fix build issues with Python 3
    - https://github.com/shaka-project/shaka-player/issues/3003
    - https://github.com/shaka-project/shaka-player/issues/3004
  - Fix running build scripts on Windows
    - https://github.com/shaka-project/shaka-player/issues/2988
  - Fix build error about stylelint paths
  - Fix build failure in context of node module

Demo App:
  - Fix keyboard navigation in settings
    - https://github.com/shaka-project/shaka-player/issues/2986

Docs:
  - Clean up doc generation
  - Fix docs generation for enums in ui
    - https://github.com/shaka-project/shaka-player/issues/2698


## 2.5.19 (2021-01-06)

Bugfixes:
  - Remove legacy Edge workarounds on new Edge
  - Fix viewport anchor calculations in TTML
    - https://github.com/shaka-project/shaka-player/pull/3065
  - Fix slow memory leak related to MediaSource object URLs
    - https://github.com/shaka-project/shaka-player/issues/2953
  - Improve cue comparison performance
    - https://github.com/shaka-project/shaka-player/issues/3018
  - Fix race condition in text stream scheduling
    - https://github.com/shaka-project/shaka-player/issues/2764
  - Fix exception when removing content from buffer
    - https://github.com/shaka-project/shaka-player/issues/2982
    - https://github.com/shaka-project/shaka-player/pull/3042
  - Work around misreported AC-3 support on Tizen
    - https://github.com/shaka-project/shaka-player/issues/2989
  - Fix trick-mode tracks associated with multiple regular tracks
    - https://github.com/shaka-project/shaka-player/pull/2992
  - Fix TS DRM failures
    - https://github.com/shaka-project/shaka-player/issues/2981
  - Ignore incompatible TrickMode streams
    - https://github.com/shaka-project/shaka-player/pull/2984

Build:
  - Fix build issues with Python 3
    - https://github.com/shaka-project/shaka-player/issues/3004
  - Fix running build scripts on Windows
    - https://github.com/shaka-project/shaka-player/issues/2988
  - Fix build error about stylelint paths
  - Fix build failure in context of node module

Demo App:
  - Fix keyboard navigation in settings
    - https://github.com/shaka-project/shaka-player/issues/2986

Docs:
  - Clean up doc generation
  - Fix docs generation for enums in ui
    - https://github.com/shaka-project/shaka-player/issues/2698


## 3.0.6 (2020-11-12)

Bugfixes:
  - Fix handling of metadata tracks for src= playback
    - https://github.com/shaka-project/shaka-player/pull/2971
  - Fix handling of role-less audio tracks
    - https://github.com/shaka-project/shaka-player/issues/2906
    - https://github.com/shaka-project/shaka-player/issues/2909
  - Fix support for multi-period encrypted live
    - https://github.com/shaka-project/shaka-player/issues/2979
    - https://github.com/shaka-project/shaka-player/issues/2645
  - Export UI externs
    - https://github.com/shaka-project/shaka-player/issues/2948
  - Fix duplicate init segment requests on manifest updates
    - https://github.com/shaka-project/shaka-player/issues/2856
    - https://github.com/shaka-project/shaka-player/pull/2942
  - Fix hard-coded TTML namespaces
    - https://github.com/shaka-project/shaka-player/issues/2756
  - Fix test failure on IE11
  - Filter out "chapters" tracks during src= playback
    - https://github.com/shaka-project/shaka-player/pull/2960
  - Fix compatibility for plugin factories
    - https://github.com/shaka-project/shaka-player/issues/2958
  - Be more permissive in vtt files
    - https://github.com/shaka-project/shaka-player/pull/2941
  - Fix renaming of UI base class protected members
    - https://github.com/shaka-project/shaka-player/issues/2923
  - Make submenu CSS apply to all submenus
    - https://github.com/shaka-project/shaka-player/issues/2925
  - Export FakeEvent for use by UI plugins
    - https://github.com/shaka-project/shaka-player/issues/2923
  - Recognize mp4a and mp4v extensions in HLS
  - Support multiple CHARACTERISTICS values in HLS
    - https://github.com/shaka-project/shaka-player/pull/2905
  - Don't auto-play after seeking while paused in the UI
    - https://github.com/shaka-project/shaka-player/pull/2898

Ad changes (BETA):
  - Allow apps to supply adsResponse property for IMA
    - https://github.com/shaka-project/shaka-player/issues/2892
    - https://github.com/shaka-project/shaka-player/pull/2946

Docs:
  - Add link to complete list of build categories
    - https://github.com/shaka-project/shaka-player/pull/2934
  - Correct receiver IDs in the UI tutorial
    - https://github.com/shaka-project/shaka-player/issues/2926
  - Update required Node version
    - https://github.com/shaka-project/shaka-player/issues/2913

Demo App:
  - Add test streams for CEA-608
    - https://github.com/shaka-project/shaka-player/pull/2939
  - Add new low latency DASH manifest
    - https://github.com/shaka-project/shaka-player/pull/2963
  - Remove redundant switch for manifest.dash.ignoreDrmInfo

Misc:
  - Add mkdir to make all build commands self-contained
    - https://github.com/shaka-project/shaka-player/issues/2973
    - https://github.com/shaka-project/shaka-player/pull/2977
  - Generate TypeScript defs with Clutz
    - https://github.com/shaka-project/shaka-player/issues/1030


## 2.5.18 (2020-11-12)

Bugfixes:
  - Fix handling of role-less audio tracks
    - https://github.com/shaka-project/shaka-player/issues/2906
    - https://github.com/shaka-project/shaka-player/issues/2909
  - Export UI externs
    - https://github.com/shaka-project/shaka-player/issues/2948
  - Fix hard-coded TTML namespaces
    - https://github.com/shaka-project/shaka-player/issues/2756
  - Filter out "chapters" tracks during src= playback
    - https://github.com/shaka-project/shaka-player/pull/2960
  - Fix renaming of UI base class protected members
    - https://github.com/shaka-project/shaka-player/issues/2923
  - Export FakeEvent for use by UI plugins
    - https://github.com/shaka-project/shaka-player/issues/2923
  - Recognize mp4a and mp4v extensions in HLS
  - Support multiple CHARACTERISTICS values in HLS
    - https://github.com/shaka-project/shaka-player/pull/2905
  - Don't auto-play after seeking while paused in the UI
    - https://github.com/shaka-project/shaka-player/pull/2898

Docs:
  - Add link to complete list of build categories
    - https://github.com/shaka-project/shaka-player/pull/2934
  - Update required Node version
    - https://github.com/shaka-project/shaka-player/issues/2913
  - Correct receiver app IDs in the UI tutorial
    - https://github.com/shaka-project/shaka-player/issues/2926

Demo App:
  - Remove redundant switch for manifest.dash.ignoreDrmInfo

Misc:
  - Add mkdir to make all build commands self-contained
    - https://github.com/shaka-project/shaka-player/issues/2973
    - https://github.com/shaka-project/shaka-player/pull/2977


## 3.0.5 (2020-10-07)

Bugfixes:
  - Fix hiding controls on mobile after touch
    - https://github.com/shaka-project/shaka-player/issues/2886
  - Ignore seek touch events on hidden controls
    - https://github.com/shaka-project/shaka-player/issues/2888
  - Fix interpretation of DEFAULT and AUTOSELECT in HLS
    - https://github.com/shaka-project/shaka-player/issues/2880
  - Avoid a race when clearing buffered content
  - Allow playback of video-only HLS via configuration
    - https://github.com/shaka-project/shaka-player/issues/2868
  - Make UITextDisplayer CSS-independent
    - https://github.com/shaka-project/shaka-player/issues/2817
    - https://github.com/shaka-project/shaka-player/pull/2819
  - Remove hard-coded tts:extent namespace in TTML parser
    - https://github.com/shaka-project/shaka-player/issues/2860
  - Don't apply seek range while content is still loading
    - https://github.com/shaka-project/shaka-player/issues/2848
    - https://github.com/shaka-project/shaka-player/issues/2748
    - https://github.com/shaka-project/shaka-player/pull/2849
  - Fix Shaka+Cast apps using IndexedDB
    - https://github.com/shaka-project/shaka-player/issues/2850
  - Permit applications to monkey-patch Date.now
    - https://github.com/shaka-project/shaka-player/pull/2857
  - Fix detection of Edge Chromium as Edge
    - https://github.com/shaka-project/shaka-player/pull/2855
  - Fix loading with global "define" set to null
    - https://github.com/shaka-project/shaka-player/issues/2847
  - Fix missing cues in UITextDisplayer
  - Fix storing modified init data for offline sessions
  - Fix duplicate text streams in multi-period DASH
    - https://github.com/shaka-project/shaka-player/pull/2885
  - Fix rapid seeking leading to infinite buffering
    - https://github.com/shaka-project/shaka-player/issues/2670
  - Fix non-deterministic exception in StreamingEngine
    - https://github.com/shaka-project/shaka-player/issues/2768
  - Fix bug where cue comparison throws
  - Fix exception on multi-period DASH
    - https://github.com/shaka-project/shaka-player/issues/2811
  - Fix embedded captions vanishing
    - https://github.com/shaka-project/shaka-player/issues/2811
  - Fix application of DRM server certificate
    - https://github.com/shaka-project/shaka-player/issues/2644
  - Fix multi-period DASH with period-specific codecs
    - https://github.com/shaka-project/shaka-player/issues/2883

Demo App:
  - Change the menu icon to a settings icon
  - Suppress bogus errors displayed during download

Docs:
  - Fix references to built-in CEA 608 support, not available in this branch
  - Add links to the roadmap
    - https://github.com/shaka-project/shaka-player/pull/2825


## 2.5.17 (2020-10-06)

Bugfixes:
  - Fix hiding controls on mobile after touch
    - https://github.com/shaka-project/shaka-player/issues/2886
  - Ignore seek touch events on hidden controls
    - https://github.com/shaka-project/shaka-player/issues/2888
  - Fix interpretation of DEFAULT and AUTOSELECT in HLS
    - https://github.com/shaka-project/shaka-player/issues/2880
  - Avoid a race when clearing buffered content
  - Allow playback of video-only HLS via configuration
    - https://github.com/shaka-project/shaka-player/issues/2868
  - Make UITextDisplayer CSS-independent
    - https://github.com/shaka-project/shaka-player/issues/2817
    - https://github.com/shaka-project/shaka-player/pull/2819
  - Remove hard-coded tts:extent namespace in TTML parser
    - https://github.com/shaka-project/shaka-player/issues/2860
  - Don't apply seek range while content is still loading
    - https://github.com/shaka-project/shaka-player/issues/2848
    - https://github.com/shaka-project/shaka-player/issues/2748
    - https://github.com/shaka-project/shaka-player/pull/2849
  - Fix Shaka+Cast apps using IndexedDB
    - https://github.com/shaka-project/shaka-player/issues/2850
  - Permit applications to monkey-patch Date.now
    - https://github.com/shaka-project/shaka-player/pull/2857
  - Fix detection of Edge Chromium as Edge
    - https://github.com/shaka-project/shaka-player/pull/2855
  - Fix loading with global "define" set to null
    - https://github.com/shaka-project/shaka-player/issues/2847
  - Fix missing cues in UITextDisplayer
  - Fix storing modified init data for offline sessions

Demo App:
  - Change the menu icon to a settings icon

Docs:
  - Fix references to built-in CEA 608 support, not available in this branch


## 3.0.4 (2020-08-25)

Bugfixes:
  - Fix case sensitivity in KEYID format check in HLS
    - https://github.com/shaka-project/shaka-player/issues/2789
    - https://github.com/shaka-project/shaka-player/pull/2790
  - Do not assume HDR for HEVC1.2 on Chromecast
    - https://github.com/shaka-project/shaka-player/issues/2813
  - Recognize "wvtt" codec in HLS WebVTT tracks
    - https://github.com/shaka-project/shaka-player/pull/2778
  - Fix case sensitivity for DRM content types
    - https://github.com/shaka-project/shaka-player/issues/2799
    - https://github.com/shaka-project/shaka-player/pull/2800
  - PlayReady only has little-endian key IDs on Edge & IE
    - https://github.com/shaka-project/shaka-player/pull/2801
  - Fix UI translation of "live" in Chinese
    - https://github.com/shaka-project/shaka-player/issues/2804

Docs:
  - Improve docs on platform support
    - https://github.com/shaka-project/shaka-player/issues/2783
    - https://github.com/shaka-project/shaka-player/pull/2787
    - https://github.com/shaka-project/shaka-player/pull/2794
    - https://github.com/shaka-project/shaka-player/pull/2795
  - Add doc on Application-Level Redirects


## 2.5.16 (2020-08-25)

Bugfixes:
  - Fix case sensitivity in KEYID format check in HLS
    - https://github.com/shaka-project/shaka-player/issues/2789
    - https://github.com/shaka-project/shaka-player/pull/2790
  - Do not assume HDR for HEVC1.2 on Chromecast
    - https://github.com/shaka-project/shaka-player/issues/2813
  - Recognize "wvtt" codec in HLS WebVTT tracks
    - https://github.com/shaka-project/shaka-player/pull/2778
  - Fix case sensitivity for DRM content types
    - https://github.com/shaka-project/shaka-player/issues/2799
    - https://github.com/shaka-project/shaka-player/pull/2800
  - PlayReady only has little-endian key IDs on Edge & IE
    - https://github.com/shaka-project/shaka-player/pull/2801
  - Fix UI translation of "live" in Chinese
    - https://github.com/shaka-project/shaka-player/issues/2804

Docs:
  - Improve docs on platform support
    - https://github.com/shaka-project/shaka-player/issues/2783
    - https://github.com/shaka-project/shaka-player/pull/2787
    - https://github.com/shaka-project/shaka-player/pull/2794
    - https://github.com/shaka-project/shaka-player/pull/2795
  - Add doc on Application-Level Redirects


## 3.0.3 (2020-08-12)

Bugfixes:
  - Fix timing of VTT in HLS without map header
    - https://github.com/shaka-project/shaka-player/issues/2714
  - Fix TTML style inheritance
  - Fix ordering of cues on IE and Edge
  - Fix VTTCue polyfill in uncompiled mode on Edge
  - Ensure the number of variants stays stable when new periods are added
    - https://github.com/shaka-project/shaka-player/issues/2716
    - https://github.com/shaka-project/shaka-player/issues/2736
  - Fix src= playback on WebOS
    - https://github.com/shaka-project/shaka-player/pull/2777
  - Filter timeline regions by seek range
    - https://github.com/shaka-project/shaka-player/issues/2716
  - Don't send duplicate license requests
    - https://github.com/shaka-project/shaka-player/issues/2754
  - Don't limit segment count for VOD
    - https://github.com/shaka-project/shaka-player/issues/2677
    - https://github.com/shaka-project/shaka-player/issues/2709
    - https://github.com/shaka-project/shaka-player/issues/2745
  - Fix data URI parsing when charset present
  - Fix rendering of TTML nested cues and spacers
    - https://github.com/shaka-project/shaka-player/issues/2760

Ad changes (BETA):
  - Add an extra log when replacing ad tag params for tracking adoption
  - Properly set tracking info for SS IMA streams

Demo App:
  - License header field for custom assets
    - https://github.com/shaka-project/shaka-player/issues/2758

Docs:
  - Correct very outdated docs on test.py


## 2.5.15 (2020-08-12)

Bugfixes:
  - Fix TTML style inheritance
  - Fix ordering of cues on IE and Edge
  - Fix src= playback on WebOS
    - https://github.com/shaka-project/shaka-player/pull/2777
  - Filter timeline regions by seek range
    - https://github.com/shaka-project/shaka-player/issues/2716
  - Don't send duplicate license requests
    - https://github.com/shaka-project/shaka-player/issues/2754
  - Fix data URI parsing when charset present
  - Fix rendering of TTML nested cues and spacers
    - https://github.com/shaka-project/shaka-player/issues/2760

Docs:
  - Correct very outdated docs on test.py


## 3.0.2 (2020-07-28)

Bugfixes:
  - Fix missing build/types/core in npm packages
    - https://github.com/shaka-project/shaka-player/issues/2752
  - Work around stalling playback on Tizen 3
    - https://github.com/shaka-project/shaka-player/issues/2620
  - Fix hang while shutting down Widevine DRM sessions
    - https://github.com/shaka-project/shaka-player/issues/2741
  - Fix initial bandwidth estimate on Tizen
  - Fix src= playback on Tizen 3
  - Work around less 3.12.0 bug
  - Improve logging of buffered ranges on WebOS
  - Fix use of --test-custom-license-server in test.py
  - Fix HLS discontinuity bug, broken playback with ads
    - https://github.com/shaka-project/shaka-player/issues/2687
  - Fix disappearing captions with certain input patterns
    - https://github.com/shaka-project/shaka-player/issues/2671
    - https://github.com/shaka-project/shaka-player/pull/2674
  - Fix missing captions when switching streams
    - https://github.com/shaka-project/shaka-player/issues/2648
    - https://github.com/shaka-project/shaka-player/pull/2672
  - Append license for language-mapping-list to output

Ad changes (BETA):
  - Proxy all client-side IMA events through the ad manager
  - Fire a shaka.Player.Metadata event on detecting ID3 metadata
    - https://github.com/shaka-project/shaka-player/issues/2592

Docs:
  - Update tutorial for seek bar color changes
    - https://github.com/shaka-project/shaka-player/issues/2708
  - Add FAQ entry for native HLS playback in Safari
  - Update tutorials and docs to async/await syntax
    - https://github.com/shaka-project/shaka-player/issues/2544
    - https://github.com/shaka-project/shaka-player/pull/2693
  - Update tutorials and docs to use modern variable syntax (const/let)
    - https://github.com/shaka-project/shaka-player/issues/2544
    - https://github.com/shaka-project/shaka-player/pull/2692

Demo App:
  - Fix demo behavior when UI fails to load (due to ad blocker)
    - https://github.com/shaka-project/shaka-player/issues/2669


## 3.0.1 (2020-06-18)

Bugfixes:
  - Fix failure with identical text streams
    - https://github.com/shaka-project/shaka-player/issues/2646
  - Fix offline progress callbacks in release mode
    - https://github.com/shaka-project/shaka-player/issues/2652
  - Fix bad segment URLs in DASH SegmentTimeline
    - https://github.com/shaka-project/shaka-player/issues/2650
  - Correct license headers in compiled output
    - https://github.com/shaka-project/shaka-player/issues/2638
  - Set an explicit font size for icons in UI
    - https://github.com/shaka-project/shaka-player/issues/2633
  - Apply upstream styles for icons font in UI
    - https://github.com/shaka-project/shaka-player/issues/2633
  - Export shaka.util.FairPlayUtils and shaka.util.BufferUtils
    - https://github.com/shaka-project/shaka-player/issues/2626
    - https://github.com/shaka-project/shaka-player/pull/2628

Ad changes (BETA):
  - Correct IMA SDK URLs in service worker and docs
  - Fix UI not showing up for server side ad streams
    - https://github.com/shaka-project/shaka-player/issues/2592
  - Expose more client side IMA info to apps

Demo App:
  - Fix centering of MDL icons
  - Fix error text overflow
  - Fix missing icon for demo app menu

Docs:
  - Update Manifest Parser tutorial
    - https://github.com/shaka-project/shaka-player/issues/2634


## 2.5.13 (2020-06-11)

Bugfixes:
  - Fix background color of nested cues
    - https://github.com/shaka-project/shaka-player/issues/2623
    - https://github.com/shaka-project/shaka-player/pull/2624
  - Fix seeking from Google Home app while casting
    - https://github.com/shaka-project/shaka-player/issues/2606
  - Fix cancelation of pending network requests on load() and destroy()
    - https://github.com/shaka-project/shaka-player/issues/2619
  - Fix pixelAspectRatio extraction from DASH
    - https://github.com/shaka-project/shaka-player/pull/2614
  - Fix nested TTML captions with time offset
    - https://github.com/shaka-project/shaka-player/issues/2601
    - https://github.com/shaka-project/shaka-player/pull/2602
  - Set explicit default font size for UI icons
    - https://github.com/shaka-project/shaka-player/issues/2633
  - Correct license headers in compiled output and generated externs
    - https://github.com/shaka-project/shaka-player/issues/2638


## 3.0.0 (2020-06-09)

Ad Features (BETA):
  - Integration with Google IMA Ads SDK
    - https://github.com/shaka-project/shaka-player/issues/2222
  - Ad-related UI elements

Offline Features:
  - Allow offline downloads to be aborted
    - https://github.com/shaka-project/shaka-player/issues/2417
    - https://github.com/shaka-project/shaka-player/issues/1362
    - https://github.com/shaka-project/shaka-player/issues/1301
  - Store creation time with offline assets
    - https://github.com/shaka-project/shaka-player/pull/2406
  - Allow multiple concurrent storage operations on one Storage instance
    - https://github.com/shaka-project/shaka-player/issues/1432
    - https://github.com/shaka-project/shaka-player/issues/2432
  - Make trackSelectionCallback async
    - https://github.com/shaka-project/shaka-player/pull/2387
  - Allow storage of manifests that are missing inline init data
    - https://github.com/shaka-project/shaka-player/pull/2042

HLS Features:
  - Add support for HLS Discontinuity
    - https://github.com/shaka-project/shaka-player/issues/2397
    - https://github.com/shaka-project/shaka-player/issues/1335
  - Add support for multiple EXT-X-MAP tags
    - https://github.com/shaka-project/shaka-player/issues/1335
    - https://github.com/shaka-project/shaka-player/issues/2397
  - Improve HLS startup latency
    - https://github.com/shaka-project/shaka-player/issues/1558
  - Add variable substitution support to HLS parser
    - https://github.com/shaka-project/shaka-player/pull/2509
  - Add a presentationDelay config for HLS live
    - https://github.com/shaka-project/shaka-player/issues/2373

UI Features:
  - Expand translations: now available in 45 languages (18 built-in by default)
  - Support setting source through HTML src attribute or source tag
    - https://github.com/shaka-project/shaka-player/issues/2088
  - Large play button is configurable, and only shows on mobile UI by default
  - Add playback speed selection to UI
    - https://github.com/shaka-project/shaka-player/issues/2362
    - https://github.com/shaka-project/shaka-player/issues/1676
  - Add loop control element to UI
    - https://github.com/shaka-project/shaka-player/issues/2362
  - Improve buffering spinner visibility
    - https://github.com/shaka-project/shaka-player/issues/2110

Subtitle/Caption Features:
  - Add support for ebutts:linePadding in TTML
    - https://github.com/shaka-project/shaka-player/pull/2443
  - Add support for cell resolution units and font percentage in TTML
    - https://github.com/shaka-project/shaka-player/issues/2403
    - https://github.com/shaka-project/shaka-player/pull/2442
  - Add support for tts:border, tts:letterSpacing and tts:opacity in TTML
    - https://github.com/shaka-project/shaka-player/pull/2408

Other Features:
  - Add API to set Cast content metadata in CastReceiver
    - https://github.com/shaka-project/shaka-player/issues/2606
  - Add liveLatency to stats
    - https://github.com/shaka-project/shaka-player/pull/2508
  - Allow configuration of presumed manifest accuracy, reduces extra fetches
    - https://github.com/shaka-project/shaka-player/issues/2291
  - Take into account the playbackRate in bandwidth calculations
    - https://github.com/shaka-project/shaka-player/pull/2329
  - Add check for E-AC3 JOC in DASH
    - https://github.com/shaka-project/shaka-player/issues/2296
  - Improve startup performance by lazily creating segment indexes
  - Support pre-standard DASH MIME type
  - Allow running tests without Babel

Bugfixes:
  - Fix background color of nested cues
    - https://github.com/shaka-project/shaka-player/issues/2623
    - https://github.com/shaka-project/shaka-player/pull/2624
  - Fix seeking from Google Home app while casting
    - https://github.com/shaka-project/shaka-player/issues/2606
  - Fix cancelation of pending network requests on load() and destroy()
    - https://github.com/shaka-project/shaka-player/issues/2619

Broken compatibility:
  - Remove support for custom DASH ContentProtection schemas
    - https://github.com/shaka-project/shaka-player/issues/2356
  - Signature for config callback "drm.initDataTransform" changed

Deprecated (with backward compatibility until v4.0):
  - Uint8ArrayUtils.equal() moved to BufferUtils
  - Factory methods are no longer called with "new"
    - https://github.com/shaka-project/shaka-player/issues/1521
  - Config "manifest.dash.defaultPresentationDelay" moved to
    "manifest.defaultPresentationDelay"
  - Storage.getStoreInProgress() deprecated (not needed with concurrent storage
    operations)

Removed after deprecation in v2.5:
  - Player.selectEmbeddedTextTrack
  - Player.usingEmbeddedTextTrack
  - Player.getManifestUri (renamed to getAssetUri)
  - load() factory parameter (replaced with MIME type parameter)
  - Storage configuration fields (moved into Player config under "offline")
  - UI getPlayer() moved to getControls().getPlayer()

Demo App Features:
  - Added trick play controls option
  - Add 'audio only' to the search terms


## 2.5.12 (2020-05-29)

Bugfixes:
  - Don't preload data on iOS
    - https://github.com/shaka-project/shaka-player/issues/2483
  - Make the controls background gradient proportional
  - Work around IE 11 bug in text region positioning
    - https://github.com/shaka-project/shaka-player/issues/2584
  - Fix PlayReady key ID endianness for TiVo
    - https://github.com/shaka-project/shaka-player/pull/2582
  - Fix shaka.log in debug builds
    - https://github.com/shaka-project/shaka-player/issues/2565
  - Add support for null TS packets in HLS
    - https://github.com/shaka-project/shaka-player/issues/2546
  - Fix live seek bar on touch screens
    - https://github.com/shaka-project/shaka-player/issues/2558
  - Fix text track change after enabling text display
    - https://github.com/shaka-project/shaka-player/issues/2553
  - Fix SegmentTimeline with t attribute missing.
    - https://github.com/shaka-project/shaka-player/issues/2590
  - Fix various text positioning bugs
    - https://github.com/shaka-project/shaka-player/issues/2524
  - Allow OPUS on Tizen 5 or higher
    - https://github.com/shaka-project/shaka-player/pull/2564
  - Fix CEA caption extraction for b-frame content
    - https://github.com/shaka-project/shaka-player/issues/2395
  - Fix module wrapper to prevent conflicting exports
    - https://github.com/shaka-project/shaka-player/issues/2549

New Features:
  - Add option to customize the polling of expiration time
    - https://github.com/shaka-project/shaka-player/issues/2252
    - https://github.com/shaka-project/shaka-player/pull/2579
  - Add new option manifest.hls.useFullSegmentsForStartTime
    - https://github.com/shaka-project/shaka-player/issues/2556
    - https://github.com/shaka-project/shaka-player/pull/2575


## 2.5.11 (2020-05-05)

New Features:
  - Add role information to text and audio tracks in src= mode
    - https://github.com/shaka-project/shaka-player/pull/2543
  - Parse HLS CHARACTERISTICS attribute and populate track roles
    - https://github.com/shaka-project/shaka-player/pull/2534
  - Recognize new CMAF file extensions cmfv, cmfa, cmft in HLS
    - https://github.com/shaka-project/shaka-player/pull/2473
  - Add configuration to enable/disable fullscreen-on-rotate
    - https://github.com/shaka-project/shaka-player/issues/2494
  - Add configuration to enable keyboard playback controls
    - https://github.com/shaka-project/shaka-player/issues/2489
  - Dismiss UI overflow menus on window click
  - Add non-standard DASH PlayReady UUID
    - https://github.com/shaka-project/shaka-player/pull/2474

Bugfixes:
  - Fix FairPlay event handling
    - https://github.com/shaka-project/shaka-player/issues/2214
  - Fix load() Promise hang on iOS
    - https://github.com/shaka-project/shaka-player/issues/2483
  - Fix language normalization with native HLS
    - https://github.com/shaka-project/shaka-player/issues/2480
  - Fix display of duplicate cues
    - https://github.com/shaka-project/shaka-player/issues/2497
  - Fix TTML position parsing
    - https://github.com/shaka-project/shaka-player/issues/2477
    - https://github.com/shaka-project/shaka-player/pull/2493
  - Fix display of line-positioned subtitles
    - https://github.com/shaka-project/shaka-player/issues/2524
  - Update to mux.js 5.5.4 to fix closed caption parsing bug
    - https://github.com/videojs/mux.js/pull/330
    - https://github.com/videojs/mux.js/pull/333
  - Fix language and role preferences in src= mode
    - https://github.com/shaka-project/shaka-player/pull/2535
    - https://github.com/shaka-project/shaka-player/pull/2506
  - Fix extra text track in src= mode
    - https://github.com/shaka-project/shaka-player/issues/2516
  - Fix Safari-prefixed fullscreen APIs
    - https://github.com/shaka-project/shaka-player/issues/2528
  - Fix display of nested cues with native text display
    - https://github.com/shaka-project/shaka-player/issues/2263
  - Fix getPlayheadTimeAsDate while loading/buffering
  - Recover from timed-out Cast connection
    - https://github.com/shaka-project/shaka-player/issues/2446
  - Fix DRM exceptions on WebOS TVs
    - https://github.com/shaka-project/shaka-player/issues/2512
    - https://github.com/shaka-project/shaka-player/pull/2513
  - Fix frameRate restrictions
  - Filter out metadata text tracks in Player tracks API
    - https://github.com/shaka-project/shaka-player/pull/2519
  - Fix PlayRateController leak
  - Fix buffer check in StallDetector
    - https://github.com/shaka-project/shaka-player/issues/1809
  - Fix offline storage picking high-bandwidth codecs
    - https://github.com/shaka-project/shaka-player/issues/2390
  - Fix nested TTML cues with non-ASCII characters
    - https://github.com/shaka-project/shaka-player/issues/2478
  - Fix UI updates when enabling captions
    - https://github.com/shaka-project/shaka-player/issues/2484
  - Fix ratechange events w/ src= playback
    - https://github.com/shaka-project/shaka-player/issues/2488
  - Fix serialization of Error objects over Cast
  - Fix missing EME polyfill in Cast receiver
  - Use the module wrapper in debug builds
    - https://github.com/shaka-project/shaka-player/issues/2465

Docs:
  - Fix broken docs for UI control events
    - https://github.com/shaka-project/shaka-player/issues/2385
  - Add FAQ entry about minBufferTime
    - https://github.com/shaka-project/shaka-player/issues/2000

Demo App:
  - Push demo app footer to the bottom of the page


## 2.5.10 (2020-03-24)

New Features:
  - Added 'doubleClickForFullscreen' config to UI
    - https://github.com/shaka-project/shaka-player/issues/2459
  - Add 'loaded' event
    - https://github.com/shaka-project/shaka-player/pull/2441
  - Update prerequisites script w/ new nodejs versions
  - Export default text parser plugins
    - https://github.com/shaka-project/shaka-player/issues/2428
  - Add config to show/hide unbuffered range at seek bar start
    - https://github.com/shaka-project/shaka-player/issues/2424
  - Approximate segment size based on bandwidth when deciding to abort a request
    - https://github.com/shaka-project/shaka-player/pull/2288
  - Always log config errors
  - Make 'offline.trackSelectionCallback' async to allow the app to prompt the
    user or do other async checks
    - https://github.com/shaka-project/shaka-player/pull/2387
  - Disable video when the media element is AUDIO
    - https://github.com/shaka-project/shaka-player/issues/2246
    - https://github.com/shaka-project/shaka-player/pull/2371

Bugfixes:
  - Fix DRM-related issues on Tizen
    - https://github.com/shaka-project/shaka-player/issues/813
    - https://github.com/shaka-project/shaka-player/issues/2447
    - https://github.com/shaka-project/shaka-player/issues/2448
    - https://github.com/shaka-project/shaka-player/pull/2449
  - Fix exceptions with very large manifests on XBox One and possibly other
    consumer electronics platforms
    - https://github.com/shaka-project/shaka-player/issues/2433
  - Fix UI exception joining existing Cast session
    - https://github.com/shaka-project/shaka-player/issues/2451
  - Fix UTCTiming when autoCorrectDrift is off
    - https://github.com/shaka-project/shaka-player/issues/2411
    - https://github.com/shaka-project/shaka-player/pull/2412
  - Fix EME polyfill exceptions on Edge
    - https://github.com/shaka-project/shaka-player/issues/2413
  - Fix offline storage with some Widevine and PlayReady content
    - https://github.com/shaka-project/shaka-player/pull/2400
  - Don't fire 'adaptation' event when not switching
    - https://github.com/shaka-project/shaka-player/issues/2392
  - Fix rare exception in isTextTrackVisible()
    - https://github.com/shaka-project/shaka-player/issues/2399
  - Fix bogus warnings about argument count in configs
  - Fix duplicate DB objects when storing offline content
    - https://github.com/shaka-project/shaka-player/issues/2389
  - Fix MIME type case sensitivity in HLS parser
  - Fix changing UI Cast app ID to empty string
  - Fix case sensitivity in TTML MIME types
    - https://github.com/shaka-project/shaka-player/issues/2378
    - https://github.com/shaka-project/shaka-player/pull/2381
  - Fix exceptions for Video Futur platform
    - https://github.com/shaka-project/shaka-player/issues/2189
    - https://github.com/shaka-project/shaka-player/pull/2368
  - Fix captions display alignment
    - https://github.com/shaka-project/shaka-player/issues/2334
    - https://github.com/shaka-project/shaka-player/issues/2157
  - Fix Cast errors in compiled mode
    - https://github.com/shaka-project/shaka-player/issues/2130

Docs:
  - Improve ClearKey examples
    - https://github.com/shaka-project/shaka-player/issues/2434
    - https://github.com/shaka-project/shaka-player/pull/2439
  - Fix truncated UI tutorial
    - https://github.com/shaka-project/shaka-player/issues/2410
  - Update offline.md
    - https://github.com/shaka-project/shaka-player/pull/2404
  - Add additional links in error code reference

Demo App:
  - Several service worker improvements and fixes
  - Load pwacompat through npm
  - Replace Live search boolean with a drop-down
  - Renamed the "search" tab to "all content"
  - Add search filters to the URL
  - Work around Material Icons font bug
  - Work around MDL button bug in iOS 13
    - https://github.com/shaka-project/shaka-player/issues/2376


## 2.5.9 (2020-02-04)

Bugfixes:
  - Fix PiP polyfill for iOS
    - https://github.com/shaka-project/shaka-player/issues/2199
  - Ban iOS < 12
    - https://github.com/shaka-project/shaka-player/issues/1920
  - Work around service worker registration hang on iOS
  - Fix display of selected language in UI
    - https://github.com/shaka-project/shaka-player/issues/2353
  - Fix race condition on HLS parser shutdown
    - https://github.com/shaka-project/shaka-player/issues/2138
  - Fix StringUtils on Xbox One
    - https://github.com/shaka-project/shaka-player/issues/2186
  - Fix selecting audio track by role when video tracks contain the same role
    - https://github.com/shaka-project/shaka-player/issues/2346
  - Fix skipping of raw format streams in HLS
  - Fix iPad 13+ detection
    - https://github.com/shaka-project/shaka-player/issues/2360
  - Fix exception thrown for Chrome & Firefox on iOS

Docs:
  - Fix typo in fairplay tutorial
    - https://github.com/shaka-project/shaka-player/issues/2344


## 2.5.8 (2020-01-16)

Bugfixes:
  - Recognize and reject raw AAC in HLS
    - https://github.com/shaka-project/shaka-player/issues/1083
    - https://github.com/shaka-project/shaka-player/issues/2337
  - Fix fullscreen on Android
    - https://github.com/shaka-project/shaka-player/issues/2324
    - https://github.com/shaka-project/shaka-player/pull/2325
  - Fix start time support in src= mode
    - https://github.com/shaka-project/shaka-player/issues/2267
    - https://github.com/shaka-project/shaka-player/pull/2271
  - Add missing events to CastProxy Player
    - https://github.com/shaka-project/shaka-player/issues/2318
  - Fix cast receiver UI update
    - https://github.com/shaka-project/shaka-player/issues/2314

New Features:
  - Add corruptedFrames to stats
    - https://github.com/shaka-project/shaka-player/pull/2328
  - Add framerate restriction to the config
    - https://github.com/shaka-project/shaka-player/issues/2068
    - https://github.com/shaka-project/shaka-player/pull/2332
  - Add option to ignore empty AdaptationSets in DASH
    - https://github.com/shaka-project/shaka-player/issues/2023
    - https://github.com/shaka-project/shaka-player/pull/2330
  - Add licenseTime to stats
    - https://github.com/shaka-project/shaka-player/pull/2297
  - Add pixelAspectRatio property from DASH
    - https://github.com/shaka-project/shaka-player/pull/2294
  - Add AirPlay support with native HLS and FairPlay
    - https://github.com/shaka-project/shaka-player/issues/2177
    - https://github.com/shaka-project/shaka-player/pull/2257
  - Add option to show text/audio roles in UI
    - https://github.com/shaka-project/shaka-player/issues/2307
  - Add "fadeDelay" option to delay fading UI controls

Demo App:
  - Update asset list and metadata


## 2.5.7 (2019-12-18)

New Features:
  - Add audioSamplingRate property
    - https://github.com/shaka-project/shaka-player/pull/2290
  - Ignore DASH image tracks
    - https://github.com/shaka-project/shaka-player/pull/2276
  - Add AV1 check and more file extensions for src mode
    - https://github.com/shaka-project/shaka-player/pull/2280
  - Allow removing text from manifests
    - https://github.com/shaka-project/shaka-player/pull/2278
  - Allow ignoreSuggestedPresentationDelay in DASH
    - https://github.com/shaka-project/shaka-player/pull/2260
  - Allow removing video from manifests
    - https://github.com/shaka-project/shaka-player/pull/2259
  - Add a polyfill for EME encryption scheme queries
  - Add support for ttml regions
    - https://github.com/shaka-project/shaka-player/issues/2191
  - Add a method to select variants by label
    - https://github.com/shaka-project/shaka-player/issues/924

Bugfixes:
  - Fix shaka.polyfill missing in externs
  - Fix width of overflow menu with wide content
    - https://github.com/shaka-project/shaka-player/issues/2249
  - Disable indexedDB support if an error is thrown
    - https://github.com/shaka-project/shaka-player/pull/2236
  - Fix setting robustness settings in DRM config
    - https://github.com/shaka-project/shaka-player/issues/2211


## 2.5.6 (2019-11-06)

Bugfixes:
  - Fix storing content with delayLicenseRequestUntilPlayed
    - https://github.com/shaka-project/shaka-player/issues/2218
  - Fix check for captions in appendBuffer
    - https://github.com/shaka-project/shaka-player/issues/2187
  - Allow 'rebufferingGoal' to change after startup
    - https://github.com/shaka-project/shaka-player/issues/2217
  - Fix default encoding when reading files
    - https://github.com/shaka-project/shaka-player/issues/2206
  - Throw for invalid TTML
    - https://github.com/shaka-project/shaka-player/issues/2157
  - Fix FairPlay default initDataTransform
    - https://github.com/shaka-project/shaka-player/issues/2136
  - Fix live seekbar on Android
    - https://github.com/shaka-project/shaka-player/issues/2169
  - Fix undefined value in HLS request filters
    - https://github.com/shaka-project/shaka-player/issues/2156
  - Fix Period transitions with embedded captions
    - https://github.com/shaka-project/shaka-player/issues/2076
  - Throw error for clear-key content with src=
    - https://github.com/shaka-project/shaka-player/issues/2139
  - Fix support for empty TTML data
    - https://github.com/shaka-project/shaka-player/pull/1960
  - Fix multi-Period handling of key statuses
    - https://github.com/shaka-project/shaka-player/issues/2135
  - Fix stall at end with src=
    - https://github.com/shaka-project/shaka-player/issues/2117
  - Fix ttml background image support
    - https://github.com/shaka-project/shaka-player/pull/2034

New Features:
  - Add config to use MSE playback on Safari
    - https://github.com/shaka-project/shaka-player/issues/2116
  - Support storing protected content without init data in manifest
    - https://github.com/shaka-project/shaka-player/issues/1531
    - https://github.com/shaka-project/shaka-player/pull/2164
  - Allow disable audio/video in manifest parsers
    - https://github.com/shaka-project/shaka-player/pull/2196
  - Enhance ttml rendering
    - https://github.com/shaka-project/shaka-player/pull/1962
  - Include event ID in DASH Event checks
    - https://github.com/shaka-project/shaka-player/issues/2077
    - https://github.com/shaka-project/shaka-player/pull/2175
  - Add support for Label element in DASH
    - https://github.com/shaka-project/shaka-player/issues/2178
    - https://github.com/shaka-project/shaka-player/pull/2197
  - Treat URL schemes as case-insensitive
    - https://github.com/shaka-project/shaka-player/issues/2173
  - Forward change event from src= playback
    - https://github.com/shaka-project/shaka-player/pull/2134
  - Export getMaxSegmentDuration() on presentationTimeline
    - https://github.com/shaka-project/shaka-player/issues/2124
  - Ignore MIME parameters in Content-Type check
    - https://github.com/shaka-project/shaka-player/issues/1946
    - https://github.com/shaka-project/shaka-player/pull/2215
  - Make seek & volume bar colors configurable
    - https://github.com/shaka-project/shaka-player/issues/2203

Demo App:
  - Improve mobile Safari PWA support in demo
    - https://github.com/shaka-project/shaka-player/issues/2143
  - Added tooltips to the search filters on the demo
  - Added "report bug" button to demo



## 2.5.5 (2019-08-23)

New Features:
  - Conditionally remove FairPlay formatting
    - https://github.com/shaka-project/shaka-player/issues/1951
  - Add sessionId field to network request
  - Make it easier to add custom overflow menu items
    - https://github.com/shaka-project/shaka-player/issues/2091
  - Add clearBufferOnQualityChange field to UI config
    - https://github.com/shaka-project/shaka-player/issues/1733
  - Allow filtering out failed HLS text tracks
    - https://github.com/shaka-project/shaka-player/issues/2065
  - Parse Accessibility tag into text "kind"
    - https://github.com/shaka-project/shaka-player/issues/2060
  - Re-add MediaSession API
    - https://github.com/shaka-project/shaka-player/issues/1934
  - Skip WebM streams in HLS instead of throwing
    - https://github.com/shaka-project/shaka-player/issues/2108
  - Convert `<mspr:pro>` elements to `pssh` init data
    - https://github.com/shaka-project/shaka-player/pull/2106
    - https://github.com/shaka-project/shaka-player/issues/2058

Bugfixes:
  - Fix duplicate resolution entries in UI menu
    - https://github.com/shaka-project/shaka-player/issues/2085
  - Fix missing tracks, race on time during startup
    - https://github.com/shaka-project/shaka-player/issues/2045
  - Fix spinner position on IE11
    - https://github.com/shaka-project/shaka-player/issues/2084
  - Fix seek bar coloring when nothing buffered
  - Fix scroll behavior on page load
    - https://github.com/shaka-project/shaka-player/issues/2063
  - Don't create a UI if the app already has one
    - https://github.com/shaka-project/shaka-player/issues/2073
  - Fix text display styling when fullscreen
    - https://github.com/shaka-project/shaka-player/issues/2051
  - Don't enter fullscreen on double click on bottom bar
    - https://github.com/shaka-project/shaka-player/issues/2053
  - Avoid errors when video ends
    - https://github.com/shaka-project/shaka-player/issues/2050
  - Fix fullscreen behavior on double click and rotate
    - https://github.com/shaka-project/shaka-player/issues/2043
  - Fix bug when clicking PIP button while casting
    - https://github.com/shaka-project/shaka-player/issues/2044
  - Fix CEA captions with multi-Period content
    - https://github.com/shaka-project/shaka-player/issues/2075
    - https://github.com/shaka-project/shaka-player/issues/2094

Demo App:
  - Added more HLS demo assets
    - https://github.com/shaka-project/shaka-player/issues/2035
  - Exit PIP on unload in the demo
    - https://github.com/shaka-project/shaka-player/issues/2055
  - Re-added hidden 'noinput' param to demo


## 2.5.4 (2019-07-19)

Bugfixes:
  - Default to transparent SMPTE-TT subtitle background
    - https://github.com/shaka-project/shaka-player/pull/2033
  - Fix seek bar on iOS
    - https://github.com/shaka-project/shaka-player/issues/1918
    - https://github.com/shaka-project/shaka-player/pull/2036
  - Allow whitespace in TTML subtitles
    - https://github.com/shaka-project/shaka-player/issues/2028
    - https://github.com/shaka-project/shaka-player/pull/2030
  - Fix play button positioning on IE 11
    - https://github.com/shaka-project/shaka-player/issues/2026
  - Match UI style with Chrome's native controls
  - Stop constant spurious time updates in UI
  - Fix volume slider jumping around while casting
    - https://github.com/shaka-project/shaka-player/issues/1913
  - Fix missing seek bar in short VOD clips
    - https://github.com/shaka-project/shaka-player/issues/2018
  - Fix demo app in Firefox private mode
    - https://github.com/shaka-project/shaka-player/issues/1926
  - Ignore case in MIME type checks
    - https://github.com/shaka-project/shaka-player/issues/1991
  - Fix problems with casting
    - https://github.com/shaka-project/shaka-player/issues/1948

New Features:
  - Add command-line arg to change the test timeout.


## 2.5.3 (2019-07-03)

Bugfixes:
  - Fix DASH bug when ignoring minBufferTime
    - https://github.com/shaka-project/shaka-player/issues/2015
  - Avoid changing variant when switching text lang
    - https://github.com/shaka-project/shaka-player/issues/2010
  - Work around platform bug when seeking to end
    - https://github.com/shaka-project/shaka-player/issues/1967
  - Allow apps to extend shaka.ui.Element
    - https://github.com/shaka-project/shaka-player/issues/2011
  - Fix bug when adding text streams while not streaming text
    - https://github.com/shaka-project/shaka-player/issues/1938
  - Fix edge case when switching text in multi-Period content
    - https://github.com/shaka-project/shaka-player/issues/1774
  - Fix playback rate bug on IE11
  - Make fast forwarding work when video is paused
    - https://github.com/shaka-project/shaka-player/issues/1801
  - Fix stack overflow in StringUtils on some platforms
    - https://github.com/shaka-project/shaka-player/issues/1985
    - https://github.com/shaka-project/shaka-player/issues/1994
  - Fix reading customData from standard Cast LOAD message
    - https://github.com/shaka-project/shaka-player/issues/1989

Docs:
  - Fix constant name in UI tutorials
    - https://github.com/shaka-project/shaka-player/issues/2005
  - Update build output name in docs
    - https://github.com/shaka-project/shaka-player/issues/1929

New Features:
  - Use trick play for fast forward when browser doesn't support high
    playbackRate
    - https://github.com/shaka-project/shaka-player/issues/1957


## 2.5.2 (2019-06-10)

Bugfixes:
  - Avoid event listener leaks in the UI
    - https://github.com/shaka-project/shaka-player/issues/1924
  - Fix style errors in TextDisplayer
    - https://github.com/shaka-project/shaka-player/issues/1852
    - https://github.com/shaka-project/shaka-player/issues/1955
  - Show spinner when buffering even if other controls are hidden
    - https://github.com/shaka-project/shaka-player/issues/1921
  - Don't recreate controls object on configure() calls
    - https://github.com/shaka-project/shaka-player/issues/1948
  - Fix UI compilation on Windows
    - https://github.com/shaka-project/shaka-player/issues/1965

New Features:
  - Add originalUri as a property on shaka.extern.Response
    - https://github.com/shaka-project/shaka-player/issues/1971
    - https://github.com/shaka-project/shaka-player/pull/1972

Demo App:
  - Fix close button styling in compiled mode
  - Fix config settings applied before playback begins
    - https://github.com/shaka-project/shaka-player/issues/1976
  - Change the style of the download/delete button
  - Fix demo error display for large errors
  - Improve cvox error check
  - Switch to using tippy.js for tooltips

Docs:
  - Add a public roadmap document
    - https://github.com/shaka-project/shaka-player/blob/main/roadmap.md


## 2.5.1 (2019-05-20)

New Features:
  - Inline external CSS for quicker load
    - You no longer need to include Material Design Icons font in your app
  - Use clean-css plugin in less.js to minify CSS

Bugfixes:
  - Deprecate ui.getPlayer for controls.getPlayer
    - https://github.com/shaka-project/shaka-player/issues/1941
  - Fix switching text displayer mid-playback
  - Improve french translations
    - https://github.com/shaka-project/shaka-player/pull/1944
  - Improve logic for aborting network requests
  - Fix initial bandwidth estimate on Chrome
  - Upgrade mux.js and use minified version
  - Fix exception on network retry
    - https://github.com/shaka-project/shaka-player/issues/1930
  - Fix API-based UI setup with default config
  - Allow two-argument configure() calls for UI and offline
  - Add missing export on ui.Overlay.getConfiguration
  - Various improvements in test reliability
  - Various fixes for compatibility with newer compiler versions

Demo App:
  - Fix asset card highlight on reload
  - Fix reconnection to cast sessions on reload
    - https://github.com/shaka-project/shaka-player/issues/1948
  - Fix handling of error events
  - Fix centering of asset card titles
  - Move download button to the corner of asset cards
  - Add WebP variants for asset icons to reduce size by 88%
  - Optimize app load time by pre-connecting to external origins
  - Defer creating tab contents until shown
  - Make name field in custom assets more permissive
  - Add link to support page in footer
  - Allow demo to load custom assets from hash
  - Do not disable controls on startup
  - Added missing config values
  - Catch certificate errors in demo
    - https://github.com/shaka-project/shaka-player/issues/1914
  - Let demo load even if storage fails to load
    - https://github.com/shaka-project/shaka-player/issues/1925
  - Re-load current asset if page reloads
  - Fix unsupported button tooltips


## 2.5.0 (2019-05-08)

**The UI is now out of beta!  Use shaka-player.ui.js and see the UI tutorials.**

Core Bugfixes:
  - Fix missing variants in HLS
    - https://github.com/shaka-project/shaka-player/issues/1908
  - Ignore manifest-provided license servers if application-provided servers
    are configured
    - https://github.com/shaka-project/shaka-player/issues/1905
  - Fix range header regression that broke IIS compatibility
  - Fix initial display of captions based on language preferences
    - https://github.com/shaka-project/shaka-player/issues/1879
  - Ignore duplicate codecs in HLS
    - https://github.com/shaka-project/shaka-player/issues/1817
  - Reject AES-128 HLS content with meaningful error
    - https://github.com/shaka-project/shaka-player/issues/1838
  - Fix React Native createObjectURL polyfill incompatibility
    - https://github.com/shaka-project/shaka-player/issues/1842
    - https://github.com/shaka-project/shaka-player/pull/1845
  - Dolby Vision fixes for Chromecast
    - https://github.com/shaka-project/shaka-player/pull/1844
  - Fix redundant initialization of MediaSource
    - https://github.com/shaka-project/shaka-player/issues/1570
  - Fix stalls on WebOS
    - https://github.com/shaka-project/shaka-player/issues/1704
    - https://github.com/shaka-project/shaka-player/pull/1820
  - Fix missing require for SimpleTextDisplayer
    - https://github.com/shaka-project/shaka-player/issues/1819
  - Fix broken version definition in compiled build
    - https://github.com/shaka-project/shaka-player/issues/1816
  - Fix video reloading on audio language change
    - https://github.com/shaka-project/shaka-player/issues/1714

UI Bugfixes:
  - Fix missing resolution menu in UI after playing audio-only content
  - Fix pointer cursor on UI spacer
  - Do not show PIP button if not allowed
  - Fix hiding captions in UI text displayer
    - https://github.com/shaka-project/shaka-player/issues/1893
  - Fix UI text displayer positioning on IE
  - Make live stream timecode accessible to screen readers in the UI
    - https://github.com/shaka-project/shaka-player/issues/1861
  - Fix ARIA pressed state for button in text selection menu
  - Show picture-in-picture btn only when the content has video
    - https://github.com/shaka-project/shaka-player/issues/1849
  - Fix multiline captions in UI text displayer
  - Fix display of cast button in UI
    - https://github.com/shaka-project/shaka-player/issues/1803
  - Fix conflict between PiP and fullscreen
  - Fix cast receiver styling

New Core Features:
  - Abort requests when network downgrading
    - https://github.com/shaka-project/shaka-player/issues/1051
  - Add FairPlay support
    - https://github.com/shaka-project/shaka-player/issues/382
  - Add native HLS support on iOS and Safari
    - https://github.com/shaka-project/shaka-player/issues/997
  - Support src= for single-file playback
    - https://github.com/shaka-project/shaka-player/issues/816
    - https://github.com/shaka-project/shaka-player/pull/1888
    - https://github.com/shaka-project/shaka-player/pull/1898
  - Add 'manifestparsed' event for early access to manifest contents
  - Add 'abrstatuschanged' event to help manage UI state
  - Make manifest redirections sticky for updates
    - https://github.com/shaka-project/shaka-player/issues/1367
    - https://github.com/shaka-project/shaka-player/pull/1880
  - Track time in "pause" state in stats
    - https://github.com/shaka-project/shaka-player/pull/1855
  - Make Stall Detector Configurable
    - https://github.com/shaka-project/shaka-player/issues/1839

New UI Features:
  - Add support for UI reconfiguration and layout changes
    - https://github.com/shaka-project/shaka-player/issues/1674
  - Add support for custom UI buttons
    - https://github.com/shaka-project/shaka-player/issues/1673
  - Add partial support for SMPTE-TT subtitles in UI text displayer
    - https://github.com/shaka-project/shaka-player/issues/840
    - https://github.com/shaka-project/shaka-player/pull/1859
  - Add PiP support in Safari
    - https://github.com/shaka-project/shaka-player/pull/1902


Demo App:
  - Complete redesign of the demo app!
  - Load non-built-in localizations from the server at runtime
    - https://github.com/shaka-project/shaka-player/issues/1688
  - Ignore spurious errors from ChromeVox
    - https://github.com/shaka-project/shaka-player/issues/1862
  - Don't handle non-app resources in service worker
    - https://github.com/shaka-project/shaka-player/issues/1256
    - https://github.com/shaka-project/shaka-player/issues/1392

Docs:
  - Document UI events
    - https://github.com/shaka-project/shaka-player/issues/1870
  - Update Manifest Parser documentation
  - Clarify track selection callback in offline tutorial
  - Fix jsdoc and markdown formatting of links
  - Add link for Shaka Player Embedded
    - https://github.com/shaka-project/shaka-player/issues/1846


## 2.5.0-beta3 (2019-02-20)

New Features:
  - Introduction of Shaka Player UI library! (beta)
    - Load dist/shaka-player.ui.js
    - See tutorial in docs/tutorials/ui.md
  - Add option to disable drift-tolerance feature for certain live streams
    - https://github.com/shaka-project/shaka-player/issues/1729
  - Upgrade mux.js to the latest (5.1.0)
  - Support HLS playlists without URI in EXT-X-MEDIA
    - https://github.com/shaka-project/shaka-player/pull/1732
  - Add safeSeekOffset to StreamingConfiguration
    - https://github.com/shaka-project/shaka-player/issues/1723
    - https://github.com/shaka-project/shaka-player/pull/1726
  - Add PlayReady license URL parsing (ms:laurl)
    - https://github.com/shaka-project/shaka-player/issues/484
    - https://github.com/shaka-project/shaka-player/pull/1644
  - Add support for HLS tags with both value and attributes
    - https://github.com/shaka-project/shaka-player/issues/1808
    - https://github.com/shaka-project/shaka-player/pull/1810

Bugfixes:
  - Fixed various typos in comments and docs
    - https://github.com/shaka-project/shaka-player/pull/1797
    - https://github.com/shaka-project/shaka-player/pull/1805
  - Fix CEA timestamps with presentationTimeOffset
  - Fix config-based clock sync for IPR content
  - Fix cast serialization of Uint8Array types
    - https://github.com/shaka-project/shaka-player/issues/1716
  - Fix event dispatch when text tracks change
  - Don't include video roles in audio-language-role pairs
    - https://github.com/shaka-project/shaka-player/issues/1731
  - Fix MediaSource failures with certain language settings
    - https://github.com/shaka-project/shaka-player/issues/1696
  - Fix build paths on Windows
    - https://github.com/shaka-project/shaka-player/issues/1700

Docs:
  - Update docs to mention ignoreMinBufferTime
    - https://github.com/shaka-project/shaka-player/issues/1547
    - https://github.com/shaka-project/shaka-player/issues/1666
  - Document restrictions on large timescales
    - https://github.com/shaka-project/shaka-player/issues/1667
  - Various small docs improvements


## 2.4.7 (2019-02-19)

Bugfixes:
  - Reject opus content on Tizen
    - https://github.com/shaka-project/shaka-player/issues/1751
  - Fix seekable range on HLS content with non-zero start time
    - https://github.com/shaka-project/shaka-player/issues/1602


## 2.4.6 (2019-01-22)

Bugfixes:
  - Fix HLS without URI attribute
    - https://github.com/shaka-project/shaka-player/issues/1086
    - https://github.com/shaka-project/shaka-player/issues/1730
    - https://github.com/shaka-project/shaka-player/pull/1732
  - Handle prereleases of npm and node in build scripts
    - https://github.com/shaka-project/shaka-player/issues/1758
  - Fix windows path handling in build scripts
    - https://github.com/shaka-project/shaka-player/issues/1759
  - Fix cast receiver errors in getStats
    - https://github.com/shaka-project/shaka-player/issues/1760
  - Fix spurious teardown exception on smart TVs
    - https://github.com/shaka-project/shaka-player/issues/1728
  - Loosen gap thresholds on Chromecast
    - https://github.com/shaka-project/shaka-player/issues/1720
  - Fix support for Safari 12
  - Fix support for relative Location URLs in DASH
    - https://github.com/shaka-project/shaka-player/issues/1668
  - Fix compliance issues in IE11 EME polyfill
    - https://github.com/shaka-project/shaka-player/issues/1689
  - Fix PlayReady playback on Tizen
    - https://github.com/shaka-project/shaka-player/issues/1712
  - Fix chopped playback in MS Edge
    - https://github.com/shaka-project/shaka-player/issues/1597
  - Fix assertions when EME sessions expire
    - https://github.com/shaka-project/shaka-player/issues/1599
  - Fix relative URIs in HLS
    - https://github.com/shaka-project/shaka-player/issues/1664
  - Fix compilation error
    - https://github.com/shaka-project/shaka-player/issues/1658
    - https://github.com/shaka-project/shaka-player/pull/1660

New Features:
  - Add extended error code for failed license request
    - https://github.com/shaka-project/shaka-player/issues/1689

Demo App:
  - Disable offline storage on some assets
    - https://github.com/shaka-project/shaka-player/issues/1768
  - Update DASH-IF livesim URLs
    - https://github.com/shaka-project/shaka-player/pull/1736


## 2.5.0-beta2 (2018-11-09)

Contains everything in v2.4.5, plus...

Bugfixes:
  - Fix Chromecast receiver id in the demo, broken since v2.5.0-beta
    - https://github.com/shaka-project/shaka-player/issues/1656
  - Fix multi-period playback issues introduced in v2.5.0-beta
    - https://github.com/shaka-project/shaka-player/issues/1601
  - Fix seekable range with non-zero start
    - https://github.com/shaka-project/shaka-player/issues/1602
  - Misc Storage and demo fixes
  - Fix support for restriction changes after playback
    - https://github.com/shaka-project/shaka-player/issues/1533
  - Fix TextEngine buffered range calculations
    - https://github.com/shaka-project/shaka-player/issues/1562

New Features:
  - Add support for CEA captions in DASH
    - https://github.com/shaka-project/shaka-player/issues/1404
  - Set server certificate before Store and Delete
    - https://github.com/shaka-project/shaka-player/issues/1623
    - https://github.com/shaka-project/shaka-player/pull/1639
  - Allow deferring deleting offline sessions.
    - https://github.com/shaka-project/shaka-player/issues/1326
  - Added progress events for Fetch plugin.
    - https://github.com/shaka-project/shaka-player/issues/1504
  - Add config field to ignore manifest minBufferTime #1547
    - https://github.com/shaka-project/shaka-player/issues/1547
    - https://github.com/shaka-project/shaka-player/pull/1581
  - Add support for 'individualization-request' messages in EME
    - https://github.com/shaka-project/shaka-player/issues/1565

Docs:
  - Update Language Normalization Documentation


## 2.4.5 (2018-11-09)

Bugfixes:
  - Fix erasure of the database with storage.deleteAll()
  - Fix MediaSource tear down race
  - Fix exception when destroying MediaSourceEngine twice
  - Fix gap jumping test failures on IE/Edge/Tizen
  - Fix stalls on Tizen TV
  - Fix display of external subtitles
    - https://github.com/shaka-project/shaka-player/issues/1596
  - Fix test failures on Safari
  - Fix filtering of HLS audio-only content
  - Preserve bandwidth estimate between loads
    - https://github.com/shaka-project/shaka-player/issues/1366
  - Retry streaming when we get back online
    - https://github.com/shaka-project/shaka-player/issues/1427
  - Fix Storage test contamination
  - Fix advanced DRM settings pollution across key systems
    - https://github.com/shaka-project/shaka-player/issues/1524
  - Fix TextEngine buffered range calculations
    - https://github.com/shaka-project/shaka-player/issues/1562

New Features:
  - Optimize processXlinks
    - https://github.com/shaka-project/shaka-player/issues/1640
  - Add support for Python3 in build scripts
  - Allow new Periods to add EME init data
    - https://github.com/shaka-project/shaka-player/issues/1360
  - Add namespace-aware parsing to TTML parser
    - https://github.com/shaka-project/shaka-player/issues/1585
  - An external Promise polyfill is no longer required!

Demo App:
  - Show logs prominently in noinput mode
    - https://github.com/shaka-project/shaka-player/issues/1610
  - Disable uncompiled mode on browsers without async
  - Restore using Enter key to load asset

Docs:
  - Fix tracks sorting in Offline tutorial sample code
    - https://github.com/shaka-project/shaka-player/issues/1608
    - https://github.com/shaka-project/shaka-player/pull/1609
  - Add a note about blank receiver IDs
  - Rename 'video' to 'mediaElem' to make it clear that audio elements work, too
    - https://github.com/shaka-project/shaka-player/issues/1555

Un-Features:
  - Un-ship VTTRegion support, which is currently broken in Chrome and does more
    harm than good
    - https://github.com/shaka-project/shaka-player/issues/1584


## 2.5.0-beta (2018-08-24)

New Features:
  - Drift is now tolerated in DASH live streams
    - https://github.com/shaka-project/shaka-player/issues/999
  - Storage can be initialized without Player
    - https://github.com/shaka-project/shaka-player/issues/1297
  - DASH Representation IDs are now exposed in a new field in Track
  - A safe margin parameter was added for clearing the buffer
    - https://github.com/shaka-project/shaka-player/pull/1154
  - Added 'retry' event to networking engine
    - https://github.com/shaka-project/shaka-player/issues/1529
  - Emsg not referenced in MPD will now be ignored
    - https://github.com/shaka-project/shaka-player/issues/1548
  - Extra data given for RESTRICTIONS_CANNOT_BE_MET
    - https://github.com/shaka-project/shaka-player/issues/1368
  - A mime type option was added to Player.load
  - Added Widevine SAMPLE-AES support in HLS
    - https://github.com/shaka-project/shaka-player/issues/1515
  - The |manifestUri| method on Player was changed to |assetUri|
  - Added new request type TIMING for clock sync requests
    - https://github.com/shaka-project/shaka-player/issues/1488
    - https://github.com/shaka-project/shaka-player/pull/1489

Deprecated:
  - Passing a ManifestParser factory to Player.load is deprecated and support
    will be removed in v3.0. Instead, please register any custom parsers with a
    MIME type, and pass a MIME type instead.  MIME types can also be used to
    force the selection of any built-in manifest parsers.
  - The |manifestUri| method on Player was changed to |assetUri|. The old method
    is deprecated and will be removed in v3.0.


## 2.4.4 (2018-08-23)

Bugfixes:
  - Fix spurious restrictions errors
    - https://github.com/shaka-project/shaka-player/issues/1541
  - Don't error when skipping mp4 boxes with bad size
    - https://github.com/shaka-project/shaka-player/issues/1535
  - Refactor HttpFetchPlugin to clarify error outcomes
    - https://github.com/shaka-project/shaka-player/issues/1519
    - https://github.com/shaka-project/shaka-player/pull/1532
  - Avoid assertions about $Time$ when it is not used
  - Stop proxying drmInfo() to reduce cast message sizes
  - Fix compiler renaming in ParsedBox
    - https://github.com/shaka-project/shaka-player/issues/1522

Docs:
  - Fixed docs for availabilityWindowOverride
    - https://github.com/shaka-project/shaka-player/issues/1530


## 2.4.3 (2018-08-06)

New Features:
  - Add availabilityWindowOverride configuration
    - https://github.com/shaka-project/shaka-player/issues/1177
    - https://github.com/shaka-project/shaka-player/issues/1307

Bugfixes:
  - Fix repeated download of the same segment in live DASH
    - https://github.com/shaka-project/shaka-player/issues/1464
    - https://github.com/shaka-project/shaka-player/issues/1486
  - Don't clear buffer with a small gap between playhead and buffer start
    - https://github.com/shaka-project/shaka-player/issues/1459
  - Allow CDATA in text nodes.
    - https://github.com/shaka-project/shaka-player/issues/1508
  - Skip text AdaptationSets with no segment info
    - https://github.com/shaka-project/shaka-player/issues/1484
  - Add error code for side-loaded text with live streams

Demo app:
  - Clarify persistent license error messages

Docs:
  - Update docs for RESTRICTIONS_CANNOT_BE_MET


## 2.3.10 and 2.4.2 (2018-06-29)

Bugfixes:
  - Fix ignored configuration when input is partially invalid (v2.4.2 only)
    - https://github.com/shaka-project/shaka-player/issues/1470
  - Silence DRM engine errors for unencrypted assets
    - https://github.com/shaka-project/shaka-player/issues/1479
  - Fix infinite seeking with HLS on V1 Chromecasts
    - https://github.com/shaka-project/shaka-player/issues/1411
  - Fix module wrapper to work with CommonJS, AMD, ES modules, as well as
    Closure and Electron
    - https://github.com/shaka-project/shaka-player/issues/1463
  - Fix TextEngine buffered range calculations

Demo App:
  - Fix custom encrypted assets in the demo app

Docs:
  - Fix generated documentation problems (v2.4.2 only)
  - Move CEA-608/708 to list of supported HLS features (v2.4.2 only)
    - https://github.com/shaka-project/shaka-player/pull/1465


## 2.3.9 and 2.4.1 (2018-06-13)

Bugfixes:
  - Default to a maximum of 360p for ABR when saveData == true
    - https://github.com/shaka-project/shaka-player/issues/855
  - Make AbrManager restrictions "soft" so they do not fail playback
  - Patch Closure Compiler to fix polyfill+wrapper
    - https://github.com/shaka-project/shaka-player/issues/1455
  - Fix assertion spam when merging a period into itself
    - https://github.com/shaka-project/shaka-player/issues/1448
  - Upgrade WebDriver module to new W3C protocol, fixes WD tests on Firefox & IE
  - Work around potential hang in transmuxer with multiplexed TS content.
    - https://github.com/shaka-project/shaka-player/issues/1449

Demo app:
  - Support clearkey license-servers in the demo UI

Misc:
  - Fix nodejs import (still not a supported environment, but does not throw)
    - https://github.com/shaka-project/shaka-player/issues/1445
    - https://github.com/shaka-project/shaka-player/pull/1446


## 2.4.0 (2018-05-24)

New features:
  - Support for TTML and VTT regions
    - https://github.com/shaka-project/shaka-player/issues/1188
  - Support for CEA captions in TS content
    - https://github.com/shaka-project/shaka-player/issues/276
  - A video element is no longer required when `Player` is constructed
    - https://github.com/shaka-project/shaka-player/issues/1087
  - New `attach()` and `detach()` methods have been added to `Player` to manage
    attachment to video elements
    - https://github.com/shaka-project/shaka-player/issues/1087
  - Allow apps to specify a preferred audio channel count
    - https://github.com/shaka-project/shaka-player/issues/1013
  - Live stream playback can begin at a negative offset from the live edge
    - https://github.com/shaka-project/shaka-player/issues/1178
  - Add new configure() syntax for easily setting single fields
    - https://github.com/shaka-project/shaka-player/issues/763
  - player.configure() returns false if player configuration is invalid
  - Fetch is now preferred over XHR when available
    - https://github.com/shaka-project/shaka-player/issues/829
  - Request type now appears in shaka.util.Error data for HTTP errors
    - https://github.com/shaka-project/shaka-player/issues/1253

Broken compatibility:
  - A third-party Promise polyfill is now required for IE 11 support
    - https://github.com/lahmatiy/es6-promise-polyfill
    - https://github.com/shaka-project/shaka-player/issues/1260
  - Text parser plugins now take a nullable segmentStart in TextContext.  All
    application-specific text-parsing plugins MUST be updated.
  - Text-parsing plugins that produce region information must do so with the new
    CueRegion class.  Any application-specific text-parsing plugins that produce
    region information MUST be updated.
  - TextDisplayer plugins that handle region information must do so with the new
    CueRegion interface.  Any application-specific TextDisplayer plugins that
    handle region information MUST be updated.
  - The API for PresentationTimeline has changed.  Manifest parser plugins that
    use certain PresentationTimeline methods MUST be updated:
    - `setAvailabilityStart()` was renamed to `setUserSeekStart()`.
    - `notifySegments()` now takes a reference array and a boolean called
      `isFirstPeriod`, instead of a period start time and a reference array.

Deprecated:
  - NetworkingEngine.request() now returns an instance of IAbortableOperation
    instead of Promise.  Applications which make application-level requests
    SHOULD update to use the new interface.
    - The old interface will be removed in v2.5.
  - Network scheme plugins now return an instance of IAbortableOperation instead
    of Promise.  Application-specific network scheme plugins SHOULD update to
    the new interface.
    - The old interface will be removed in v2.5.

Demo app:
  - Improve support for custom assets and license servers in demo app URI

Misc:
  - We have started transitioning the code to ES6 and the new JS style guide
    - https://google.github.io/styleguide/jsguide.html


## 2.3.8 (2018-05-23)

Bugfixes:
  - Fix non-default namespace names in DASH
    - https://github.com/shaka-project/shaka-player/issues/1438
  - Fix use after destroy() in CastProxy
    - https://github.com/shaka-project/shaka-player/issues/1423
  - Fix text track visibility state
    - https://github.com/shaka-project/shaka-player/issues/1412
  - Remove licenses when wiping offline storage
    - https://github.com/shaka-project/shaka-player/issues/1277
  - Restore backward compatibility for v2.2.x offline storage
    - https://github.com/shaka-project/shaka-player/issues/1248

Demo app:
  - Update DASH-IF Big Buck Bunny asset

Docs:
  - Fix typos and formatting
  - Build docs as part of build/all.py
    - https://github.com/shaka-project/shaka-player/issues/1421


## 2.3.7 (2018-04-24)

Bugfixes:
  - Fixed manifest update frequency calculations
    - https://github.com/shaka-project/shaka-player/issues/1399
  - Fixed repeated seeking during HLS live streaming on Chromecast
    - https://github.com/shaka-project/shaka-player/issues/1411

Demo app:
  - Fixed updating of the app URL on Android when pasting into the custom asset
    field
    - https://github.com/shaka-project/shaka-player/issues/1079
  - Added Axinom live test assets
    - https://github.com/shaka-project/shaka-player/pull/1409


## 2.3.6 (2018-04-11)

Bugfixes:
  - Handle HLS segments tags that occur before playlist tags
    - https://github.com/shaka-project/shaka-player/issues/1382
  - Avoid telling AbrManager about key-system-restricted streams, to simplify
    building AbrManager plugins.
  - Fixed exported enum definition for network plugin priorities
  - Fixed ES5 strict mode compatibility in our module wrapper
    - https://github.com/shaka-project/shaka-player/pull/1398

Demo app:
  - Fixed playback of VDMS assets by updating the license request details
    - https://github.com/shaka-project/shaka-player/pull/1388


## 2.3.5 (2018-03-29)

New features:
  - Do not buffer audio far ahead of video
    - https://github.com/shaka-project/shaka-player/issues/964

Bugfixes:
  - Fixed early seeking (immediately upon load)
    - https://github.com/shaka-project/shaka-player/issues/1298
  - Fixed repeated seeking in HLS live (also affects DASH with
    timeShiftBufferDepth of zero)
    - https://github.com/shaka-project/shaka-player/issues/1331
  - Fixed VTT+MP4 parsing with respect to TRUN box
    - https://github.com/shaka-project/shaka-player/issues/1266
  - Fixed hang in StreamingEngine when playing at the left edge of the seek
    range on slow embedded devices
  - Work around slow DASH parsing on embedded devices

Demo app:
  - Fixed CSS for display on Chromecast and other TV devices
  - Added "startTime" URL parameter for debugging purposes


## 2.3.4 (2018-03-22)

New features:
  - Support for non-standard DASH SegmentTemplate strings using formats other
    than "d" (such as "x" and "o").
    - https://github.com/Dash-Industry-Forum/DASH-IF-IOP/issues/177

Bugfixes:
  - Fixed rapid seeking in zero-width seek ranges, such as in HLS live
    - https://github.com/shaka-project/shaka-player/issues/1331
  - Fixed use of native controls for text display
    - https://github.com/shaka-project/shaka-player/issues/1332
  - Fixed parsing of multiple 'emsg' boxes
    - https://github.com/shaka-project/shaka-player/issues/1340

Demo app:
  - Added an "unload" button to the demo app
  - Fixed enabling of TS assets in the demo app
    - https://github.com/shaka-project/shaka-player/issues/1214

Docs:
  - Added a doc describing DASH manifests
    - https://github.com/shaka-project/shaka-player/issues/1233
  - Fixed documentation of CONTENT_UNSUPPORTED_BY_BROWSER error
    - https://github.com/shaka-project/shaka-player/issues/1349
  - Updated architecture diagrams
    - https://github.com/shaka-project/shaka-player/issues/1197


## 2.3.3 (2018-03-01)

New features:
  - Warn if parsing the date from UTCTiming fails
    - https://github.com/shaka-project/shaka-player/issues/1317
    - https://github.com/shaka-project/shaka-player/pull/1318
  - Backpropagate language selections on track change
    - https://github.com/shaka-project/shaka-player/issues/1299

Bugfixes:
  - Fix MP4+VTT in HLS
    - https://github.com/shaka-project/shaka-player/issues/1270
  - Fix track selection during "streaming" event
    - https://github.com/shaka-project/shaka-player/issues/1119
  - Work around MSE rounding errors in Edge
    - https://github.com/shaka-project/shaka-player/issues/1281
    - Edge bug: https://bit.ly/2ttKiBU
  - Fix IE stuck buffering at the end after replay
    - https://github.com/shaka-project/shaka-player/issues/979
  - Fix catastrophic backtracking in TTML text parser
    - https://github.com/shaka-project/shaka-player/issues/1312
  - Fix infinite loop when jumping very small gaps
    - https://github.com/shaka-project/shaka-player/issues/1309
  - Fix seek range for live content with less than a full availability window
    - https://github.com/shaka-project/shaka-player/issues/1224
  - Remove misleading logging in DrmEngine#fillInDrmInfoDefaults
    - https://github.com/shaka-project/shaka-player/pull/1288
    - https://github.com/shaka-project/shaka-player/issues/1284
  - Fix old text cues displayed after loading new text stream
    - https://github.com/shaka-project/shaka-player/issues/1293
  - Fix truncated HLS duration with short text streams
    - https://github.com/shaka-project/shaka-player/issues/1271
  - Fix DASH SegmentTemplate w/ duration
    - https://github.com/shaka-project/shaka-player/issues/1232

Docs:
  - Fix out-of-date docs for error 6014 EXPIRED
    - https://github.com/shaka-project/shaka-player/issues/1319
  - Simplify prerequisite installation on Linux
    - https://github.com/shaka-project/shaka-player/issues/1175
  - Simplify the debugging tutorial
  - Fix various typos
    - https://github.com/shaka-project/shaka-player/pull/1272
    - https://github.com/shaka-project/shaka-player/pull/1274


## 2.3.2 (2018-02-01)

New features:
  - Add Storage.deleteAll() to clear storage when database upgrades fail
    - https://github.com/shaka-project/shaka-player/issues/1230
    - https://github.com/shaka-project/shaka-player/issues/1248
  - Make DASH default presentation delay configurable
    - https://github.com/shaka-project/shaka-player/issues/1234
    - https://github.com/shaka-project/shaka-player/pull/1235

Bugfixes:
  - Fix stall during eviction with small bufferBehind values
    - https://github.com/shaka-project/shaka-player/issues/1123
  - Fix deletion of offline licenses for demo content
    - https://github.com/shaka-project/shaka-player/issues/1229
  - Fix compiler renaming in Player language APIs
    - https://github.com/shaka-project/shaka-player/issues/1258
  - Rename Timeline events to include the "Event" suffix
    - https://github.com/shaka-project/shaka-player/pull/1267

Docs:
  - Fix incorrect year in the change log
    - https://github.com/shaka-project/shaka-player/pull/1263
  - Fix some bad annotations found while upgrading jsdoc
    - https://github.com/shaka-project/shaka-player/issues/1259


## 2.3.1 (2018-01-22)

New features:
  - All features released in 2.2.10, plus...
  - DRM content is now implied by DRM config, fixes some ad insertion cases
    - https://github.com/shaka-project/shaka-player/pull/1217
    - https://github.com/shaka-project/shaka-player/issues/1094
  - Add support for mp4a.40.34 mp3 in HLS
    - https://github.com/shaka-project/shaka-player/issues/1210
  - Allow ES6 syntax
  - Replaced deprecated gjslint with eslint

Bugfixes:
  - All fixes released in 2.2.10, plus...
  - Handle MPEGTS timestamp rollover issues, including WebVTT HLS
    - https://github.com/shaka-project/shaka-player/issues/1191
  - Fix MP4 timescale assumptions in HLS
    - https://github.com/shaka-project/shaka-player/issues/1191
  - Update muxjs to use new keepOriginalTimestamps option
    - https://github.com/shaka-project/shaka-player/issues/1194
  - Avoids line-length limits when building on Windows
    - https://github.com/shaka-project/shaka-player/issues/1228
  - Force JS files to use unix newlines on Windows
    - https://github.com/shaka-project/shaka-player/issues/1228
  - Fix selection of text streams with no role
    - https://github.com/shaka-project/shaka-player/issues/1212

Docs:
  - All fixes released in 2.2.10, plus...
  - Fix upgrade guide links


## 2.2.10 (2018-01-22)

New features:
  - Update Widevine HLS parsing support for SAMPLE-AES-CTR
    - https://github.com/shaka-project/shaka-player/issues/1227

Bugfixes:
  - Fix display of duration in Chrome cast dialog
    - https://github.com/shaka-project/shaka-player/issues/1174
  - Compensate for rounding errors in multi-period manifests
  - Delay gap-jumping until after seeking is complete
    - https://github.com/shaka-project/shaka-player/issues/1061
  - Fix SegmentTemplate w/ duration for live
    - https://github.com/shaka-project/shaka-player/issues/1204

Docs:
  - Add FAQ entry for file:// requests in Electron
    - https://github.com/shaka-project/shaka-player/issues/1222
  - Fixed typos and extraneous tags
  - Added missing @exportDoc annotations
    - https://github.com/shaka-project/shaka-player/pull/1208


## 2.3.0 (2017-12-22)

New features:
  - Support for HLS live streams
    - https://github.com/shaka-project/shaka-player/issues/740
  - Support for HLS VOD streams that do not start at t=0
    - https://github.com/shaka-project/shaka-player/issues/1011
    - Previously supported through configuration, now automatic
  - MPEG-2 TS content can be transmuxed to MP4 for playback on all browsers
    - https://github.com/shaka-project/shaka-player/issues/887
    - Requires apps to load https://github.com/videojs/mux.js/
  - Do not stream captions until they are shown
    - https://github.com/shaka-project/shaka-player/issues/1058
  - Use NetworkInformation API to get initial bandwidth estimate
    - https://github.com/shaka-project/shaka-player/issues/994
    - https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation
  - Added a method to list language/role combinations
    - https://github.com/shaka-project/shaka-player/issues/967

Demo app:
  - The demo app is now a Progressive Web App (PWA) and can be used offline
    - https://github.com/shaka-project/shaka-player/issues/876
    - https://developers.google.com/web/progressive-web-apps/
  - Lighthouse: improved page load latency, text contrast ratio, UI performance
    - https://github.com/shaka-project/shaka-player/issues/905
    - https://developers.google.com/web/tools/lighthouse/
  - Roles can now be selected in the demo app
    - https://github.com/shaka-project/shaka-player/issues/967
  - Added quick links to change between compiled, debug, and uncompiled builds

Bugfixes:
  - Fixed interpretation of EXT-X-START in HLS
    - https://github.com/shaka-project/shaka-player/issues/1011
  - Fixed URI extension parsing in HLS
    - https://github.com/shaka-project/shaka-player/issues/1085
  - Offline storage API can now download multiple items in parallel
    - https://github.com/shaka-project/shaka-player/issues/1047

Docs:
  - FAQ, architecture diagrams, and tutorials have all been updated.
    - https://github.com/shaka-project/shaka-player/issues/1183

Broken compatibility:
  - Text parser plugins now take a Uint8Array, not an ArrayBuffer.  All
    application-specific text-parsing plugins MUST be updated.
    - https://github.com/shaka-project/shaka-player/issues/1022

Deprecated:
  - The AbrManager configuration interfaces and plugin APIs which were
    deprecated in v2.2 have now been removed.  Applications with custom
    AbrManager implementations MUST be upgraded to the v2.2 API now.
  - The plugin interface for text parsers which was deprecated in v2.1 has now
    been removed.
  - The `remove()` method on `shaka.offline.Storage` now takes a URI instead of
    a `StoredContent` instance.  Applications which use offline storage SHOULD
    update to the new API.  Support for the old argument will be removed in
    v2.4.
  - The `streaming.infiniteRetriesForLiveStreams` config was removed.
    Applications using this feature MUST use the `streaming.failureCallback`
    config and the method `player.retryStreaming()` instead.


## 2.2.9 (2017-12-22)

Bugfixes:
  - Fix excessive memory usage during storage
    - https://github.com/shaka-project/shaka-player/issues/1167
  - Fix offline storage with temporary license
    - https://github.com/shaka-project/shaka-player/issues/1159
  - Fix exception while casting
    - https://github.com/shaka-project/shaka-player/issues/1128
  - Reduced bandwidth of cast messaging
    - https://github.com/shaka-project/shaka-player/issues/1128
  - Fix exception when destroying TextDisplayer
    - https://github.com/shaka-project/shaka-player/issues/1187
  - Fix presentationTimeOffset in SegmentTemplate
    - https://github.com/shaka-project/shaka-player/issues/1164
  - Fix inconsistencies in text visibility across playbacks
    - https://github.com/shaka-project/shaka-player/issues/1185
  - Work around bad header formatting in IE 11
    - https://github.com/shaka-project/shaka-player/issues/1172
  - Fix Chromecast PlayReady playback
    - https://github.com/shaka-project/shaka-player/issues/1070
  - Fix subtitle display with VTTRegion enabled in Chrome
    - https://github.com/shaka-project/shaka-player/issues/1188


## 2.2.8 (2017-12-06)

Bugfixes:
  - Do not allow seeking/startup at duration (bump back by 1s)
    - https://github.com/shaka-project/shaka-player/issues/1014
  - Don't wait for sessions to close on DrmEngine.destroy
    - https://github.com/shaka-project/shaka-player/issues/1093
    - https://github.com/shaka-project/shaka-player/pull/1168
  - Do not clear buffers on configuration changes unless required
    - https://github.com/shaka-project/shaka-player/issues/1138
  - Ignore unsupported STYLE blocks in WebVTT
    - https://github.com/shaka-project/shaka-player/issues/1104
  - Fix a null exception in CastReceiver.destroy


Demo app:
  - Fix "ended" video control state on IE
    - https://github.com/shaka-project/shaka-player/issues/979
  - Fix updates to demo app URL hash on Edge & IE 11
    - https://github.com/shaka-project/shaka-player/issues/1111
  - Fix demo app page-load race on IE 11


## 2.2.7 (2017-11-28)

Bugfixes:
  - Allow playhead to recover from drift
    - https://github.com/shaka-project/shaka-player/issues/1105
  - Fix exception and race which prevented cast status updates
    - https://github.com/shaka-project/shaka-player/issues/1128
  - Fix live broadcast startup issues
    - https://github.com/shaka-project/shaka-player/issues/1150
  - Fix mis-detection of live streams as IPR
    - https://github.com/shaka-project/shaka-player/issues/1148
  - Fix buffering of live streams while paused
    - https://github.com/shaka-project/shaka-player/issues/1121

Demo app:
  - Add multi-DRM assets from VDMS
    - https://github.com/shaka-project/shaka-player/issues/780
    - https://github.com/shaka-project/shaka-player/pull/781
  - Add certificate URI field in the custom asset section
    - https://github.com/shaka-project/shaka-player/issues/1135
    - https://github.com/shaka-project/shaka-player/pull/1136
  - Fix broken HLS asset
    - https://github.com/shaka-project/shaka-player/issues/1137
  - Update Widevine proxy URI

Docs:
  - Refactor main README.md
  - Fix build/README.md typo
    - https://github.com/shaka-project/shaka-player/pull/1139
  - Fix typo in config tutorial
    - https://github.com/shaka-project/shaka-player/pull/1124


## 2.2.6 (2017-11-14)

Bugfixes:
  - Cancel network retries when the Player is destroyed
    - https://github.com/shaka-project/shaka-player/issues/1084
  - Do not overwrite media from an earlier period when new period is shifted
    - https://github.com/shaka-project/shaka-player/issues/1098
  - Do not assume same timescale in manifest and media
    - https://github.com/shaka-project/shaka-player/issues/1098
  - Do not fail assertions when media references are shifted outside the period
    - https://github.com/shaka-project/shaka-player/issues/1098
  - Fix custom builds which exclude text parsing plugins
    - https://github.com/shaka-project/shaka-player/issues/1115

Demo app:
  - Rename demo "Autoplay" in demo UI to "Auto-load on page refresh"
    - https://github.com/shaka-project/shaka-player/issues/1114


## 2.2.5 (2017-11-02)

New features:
  - Add streaming event to allow reconfiguration before streaming starts
    - https://github.com/shaka-project/shaka-player/issues/1043
  - Add method to get the parsed manifest structure
    - https://github.com/shaka-project/shaka-player/issues/1074
  - Log about deprecated APIs, even in a compiled build with other logs disabled

Bugfixes:
  - Fix interpretation of DASH presentationTimeOffset in SegmentBase
    - https://github.com/shaka-project/shaka-player/issues/1099


## 2.1.9 (2017-11-02)

Bugfixes:
  - Fix interpretation of DASH presentationTimeOffset in SegmentBase
    - https://github.com/shaka-project/shaka-player/issues/1099


## 2.2.4 (2017-10-23)

Bugfixes:
  - Don't enforce seek range while paused in live streams (stays paused)
    - https://github.com/shaka-project/shaka-player/issues/982
  - Fix start time in live streams
    - https://github.com/shaka-project/shaka-player/issues/1069
  - Fix handling & transmission of errors from cast receiver to sender
    - https://github.com/shaka-project/shaka-player/issues/1065

Docs:
  - Added a tutorial for the offline storage and playback APIs
    - https://github.com/shaka-project/shaka-player/issues/1037


## 2.2.3 (2017-10-17)

New features:
  - Publish an event when the CDM accepts a license
    - https://github.com/shaka-project/shaka-player/issues/1035
    - https://github.com/shaka-project/shaka-player/pull/1049
  - Added assertions and logging to the debug build
  - Added a debugging method on Player to get buffered ranges

Bugfixes:
  - Fixed race between gap-jumping and seeking
    - https://github.com/shaka-project/shaka-player/issues/1061
  - Fixed startTime == 0 in player.load()
    - https://github.com/shaka-project/shaka-player/issues/1069
  - Avoid clearing buffer on configure unless restrictions change
    - https://github.com/shaka-project/shaka-player/issues/1009
  - Fixed exceptions in the cast receiver demo
    - https://github.com/shaka-project/shaka-player/issues/1064
  - Various fixes for concurrent use of CastProxy and related APIs
    - https://github.com/shaka-project/shaka-player/issues/768
  - Polyfilled various MediaSource issues on Safari 11
    - https://github.com/shaka-project/shaka-player/issues/1048
  - Reject TS content on Safari due to MediaSource bugs
    - https://github.com/shaka-project/shaka-player/issues/743
  - Fixed stuck progress bar on cast receiver demo
    - https://github.com/shaka-project/shaka-player/issues/1064

Demo app:
  - Rotating mobile devices triggers fullscreen mode
    - https://github.com/shaka-project/shaka-player/issues/883
  - Added robustness suggestions for Widevine
    - https://github.com/shaka-project/shaka-player/pull/1008

Docs:
  - Fixed docs with regard to shaka.text namespace
    - https://github.com/shaka-project/shaka-player/issues/1046


## 2.2.2 (2017-09-27)

New features:
  - Support for MP4+TTML text streams with multiple MDAT boxes
    - https://github.com/shaka-project/shaka-player/issues/1028

Bugfixes:
  - Fixed playback hangs in certain content due to rounding error
    - https://github.com/shaka-project/shaka-player/issues/979
  - Fixed exception when TextTrack mode is set to "disabled"
    - https://github.com/shaka-project/shaka-player/issues/990
  - Fixed subtitle failures in Safari
    - https://github.com/shaka-project/shaka-player/issues/991
    - https://github.com/shaka-project/shaka-player/issues/1012
  - Fixed renaming issues in compiled builds
  - Fixed exceptions on Tizen 2016
    - https://github.com/shaka-project/shaka-player/issues/1022
    - https://github.com/shaka-project/shaka-player/issues/935
  - Fixed TTML region parsing
    - https://github.com/shaka-project/shaka-player/issues/1020

Demo app:
  - Auto-select offline copy of an asset after storing it offline
    - https://github.com/shaka-project/shaka-player/issues/996
    - https://github.com/shaka-project/shaka-player/pull/1001
  - Removed YouTube-sourced assets, which were very outdated
    - https://github.com/shaka-project/shaka-player/issues/1015
  - Added "Shaka Player History" live stream

Docs:
  - Added CORS explanation to the docs
    - https://github.com/shaka-project/shaka-player/issues/1018


## 2.2.1 (2017-09-01)

New features:
  - Support MP4+TTML in HLS
    - https://github.com/shaka-project/shaka-player/issues/986

Bugfixes:
  - Fixed display of old text cues after loading new content
    - https://github.com/shaka-project/shaka-player/issues/984
  - Fixed text cue alignment in compiled mode
    - https://github.com/shaka-project/shaka-player/issues/987
  - Fixed exception triggered when storing offline content
    - https://github.com/shaka-project/shaka-player/issues/988
  - Fixed cast state when multiple cast senders exist at once
    - https://github.com/shaka-project/shaka-player/issues/768
  - Fixed several Cast UI issues
  - Fixed (harmless) assertion failures on Cast receivers

Demo app:
  - Demo UI on mobile now shows help text on store/delete button
    - https://github.com/shaka-project/shaka-player/pull/995

Docs:
  - Document lack of IE support on Windows 7
    - https://github.com/shaka-project/shaka-player/pull/993


## 2.2.0 (2017-08-23)

New features:
  - Add support for EVENT type playlists in HLS
    - https://github.com/shaka-project/shaka-player/issues/740
  - Add new option for offline protected content without persistent licensing
    - https://github.com/shaka-project/shaka-player/issues/873
  - Allow applications to render their own text tracks
    - https://github.com/shaka-project/shaka-player/issues/796
  - Allow applications to control streaming retry behavior
    - https://github.com/shaka-project/shaka-player/issues/960
  - Add support for additional TTML styles
    - https://github.com/shaka-project/shaka-player/issues/923
    - https://github.com/shaka-project/shaka-player/issues/927
  - Add channel count information for both DASH & HLS
    - https://github.com/shaka-project/shaka-player/issues/424
    - https://github.com/shaka-project/shaka-player/issues/826
  - Add basic xlink support in DASH (actuate=onLoad only)
    - https://github.com/shaka-project/shaka-player/issues/587
    - https://github.com/shaka-project/shaka-player/issues/788
  - Add API to limit playable/seekable range for VOD content.
    - https://github.com/shaka-project/shaka-player/issues/246
  - Add new error code for container/codec support issues
    - https://github.com/shaka-project/shaka-player/issues/868
  - The default ABR manager is much more configurable
    - https://github.com/shaka-project/shaka-player/issues/744
  - Add stream bandwidth info to variant tracks
    - https://github.com/shaka-project/shaka-player/issues/834
  - Add player.isAudioOnly()
    - https://github.com/shaka-project/shaka-player/issues/942
  - Expose presentation start time through player
    - https://github.com/shaka-project/shaka-player/issues/957
  - Add bandwidth info to switch history
  - Improved Chromecast media queries
  - Stricter runtime type-checking of EME cert configuration
    - https://github.com/shaka-project/shaka-player/issues/784

Bugfixes:
  - Fix flakiness in offline-related tests
    - https://github.com/shaka-project/shaka-player/issues/903

Demo app:
  - Added robustness fields to the UI
    - https://github.com/shaka-project/shaka-player/issues/889

Docs:
  - Updated upgrade guide for v2.2
    - https://github.com/shaka-project/shaka-player/issues/930

Broken compatibility:
  - The text-parsing plugin API has changed.  Plugins now return shaka.text.Cue
    objects instead of VTTCue or TextTrackCue objects.  All application-specific
    text-parsing plugins MUST be updated.
    - https://github.com/shaka-project/shaka-player/issues/796

Deprecated:
  - The configuration for a custom ABR manager has changed.  Applications with
    custom AbrManager implementations SHOULD now configure abrFactory instead of
    abr.manager.
    - https://github.com/shaka-project/shaka-player/issues/744
    - The old interface will be removed in v2.3.
  - The config API for AbrManager has changed.  setDefaultEstimate() and
    setRestrictions() have been replaced with configure().  Applications with
    custom AbrManager implementations SHOULD implement the new configure()
    method.
    - https://github.com/shaka-project/shaka-player/issues/744
    - The old interface will be removed in v2.3.
  - The choice API for AbrManager has changed.  chooseStreams() has been
    replaced with chooseVariants(), and the switch callback now takes a variant.
    - https://github.com/shaka-project/shaka-player/issues/954
    - The old interface will be removed in v2.3.
  - The getTracks() and selectTrack() methods which were deprecated in v2.1 have
    now been removed.


## 2.1.8 (2017-08-23)

Bugfixes:
  - Add player.isAudioOnly() to fix flash of audio-only icon when casting
    - https://github.com/shaka-project/shaka-player/issues/969
  - Fix cast proxying of isAudioOnly and getMediaElement


## 2.1.7 (2017-08-14)

Bugfixes:
  - Fixed "Invalid argument" exceptions for subtitles in IE & Edge
  - Fixed buffering at the end of the stream for some content in IE & Edge
    - https://github.com/shaka-project/shaka-player/issues/913
  - Fixed seeking with native controls in Edge
    - https://github.com/shaka-project/shaka-player/issues/951
  - Fixed role selection to clear audio buffer right away
    - https://github.com/shaka-project/shaka-player/issues/948

Docs:
  - Fixed a bug in the upgrade guide for selecting tracks and disabling ABR
    - https://github.com/shaka-project/shaka-player/issues/962


## 2.1.6 (2017-08-09)

New features:
  - Add vp9, opus, and flac mp4 to probeSupport
    - https://github.com/shaka-project/shaka-player/issues/944

Bugfixes:
  - Never adapt across roles or languages
    - https://github.com/shaka-project/shaka-player/issues/918
    - https://github.com/shaka-project/shaka-player/issues/947
  - Fix parsing byterange attribute in HlsParser
    - https://github.com/shaka-project/shaka-player/issues/925
  - Fix incorrect segment position after update in some DASH live streams
    - https://github.com/shaka-project/shaka-player/pull/838
  - Fix support for live streams with no seek range
    - https://github.com/shaka-project/shaka-player/issues/916
  - Fix display order of cues with identical ranges
    - https://github.com/shaka-project/shaka-player/issues/848
  - Fix missing cues in WVTT MP4s using default sample duration
    - https://github.com/shaka-project/shaka-player/issues/919
  - Accept non-integer settings in VTT
    - https://github.com/shaka-project/shaka-player/issues/919
  - Tolerate bandwidth of 0 or missing bandwidth
    - https://github.com/shaka-project/shaka-player/issues/938
    - https://github.com/shaka-project/shaka-player/issues/940
  - Fix multiple pipeline flushes on some platforms
  - Make it safe to install polyfills twice
    - https://github.com/shaka-project/shaka-player/issues/941

Demo app:
  - Fix compiled mode in the demo app.  Does not affect the library.
    Removed defaultConfig_ reference in demo.
    - https://github.com/shaka-project/shaka-player/issues/929
  - Update license URI for PlayReady test asset
    - https://github.com/shaka-project/shaka-player/pull/953
    - https://github.com/shaka-project/shaka-player/issues/945


## 2.1.5 (2017-07-17)

New features:
  - Add more information to video errors in Chrome

Bugfixes:
  - Fix key status problems on IE11 and Tizen TVs
    - https://github.com/shaka-project/shaka-player/issues/884
    - https://github.com/shaka-project/shaka-player/issues/890
  - Fix period switching when streams are not yet available
    - https://github.com/shaka-project/shaka-player/issues/839
  - Filter out audio-only HLS variants that can't be switched to
    - https://github.com/shaka-project/shaka-player/issues/824
    - https://github.com/shaka-project/shaka-player/issues/861
  - Fix parsing of Microsoft-packaged HLS content
  - Fix rounding issues with multi-Period content
    - https://github.com/shaka-project/shaka-player/issues/882
    - https://github.com/shaka-project/shaka-player/issues/909
    - https://github.com/shaka-project/shaka-player/issues/911
  - Fix exceptions thrown in some cases when switching text tracks
    - https://github.com/shaka-project/shaka-player/issues/910
  - Fix DASH date parsing when timezone is missing
    - https://github.com/shaka-project/shaka-player/issues/901
  - Fix persistent storage detection on IE11 and Tizen TVs
  - Fix test issues on Tizen
    - https://github.com/shaka-project/shaka-player/issues/893
  - Fix version detection when compiling from the NPM package
    - https://github.com/shaka-project/shaka-player/issues/871
  - Work around lack of key statuses on Tizen
    - https://github.com/shaka-project/shaka-player/issues/891
    - https://github.com/shaka-project/shaka-player/issues/894

Demo app:
  - Fix missing fullscreen button on IE11
    - https://github.com/shaka-project/shaka-player/issues/787
  - Added configuration for gap jumping

Docs:
  - Document HTTPS requirement for EME
    - https://github.com/shaka-project/shaka-player/issues/867
    - https://github.com/shaka-project/shaka-player/issues/928
  - Update tutorials
    - https://github.com/shaka-project/shaka-player/issues/862
  - Add FAQ entry on EME robustness
    - https://github.com/shaka-project/shaka-player/issues/866
  - Update HLS FAQ
  - Document that we test on Tizen TV now


## 2.1.4 (2017-06-16)

New features:
  - Allow role to be specified in selectAudioLanguage and selectTextLanguage
    - https://github.com/shaka-project/shaka-player/issues/767

Bugfixes:
  - Fix changing languages close to a period boundary
    - https://github.com/shaka-project/shaka-player/issues/797
  - Fix hang in load() when there are pending failures
    - https://github.com/shaka-project/shaka-player/issues/782
  - Fix DASH parser ignoring certain text streams
    - https://github.com/shaka-project/shaka-player/issues/875
  - Fix exceptions when side-loading text tracks
    - https://github.com/shaka-project/shaka-player/issues/821
  - Fix PlayReady support on Chromecast
    - https://github.com/shaka-project/shaka-player/issues/852
  - Fix version number issues during publication on NPM
    - https://github.com/shaka-project/shaka-player/issues/869
  - Fix pollution from npm on Windows
    - https://github.com/shaka-project/shaka-player/issues/776
  - Fix support for npm v5
    - https://github.com/shaka-project/shaka-player/issues/854

Demo app:
  - Fix control visibility in fullscreen mode on mobile phones
    - https://github.com/shaka-project/shaka-player/issues/663

Docs:
  - Updated welcome docs
  - Updated list of supported platforms
    - https://github.com/shaka-project/shaka-player/issues/863
  - Updated FAQ
    - https://github.com/shaka-project/shaka-player/issues/864
    - https://github.com/shaka-project/shaka-player/issues/865


## 2.1.3 (2017-06-06)

New features:
  - Limit network retries for VOD, only retry forever on live
    - https://github.com/shaka-project/shaka-player/issues/762
    - https://github.com/shaka-project/shaka-player/issues/830
    - https://github.com/shaka-project/shaka-player/pull/842
  - Add stream IDs in getStats().switchHistory
    - https://github.com/shaka-project/shaka-player/issues/785
    - https://github.com/shaka-project/shaka-player/issues/823
    - https://github.com/shaka-project/shaka-player/pull/846
  - Add label attribute to tracks
    - https://github.com/shaka-project/shaka-player/issues/825
    - https://github.com/shaka-project/shaka-player/pull/811
    - https://github.com/shaka-project/shaka-player/pull/831
  - Expose role attributes on tracks
    - https://github.com/shaka-project/shaka-player/issues/767
  - Silence confusing browser-generated errors related to play()
    - https://github.com/shaka-project/shaka-player/issues/836

Bugfixes:
  - Fix offline storage in compiled mode
  - Choose lowest-bandwidth codecs when multiple are possible
    - https://github.com/shaka-project/shaka-player/issues/841
  - Fix PlayReady on IE and Edge
    - https://github.com/shaka-project/shaka-player/issues/837
  - Fix rounding errors on IE11
    - https://github.com/shaka-project/shaka-player/pull/832
  - Clean up demo app loader
  - Fix PlayReady test failures


## 2.1.2 (2017-05-23)

New features:
  - Make educated guesses about missing HLS info (CODECS no longer required)
    - https://github.com/shaka-project/shaka-player/issues/805
  - Add support for PlayReady on Chromecast and Tizen
    - https://github.com/shaka-project/shaka-player/issues/814
    - https://github.com/shaka-project/shaka-player/pull/815

Bugfixes:
  - Fix flakiness in RESTRICTIONS\_CANNOT\_BE\_MET errors
  - Make isBrowserSupported more strict about MediaSource
  - Fix detection of audio-only assets in the demo
    - https://github.com/shaka-project/shaka-player/issues/794
  - Fix exports and generated externs that were broken in v2.1.0 and v2.1.1
  - Speed up deletion of offline content
    - https://github.com/shaka-project/shaka-player/issues/756

Docs:
  - Fix docs on subtitles and captions
    - https://github.com/shaka-project/shaka-player/issues/808
  - Add notes on adaptation to upgrade guide


## 2.0.9 (2017-05-10)

Backported bugfixes from v2.1.x:
  - Fix offline download stalls on Android
    - https://github.com/shaka-project/shaka-player/issues/747
  - Fix track restriction based on key status
    - https://github.com/shaka-project/shaka-player/issues/761
  - Fix exception in fullscreen polyfill on IE 11
    - https://github.com/shaka-project/shaka-player/pull/777
  - Fix exception when reconfiguring serverCertificate
    - https://github.com/shaka-project/shaka-player/issues/784


## 2.1.1 (2017-05-10)

New features:
  - Separate audio and video codec in Track
    - https://github.com/shaka-project/shaka-player/issues/758
  - Make segment request to establish HLS media MIME type
    - https://github.com/shaka-project/shaka-player/issues/769

Bugfixes:
  - Fix exception in fullscreen polyfill on IE 11
    - https://github.com/shaka-project/shaka-player/pull/777
  - Fix exception when reconfiguring serverCertificate
    - https://github.com/shaka-project/shaka-player/issues/784
  - Don't fire 'trackschanged' event twice
    - https://github.com/shaka-project/shaka-player/issues/783
  - Fix track restriction based on key status
    - https://github.com/shaka-project/shaka-player/issues/761
  - Fix offline download stalls on Android
    - https://github.com/shaka-project/shaka-player/issues/747
  - Fix race condition in gap-jumping code
  - Fix poster visibility in fullscreen mode
    - https://github.com/shaka-project/shaka-player/issues/778


## 2.1.0 (2017-04-25)

New features:
  - Add basic HLS support
    - VOD only
    - Widevine & clear content only
    - No support for CEA-708
    - https://github.com/shaka-project/shaka-player/issues/279
  - Tolerate gaps in the presentation timeline and jump over them
    - https://github.com/shaka-project/shaka-player/issues/555
  - Add an indicator for critical errors
    - https://github.com/shaka-project/shaka-player/issues/564
  - Do not retry on HTTP 401/403 errors
    - https://github.com/shaka-project/shaka-player/issues/620
  - Expand player stats and track metadata
    - Add loadLatency stat
    - Add mimeType to tracks
    - Track state changes (buffering, playing, paused, ended)
  - DASH trick mode support
    - https://github.com/shaka-project/shaka-player/issues/538
  - Expose license expiration times through Player
    - https://github.com/shaka-project/shaka-player/issues/727
  - Add support for EventStream elements in DASH
    - https://github.com/shaka-project/shaka-player/issues/462
  - Add support for Chromecast Media Playback messages from generic senders
    - https://github.com/shaka-project/shaka-player/issues/722
  - Add config to ignore key system and init data in DASH manifest
    - https://github.com/shaka-project/shaka-player/issues/750
  - Add support for asynchronous response filters
    - https://github.com/shaka-project/shaka-player/issues/610
  - Filter duplicate initData from manifest by key ID
    - https://github.com/shaka-project/shaka-player/issues/580
  - Optionally adjust start time to segment boundary
    - https://github.com/shaka-project/shaka-player/issues/683
  - StringUtils and Uint8ArrayUtils are now exported, to make filters easier
    - https://github.com/shaka-project/shaka-player/issues/667
  - Add audio adaptation to default AbrManager
  - Add an API to force the Chromecast to disconnect
    - https://github.com/shaka-project/shaka-player/issues/523
  - Add possibility to delay license request until playback is started
    - https://github.com/shaka-project/shaka-player/issues/262
  - Add API to get live stream position as Date
    - https://github.com/shaka-project/shaka-player/issues/356
  - Don't clear buffer if switching to the same stream
    - https://github.com/shaka-project/shaka-player/issues/693
  - Demo app permalink support through URL hash parameters
    - https://github.com/shaka-project/shaka-player/issues/709
  - Add a flag so scheme plugins can ask us to ignore cache hits for ABR
  - Allow passing durations from scheme plugins to compute throughput
    - https://github.com/shaka-project/shaka-player/issues/621
  - Make ES6 imports easier
    - https://github.com/shaka-project/shaka-player/issues/466
  - Add separate restrictions to AbrManager
    - https://github.com/shaka-project/shaka-player/issues/565
  - Allow network plugins to see the request type
    - https://github.com/shaka-project/shaka-player/issues/602

Bugfixes:
  - Make language selection explicit
    - https://github.com/shaka-project/shaka-player/issues/412
  - Make text track visibility explicit
    - https://github.com/shaka-project/shaka-player/issues/626
  - Fix firing of 'trackschanged' event for multi-Period content
    - https://github.com/shaka-project/shaka-player/issues/680
  - Correct time parsing for MP4 VTT subtitles
    - https://github.com/shaka-project/shaka-player/issues/699
  - Fix playback of live when segments do not extend to the end of the Period
    - https://github.com/shaka-project/shaka-player/issues/694
  - Allow seeking to 0 in live streams
    - https://github.com/shaka-project/shaka-player/issues/692
  - Add explicit timestamps to 'emsg' events
    - https://github.com/shaka-project/shaka-player/issues/698
  - Fix playback of YouTube demo assets
    - https://github.com/shaka-project/shaka-player/issues/682
  - Allow text parsers to change during playback
    - https://github.com/shaka-project/shaka-player/issues/571

Docs:
  - Add offline storage to v2 upgrade guide
  - Add additional docs for AbrManager
    - https://github.com/shaka-project/shaka-player/issues/629
  - Add manifest parser plugin tutorial

Broken Compatibility:
  - Track types 'video' and 'audio' have been combined into 'variant'.
    - Any application looking at track.type will need to be updated.
  - Removed useRelativeCueTimestamps option
    - All segmented WebVTT cue timestamps are now segment-relative
    - https://github.com/shaka-project/shaka-player/issues/726
  - Plugin interface for text parsers has changed
    - Both old & new interfaces still supported
    - Support for old interface will be removed in v2.2
  - Plugin interface for ManifestParser.start has changed
    - Now takes an object with named parameters instead of positional params
    - Both old & new interfaces still supported
    - Support for old interface will be removed in v2.2
  - Retired the INVALID\_TTML error code
    - Folded into the INVALID\_XML error code


## 2.0.8 (2017-04-07)

Bugfixes:
  - Suppress controls UI updates when hidden
    - https://github.com/shaka-project/shaka-player/issues/749
  - Revert keyboard navigation changes in demo, failing on Firefox


## 2.0.7 (2017-03-29)

New Features:
  - Improved keyboard navigation in demo page for accessibility
  - Play through small gaps at the start of the timeline
  - Add a method for accessing the HTMLMediaElement from the Player
    - https://github.com/shaka-project/shaka-player/pull/723
  - Improved error reporting for HTTP errors

Bugfixes:
  - Fixed a DASH compliance bug in SegmentList w/ presentationTimeOffset
  - Fixed compiler renaming in emsg events.
    - https://github.com/shaka-project/shaka-player/issues/717
  - Fix period transitions where text streams may be absent
    - https://github.com/shaka-project/shaka-player/issues/715
  - Fix Firefox DRM detection
  - Fix cleanup of expired EME sessions for offline
  - Fix demo app error thrown when offline is not supported
  - Fix infinite loop in offline storage of SegmentTemplate-based DASH
    - https://github.com/shaka-project/shaka-player/issues/739
  - Fix contamination between tests


## 2.0.6 (2017-02-24)

New Features:
  - Add Media Session info to demo
    - https://github.com/shaka-project/shaka-player/pull/689
  - Add support for xml:space in TTML parser
    - https://github.com/shaka-project/shaka-player/issues/665
  - Add fullscreenEnabled property to fullscreen polyfill
    - https://github.com/shaka-project/shaka-player/issues/669
  - Allow InbandEventStream elements at Representation level
    - https://github.com/shaka-project/shaka-player/pull/687
    - https://github.com/shaka-project/shaka-player/issues/686
  - Warning for unsupported indexRange attribute
  - Warning for duplicate Representation IDs

Bugfixes:
  - Fix cast support broken since 2.0.3
    - https://github.com/shaka-project/shaka-player/issues/675
  - Fix timeout errors in cast demo
    - https://github.com/shaka-project/shaka-player/issues/684
  - Fix infinite buffering caused by a race
    - https://github.com/shaka-project/shaka-player/issues/600
  - Fix race in StreamingEngine for multi-Period content
    - https://github.com/shaka-project/shaka-player/issues/655
  - Hide the controls when going fullscreen on phones
    - https://github.com/shaka-project/shaka-player/issues/663
  - Improve calculation of $TIME$ in SegmentTemplate
    - https://github.com/shaka-project/shaka-player/issues/690
    - https://github.com/shaka-project/shaka-player/pull/706
  - Fix YouTube asset on demo app
    - https://github.com/shaka-project/shaka-player/issues/682


## 2.0.5 (2017-01-30)

Bugfixes:
  - Fix several bugs with multi-Period content
    - Possible hang when seeking
    - Fix race between buffering and Period transition
    - Fix race between rapid Period transitions
    - https://github.com/shaka-project/shaka-player/issues/655
  - Fix hang in destroy() when EME sessions are in a bad state
    - https://github.com/shaka-project/shaka-player/issues/664
  - Fix doubling of time offset for segment-relative cues
    - https://github.com/shaka-project/shaka-player/issues/595
    - https://github.com/shaka-project/shaka-player/pull/599


## 2.0.4 (2017-01-24)

New features:
  - Support for 4k on Chromecast Ultra
  - Support for text tracks on Toshiba dTV
    - https://github.com/shaka-project/shaka-player/issues/635
    - https://github.com/shaka-project/shaka-player/pull/643

Bugfixes:
  - Fixed buffering issues at the end of streams in IE/Edge
    - https://github.com/shaka-project/shaka-player/issues/658
  - Fixed parsing of empty divs in TTML
    - https://github.com/shaka-project/shaka-player/issues/646
    - https://github.com/shaka-project/shaka-player/pull/650
  - Fixed subtle bug in Promise.resolve polyfill on IE
  - Fixed test failures on Chromecast

Docs:
  - Added additional docs for offline storage
  - Updated and clarified debugging tutorial
    - https://github.com/shaka-project/shaka-player/issues/653


## 2.0.3 (2017-01-09)

New features:
  - Treat HTTP 202 status codes as failures
    - https://github.com/shaka-project/shaka-player/issues/645

Bugfixes:
  - Fix race condition in StreamingEngine
  - Fix race in load/unload in Player
    - https://github.com/shaka-project/shaka-player/pull/613
    - https://github.com/shaka-project/shaka-player/issues/612
  - Update workarounds for Edge EME bugs
    - https://github.com/shaka-project/shaka-player/issues/634
  - Add missing events and methods to cast proxy
  - Fix exclusion of standard features in custom builds
  - Be more permissive of text failures
    - Permit text parsing errors as well as streaming errors with the
      ignoreTextStreamFailures config option.
    - Do not fail StreamingEngine startup because of text streams,
      regardless of config.
    - https://github.com/shaka-project/shaka-player/issues/635
  - Fix selectTrack() call with no text tracks
    - https://github.com/shaka-project/shaka-player/issues/640
  - Fix buffering state for live streams (stop at live edge)
    - https://github.com/shaka-project/shaka-player/issues/636


## 2.0.2 (2016-12-15)

New features:
  - Add support for Toshiba dTV
    - https://github.com/shaka-project/shaka-player/pull/605
  - TTML subtitles: Support for \<br\> inside a paragraph
    - https://github.com/shaka-project/shaka-player/pull/572
    - https://github.com/shaka-project/shaka-player/pull/584
  - Parse TTML textAlign settings into align property of a VTTCue
    - https://github.com/shaka-project/shaka-player/pull/573
  - Improved test stability and coverage reports

Bugfixes:
  - Fix DASH content type parsing
    - https://github.com/shaka-project/shaka-player/issues/631
  - Tolerate larger gaps at the start
    - https://github.com/shaka-project/shaka-player/issues/579
  - Fixes for TTML alignment, positioning and cue externs
    - https://github.com/shaka-project/shaka-player/pull/588
    - https://github.com/shaka-project/shaka-player/pull/594
  - Keep ewma sampling from failing on 0 duration segments
    - https://github.com/shaka-project/shaka-player/issues/582
    - https://github.com/shaka-project/shaka-player/pull/583
   - Allow text parsers to change during playback
    - https://github.com/shaka-project/shaka-player/issues/571
  - Fix playback when IE11 modifies the XML DOM
    - https://github.com/shaka-project/shaka-player/issues/608
    - https://github.com/shaka-project/shaka-player/pull/611
  - Update MediaSource polyfills for Safari 10
    - https://github.com/shaka-project/shaka-player/issues/615
  - Throw explicit error on empty manifests
    - https://github.com/shaka-project/shaka-player/issues/618

Docs:
  - Link to error docs from the demo app


## 2.0.1 (2016-10-26)

New features:
  - Faster ABR decisions
  - Add config option for using segment relative timestamps for VTT
    - https://github.com/shaka-project/shaka-player/issues/480
    - https://github.com/shaka-project/shaka-player/pull/542
  - Log and ignore non-standard WebVTT settings instead of failing
    - https://github.com/shaka-project/shaka-player/issues/509
  - Make key IDs from the manifest available through DrmInfo
    - https://github.com/shaka-project/shaka-player/pull/529
  - Provide framerate and codecs information on video tracks
    - https://github.com/shaka-project/shaka-player/issues/516
    - https://github.com/shaka-project/shaka-player/pull/533
  - Dispatch more useful network error when HEAD request fails

Bugfixes:
  - Fix ABR quality issues when switching tracks (stutters, glitches, etc.)
    - https://github.com/shaka-project/shaka-player/issues/520
  - Keep user selected text track when switching audio
    - https://github.com/shaka-project/shaka-player/issues/514
  - Fix vtt with one digit hour
    - https://github.com/shaka-project/shaka-player/pull/522
  - Fix build scripts for Windows
    - https://github.com/shaka-project/shaka-player/issues/526
  - Fix buffering event delay
    - https://github.com/shaka-project/shaka-player/issues/511
  - Workaround bug in Edge buffered ranges
    - https://github.com/shaka-project/shaka-player/issues/530
  - Fix handling of internal-error key status
    - https://github.com/shaka-project/shaka-player/issues/539
  - Ignore trick mode tracks
    - https://github.com/shaka-project/shaka-player/issues/538
  - Fix AdaptationSetSwitching support
  - Fix buffering logic when switching periods
    - https://github.com/shaka-project/shaka-player/issues/537
    - https://github.com/shaka-project/shaka-player/issues/545
  - Use data URI content-type for manifest type detection
    - https://github.com/shaka-project/shaka-player/pull/550
  - Fix audio language changes on Chromecast
    - https://github.com/shaka-project/shaka-player/issues/544
  - Fix Chromecast receiver idle behavior when looping or replaying
    - https://github.com/shaka-project/shaka-player/issues/558
  - Fix exception-causing race when TextEngine is destroyed

Demo app improvements:
  - Hide volume & mute buttons on mobile-sized screens
  - Probe both MP4 and WebM support in DrmEngine
    - https://github.com/shaka-project/shaka-player/issues/540
  - Update Axinom test assets to v7
  - Fix accessibility issues in the demo app
    - https://github.com/shaka-project/shaka-player/issues/552

Docs:
  - Rewrote the debugging tutorial
  - Misc docs cleanup
    - https://github.com/shaka-project/shaka-player/pull/536


## 2.0.0 (2016-09-07)

The first full release of v2!

New features:
  - Improved Chromecast support
    - Cast from the built-in Chrome dialog as well as the video controls
    - Use the built-in Chrome dialog to disconnect
  - Support for in-progress recordings (IPR)
    - https://github.com/shaka-project/shaka-player/issues/477
  - Can be configured to tolerate text stream failures
    - https://github.com/shaka-project/shaka-player/issues/474
  - Ignore small gaps in the timeline
    - https://github.com/shaka-project/shaka-player/issues/472
  - Added EMSG box support
    - https://github.com/shaka-project/shaka-player/issues/259
  - Reduced test flakiness and improved test speed
  - Improved VTT parsing
    - https://github.com/shaka-project/shaka-player/issues/469
  - Improved EME error reporting
    - https://github.com/shaka-project/shaka-player/issues/468
  - Improved demo app UI for touch screens
  - Smaller demo app UI (video element above the fold on Nexus 5X)

Bugfixes:
  - Fixed text-related issues in IE11
    - https://github.com/shaka-project/shaka-player/issues/501
    - https://github.com/shaka-project/shaka-player/issues/502
  - Fixed a few live edge corner cases
    - https://github.com/shaka-project/shaka-player/issues/490
    - https://github.com/shaka-project/shaka-player/issues/504
  - Fixed TTML parsing exceptions
    - https://github.com/shaka-project/shaka-player/issues/473
    - https://github.com/shaka-project/shaka-player/issues/506
  - Fixed text encoding issues with subs
  - Fixed issues with multi-period eviction
    - https://github.com/shaka-project/shaka-player/pull/483
  - Defined order of AdaptationSet preference (prefer high quality, low bw)
    - https://github.com/shaka-project/shaka-player/issues/476
  - Fixed support for manifests with multiple text formats
  - Fixed support for DASH Representations with multiple Roles
    - https://github.com/shaka-project/shaka-player/issues/500
  - Fixed CSP compliance for Chrome apps
    - https://github.com/shaka-project/shaka-player/issues/487

Planned features we cut:
  - Cache-detecting bandwidth estimation
    - https://github.com/shaka-project/shaka-player/issues/324


## 2.0.0-beta3 (2016-07-29)

Restored Features from v1 Missing in v2.0.0-beta2:
  - Offline storage and playback
    - https://github.com/shaka-project/shaka-player/issues/343
  - Clearkey license server support
    - https://github.com/shaka-project/shaka-player/issues/403

New features:
  - Built-in Chromecast support
    - https://github.com/shaka-project/shaka-player/issues/261
  - TTML text support
    - https://github.com/shaka-project/shaka-player/issues/111
  - TTML in MP4
    - https://github.com/shaka-project/shaka-player/issues/278
  - VTT in MP4
    - https://github.com/shaka-project/shaka-player/issues/277
  - Handle QuotaExceededError, automatically reduce buffering goals
    - https://github.com/shaka-project/shaka-player/issues/258
  - Faster template processing in DASH
    - https://github.com/shaka-project/shaka-player/issues/405
  - Bitrate upgrades take effect faster
  - Add a specific error for missing license server URI
    - https://github.com/shaka-project/shaka-player/issues/371
  - Add adaptation events for language changes
  - Don't treat network errors as fatal in StreamingEngine
    - https://github.com/shaka-project/shaka-player/issues/390
  - Provide the application access to DrmInfo structure
    - https://github.com/shaka-project/shaka-player/issues/272
  - Restructure test/ folder to mimic lib/ folder structure
    - https://github.com/shaka-project/shaka-player/pull/434
  - Upgrade closure compiler
    - https://github.com/shaka-project/shaka-player/pull/421
  - New logo!

Bugfixes:
  - Revert ABR changes that caused bandwidth samples to be ignored
    - https://github.com/shaka-project/shaka-player/issues/367
  - Fix buffering of multi-period text
    - https://github.com/shaka-project/shaka-player/issues/411
  - Fix various ABR issues
    - https://github.com/shaka-project/shaka-player/issues/435
  - Fix stuck playback on seek
    - https://github.com/shaka-project/shaka-player/issues/366
  - Stop refreshing live manifests when unloaded
    - https://github.com/shaka-project/shaka-player/issues/369
  - Don't adapt between incompatible codecs (mp4a & ec-3)
    - https://github.com/shaka-project/shaka-player/issues/391
  - Fix race in player WRT external text tracks
    - https://github.com/shaka-project/shaka-player/issues/418
  - Fix Edge EME workarounds on IE11
    - https://github.com/shaka-project/shaka-player/issues/393
  - Work around Safari MSE bugs
  - Fix relative paths in UTCTiming
    - https://github.com/shaka-project/shaka-player/issues/376
  - Fix source map paths on windows
    - https://github.com/shaka-project/shaka-player/issues/413
  - Improve demo app CSS on mobile
  - Fix buffering state on unload
  - Fix load/unload/destroy race conditions
  - Reduce test flake (async tests still flakey on Safari)
  - Fix context menu display in demo app
    - https://github.com/shaka-project/shaka-player/issues/422
  - Fix key status, session expiration, and DRM error dispatch
  - Fix demo app play controls on Android
    - https://github.com/shaka-project/shaka-player/issues/432
  - Fix corner cases when seeking to the live edge

Docs:
  - Add a license-wrapping tutorial
  - Add track restriction docs
    - https://github.com/shaka-project/shaka-player/issues/387
  - Update track and adaptation docs
    - https://github.com/shaka-project/shaka-player/issues/447

Broken Compatibility compared to v2.0.0-beta2:
  - The asynchronous Player.support() has been replaced with the synchronous
    Player.isBrowserSupported() call
    - https://github.com/shaka-project/shaka-player/issues/388
  - AbrManager implementations must now handle a partial StreamSet map in
    chooseStreams()
  - The wrong keys error has been dropped due to false positives


## 2.0.0-beta2 (2016-05-04)

Restored Features from v1 Missing in v2.0.0-beta:
  - Track restrictions API
    - https://github.com/shaka-project/shaka-player/issues/326
    - https://github.com/shaka-project/shaka-player/issues/327
  - Custom controls demo for live
    - https://github.com/shaka-project/shaka-player/issues/322
  - Trick play demo
    - https://github.com/shaka-project/shaka-player/issues/328

New features:
  - Reduced startup latency
  - Added player.resetConfiguration()
  - Added response text to HTTP errors
    - https://github.com/shaka-project/shaka-player/issues/319
  - Demo controls redesigned with material design icons
  - Emit an error if the wrong keys are retrieved
    - https://github.com/shaka-project/shaka-player/issues/301
  - Human-readable errors shown in demo app
  - Cache-friendly bandwidth estimation
    - https://github.com/shaka-project/shaka-player/issues/324
  - Improved trick play and playbackRate support
    - https://github.com/shaka-project/shaka-player/issues/344
  - Allow apps to reset ABR manager estimates
    - https://github.com/shaka-project/shaka-player/issues/355
  - Support non-zero start times for VOD
    - https://github.com/shaka-project/shaka-player/issues/341
    - https://github.com/shaka-project/shaka-player/issues/348
    - https://github.com/shaka-project/shaka-player/issues/357

Bugfixes:
  - Fix playback of DASH with unaligned Representations
  - Fixed race conditions on seek
    - https://github.com/shaka-project/shaka-player/issues/334
  - Improved drift handling
    - https://github.com/shaka-project/shaka-player/issues/330
  - Fixed stack overflow in StringUtils
    - https://github.com/shaka-project/shaka-player/issues/335
  - Improved live support
    - https://github.com/shaka-project/shaka-player/issues/331
    - https://github.com/shaka-project/shaka-player/issues/339
    - https://github.com/shaka-project/shaka-player/issues/340
    - https://github.com/shaka-project/shaka-player/issues/351
  - Fixed player.addTextTrack
  - Handle CDMs which don't support the same types MSE does
    - https://github.com/shaka-project/shaka-player/issues/342
  - Fix audio-only encrypted playback
    - https://github.com/shaka-project/shaka-player/issues/360
  - Fix renaming of event properties
    - https://github.com/shaka-project/shaka-player/issues/361
  - Warn about missing clock sync elements in live manfiests
    - https://github.com/shaka-project/shaka-player/issues/290
  - Add option for default clock sync URI
    - https://github.com/shaka-project/shaka-player/issues/290
  - Fix crash in TextEngine when subs are turned off

Docs:
  - Shaka v2 upgrade guide
    - http://shaka-player-demo.appspot.com/docs/api/tutorial-upgrade.html
  - Added enum values (not just names) to generated docs
    - https://github.com/shaka-project/shaka-player/issues/337

Broken Compatibility compared to v2.0.0-beta:
  - None!


## 1.6.5 (2016-04-08)

Bugfixes:
  - Always build the same input files to a stable output
    - https://github.com/shaka-project/shaka-player/pull/299
  - Properly extern the 'xhr' property of HTTP errors
    - https://github.com/shaka-project/shaka-player/pull/319


## 2.0.0-beta (2016-04-07)

New Features:
  - DASH support for:
    - Multi-Period content
      - https://github.com/shaka-project/shaka-player/issues/186
    - Location elements
      - https://github.com/shaka-project/shaka-player/issues/298
    - UTCTiming elements (for clock synchronization)
      - https://github.com/shaka-project/shaka-player/issues/241
  - Better browser compatibility
    - Testing on Safari 9, IE 11, Edge, Firefox 45+, Opera, Chrome
    - https://github.com/shaka-project/shaka-player/issues/101
  - New plugin and build system to extend Shaka
    - Networking plugins
      - https://github.com/shaka-project/shaka-player/issues/228
      - https://github.com/shaka-project/shaka-player/issues/198
  - Cache-friendly networking
    - https://github.com/shaka-project/shaka-player/issues/76
    - https://github.com/shaka-project/shaka-player/issues/191
    - https://github.com/shaka-project/shaka-player/issues/235
  - Limit memory usage by clearing old data from buffer
    - https://github.com/shaka-project/shaka-player/issues/247
  - Simpler, more mobile-friendly demo app
  - New test assets
    - https://github.com/shaka-project/shaka-player/issues/224
  - Made play()/pause() independent of buffering
    - https://github.com/shaka-project/shaka-player/issues/233
  - Numerical error code system
    - https://github.com/shaka-project/shaka-player/issues/201
  - Distinguish between subtitle and caption tracks
    - https://github.com/shaka-project/shaka-player/issues/206
  - Separate audio & text language preferences
    - https://github.com/shaka-project/shaka-player/issues/207
  - Update timeShiftBufferDepth when updating the manifest
    - https://github.com/shaka-project/shaka-player/issues/295
  - Simplified clearkey setup using configure()
  - Initial bandwidth is now configurable:
    - https://github.com/shaka-project/shaka-player/issues/268

Bugfixes:
  - Stopped using Date headers for clock sync
    - https://github.com/shaka-project/shaka-player/issues/205
    - https://github.com/shaka-project/shaka-player/issues/241

Docs:
  - New tutorials!

Missing Features from v1 (to be added later):
  - Custom controls demo for live streams
    - https://github.com/shaka-project/shaka-player/issues/322
  - Chromecast demo
  - Trick play demo
  - Track restrictions based on key status
  - Offline support

Broken Compatibility:
  - Almost everything! (v2 upgrade guide coming soon)


## 1.6.4 (2016-03-03)

Bugfixes:
  - Updated Promise polyfill with fixes backported from v2
  - Fixed Edge EME compatibility & InvalidStateErrors
    - https://github.com/shaka-project/shaka-player/issues/282
  - Fixed HttpVideoSource use with clear content (Thanks, Sanborn!)
    - https://github.com/shaka-project/shaka-player/pull/292
  - Fixed uncompiled-mode performance regression introduced in v1.6.3
    - https://github.com/shaka-project/shaka-player/issues/288


## 1.6.3 (2016-02-08)

Features:
  - Added opt\_clearBufferOffset for audio  (Thanks, Itay)
    - https://github.com/shaka-project/shaka-player/pull/254
  - Fetch segments from new location after manifest redirect  (Thanks, Rob)
    - https://github.com/shaka-project/shaka-player/pull/266

Bugfixes:
  - Several IE11 stability issues and race conditions fixed
    - Fixed incompatibilities when clearing the SourceBuffer
    - Ignore spurious 'updateend' events
    - Added stack-based messages to all assertions
    - Fixed some unit test compatibility issues
    - Fixed race conditions caused by Promise polyfill
    - https://github.com/shaka-project/shaka-player/issues/251

Docs:
  - Update browser support docs with regard to IE & Firefox

Test app fixes:
  - Fixed slider controls for IE11
  - Turned off seek bar tooltips for IE11


## 1.6.2 (2015-12-14)

Features:
  - Added a new configure parameter to allow a user to completely disable
    the cache-buster.  This is necessary for certain CDNs, but please note
    the tradeoffs before using.  Bandwidth estimation can be adversely
    affected, particularly for low-bandwidth users.
    - https://github.com/shaka-project/shaka-player/issues/235
    - https://github.com/shaka-project/shaka-player/issues/238
    - https://github.com/shaka-project/shaka-player/issues/76

Bugfixes:
  - Fixed interpretation of startNumber for SegmentTemplate w/ duration.
    - https://github.com/shaka-project/shaka-player/issues/237


## 1.6.1 (2015-12-07)

Bugfixes:
  - Fixed handling when all streams are removed in a manifest update.
  - Fixed annotation mistakes in preparation for a new compiler release.
  - Fixed Promise polyfill errors in compiled mode.
    - https://github.com/shaka-project/shaka-player/issues/236


## 1.6.0 (2015-11-17)

Features:
  - Partial IE11 & PlayReady support.  (Thanks, Jono!)
    - https://github.com/shaka-project/shaka-player/pull/176
    - *live and offline content not working*
    - *non-zero start times not working*
    - *IE11 fails to decode some test assets*
      - https://github.com/shaka-project/shaka-player/issues/224
  - Added support for setPlaybackStartTime on live streams.
    - https://github.com/shaka-project/shaka-player/pull/231
  - Improved support for live streaming corner cases.
    - https://github.com/shaka-project/shaka-player/issues/139
    - https://github.com/shaka-project/shaka-player/issues/140
    - https://github.com/shaka-project/shaka-player/issues/141
    - https://github.com/shaka-project/shaka-player/issues/145
    - https://github.com/shaka-project/shaka-player/issues/185
  - Now builds with three different configs by default.
    - Full build (all features enabled).
    - DASH MP4 VOD. (Only DASH w/ SegmentBase, no WebM.)
    - DASH MP4 live. (Only DASH w/o SegmentBase, no WebM.)
    - https://github.com/shaka-project/shaka-player/issues/116
  - Changed startNumber implementation to be more consistent.
    - https://github.com/shaka-project/shaka-player/issues/192
  - Added a new Promise polyfill for IE11.
  - Added support for WebM w/ unknown size in the Segment element.

Bugfixes:
  - Expired sessions (for example, when using key rotation) are now cleaned up.
    - https://github.com/shaka-project/shaka-player/issues/210
  - Manifests can now be reprocessed without an update when
    availabilityStartTime passes.
    - https://github.com/shaka-project/shaka-player/issues/172

Test app features:
  - Added Chromecast support to the demo app.
    (No changes to the library for this.)
    - https://github.com/shaka-project/shaka-player/issues/117
  - Removed force-prefixed feature for improved IE11 support.
    - https://github.com/shaka-project/shaka-player/issues/222
  - Added links to the project and the docs.

Broken Compatibility:
  - Removed Player methods deprecated since v1.5.0.
    - enableAdaptation
    - getAdaptationEnabled
    - setStreamBufferSize
    - getStreamBufferSize
    - setLicenseRequestTimeout
    - setMpdRequestTimeout
    - setRangeRequestTimeout
    - setPreferredLanguage
    - setRestrictions
    - getRestrictions
    - https://github.com/shaka-project/shaka-player/issues/203
    - https://github.com/shaka-project/shaka-player/issues/93
  - Removed support for the old-style ContentProtection callback, deprecated
    since v1.5.0.
    - https://github.com/shaka-project/shaka-player/issues/203
    - https://github.com/shaka-project/shaka-player/issues/71


## 1.5.2 (2015-11-12)

A roll-up of recent bugfixes.

Bugfixes:
  - Fixed timestamp correction for some live streams from Elemental.
    - https://github.com/shaka-project/shaka-player/issues/200
  - Fixed support for manifests with different PSSHs per Representation.
    - https://github.com/shaka-project/shaka-player/issues/229
  - Fixed support for ContentProtection elements at both AdaptationSet and
    Representation level in the same manifest.
    - https://github.com/shaka-project/shaka-player/issues/230
  - Fixed support for bound DrmInfo callbacks.
    - https://github.com/shaka-project/shaka-player/issues/227
  - Fixed the 'enabled' flag of text tracks when manipulated directly by the
    video element.
    - https://github.com/shaka-project/shaka-player/issues/214
  - Fixed buffering to use the correct goal (minBufferTime) when re-buffering.
    - https://github.com/shaka-project/shaka-player/issues/190
  - Fixed a broken link in the documentation.  (Thanks, Leandro.)
    - https://github.com/shaka-project/shaka-player/issues/217
    - https://github.com/shaka-project/shaka-player/pull/218

Test app features:
  - Added a Widevine-encrypted version of the Sintel 4k test asset.


## 1.5.1 (2015-10-07)

A roll-up of recent bugfixes.

Bugfixes:
  - Fixed a major memory leak introduced in 1.5.0.
    - https://github.com/shaka-project/shaka-player/issues/184
  - Deleting encrypted offline content now deletes persistent sessions.
    - https://github.com/shaka-project/shaka-player/issues/171
  - Static content using SegmentTemplate is now truncated at the Period's
    duration.
    - https://github.com/shaka-project/shaka-player/issues/187
    - https://github.com/shaka-project/shaka-player/issues/173
  - Key status error reporting is now more consistent and provides more
    information.
  - Reduced flakiness in some tests.
  - Requests used for clock sync no longer allow caching.
    - https://github.com/shaka-project/shaka-player/issues/191


## 1.5.0 (2015-09-17)

Features:
  - Added method to set playback start time.
    - https://github.com/shaka-project/shaka-player/issues/122
    - https://github.com/shaka-project/shaka-player/pull/123
  - Added a text-styling API.
    - https://github.com/shaka-project/shaka-player/issues/115
  - Added support for AdaptationSet groups.
    - https://github.com/shaka-project/shaka-player/issues/67
  - Added a new configuration API.
    - https://github.com/shaka-project/shaka-player/issues/93
  - License preprocessing can now modify HTTP method and server URL.
    - https://github.com/shaka-project/shaka-player/issues/134
    - https://github.com/shaka-project/shaka-player/issues/135
  - Added an API to load captions not specified in the manifest.
    - https://github.com/shaka-project/shaka-player/issues/133
  - Added support for live streams using SegmentList.
    - https://github.com/shaka-project/shaka-player/issues/88
  - Added support for multiple BaseURL elements for failover.
    - https://github.com/shaka-project/shaka-player/issues/68
  - Gave IAbrManager implementation the ability to clear the buffer when
    switching streams.
    - https://github.com/shaka-project/shaka-player/pull/144
  - Added setNetworkCallback API to DashVideoSource to modify network requests.
    - https://github.com/shaka-project/shaka-player/issues/148
  - Improved error reporting for unplayable content.
  - Added support for multiple DRM schemes per ContentProtection and simplified
    DRM scheme configuration.
    - https://github.com/shaka-project/shaka-player/issues/71
  - Improved documentation for license pre- and post-processing.
    - https://github.com/shaka-project/shaka-player/issues/137

Bugfixes:
  - Restricting all video tracks now fires an error event.
    - https://github.com/shaka-project/shaka-player/issues/179
    - https://github.com/shaka-project/shaka-player/issues/170
  - Changing text tracks now fires an adaptation event.
    - https://github.com/shaka-project/shaka-player/issues/147
  - Fixed bad interactions between pausing and negative playback rates.
    - https://github.com/shaka-project/shaka-player/issues/130
  - Fixed support for negative r values in SegmentTimeline.
    - https://github.com/shaka-project/shaka-player/issues/162
  - Fixed bugs that could cause infinite buffering for certain configurations.
    - https://github.com/shaka-project/shaka-player/issues/166
  - Fixed exceptions fired during rapid Player destroy().
    - https://github.com/shaka-project/shaka-player/issues/151
  - Fixed linting with conflicting globally-installed copy of linter library.
    - https://github.com/shaka-project/shaka-player/issues/153
  - Fixed support for SegmentTimelines with presentationTimeOffset.
    - https://github.com/shaka-project/shaka-player/issues/143
  - Fixed support for apps/content which specify multiple DRM scheme configs.
    - https://github.com/shaka-project/shaka-player/issues/177

Broken Compatibility:
  - Removed Player methods deprecated since v1.3.0.
    - getCurrentResolution
    - getCurrentTime
    - getDuration
    - getMuted
    - getVolume
    - play
    - pause
    - requestFullscreen
    - seek
    - setMuted
    - setVolume
    - https://github.com/shaka-project/shaka-player/issues/118

Deprecated:
  - The following methods on Player are deprecated in favor of
    configure()/getConfiguration() and will be removed in v1.6.0:
    - enableAdaptation
    - getAdaptationEnabled
    - setStreamBufferSize
    - getStreamBufferSize
    - setLicenseRequestTimeout
    - setMpdRequestTimeout
    - setRangeRequestTimeout
    - setPreferredLanguage
    - setRestrictions
    - getRestrictions
    - https://github.com/shaka-project/shaka-player/issues/93
  - A new two-argument ContentProtectionCallback has been added to
    DashVideoSource, and the old style is deprecated and will be removed
    in v1.6.0.
    - https://github.com/shaka-project/shaka-player/issues/71


## 1.4.2 (2015-09-04)

A roll-up of recent bugfixes.

Bugfixes:
  - Fix storage of duplicate session IDs for encrypted offline content.
  - Specify EME sessionTypes, required in newer EME draft.
    - https://github.com/shaka-project/shaka-player/issues/128
  - Fix regression in rewind support, once more working outside buffered range.
    - https://github.com/shaka-project/shaka-player/issues/165
  - Support renamed output protection errors from newer EME draft.
  - Fix seeking in custom controls on Android.
    - https://github.com/shaka-project/shaka-player/issues/164
  - Fix missing final chunk when storing certain videos for offline playback.
    - https://github.com/shaka-project/shaka-player/issues/157
  - Prevent crashing of module loaders which use 'define' but are not full AMD
    loaders.
    - https://github.com/shaka-project/shaka-player/issues/163

Test app features:
  - Added 'offline' URL param.


## 1.4.1 (2015-08-18)

A roll-up of recent bugfixes and small improvements.

Bugfixes:
  - An exception is no longer thrown from StreamVideoSource in uncompiled mode
    when the stream limits cannot be computed.
  - Fixed support for multiple encrypted audio tracks.
    - https://github.com/shaka-project/shaka-player/issues/112
  - Fixed support for manifests that use SegmentList with a single URL.
  - Fixed support for audio and video robustness settings in compiled mode.
  - The MPD 'main' property is now defined in the correct class.
  - The same initialization segment is no longer inserted multiple times into
    the SourceBuffer.
  - Removed a race in Stream that could stop AdaptationEvents from firing.
  - Stopped the compiler from renaming PersistentState and DistinctiveIdentifier
    enum values.
  - Removed a race in Player.getStats() that could cause NaN stats.
  - Fixed support to recover from failed segment requests.
    - https://github.com/shaka-project/shaka-player/issues/131
  - Made rewind, pause, play, and fast-forward consistent with normal video
    element behavior, the UI, and Player.setPlaybackRate().
    - https://github.com/shaka-project/shaka-player/issues/130
    - https://github.com/shaka-project/shaka-player/issues/138
  - Improved seek handling during stream startup.
    - https://github.com/shaka-project/shaka-player/issues/136
  - Unnecessary seeking events during stream startup are no longer fired.
    - https://github.com/shaka-project/shaka-player/issues/132
  - Segment fetches are no longer retried if the Stream has been destroyed.
    - https://github.com/shaka-project/shaka-player/issues/156
  - Fixed support for offline in compiled mode.

Features:
  - The version indicator on the demo page now displays the NPM version (if
    available) when the git version is unavailable.
  - Added support to clear the audio buffer when switching tracks.
    - https://github.com/shaka-project/shaka-player/issues/119
  - Added the ability to detect and recover from multiple buffered ranges.
    - https://github.com/shaka-project/shaka-player/issues/121
  - Improved error messages when persistent licenses are not supported.
    - https://github.com/shaka-project/shaka-player/issues/85

Testing:
  - Reduced test flakiness overall.
  - Certain (unavoidable) decode errors are now suppressed on Chrome Linux.
  - Added waitUntilBuffered() function to help reduce test flakiness.


## 1.4.0 (2015-07-06)

Code health release.  Major refactoring of streaming logic.

Bugfixes:
  - Overriding a license server URL in the test app no longer causes a PSSH
    from the MPD to be ignored.
  - Fixed possible event listener leak.
    - https://github.com/shaka-project/shaka-player/issues/109

Features:
  - Player.destroy() now returns a Promise.
  - DrmSchemeInfo now has distinctiveIdentifier, persistentState, and
    robustness parameters.
  - Clarified buffering event policies.
    - https://github.com/shaka-project/shaka-player/issues/77
  - Added a license pre-processor.
    - https://github.com/shaka-project/shaka-player/issues/62
  - Added support for the MPD Location element.
    - https://github.com/shaka-project/shaka-player/issues/65
  - Custom BandwidthEstimators can now allow XHR caching.
    - https://github.com/shaka-project/shaka-player/issues/76
  - Added support for startNumber of 0, per the recent DASH spec corrigendum.
    - https://github.com/shaka-project/shaka-player/issues/10
  - Added support for server certificate APIs through DrmSchemeInfo.
    - https://github.com/shaka-project/shaka-player/issues/84
  - Major refactor of streaming.  Switching representations is now faster and
    more flexible.  Live stream seek ranges are more accurate.
    - https://github.com/shaka-project/shaka-player/issues/51
  - XHR timeout is now runtime-configurable.
    - https://github.com/shaka-project/shaka-player/issues/50
  - Buffering goals are now runtime-configurable.
    - https://github.com/shaka-project/shaka-player/issues/49
  - Alternative IAbrManager implementations can now be injected at runtime.
    - https://github.com/shaka-project/shaka-player/issues/48

Test app features:
  - Added "buffered ahead" and "buffered behind" indicators.
    - https://github.com/shaka-project/shaka-player/issues/47
  - Converted cycle buttons into checkboxes so cycling can be stopped during
    playback.
    - https://github.com/shaka-project/shaka-player/issues/46
  - Test app now jumps to live when the user clicks on the time code in a live
    stream.
  - Added an example of a trick-play UI built on the Player API.
    - https://github.com/shaka-project/shaka-player/issues/54

Testing:
  - Disabled code coverage stats in unit tests by default.
    - https://github.com/shaka-project/shaka-player/issues/105
  - Split unit tests and integration tests into separate test runners.
    - https://github.com/shaka-project/shaka-player/issues/104
  - Added a Karma config file to make automated testing easier.
  - Added checks for offline features to the support-testing page.

Documentation:
  - Documented the fact that autoplay does not work on mobile, and why.
  - Documented error events and how to handle them.
    - https://github.com/shaka-project/shaka-player/issues/106
  - Documented browser support and porting.
    - https://github.com/shaka-project/shaka-player/issues/66
  - Documented Player APIs for trick play interface.
    - https://github.com/shaka-project/shaka-player/issues/54


## 1.3.2 (2015-07-06)

A roll-up of recent bugfixes.

Bugfixes:
  - Fixed case-sensitive scheme URI check in the test app.
  - Fixed support-testing page for very old browsers.
  - Fixed multi-lingual encrypted content.
    - https://github.com/shaka-project/shaka-player/issues/112
  - Fixed load-time exceptions in IE 9.
    - https://github.com/shaka-project/shaka-player/issues/87
    - https://github.com/shaka-project/shaka-player/pull/110


## 1.3.1 (2015-05-22)

A roll-up of recent bugfixes and small improvements.

Bugfixes:
  - Fixed some broken tests.
  - Fixed buffering states.
    - https://github.com/shaka-project/shaka-player/issues/61
  - Fixed fullscreen polyfill installation.
    - https://github.com/shaka-project/shaka-player/issues/81
  - Fixed handling of live content with minimumUpdatePeriod of 0.
    - https://github.com/shaka-project/shaka-player/pull/64
  - Fixed selection of live content (type=dynamic).
    - https://github.com/shaka-project/shaka-player/issues/69
    - https://github.com/shaka-project/shaka-player/issues/70
  - Fixed AJAX request timeouts.
    - https://github.com/shaka-project/shaka-player/issues/78
    - https://github.com/shaka-project/shaka-player/pull/79
  - Fixed spec compliance for polyfilled session expiration.
  - Fixed buffer time for offline playback.
  - Fixed offline API consistency.
    - https://github.com/shaka-project/shaka-player/issues/72

Features:
  - Refactored and updated support test page.
    - http://shaka-player-demo.appspot.com/support.html
  - Simplified polyfill installation. (shaka.polyfill.installAll)
  - New polyfill for CustomEvent.
  - Small improvements to browser compatibility.
    - (node.childNodes, node.textContent, currentScript, CSS fixes, etc.)
  - Documented clock sync and CORS issues with live content.
    - https://github.com/shaka-project/shaka-player/issues/53
  - Documented JRE requirements.
  - Test app now accepts a URL parameter to make ChromeCast testing easier.
    - https://github.com/shaka-project/shaka-player/issues/56
  - Stopped using deprecated methods in tests and tutorials.
    - https://github.com/shaka-project/shaka-player/issues/73
  - Added progress events for storing offline content.
  - Documented offline APIs.
    - https://github.com/shaka-project/shaka-player/issues/60


## 1.3.0 (2015-04-16)

Feature release, introducing live streaming and offline playback.

Bugfixes:
  - Fixed playback and buffering of streams whose index is inaccurate.
  - Fixed EME spec compliance.
    - https://github.com/shaka-project/shaka-player/issues/45
  - Fixed FakeEventTarget exception handling.
  - Fixed aggressive dead code stripping by the compiler.
  - Fixed a bug in which subtitles were enabled by default without a subtitle
    language match.

Features:
  - Added offline playback support.
    - https://github.com/shaka-project/shaka-player/issues/22
  - Added offline support for encrypted content (on platforms which support
    persistent licenses).
    - https://github.com/shaka-project/shaka-player/issues/23
  - Added live stream support.
    - https://github.com/shaka-project/shaka-player/issues/21
  - Added support for header-based clock synchronization.
  - Added support for inheriting Segment{Base,List,Template} across levels in
    MPDs.
  - Add polyfill support for fullscreen events.
  - Updated EME usage to the March 12 draft.
  - Added Player.getAdaptationEnabled().
    - https://github.com/shaka-project/shaka-player/pull/31
  - Added support for bandwidth restrictions and restrictions not based on
    license responses.
    - https://github.com/shaka-project/shaka-player/pull/36
  - Added support for requireJS and improved support for commonJS.
  - Sped up integration tests and improved test robustness.
  - Bandwidth estimates can now be persisted across playbacks.
  - Custom bandwidth estimator objects can now be injected into the Player.
  - Improved EME v0.1b polyfill consistency with native EME in Chrome.
  - Improved buffering and underflow mechanisms.
  - Improved error reporting if DRM info is missing.
  - Improved robustness in the face of HTTP 404 and 410 errors during segment
    fetch.
  - Improved documentation for Role tags and multilingual assets.

Test app features:
  - Example player controls in the test app.

Deprecated:
  - The following methods on Player are deprecated.  They will be removed in
    v1.4.0:
    - getCurrentResolution() (replace with video.videoWidth & video.videoHeight)
    - getCurrentTime()/seek() (replace with video.currentTime)
    - getDuration() (replace with video.duration)
    - getMuted()/setMuted() (replace with video.muted)
    - getVolume()/setVolume() (replace with video.volume)
    - play() (replace with video.play)
    - pause() (replace with video.pause)
    - requestFullscreen() (replace with video.requestFullscreen())

Broken compatibility:
  - The license postprocessor callback is no longer given a Restrictions
    argument.  See Player.getRestrictions()/setRestrictions().
  - The suppressMultipleEvents flag has been dropped from DrmSchemeInfo, which
    changes the constructor signature.  This flag interfered with key rotation.


## 1.2.3 (2015-04-07)

A roll-up of recent bugfixes.

Bugfixes:
  - Fixed consistency of setPlaybackRate(0).
  - Fixed support for mp4a.40.5 audio content.
  - Improved rewind accuracy.
  - Fixed decode of query parameters in content URLs.
    - https://github.com/shaka-project/shaka-player/pull/40
  - Fixed FakeEventTarget for Chrome 43+.
  - Removed flaky assertion in EME polyfill.
  - Made AbrManager less aggressive.
  - Fixed EME spec compatibility and encrypted playback in Chrome 43+.
    - https://github.com/shaka-project/shaka-player/issues/45

Features:
  - Added support for module.exports.
    - https://github.com/shaka-project/shaka-player/pull/35

Test app features:
  - Added a new 4k test asset.


## 1.2.2 (2015-03-11)

Bugfixes:
  - Version 1.2.1 had multiple issues with its version numbering.  These
    are now corrected, but npm requires unique version numbers to publish.
    Version 1.2.1 has been pulled from npm.
    - https://github.com/shaka-project/shaka-player/issues/30

Features:
  - Added getAdaptationEnabled() to Player.
    - https://github.com/shaka-project/shaka-player/issues/29


## 1.2.1 (2015-03-10)

A roll-up of recent bugfixes, plus a few minor additions to the test app.
Branched from v1.2.0.

Bugfixes:
  - Try to recover from a streaming failure.
    - https://github.com/shaka-project/shaka-player/issues/28
  - Ignore spurious error events from the video tag.
  - Update docs WRT content restrictions and folder organization.
  - Fix clearkey errors in Chrome 42+.
  - Fix computation of the number of segments in MpdProcessor.
    - Only affects assets which use SegmentTemplate with a duration attribute.

Test app features:
  - Rename a confusing asset.
  - Add a button to cycle video tracks.
  - Support MPD init data overrides for all DRM schemes.


## 1.2.0 (2015-02-24)

Lots of internal refactoring and bugfixes, and a few new features.

Bugfixes:
  - Buffer eviction no longer causes hangs on seek.
    - https://github.com/shaka-project/shaka-player/issues/15
  - Adaptation no longer causes hangs on looping and seeking backward.
    - https://github.com/shaka-project/shaka-player/issues/26
  - StreamStats no longer shows null for width and height before adaptation.
    - https://github.com/shaka-project/shaka-player/issues/16
  - Content with differing start times for the audio & video streams no longer
    exhibits A/V sync issues.
    - https://github.com/shaka-project/shaka-player/issues/17
  - DrmSchemeInfo's suppressMultipleEncryptedEvents flag is now correctly
    honored regardless of the timing of events.
  - Calculations for the $Time$ placeholder in MPD SegmentTemplates has been
    corrected.
  - The test app no longer causes mixed-content errors when served over HTTPS.
  - Small mistakes in URLs and asset names in the test app have been corrected.
  - Windows checkouts now have consistent newline style.
    - https://github.com/shaka-project/shaka-player/issues/12
  - Windows build steps documented.
    - https://github.com/shaka-project/shaka-player/issues/13

Features:
  - The isTypeSupported polyfill has been removed and all EME APIs have been
    updated to the [Feb 9 2015 EME spec].
    - https://github.com/shaka-project/shaka-player/issues/2
  - Gaps and overlaps in SegmentTimeline are no longer treated as an error.
    Large gaps/overlaps will still generate a warning.
    - https://github.com/shaka-project/shaka-player/issues/24
  - HDCP-related failures are now translated into error events in Chrome 42+.
    - https://github.com/shaka-project/shaka-player/issues/14
  - The MPD Role tag is now supported as a way of indicating the main
    AdaptationSet for the purposes of language matching.
    - https://github.com/shaka-project/shaka-player/issues/20
  - More detail added to AJAX error events.
    - https://github.com/shaka-project/shaka-player/issues/18
  - The Player now dispatches buffering events.
    - https://github.com/shaka-project/shaka-player/issues/25
  - Parser support for the new v1 PSSH layout, including parsing of key IDs.
    - https://github.com/shaka-project/shaka-player/issues/19
  - The fullscreen polyfill has been updated and expanded.
  - DashVideoSource refactored to split DASH-independent functionality into the
    generic StreamVideoSource.  This should simplify the implementation of new
    video sources for non-DASH manifest formats.  (Contributions welcome.)
  - Automatic build numbering has been added, with version numbers appearing in
    the test app UI.
  - The library has been published on [npm] and [cdnjs].
  - Release version numbering follows the [semantic versioning spec].

Broken Compatibility:
  - System IDs in PSSH objects are now hex strings instead of raw strings.

[Feb 9 2015 EME spec]: https://bit.ly/EmeFeb15
[npm]: https://www.npmjs.com/package/shaka-player
[cdnjs]: https://cdnjs.com/libraries/shaka-player
[semantic versioning spec]: http://semver.org/


## 1.1 (2015-01-14)

Maintenance release.

Bugfixes:
  - The enabled flag for text tracks is now preserved when switching tracks.
    Player.enableTextTrack() is no longer required after selectTextTrack().
    - https://github.com/shaka-project/shaka-player/issues/1
  - The documentation for Player methods enableTextTrack, setPreferredLanguage,
    and getCurrentResolution has been corrected.
    - https://github.com/shaka-project/shaka-player/issues/3
    - https://github.com/shaka-project/shaka-player/issues/4
    - https://github.com/shaka-project/shaka-player/issues/6
  - The AbrManager class is now correctly destroyed.
    - https://github.com/shaka-project/shaka-player/issues/5
  - Clearkey support for Chrome 41+ has been fixed.
    - https://github.com/shaka-project/shaka-player/issues/8
  - A new polyfill has been added to compensate for Chrome 41+'s removal of
    MediaKeys.isTypeSupported.
    - https://github.com/shaka-project/shaka-player/issues/7
  - Several unused internal methods have been removed from the codebase.
  - Fixed a failing assertion in one of the MediaKeys polyfills.
  - Fixed failing code coverage analysis and related parse errors in several
    tests.
  - Fixed support for MPDs with SegmentTemplate@duration and
    MPD@mediaPresentationDuration, but no Period@duration attribute.
    - https://github.com/shaka-project/shaka-player/issues/9

Features:
  - Tests are now checked for style.
  - Tests have been expanded to increase coverage and exercise more Player
    features:
    - playback rate
    - stats
    - language preference
    - license restrictions
    - WebM/VP9
    - error events
  - Integration tests now run much faster.
  - MediaKeys polyfills have received minor updates to improve compatibility
    with Chrome 41.
  - New sample assets and code in app.js to demonstrate how to use a PSSH from
    an MPD to override what's in the content itself.

Broken Compatibility:
  - None!


## 1.0 (2014-12-19)

First public release.

Bugfixes:
  - Text tracks are no longer ignored in MPD manifests.
  - Adaptation decisions are now quicker and more reliable.
    - (This bug was more noticeable on faster internet connections.)
  - Playback no longer gets "stuck" on certain content.
  - Playback no longer gets "stuck" after certain seek patterns.
  - Player get/select/enable methods can now be called without a video source.
  - A \<video\> tag's "videoWidth"/"videoHeight" attributes now update
    correctly on Chrome >= 40.
  - Manual adaptation while paused no longer unpauses the video.
  - Credentials can now be used on cross-domain license requests.
  - Range headers are no longer sent for all segment requests.
    - (This fixes issues with IIS.)
  - A missing declaration of getVideoPlaybackQuality() has been added.
  - The compiled code no longer pollutes the global namespace.
  - DASH manifests using \<SegmentList\> are now parsed correctly.
  - Formatting has been fixed in the "Shaka Player Development" tutorial.

Features:
  - The Player is now reusable.  You can call load() multiple times without
    calling destroy().
  - The JS linter is now included in sources, fixing compatibility issues
    between versions.
  - The test suite now includes playback integration tests.
  - The Player has been updated to support the 01 Dec 2014 draft of the EME
    specification.
  - The loader in load.js no longer makes assumptions about app.js.  You can
    now use load.js to bootstrap other applications.
  - The test app now uses less screen real estate.
  - All custom events have been documented, and a new tutorial has been added
    to demonstrate how they can be used.
  - The Player now has a support-check API to determine if the browser has all
    necessary features for playback.
  - Sample code in the tutorials is now marked up to highlight changes from the
    previous sample.
  - Code coverage in unit tests has been increased.
  - Flakiness in unit tests has been reduced.
  - DASH manifests using \<SegmentTemplate\> without a segment index or segment
    timeline are now supported.
  - The DASH "presentationTimeOffset" attribute is now supported.

Broken Compatibility:
  - ContentProtectionCallback no longer takes a "mimeType" argument.
  - DrmSchemeInfo constructor no longer takes a "mimeType" argument.
  - DrmSchemeInfo constructor's "initData" argument is now an object with
    fields instead of a Uint8Array.
  - DrmSchemeInfo now takes a "withCredentials" argument.
  - lib.js has been renamed to shaka-player.compiled.js.


## 0.1b (2014-11-21)

Private beta release.
