# ****************************************************************************
#  Copyright (C) 2015 Karol Roslaniec <mariacpp@roslaniec.net>
# 
#  This library is free software; you can redistribute it and/or
#  modify it under the terms of the GNU Lesser General Public
#  License as published by the Free Software Foundation; either
#  version 2.1 of the License, or (at your option) any later version.
#
#  This library is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
#  Lesser General Public License for more details.
#
#  You should have received a copy of the GNU Lesser General Public
#  License along with this library; if not see <http://www.gnu.org/licenses>
#  or write to the Free Software Foundation, Inc.,
#  51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA
# ****************************************************************************

CMAKE_MINIMUM_REQUIRED (VERSION 2.8)
PROJECT(mariacpp)

SET(CPACK_PACKAGE_VERSION_MAJOR 1)
SET(CPACK_PACKAGE_VERSION_MINOR 0)
SET(CPACK_PACKAGE_VERSION_PATCH 1)
SET(CPACK_PACKAGE_VERSION "${CPACK_PACKAGE_VERSION_MAJOR}.${CPACK_PACKAGE_VERSION_MINOR}.${CPACK_PACKAGE_VERSION_PATCH}")


INCLUDE(${CMAKE_SOURCE_DIR}/cmake/FindMariaDB.cmake)

set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
find_package(Threads REQUIRED)
if (CMAKE_USE_PTHREADS_INIT)
  set(CMAKE_C_FLAGS ${CMAKE_C_FLAGS} "-pthread")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")
endif()
  

enable_testing()
add_subdirectory(mariacpp)
add_subdirectory(src)
add_subdirectory(test)


SET(CPACK_GENERATOR "TGZ")
SET(CPACK_SOURCE_GENERATOR "TGZ")
SET(CPACK_PACKAGE_VENDOR "LINKO")
SET(CPACK_PACKAGE_DESCRIPTION
  "MariaCpp. A library for connecting to MariaDB and MySQL servers")
STRING(TOLOWER ${CMAKE_SYSTEM_NAME} system_name)
SET(CPACK_PACKAGE_FILE_NAME
  "mariacpp-${CPACK_PACKAGE_VERSION}-${system_name}-${CMAKE_SYSTEM_PROCESSOR}")
SET(CPACK_SOURCE_PACKAGE_FILE_NAME
  "mariacpp-${CPACK_PACKAGE_VERSION}-src")
SET(CPACK_INCLUDE_TOPLEVEL_DIRECTORY 1)
SET(CPACK_SOURCE_IGNORE_FILES
  .hg/
  .hgignore
  build/
  ~$
  )
INCLUDE(CPack)
