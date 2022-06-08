# SPDX-FileCopyrightText: 2022 Alexander Dahl <post@lespocky.de>
# SPDX-License-Identifier: GPL-3.0-or-later
cmake_minimum_required(VERSION 3.1)
project(glowing-tribble
	LANGUAGES CXX
)

find_package(PkgConfig REQUIRED)
pkg_check_modules(PC_HTTPSERVER REQUIRED IMPORTED_TARGET
				  libhttpserver>=0.19)
#pkg_check_modules(PC_MICROHTTPD REQUIRED IMPORTED_TARGET
#				  libmicrohttpd>=0.9.52)

add_executable(hello_world
	hello_world.cpp
)

set_target_properties(hello_world PROPERTIES
	CXX_STANDARD			11
	CXX_STANDARD_REQUIRED	TRUE
)

target_link_libraries(hello_world
	PRIVATE
		PkgConfig::PC_HTTPSERVER
#		PkgConfig::PC_MICROHTTPD
)
