# CMakeList.txt : CMake project for RedisDB, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("RedisDB")

# Add source to this project's executable.
set(Boost_INCLUDE_DIR C:/boost_1_81_0) #C:/boost_1_81_0
set(Boost_LIBRARY_DIR C:/boost_1_81_0/stage/lib) # C:/boost_1_81_0/stage/lib
find_package(Boost REQUIRED COMPONENTS system)
add_executable(RedisDB RedisDB.cpp RedisDB.h)
target_link_libraries(RedisDB PRIVATE Boost::system)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET RedisDB PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
