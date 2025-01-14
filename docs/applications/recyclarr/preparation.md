Here is the exact configuration I used in the video


## Sonarr v3 Setup
> I no longer use this, I use the v4 option below

```
# Starter config to use with Recyclarr. Most values are set to "reasonable defaults". Update the
# values below as needed for your instance. You will be required to update the API Key and URL for
# each instance you want to use.
#
# Many optional settings have been omitted to keep this template simple.
#
# For more details on the configuration, see the Configuration Reference on the wiki here:
# https://github.com/recyclarr/recyclarr/wiki/Configuration-Reference

# Configuration specific to Sonarr
sonarr:
  # Set the URL/API Key to your actual instance
  - base_url: http://sonarr-custom-app.ix-sonarr.svc.cluster.local:8989
    api_key: sdfgsadfhadfhadfgsdfgs

    # Quality definitions from the guide to sync to Sonarr. Choice: anime, series, hybrid
    quality_definition: anime

    # Release profiles from the guide to sync to Sonarr.
    # You can optionally add tags and make negative scores strictly ignored
    release_profiles:
      # Series
      - trash_ids:
          - EBC725268D687D588A20CBC5F97E538B # Low Quality Groups
          - 1B018E0C53EC825085DD911102E2CA36 # Release Sources (Streaming Service)
          - 71899E6C303A07AF0E4746EFF9873532 # P2P Groups + Repack/Proper
        tags: [non-anime]
      # Anime (Uncomment below if you want it)
      - trash_ids:
          - d428eda85af1df8904b4bbe4fc2f537c # Anime - First release profile
          - 6cd9e10bb5bb4c63d2d7cd3279924c7b # Anime - Second release profile
        tags: [anime]
      # Optionals
      - trash_ids: [76e060895c5b8a765c310933da0a5357] # Optionals
        filter:
          exclude:
            - cec8880b847dd5d31d29167ee0112b57 # Golden rule
            - ea83f4740cec4df8112f3d6dd7c82751 # Prefer Season Packs
        tags: [non-anime]


# Configuration specific to Radarr.
radarr:
  # Set the URL/API Key to your actual instance
  - base_url: http://radarrnl-custom-app.ix-radarrnl.svc.cluster.local:7878
    api_key: sadfasdgsdbvsdfv

    # Which quality definition in the guide to sync to Radarr. Only choice right now is 'movie'
    quality_definition:
      type: movie

    # Set to 'true' to automatically remove custom formats from Radarr when they are removed from
    # the guide or your configuration. This will NEVER delete custom formats you manually created!
    delete_old_custom_formats: true

    custom_formats:
      # A list of custom formats to sync to Radarr. Must match the "trash_id" in the guide JSON.
      - trash_ids:
      
          # Audio Advanced
          - 496f355514737f7d83bf7aa4d24f8169 # TrueHD ATMOS
          - 2f22d89048b01681dde8afe203bf2e95 # DTS X
          - 417804f7f2c4308c1f4c5d380d4c4475 # ATMOS (undefined)
          - 1af239278386be2919e1bcee0bde047e # DD+ ATMOS
          - 3cafb66171b47f226146a0770576870f # TrueHD
          - dcf3ec6938fa32445f590a4da84256cd # DTS-HD MA
          - a570d4a0e56a2874b64e5bfa55202a1b # FLAC
          - e7c2fcae07cbada050a0af3357491d7b # PCM
          - 8e109e50e0a0b83a5098b056e13bf6db # DTS-HD HRA
          - 185f1dd7264c4562b9022d963ac37424 # DD+
          - f9f847ac70a0af62ea4a08280b859636 # DTS-ES
          - 1c1a4c5e823891c75bc50380a6866f73 # DTS
          - 240770601cc226190c367ef59aba7463 # AAC
          - c2998bd0d90ed5621d8df281e839436e # DD
          - 6ba9033150e7896bdc9ec4b44f2b230f # MP3
          - a061e2e700f81932daf888599f8a8273 # Opus
          
          #Audio Channels
          - b124be9b146540f8e62f98fe32e49a2a # 1.0 Mono
          - 89dac1be53d5268a7e10a19d3c896826 # 2.0 Stereo
          - 205125755c411c3b8622ca3175d27b37 # 3.0 Sound
          - 373b58bd188fc00c817bd8c7470ea285 # 4.0 Sound
          - 77ff61788dfe1097194fd8743d7b4524 # 5.1 Surround
          - 6fd7b090c3f7317502ab3b63cc7f51e3 # 6.1 Surround
          - e77382bcfeba57cb83744c9c5449b401 # 7.1 Surround
          - f2aacebe2c932337fe352fa6e42c1611 # 9.1 Surround
          
          #HDR Formats
          - e23edd2482476e595fb990b12e7c609c # DV HDR10
          - 58d6a88f13e2db7f5059c41047876f00 # DV
          - 55d53828b9d81cbe20b02efd00aa0efd # DV HLG
          - a3e19f8f627608af0211acd02bf89735 # DV SDR
          - b974a6cd08c1066250f1f177d7aa1225 # HDR10+
          - dfb86d5941bc9075d6af23b09c2aeecd # HDR10
          - e61e28db95d22bedcadf030b8f156d96 # HDR
          - 2a4d9069cc1fe3242ff9bdaebed239bb # HDR (undefined)
          - 08d6d8834ad9ec87b1dc7ec8148e7a1f # PQ
          - 9364dd386c9b4a1100dde8264690add7 # HLG
          
          #Movie Versions
          - 0f12c086e289cf966fa5948eac571f44 # Hybrid
          - 570bc9ebecd92723d2d21500f4be314c # Remaster
          - eca37840c13c6ef2dd0262b141a5482f # 4K Remaster
          - e0c07d59beb37348e975a930d5e50319 # Criterion Collection
          - e9001909a4c88013a359d0b9920d7bea # Theatrical Cut
          - 957d0f44b592285f26449575e8b1167e # Special Edition
          - eecf3a857724171f968a66cb5719e152 # IMAX
          - 9f6cbff8cfe4ebbc1bde14c7b7bec0de # IMAX Enhanced

          #Unwanted
          - ed38b889b31be83fda192888e2286d83 # BR-DISK
          - 90a6f9a284dff5103f6346090e6280c8 # LQ
          - b8cd450cbfa689c0259a01d9e29ba3d6 # 3D
#          - dc98083864ea246d05a42df0d05f81cc # x265 (HD)
          
          #Optional
          - b6832f586342ef70d9c128d40c07b872 # Bad Dual Groups
          - 923b6abef9b17f937fab56cfcf89e1f1 # DV (WEBDL)
          - 90cedc1fea7ea5d11298bebd3d1d3223 # EVO (no WEBDL)
#          - ae9b7c9ebde1f3bd336a8cbd1ec4c5e5 # No-RlsGroup
          - 7357cf5161efbf8c4d5d0c30b4815ee2 # Obfuscated
          - 5c44f52a8714fdd79bb4d98e2673be1f # Retags
          - 839bea857ed2c0a8e084f3cbdbd65ecb # x265 (no HDR/DV)
          
          #Misc
          - e7718d7a3ce595f289bfee26adc178f5 # Repack/Proper
          - ae43b294509409a6a13919dedd4764c4 # Repack2
          - 2899d84dc9372de3408e6d8cc18e9666 # x264
          - 9170d55c319f4fe40da8711ba9d8050d # x265
#          - 0d91270a7255a1e388fa85e959f359d8 # FreeLeech
#          - 9de657fd3d327ecf144ec73dfe3a3e9a # Dutch Groups
          - ff86c4326018682f817830ced463332b # MPEG2
          - 4b900e171accbfb172729b63323ea8ca # Multi
          
          #HQ Source Groups
          - 3a3ff47579026e76d6504ebea39390de # Remux Tier 01
          - 9f98181fe5a3fbeb0cc29340da2a468a # Remux Tier 02
          - ed27ebfef2f323e964fb1f61391bcb35 # HD Bluray Tier 01
          - c20c8647f2746a1f4c4262b0fbbeeeae # HD Bluray Tier 02
          - c20f169ef63c5f40c2def54abaf4438e # WEB Tier 01
          - 403816d65392c79236dcb6dd591aeda4 # WEB Tier 02
          - af94e0fe497124d1f9ce732069ec8c3b # WEB Tier 03
#          - ffebc267e9c98d3d383f37b238550079 # UHD (W4NK3R)
#          - 403f3f6266b90439cacc1e07cae4dc2d # HQ-Remux
#          - 1c7d7b04b15cc53ea61204bebbcc1ee2 # HQ
#          - 26fa26253af4001701fedb56cec376dc # HQ-WEBDL
#          - 4da96773192a51cf96178212642ca3bb # UHD (LEGi0N)
#          - 96848626e1570c122aba8642fe2714a2 # UHD (HQMUX)
#          - ac49fdbf6a662d380556f40ff4856f29 # UHD (WEBDV)
#          - afeb99e5db09290546f742503ce1cdb6 # UHD (DON)
#          - 66aaa8c2c03c0191a95f0d655b75ab10 # UHD (CtrlHD)
#          - 65be7ce5ec4c31e684c7b8368b8bd6bb # UHD (SPHD)
#          - 5153ec7413d9dae44e24275589b5e944 # BHDStudio
#          - ff5bc9e8ce91d46c997ca3ac6994d6f8 # FraMeSToR
#          - 8cd3ac70db7ac318cf9a0e01333940a4 # SiC

          #Streaming Services
          - c9fd353f8f5f1baf56dc601c4cb29920 # PCOK
          - 526d445d4c16214309f0fd2b3be18a89 # Hulu
          - 2a6039655313bf5dab1e43523b62c374 # MA
          - e36a0ba1bc902b26ee40818a1d59b8bd # PMTP
          - 84272245b2988854bfb76a16e60baea5 # DSNP
          - 5763d1b0ce84aff3b21038eea8e9b8ad # HMAX
          - 40e9380490e748672c2522eaaeb692f7 # ATVP
          - b3b3a6ac74ecbd56bcdbefa4799fb9df # AMZN
          - 170b1d363bd8516fbf3a3eb05d4faff6 # NF

          # IDK
#          - 820b09bb9acbfde9c35c71e0e565dad8 # 1080p
#          - b2be17d608fc88818940cd1833b0b24c # 720p
#          - fb392fb0d61a010ae38e49ceaa24a1ef # 2160p
#          - 0a3f082873eb454bde444150b70253cc # Extras
#          - 1d433e1e075704f1a8a1ae3e1c371460 # Flights (no IMAX)
        quality_profiles:
          - name: HD - 720p/1080p

### Anime ###
      - trash_ids:
          - fb3ccc5d5cc8f77c9055d4cb4561dded # Anime BD Tier 01 (Top SeaDex Muxers)
          - 66926c8fa9312bc74ab71bf69aae4f4a # Anime BD Tier 02 (SeaDex Muxers)
          - fa857662bad28d5ff21a6e611869a0ff # Anime BD Tier 03 (SeaDex Muxers)
          - f262f1299d99b1a2263375e8fa2ddbb3 # Anime BD Tier 04 (SeaDex Muxers)
          - ca864ed93c7b431150cc6748dc34875d # Anime BD Tier 05 (Remuxes)
          - 9dce189b960fddf47891b7484ee886ca # Anime BD Tier 06 (FanSubs)
          - 1ef101b3a82646b40e0cab7fc92cd896 # Anime BD Tier 07 (P2P/Scene)
          - 6115ccd6640b978234cc47f2c1f2cadc # Anime BD Tier 08 (Mini Encodes)
          - 8167cffba4febfb9a6988ef24f274e7e # Anime Web Tier 01 (Muxers)
          - 8526c54e36b4962d340fce52ef030e76 # Anime Web Tier 02 (Top FanSubs)
          - de41e72708d2c856fa261094c85e965d # Anime Web Tier 03 (Official Subs)
          - 9edaeee9ea3bcd585da9b7c0ac3fc54f # Anime Web Tier 04 (Official Subs)
          - 22d953bbe897857b517928f3652b8dd3 # Anime Web Tier 05 (FanSubs)
          - a786fbc0eae05afe3bb51aee3c83a9d4 # Anime Web Tier 06 (FanSubs)
          - 06b6542a47037d1e33b15aa3677c2365 # Anime Raws
          - b0fdc5897f68c9a68c70c25169f77447 # Anime LQ Groups
          - 064af5f084a0a24458cc8ecd3220f93f # Uncensored
          - c259005cbaeb5ab44c06eddb4751e70c # v0
          - 5f400539421b8fcf71d51e6384434573 # v1
          - 3df5e6dfef4b09bb6002f732bed5b774 # v2
          - db92c27ba606996b146b57fbe6d09186 # v3
          - d4e5e842fad129a3c097bdb2d20d31a0 # v4
          - 60f6d50cbd3cfc3e9a8c00e3a30c3114 # VRV
          - a5d148168c4506b55cf53984107c396e # 10bit
          - 4a3b087eea2ce012fcc1ce319259a3be # Anime Dual Audio          
#          - b23eae459cc960816f2d6ba84af45055 # Dubs Only
          - b0fdc5897f68c9a68c70c25169f77447 # Anime LQ Groups
        quality_profiles:
          - name: Anime
```


## Sonarr v4 Setup

```
# yaml-language-server: $schema=https://raw.githubusercontent.com/recyclarr/recyclarr/master/schemas/config-schema.json

# A starter config to use with Recyclarr. Most values are set to "reasonable defaults". Update the
# values below as needed for your instance. You will be required to update the API Key and URL for
# each instance you want to use.
#
# Many optional settings have been omitted to keep this template simple. Note that there's no "one
# size fits all" configuration. Please refer to the guide to understand how to build the appropriate
# configuration based on your hardware setup and capabilities.
#
# For any lines that mention uncommenting YAML, you simply need to remove the leading hash (`#`).
# The YAML comments will already be at the appropriate indentation.
#
# For more details on the configuration, see the Configuration Reference on the wiki here:
# https://recyclarr.dev/wiki/reference/config-reference

# Configuration specific to Sonarr
sonarr:
  instance_name:
    # Set the URL/API Key to your actual instance
    base_url: http://sonarrnll-custom-app.ix-sonarrnll.svc.cluster.local:8989
    api_key: API_KEY_HERE

    # Quality Definition Settings
    quality_definition:
      type: anime

    # Custom Format Settings
    delete_old_custom_formats: true
    custom_formats:
      - trash_ids:

          # [No Category]
          - 290078c8b266272a5cc8e251b5e2eb0b # 1080p
          - 1bef6c151fa35093015b0bfef18279e5 # 2160p
#          - 180c1f36241300dc27ff42918a81e9e3 # FR Anime Tier Optional


          # Audio Advanced #1
          - b6fbafa7942952a13e17e2b1152b539a # ATMOS (undefined)
          - 63487786a8b01b7f20dd2bc90dd4a477 # DD+
          - 4232a509ce60c4e208d13825b7c06264 # DD+ ATMOS
          - 5964f2a8b3be407d083498e4459d05d0 # DTS
          - 9d00418ba386a083fbf4d58235fc37ef # DTS X
          - c1a25cd67b5d2e08287c957b1eb903ec # DTS-ES
          - c429417a57ea8c41d57e6990a8b0033f # DTS-HD MA
          - 1808e4b9cee74e064dfae3f1db99dbfe # TrueHD
          - 0d7824bb924701997f874e7ff7d4844a # TrueHD ATMOS

          # Audio Advanced #2
          - a50b8a0c62274a7c38b09a9619ba9d86 # AAC
          - dbe00161b08a25ac6154c55f95e6318d # DD
          - cfa5fbd8f02a86fc55d8d223d06a5e1f # DTS-HD HRA
          - 851bd64e04c9374c51102be3dd9ae4cc # FLAC
          - 3e8b714263b26f486972ee1e0fe7606c # MP3
          - 28f6ef16d61e2d1adfce3156ed8257e3 # Opus
          - 30f70576671ca933adbdcfc736a69718 # PCM

          # Audio Channels
          - bd6dd5e043aa27ff4696a08d011c7d96 # 1.0 Mono
          - 834e534f103938853ffced4203b53e72 # 2.0 Stereo
          - 42cba7e38c7947a6d1d0a62580ee6d62 # 3.0 Sound
          - 1895195e84767de180653914ce207245 # 4.0 Sound
          - 3fbafa924f361e66fbc6187af82dfa85 # 5.1 Surround
          - 9fb6d778592c293467437593ef394bf1 # 6.1 Surround
          - 204c8c3e7315bb0ea81332774fa888d6 # 7.1 Surround
          - a377864de6228b252d6e28962673cedd # 9.1 Surround

          # French Audio Version
#          - 84f0acbda9c0c9de783894fb66df25aa # FanSUB
#          - ea0bb4b6ba388992fad1092703b5ff7b # FastSUB
#          - 4721382d9ee05f1b4967a25e75072911 # French Audio
#          - 2f6e84efc47246ec9071e311e71c4953 # Multi-Audio
#          - 7982e39789f17864f57b11f1996844f4 # Multi-French
#          - 0ce1e39a4676c6692ce47935278dac76 # VFB
#          - 2c29a39a4fdfd6d258799bc4c09731b9 # VFF
#          - b6816a0e1d4b64bf3550ad3b74b009b6 # VFI
#          - 7a7f4e4f58bd1058440236d033a90b67 # VFQ
#          - 7ae924ee9b2f39df3283c6c0beb8a2aa # VOF
#          - 07a32f77690263bb9fda1842db7e273f # VOSTFR
#          - 82085412d9a53ba8d8e46fc624eb701d # VQ

          # French Source Groups
#          - 44b6c964dad997577d793fd004a39224 # FR Anime FanSub
#          - db13a377f7afb29975ea39470434d2ef # FR Anime Tier 01
#          - 4e6134a384dbc0ef166234cc0e45d26d # FR Anime Tier 02
#          - d844321db5e126d2e7e46152f0706532 # FR HD Bluray Tier 01
#          - 3ba797e5dc13af4b8d9bb25e83d90de2 # FR LQ
#          - b8e91cc8fb2bd96468fab74730c30d18 # FR Remux Tier 01
#          - 2f3422339d185eb227a324644a2fbfca # FR Scene Groups
#          - ddb8eaa9c85a549c50034d280539d54d # FR WEB Tier 01
#          - a4c51febd4d8b2a0db10a3c974f21d92 # FR WEB Tier 02
#          - dbfc0a4b5cb4cbd693311c4482ae9683 # FR WEB Tier 03

          # HDR Formats
          - 6d0d8de7b57e35518ac0308b0ddf404e # DV
          - 7878c33f1963fefb3d6c8657d46c2f0a # DV HDR10
          - 1f733af03141f068a540eec352589a89 # DV HLG
          - 27954b0a80aab882522a88a4d9eae1cd # DV SDR
          - 3e2c4e748b64a1a1118e0ea3f4cf6875 # HDR
          - bb019e1cd00f304f80971c965de064dc # HDR (undefined)
          - 3497799d29a085e2ac2df9d468413c94 # HDR10
          - a3d82cbef5039f8d295478d28a887159 # HDR10+
          - 17e889ce13117940092308f48b48b45b # HLG
          - 2a7e3be05d3861d6df7171ec74cad727 # PQ

          # HQ Source Groups
          - d6819cba26b1a6508138d25fb5e32293 # HD Bluray Tier 01
          - c2216b7b8aa545dc1ce8388c618f8d57 # HD Bluray Tier 02
          - 9965a052eb87b0d10313b1cea89eb451 # Remux Tier 01
          - 8a1d0c3d7497e741736761a1da866a2e # Remux Tier 02
          - d0c516558625b04b363fa6c5c2c7cfd4 # WEB Scene
          - e6258996055b9fbab7e9cb2f75819294 # WEB Tier 01
          - 58790d4e2fdcd9733aa7ae68ba2bb503 # WEB Tier 02
          - d84935abd3f8556dcd51d4f27e22d0a6 # WEB Tier 03

          # Misc
          - 4aee45b0868229c4fbd8bad3e315f1d0 # MPEG2
          - 7ba05c6e0e14e793538174c679126996 # Multi
          - eb3d5cc0a2be0db205fb823640db6a3c # Repack v2
          - 44e7c4de10ae50265753082e5dc76047 # Repack v3
          - ec8fa7296b64e8cd390a1600981f3923 # Repack/Proper
          - cddfb4e32db826151d97352b8e37c648 # x264
          - c9eafd50846d299b862ca9bb6ea91950 # x265

          # Optional
          - 15a05bc7c1a36e2b57fd628f8977e2fc # AV1
          - 32b367365729d530ca1c124a0b180c64 # Bad Dual Groups
          - ef4963043b0987f8485bc9106f16db38 # DV (FEL)
          - 9b27ab6498ec0f31a3353992e19434ca # DV (WEBDL)
          - 0dad0a507451acddd754fe6dc3a7f5e7 # HDR10+ Boost
          - 82d40da2bc6923f41e14394075dd4b03 # No-RlsGroup
          - e1a997ddb54e3ecbfe06341ad323c458 # Obfuscated
          - 06d66ab109d4d2eddb2794d21526d140 # Retags
          - 2016d1676f5ee13a5b7257ff86ac9a93 # SDR
#          - 1b3994c551cbb92a2c781af061f4ab44 # Scene
          - 3bc5f395426614e155e585a2f056cdf1 # Season Pack
          - 9b64dff695c2115facf1b6ea59c9bd07 # x265 (no HDR/DV)

          # Series Versions
          - 3a4127d8aa781b44120d907f2cd62627 # Hybrid
          - b735f09d3c025cbb7d75a5d38325b73b # Remaster

          # Streaming Services
          - d660701077794679fd59e8bdf4ce3a29 # AMZN
          - f67c9ca88f463a48346062e8ad07713f # ATVP
          - f27d46a831e6b16fa3fee2c4e5d10984 # CANAL+
          - 77a7b25585c18af08f60b1547bb9b4fb # CC
          - 36b72f59f4ea20aad9316f475f2d9fbb # DCU
          - 89358767a60cc28783cdc3d0be9388a4 # DSNP
          - 7a235133c87f7da4c8cccceca7e3c7a6 # HBO
          - a880d6abc21e7c16884f3ae393f84179 # HMAX
          - f6cce30f1733d5c8194222a7507909bb # HULU
          - d34870697c9db575f17700212167be23 # NF
          - b2b980877494b560443631eb1f473867 # NLZ
          - 1656adc6d7bb2c8cca6acfb6592db421 # PCOK
          - c67a75ae4a1715f2bb4d492755ba4195 # PMTP
          - 3ac5d84fce98bab1b531393e9c82f467 # QIBI
          - c30d2958827d1867c73318a5a2957eb1 # RED
          - b0d6195c23ae254932da00512db7e8a8 # RTBF
          - 0455d6519a550dbf648c97b56e7231d2 # SALTO
          - ae58039e1319178e6be73caab5c42166 # SHO
          - 1efe8da11bfd74fbbcd4d8117ddb9213 # STAN
          - 5d2317d99af813b6529c7ebf01c83533 # VDL
          - 0ac24a2a68a9700bcb7eeca8e5cd644c # iT

          # Unwanted
          - 85c61753df5da1fb2aab6f2a47426b09 # BR-DISK
          - 9c11cd3f07101cdba90a2d81cf0e56b4 # LQ
#          - 47435ece6b99a0b477caf360e79ba0bb # x265 (HD)
        quality_profiles:
          - name: Non-Anime


### Anime ###
      - trash_ids:
          # Anime Misc/Streaming Services
          - d54cd2bf1326287275b56bccedb72ee2 # ADN
          - 7dd31f3dee6d2ef8eeaa156e23c3857e # B-Global
          - 4c67ff059210182b59cdd41697b8cb08 # Bilibili
          - 3e0b26604165f463f3e8e192261e7284 # CR
          - 1284d18e693de8efe0fe7d6b3e0b9170 # FUNi
          - 570b03b3145a25011bf073274a407259 # HIDIVE
          - 44a8ee6403071dd7b8a3a8dd3fe8cb20 # VRV
          - e5e6405d439dcd1af90962538acd4fe0 # WKN
          - d2d7b8a9d39413da5f44054080e028a3 # v0
          - 273bd326df95955e1b6c26527d1df89b # v1
          - 228b8ee9aa0a609463efca874524a6b8 # v2
          - 0e5833d3af2cc5fa96a0c29cd4477feb # v3
          - 4fc15eeb8f2f9a749f918217d4234ad8 # v4

          # Anime Source Groups
          - 949c16fe0a8147f50ba82cc2df9411c9 # Anime BD Tier 01 (Top SeaDex Muxers)
          - ed7f1e315e000aef424a58517fa48727 # Anime BD Tier 02 (SeaDex Muxers)
          - 096e406c92baa713da4a72d88030b815 # Anime BD Tier 03 (SeaDex Muxers)
          - 30feba9da3030c5ed1e0f7d610bcadc4 # Anime BD Tier 04 (SeaDex Muxers)
          - 545a76b14ddc349b8b185a6344e28b04 # Anime BD Tier 05 (Remuxes)
          - 25d2afecab632b1582eaf03b63055f72 # Anime BD Tier 06 (FanSubs)
          - 0329044e3d9137b08502a9f84a7e58db # Anime BD Tier 07 (P2P/Scene)
          - c81bbfb47fed3d5a3ad027d077f889de # Anime BD Tier 08 (Mini Encodes)
          - e3515e519f3b1360cbfc17651944354c # Anime LQ Groups
          - b4a1b3d705159cdca36d71e57ca86871 # Anime Raws
          - e0014372773c8f0e1bef8824f00c7dc4 # Anime Web Tier 01 (Muxers)
          - 19180499de5ef2b84b6ec59aae444696 # Anime Web Tier 02 (Top FanSubs)
          - c27f2ae6a4e82373b0f1da094e2489ad # Anime Web Tier 03 (Official Subs)
          - 4fd5528a3a8024e6b49f9c67053ea5f3 # Anime Web Tier 04 (Official Subs)
          - 29c2a13d091144f63307e4a8ce963a39 # Anime Web Tier 05 (FanSubs)
          - dc262f88d74c651b12e9d90b39f6c753 # Anime Web Tier 06 (FanSubs)
          # Anime Optional
          - b2550eb333d27b75833e25b8c2557b38 # 10bit
          - 418f50b10f1907201b6cfdf881f467b7 # Anime Dual Audio
#          - 9c14d194486c4014d422adc64092d794 # Dubs Only
          - 026d5aadd1a6b4e550b134cb6c72b3ca # Uncensored
        quality_profiles:
          - name: Anime





# Configuration specific to Radarr.
radarr:
  instance_name:
    # Set the URL/API Key to your actual instance
    base_url: http://radarrnl-custom-app.ix-radarrnl.svc.cluster.local:7878
    api_key: API_KEY_HERE

    # Which quality definition in the guide to sync to Radarr. Only choice right now is 'movie'
    quality_definition:
      type: movie

    # Set to 'true' to automatically remove custom formats from Radarr when they are removed from
    # the guide or your configuration. This will NEVER delete custom formats you manually created!
    delete_old_custom_formats: true
    custom_formats:
      - trash_ids:

          # [No Category]
          - 820b09bb9acbfde9c35c71e0e565dad8 # 1080p
          - fb392fb0d61a010ae38e49ceaa24a1ef # 2160p
          - b2be17d608fc88818940cd1833b0b24c # 720p
          - 5153ec7413d9dae44e24275589b5e944 # BHDStudio
          - 0a3f082873eb454bde444150b70253cc # Extras
          - ff5bc9e8ce91d46c997ca3ac6994d6f8 # FraMeSToR
          - 8cd3ac70db7ac318cf9a0e01333940a4 # SiC

          # Audio Advanced #1
          - 417804f7f2c4308c1f4c5d380d4c4475 # ATMOS (undefined)
          - 185f1dd7264c4562b9022d963ac37424 # DD+
          - 1af239278386be2919e1bcee0bde047e # DD+ ATMOS
          - 1c1a4c5e823891c75bc50380a6866f73 # DTS
          - 2f22d89048b01681dde8afe203bf2e95 # DTS X
          - f9f847ac70a0af62ea4a08280b859636 # DTS-ES
          - dcf3ec6938fa32445f590a4da84256cd # DTS-HD MA
          - 3cafb66171b47f226146a0770576870f # TrueHD
          - 496f355514737f7d83bf7aa4d24f8169 # TrueHD ATMOS

          # Audio Advanced #2
          - 240770601cc226190c367ef59aba7463 # AAC
          - c2998bd0d90ed5621d8df281e839436e # DD
          - 8e109e50e0a0b83a5098b056e13bf6db # DTS-HD HRA
          - a570d4a0e56a2874b64e5bfa55202a1b # FLAC
          - 6ba9033150e7896bdc9ec4b44f2b230f # MP3
          - a061e2e700f81932daf888599f8a8273 # Opus
          - e7c2fcae07cbada050a0af3357491d7b # PCM

          # Audio Channels
          - b124be9b146540f8e62f98fe32e49a2a # 1.0 Mono
          - 89dac1be53d5268a7e10a19d3c896826 # 2.0 Stereo
          - 205125755c411c3b8622ca3175d27b37 # 3.0 Sound
          - 373b58bd188fc00c817bd8c7470ea285 # 4.0 Sound
          - 77ff61788dfe1097194fd8743d7b4524 # 5.1 Surround
          - 6fd7b090c3f7317502ab3b63cc7f51e3 # 6.1 Surround
          - e77382bcfeba57cb83744c9c5449b401 # 7.1 Surround
          - f2aacebe2c932337fe352fa6e42c1611 # 9.1 Surround

          # French Audio Version
#          - 6d27683346c78d6a3f772e30877910a7 # French Audio
#          - 72b1548df1ac3175ca105a9ce7043c91 # Multi-Audio
#          - d5f3a1afdb77e6b95e489f7654532d04 # Multi-French
#          - b3fb499641d7b3c2006be1d9eb014cb3 # VFB
#          - 404c08fd0bd67f39b4d8e5709319094e # VFF
#          - 52772f1cad6b5d26c2551f79bc538a50 # VFI
#          - b6ace47331a1d3b77942fc18156f6df6 # VFQ
#          - 4cafa20d5584f6ba1871d1b8941aa3cb # VOF
#          - 9172b2f683f6223e3a1846427b417a3d # VOSTFR
#          - 95aa50f71a01c82354a7a2b385f1c4d8 # VQ

          # French Source Groups
#          - 5322da05b19d857acc1e75be3edf47b3 # FR HD Bluray Tier 01
#          - 57f34251344be2e283fc30e00e458be6 # FR HD Bluray Tier 02
#          - 48f031e76111f17ea94898f4cdc34fdc # FR LQ
#          - 5583260016e0b9f683f53af41fb42e4a # FR Remux Tier 01
#          - 9019d81307e68cd4a7eb06a567e833b8 # FR Remux Tier 02
#          - 0d94489c0d5828cd3bf9409d309fb32b # FR Scene Groups
#          - 64f8f12bbf7472a6ccf838bfd6b5e3e8 # FR UHD Bluray Tier 01
#          - 0dcf0c8a386d82e3f2d424189af14065 # FR UHD Bluray Tier 02
#          - 9790a618cec1aeac8ce75601a17ea40d # FR WEB Tier 01
#          - 3c83a765f84239716bd5fd2d7af188f9 # FR WEB Tier 02

          # HDR Formats
          - 58d6a88f13e2db7f5059c41047876f00 # DV
          - e23edd2482476e595fb990b12e7c609c # DV HDR10
          - 55d53828b9d81cbe20b02efd00aa0efd # DV HLG
          - a3e19f8f627608af0211acd02bf89735 # DV SDR
          - e61e28db95d22bedcadf030b8f156d96 # HDR
          - 2a4d9069cc1fe3242ff9bdaebed239bb # HDR (undefined)
          - dfb86d5941bc9075d6af23b09c2aeecd # HDR10
          - b974a6cd08c1066250f1f177d7aa1225 # HDR10+
          - 9364dd386c9b4a1100dde8264690add7 # HLG
          - 08d6d8834ad9ec87b1dc7ec8148e7a1f # PQ

          # HQ Release Groups
          - ed27ebfef2f323e964fb1f61391bcb35 # HD Bluray Tier 01
          - c20c8647f2746a1f4c4262b0fbbeeeae # HD Bluray Tier 02
          - 3a3ff47579026e76d6504ebea39390de # Remux Tier 01
          - 9f98181fe5a3fbeb0cc29340da2a468a # Remux Tier 02
          - 4d74ac4c4db0b64bff6ce0cffef99bf0 # UHD Bluray Tier 01
          - a58f517a70193f8e578056642178419d # UHD Bluray Tier 02
          - e71939fae578037e7aed3ee219bbe7c1 # UHD Bluray Tier 03
          - c20f169ef63c5f40c2def54abaf4438e # WEB Tier 01
          - 403816d65392c79236dcb6dd591aeda4 # WEB Tier 02
          - af94e0fe497124d1f9ce732069ec8c3b # WEB Tier 03

          # Misc
#          - 9de657fd3d327ecf144ec73dfe3a3e9a # Dutch Groups
#          - 0d91270a7255a1e388fa85e959f359d8 # FreeLeech
          - ff86c4326018682f817830ced463332b # MPEG2
          - 4b900e171accbfb172729b63323ea8ca # Multi
          - e7718d7a3ce595f289bfee26adc178f5 # Repack/Proper
          - ae43b294509409a6a13919dedd4764c4 # Repack2
          - 2899d84dc9372de3408e6d8cc18e9666 # x264
          - 9170d55c319f4fe40da8711ba9d8050d # x265

          # Movie Versions
          - eca37840c13c6ef2dd0262b141a5482f # 4K Remaster
          - e0c07d59beb37348e975a930d5e50319 # Criterion Collection
          - 0f12c086e289cf966fa5948eac571f44 # Hybrid
          - eecf3a857724171f968a66cb5719e152 # IMAX
          - 9f6cbff8cfe4ebbc1bde14c7b7bec0de # IMAX Enhanced
          - 9d27d9d2181838f76dee150882bdc58c # Masters of Cinema
          - 09d9dd29a0fc958f9796e65c2a8864b4 # Open Matte
          - 570bc9ebecd92723d2d21500f4be314c # Remaster
          - 957d0f44b592285f26449575e8b1167e # Special Edition
          - e9001909a4c88013a359d0b9920d7bea # Theatrical Cut

          # Optional
          - cae4ca30163749b891686f95532519bd # AV1
          - b6832f586342ef70d9c128d40c07b872 # Bad Dual Groups
          - f700d29429c023a5734505e77daeaea7 # DV (FEL)
          - 923b6abef9b17f937fab56cfcf89e1f1 # DV (WEBDL)
          - 90cedc1fea7ea5d11298bebd3d1d3223 # EVO (no WEBDL)
          - b17886cb4158d9fea189859409975758 # HDR10+ Boost
          - c465ccc73923871b3eb1802042331306 # Line/Mic Dubbed
          - ae9b7c9ebde1f3bd336a8cbd1ec4c5e5 # No-RlsGroup
          - 7357cf5161efbf8c4d5d0c30b4815ee2 # Obfuscated
          - 5c44f52a8714fdd79bb4d98e2673be1f # Retags
          - 9c38ebb7384dada637be8899efa68e6f # SDR
          - f537cf427b64c38c8e36298f657e4828 # Scene
          - 839bea857ed2c0a8e084f3cbdbd65ecb # x265 (no HDR/DV)

          # Streaming Services
          - b3b3a6ac74ecbd56bcdbefa4799fb9df # AMZN
          - 40e9380490e748672c2522eaaeb692f7 # ATVP
          - cc5e51a9e85a6296ceefe097a77f12f4 # BCORE
          - 84272245b2988854bfb76a16e60baea5 # DSNP
          - 509e5f41146e278f9eab1ddaceb34515 # HBO
          - 5763d1b0ce84aff3b21038eea8e9b8ad # HMAX
          - 526d445d4c16214309f0fd2b3be18a89 # Hulu
          - 2a6039655313bf5dab1e43523b62c374 # MA
          - 170b1d363bd8516fbf3a3eb05d4faff6 # NF
          - c9fd353f8f5f1baf56dc601c4cb29920 # PCOK
          - e36a0ba1bc902b26ee40818a1d59b8bd # PMTP
          - bf7e73dd1d85b12cc527dc619761c840 # Pathe
          - c2863d2a50c9acad1fb50e53ece60817 # STAN

          # Unwanted
          - b8cd450cbfa689c0259a01d9e29ba3d6 # 3D
          - ed38b889b31be83fda192888e2286d83 # BR-DISK
          - 90a6f9a284dff5103f6346090e6280c8 # LQ
          - bfd8eb01832d646a0a89c4deb46f8564 # Upscaled
#          - dc98083864ea246d05a42df0d05f81cc # x265 (HD)
        quality_profiles:
          - name: Non-Anime


### Anime ###
      - trash_ids:
          # Anime
          - fb3ccc5d5cc8f77c9055d4cb4561dded # Anime BD Tier 01 (Top SeaDex Muxers)
          - 66926c8fa9312bc74ab71bf69aae4f4a # Anime BD Tier 02 (SeaDex Muxers)
          - fa857662bad28d5ff21a6e611869a0ff # Anime BD Tier 03 (SeaDex Muxers)
          - f262f1299d99b1a2263375e8fa2ddbb3 # Anime BD Tier 04 (SeaDex Muxers)
          - ca864ed93c7b431150cc6748dc34875d # Anime BD Tier 05 (Remuxes)
          - 9dce189b960fddf47891b7484ee886ca # Anime BD Tier 06 (FanSubs)
          - 1ef101b3a82646b40e0cab7fc92cd896 # Anime BD Tier 07 (P2P/Scene)
          - 6115ccd6640b978234cc47f2c1f2cadc # Anime BD Tier 08 (Mini Encodes)
          - b0fdc5897f68c9a68c70c25169f77447 # Anime LQ Groups
          - 06b6542a47037d1e33b15aa3677c2365 # Anime Raws
          - 8167cffba4febfb9a6988ef24f274e7e # Anime Web Tier 01 (Muxers)
          - 8526c54e36b4962d340fce52ef030e76 # Anime Web Tier 02 (Top FanSubs)
          - de41e72708d2c856fa261094c85e965d # Anime Web Tier 03 (Official Subs)
          - 9edaeee9ea3bcd585da9b7c0ac3fc54f # Anime Web Tier 04 (Official Subs)
          - 22d953bbe897857b517928f3652b8dd3 # Anime Web Tier 05 (FanSubs)
          - a786fbc0eae05afe3bb51aee3c83a9d4 # Anime Web Tier 06 (FanSubs)
          - 60f6d50cbd3cfc3e9a8c00e3a30c3114 # VRV
          - c259005cbaeb5ab44c06eddb4751e70c # v0
          - 5f400539421b8fcf71d51e6384434573 # v1
          - 3df5e6dfef4b09bb6002f732bed5b774 # v2
          - db92c27ba606996b146b57fbe6d09186 # v3
          - d4e5e842fad129a3c097bdb2d20d31a0 # v4

          # Anime Optional
          - a5d148168c4506b55cf53984107c396e # 10bit
          - 4a3b087eea2ce012fcc1ce319259a3be # Anime Dual Audio
#          - b23eae459cc960816f2d6ba84af45055 # Dubs Only
          - 064af5f084a0a24458cc8ecd3220f93f # Uncensored
        quality_profiles:
          - name: Anime
```
