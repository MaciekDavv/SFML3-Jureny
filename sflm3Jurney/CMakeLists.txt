cmake_minimum_required(VERSION 3.20)
project(Pong)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)

FetchContent_Declare(
  sfml
  GIT_REPOSITORY https://github.com/SFML/SFML.git
  GIT_TAG master     # lub konkretny commit
)

FetchContent_MakeAvailable(sfml)

file(GLOB SOURCES *.cpp)

foreach(FILE ${SOURCES})
    get_filename_component(BINNAME ${FILE} NAME_WE)
    add_executable(${BINNAME} ${FILE})
    target_link_libraries(${BINNAME} PRIVATE sfml-graphics sfml-window sfml-system)
endforeach(FILE)

#add_executable(pong main.cpp)