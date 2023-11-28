cmake_minimum_required(VERSION 3.16)

project(sercomm-ui VERSION 0.1.0)

set(CGI_BIN sercomm.cgi)

set(CGI_SRCS
  src/main.c  
  src/sc_data.c  
  src/sc_language.c  
  src/sc_login.c 
  src/sc_pages.c
  src/sc_reset.c
  src/sc_user.c
  src/sc_util.c
)

add_executable(${CGI_BIN} ${CGI_SRCS})
## Uncomment when you need to add libraries.
# target_link_libraries(${CGI_BIN} some-library)

target_include_directories(${CGI_BIN} PRIVATE include)

# set_target_properties(${CGI_BIN} PROPERTIES VERSION 0.1.0)

install(TARGETS ${CGI_BIN} DESTINATION ${CMAKE_PREFIX_INSTALL}/www/sercomm_ui/cgi-bin)
install(
  DIRECTORY 
  files/sercomm_ui
  DESTINATION 
  ${CMAKE_PREFIX_INSTALL}/www)
install(
  FILES
  files/40-sercomm-ui.conf
  DESTINATION
  ${CMAKE_PREFIX_INSTALL}/etc/lighttpd/conf.d)
