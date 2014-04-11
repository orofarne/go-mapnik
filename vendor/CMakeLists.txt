include(ExternalProject)

# mapnik-c-api
ExternalProject_Add(mapnik-c-api
  URL "https://github.com/orofarne/mapnik-c-api/archive/cmake.zip"
  DOWNLOAD_DIR ${CMAKE_CURRENT_BINARY_DIR}
  SOURCE_DIR ${CMAKE_CURRENT_BINARY_DIR}/mapnik-c-api
  BUILD_IN_SOURCE 1
  CONFIGURE_COMMAND cmake -DSTATICLIB=ON .
  BUILD_COMMAND make
  TEST_COMMAND make test
  INSTALL_COMMAND ""
)

set(MAPNIKC-CFLAGS "-I${CMAKE_CURRENT_BINARY_DIR}/mapnik-c-api" PARENT_SCOPE)
set(MAPNIKC-LDFLAGS
	"${CMAKE_CURRENT_BINARY_DIR}/mapnik-c-api/libmapnik_c_static.a -lboost_system -lstdc++" PARENT_SCOPE)
