cmake_minimum_required(VERSION 3.13)
project(transitive-object-library-link-issue VERSION 1.0.0 LANGUAGES C)

add_library(objA OBJECT a.c)

add_library(objB OBJECT b.c)
target_link_libraries(objB PUBLIC objA)

# Should link with 'a.o', since 'objA' is "linked" by 'objB'
add_executable(main main.c)
target_link_libraries(main objB)
