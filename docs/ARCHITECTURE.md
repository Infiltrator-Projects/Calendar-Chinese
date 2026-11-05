# Traditional Chinese Lunisolar Calendar — source boundaries

This repo owns its traditional Chinese chronology and ICU-specific provider adapter. Common 1.19.81 (a99ef676b0e43c7e645c81756e3fd38be0a54406) owns generic arithmetic, civil coordinates, dynamic-library services and the public provider ABI. Builds link its authoritative static archive from the exact submodule. Former private copies of Common code and headers have been eliminated; independent provider fixtures and native offline installers remain required.
