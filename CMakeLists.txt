cmake_minimum_required(VERSION 2.6)

project(sfp-nodewatcher-agent C)
add_definitions(-Os -Wall -Werror --std=gnu99 -Wmissing-declarations)

set(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")

set(SOURCES
  main.c
)

set(LIBS
  nodewatcher-agent-common
)

add_library(sfp_module MODULE main.c)
target_link_libraries(sfp_module ${LIBS})
set_target_properties(sfp_module PROPERTIES OUTPUT_NAME sfp PREFIX "")

install(TARGETS sfp_module LIBRARY DESTINATION lib/nodewatcher-agent)
