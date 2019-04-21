cmake_minimum_required(VERSION 3.4.1)
include_directories(crypto curve25519 ed25519 playfair plist/plist )


aux_source_directory(. play_src)
set(DIR_SRCS ${play_src})

add_library( play-lib
        SHARED
        ${DIR_SRCS}
        )

if(UNIX AND NOT APPLE)
target_link_libraries( play-lib
		dns_sd
		pthread
        crypto
        curve25519
        ed25519
        playfair
        plist )
else()
target_link_libraries( play-lib
		pthread
        crypto
        curve25519
        ed25519
        playfair
        plist )
endif()
        