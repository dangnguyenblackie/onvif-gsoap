CMAKE_MINIMUM_REQUIRED(VERSION 3.4.1)
project(test_gSOAP)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-DWITH_OPENSSL -DWITH_DOM")

include_directories(/usr/local/include/
                    /usr/local/include/custom
                    /usr/local/include/plugin
                    /usr/local/include/soapProxy
        )
link_directories(/usr/local/lib)


include_directories(${PROJECT_SOURCE_DIR}/3rdparty/include)
link_directories("${PROJECT_SOURCE_DIR}/3rdparty/lib")

add_subdirectory(${PROJECT_SOURCE_DIR}/deviceBinding)