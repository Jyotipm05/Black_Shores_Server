cmake_minimum_required(VERSION 3.31)

set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file")
#It's important to set the toolchain file before the project command
#Here "VCPKG_ROOT" is an environment variable that points to the root of your vcpkg installation

project(Tethis_System VERSION 0.1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_SCAN_FOR_MODULES ON)
#set(CMAKE_CXX_EXTENSIONS OFF)

find_package(wt CONFIG REQUIRED COMPONENTS)
find_package(openssl CONFIG REQUIRED)
find_package(boost CONFIG REQUIRED COMPONENTS filesystem system)
find_package(curl CONFIG REQUIRED)

target_link_libraries(your-target
        wt::wt
        Boost::boost
        OpenSSL::SSL
        OpenSSL::Crypto
        CURL::libcurl
)

add_executable(${PROJECT_NAME}
    src/main.cpp
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    wt::wt
    OpenSSL::SSL
    OpenSSL::Crypto
    Boost::filesystem
    Boost::system
    CURL::libcurl
)
