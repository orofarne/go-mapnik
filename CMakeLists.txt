cmake_minimum_required(VERSION 2.8)

project(go-mapnik C CXX)

# mapnik c binding
add_subdirectory(vendor)

# mapnig config
execute_process(COMMAND mapnik-config --cflags
	OUTPUT_VARIABLE MAPNIK-CONFIG-CFLAGS OUTPUT_STRIP_TRAILING_WHITESPACE)
message(STATUS "MAPNIK-CONFIG-CFLAGS: ${MAPNIK-CONFIG-CFLAGS}")
execute_process(COMMAND mapnik-config --libs
	OUTPUT_VARIABLE MAPNIK-CONFIG-LIBS OUTPUT_STRIP_TRAILING_WHITESPACE)
message(STATUS "MAPNIK-CONFIG-LIBS: ${MAPNIK-CONFIG-LIBS}")
execute_process(COMMAND mapnik-config --fonts
	OUTPUT_VARIABLE MAPNIK-CONFIG-FONTS OUTPUT_STRIP_TRAILING_WHITESPACE)
message(STATUS "MAPNIK-CONFIG-FONTS: ${MAPNIK-CONFIG-FONTS}")
execute_process(COMMAND mapnik-config --input-plugins
	OUTPUT_VARIABLE MAPNIK-CONFIG-INPUT-PLUGINS OUTPUT_STRIP_TRAILING_WHITESPACE)
message(STATUS "MAPNIK-CONFIG-INPUT-PLUGINS: ${MAPNIK-CONFIG-INPUT-PLUGINS}")

# boost
find_package( Boost 1.48.0 COMPONENTS system REQUIRED )
include_directories(${Boost_INCLUDE_DIRS})

# cgo config
set(LDFLAGS "${LDFLAGS} $ENV{GO_MAPNIK_LDFLAGS} ${MAPNIKC-LDFLAGS} ${MAPNIK-CONFIG-LIBS}")
message(STATUS "LDFLAGS: ${LDFLAGS}")

configure_file(mapnik.go.in
	${CMAKE_CURRENT_BINARY_DIR}/mapnik.go)
configure_file(mapnik_test.go.in
	${CMAKE_CURRENT_BINARY_DIR}/mapnik_test.go)
