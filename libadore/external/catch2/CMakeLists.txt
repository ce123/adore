# SPDX-FileCopyrightText: 2019 German Aerospace Center (DLR)
#
# SPDX-License-Identifier: EPL-2.0

cmake_minimum_required(VERSION 3.13)

project(catch2download VERSION 0.0.1
             DESCRIPTION "testing library"
             HOMEPAGE_URL "https://github.com/catchorg/Catch2")

include(GNUInstallDirs)

set(catch2download_dir ${CMAKE_CURRENT_SOURCE_DIR}/catch2_external_sources)
if(NOT EXISTS ${catch2download_dir})
message(NOTICE "catch2 sources must be downloaded")
  find_package(Git REQUIRED)
  execute_process(
      COMMAND ${GIT_EXECUTABLE} clone --branch v2.10.2 https://github.com/catchorg/Catch2.git ${catch2download_dir}
  )
endif()

add_subdirectory("${catch2download_dir}" "${CMAKE_CURRENT_BINARY_DIR}/catch2")