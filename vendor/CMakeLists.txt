include(ExternalProject)

# mapnik-c-api
ExternalProject_Add(mapnik-c-api
# GIT_REPOSITORY "https://github.com/orofarne/mapnik-c-api.git"
  URL "https://github.com/orofarne/mapnik-c-api/archive/master.zip"
  URL_MD5 "66604fff5856b2df4a1d4ab9dccefffe"
  DOWNLOAD_DIR ${CMAKE_CURRENT_BINARY_DIR}
  SOURCE_DIR ${CMAKE_CURRENT_BINARY_DIR}/mapnik-c-api
  BUILD_IN_SOURCE 1
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make
  TEST_COMMAND make test
  INSTALL_COMMAND ""
)

set(MAPNIKC-CFLAGS "-I${CMAKE_CURRENT_BINARY_DIR}/mapnik-c-api" PARENT_SCOPE)
set(MAPNIKC-LDFLAGS
	"${CMAKE_CURRENT_BINARY_DIR}/mapnik-c-api/libmapnik_c.a -lboost_system -lstdc++" PARENT_SCOPE)
