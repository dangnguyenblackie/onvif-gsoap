CMAKE_MINIMUM_REQUIRED(VERSION 3.4.1)
project(OnvifClient_gSOAP)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-DWITH_OPENSSL -DWITH_DOM")

include_directories(${PROJECT_SOURCE_DIR}/include
        ${PROJECT_SOURCE_DIR}/include/custom
        ${PROJECT_SOURCE_DIR}/include/plugin
        ${PROJECT_SOURCE_DIR}/include/soapProxy
        )

aux_source_directory(${PROJECT_SOURCE_DIR}/gsoap src)
aux_source_directory(${PROJECT_SOURCE_DIR}/gsoap/custom custom_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/gsoap/plugin plugin_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/gsoap/soapProxy soapProxy_src)

include_directories(${PROJECT_SOURCE_DIR}/3rdparty/include)
link_directories("${PROJECT_SOURCE_DIR}/3rdparty/lib/openssl")

set(sourcecode
        ${src}
        ${custom_src}
        ${plugin_src}
        ${soapProxy_src}
        )

add_library(gsoap SHARED ${sourcecode})

install(TARGETS gsoap
        LIBRARY DESTINATION /usr/local/lib)

install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/
        DESTINATION /usr/local/include)