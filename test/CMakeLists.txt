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


# MESSAGE(STATUS "MariaDB library: ${MARIADB_LIBRARY}")
# MESSAGE(STATUS "MariaDB includes: ${MARIADB_INCLUDE_DIR}")

SET(TEST_DB_URI "tcp://localhost:3306/test" CACHE STRING "DB URI")
SET(TEST_DB_USER "test" CACHE STRING "DB user")
SET(TEST_DB_PASSWD "" CACHE STRING "DB password")

add_test(Connect connect)
add_test(MultiThreads threads)
add_test(SimpleQuery query)
add_test(PrepStmt-C prepstmtc)
add_test(PrepStmt-C++ prepstmtcpp)
add_test(Example example)

SET(TMP "TEST_DB_URI=${TEST_DB_URI}")
SET(TMP "${TMP};TEST_DB_USER=${TEST_DB_USER}")
SET(TMP "${TMP};TEST_DB_PASSWD=${TEST_DB_PASSWD}")
SET_TESTS_PROPERTIES(
  Connect MultiThreads SimpleQuery PrepStmt-C PrepStmt-C++ Example
  PROPERTIES ENVIRONMENT "${TMP}")

link_libraries(
  mariacpp
  ${MARIADB_LIBRARY})  
include_directories(
  ${MARIADB_INCLUDE_DIR}
  ${CMAKE_SOURCE_DIR})

add_executable(connect connect.cpp)
add_executable(threads threads.cpp)
add_executable(query query.cpp)
add_executable(prepstmtc prepstmtc.cpp)
add_executable(prepstmtcpp prepstmtcpp.cpp)
add_executable(example example.cpp)
