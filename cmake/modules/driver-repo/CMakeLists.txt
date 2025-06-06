#
# Copyright (C) 2013-2022 Draios Inc dba Sysdig.
#
# This file is part of sysdig .
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

cmake_minimum_required(VERSION 3.5.1)

project(driver-repo NONE)

include(ExternalProject)
message(STATUS "Driver version: ${DRIVER_VERSION}")

ExternalProject_Add(
  driver
  URL "https://github.com/falcosecurity/libs/archive/${DRIVER_VERSION}.tar.gz"
  URL_HASH "${DRIVER_CHECKSUM}"
  CONFIGURE_COMMAND ""
  BUILD_COMMAND ""
  INSTALL_COMMAND ""
  TEST_COMMAND ""
  PATCH_COMMAND sh -c "mv ./driver ../driver.tmp && rm -rf ./* && mv ../driver.tmp/* ."
)
