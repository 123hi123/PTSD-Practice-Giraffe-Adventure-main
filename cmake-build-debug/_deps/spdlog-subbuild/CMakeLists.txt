# Distributed under the OSI-approved BSD 3-Clause License.  See accompanying
# file Copyright.txt or https://cmake.org/licensing for details.

cmake_minimum_required(VERSION 3.30.5)

# Reject any attempt to use a toolchain file. We must not use one because
# we could be downloading it here. If the CMAKE_TOOLCHAIN_FILE environment
# variable is set, the cache variable will have been initialized from it.
unset(CMAKE_TOOLCHAIN_FILE CACHE)
unset(ENV{CMAKE_TOOLCHAIN_FILE})

# We name the project and the target for the ExternalProject_Add() call
# to something that will highlight to the user what we are working on if
# something goes wrong and an error message is produced.

project(spdlog-populate NONE)



include(ExternalProject)
ExternalProject_Add(spdlog-populate
                     "UPDATE_DISCONNECTED" "False" "DOWNLOAD_EXTRACT_TIMESTAMP" "FALSE" "EXTERNALPROJECT_INTERNAL_ARGUMENT_SEPARATOR" "URL" "https://github.com/gabime/spdlog/archive/refs/tags/v1.10.0.zip" "URL_HASH" "MD5=031565384b28f29e44c6e7fb247ad48a"
                    SOURCE_DIR          "C:/Users/joego/OneDrive/Desktop/PTSD-Practice-Giraffe-Adventure-main/PTSD/lib/spdlog"
                    BINARY_DIR          "C:/Users/joego/OneDrive/Desktop/PTSD-Practice-Giraffe-Adventure-main/cmake-build-debug/_deps/spdlog-build"
                    CONFIGURE_COMMAND   ""
                    BUILD_COMMAND       ""
                    INSTALL_COMMAND     ""
                    TEST_COMMAND        ""
                    USES_TERMINAL_DOWNLOAD  YES
                    USES_TERMINAL_UPDATE    YES
                    USES_TERMINAL_PATCH     YES
)


