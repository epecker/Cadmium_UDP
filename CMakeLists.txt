cmake_minimum_required(VERSION 3.20)

project(cadmium_udp_models)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Setup configured header file
configure_file("${CMAKE_SOURCE_DIR}/include/config.hpp.in" "${CMAKE_SOURCE_DIR}/include/config.hpp")

# Cadmium requires this to be set to run in parallel
add_compile_definitions(CADMIUM_EXECUTE_CONCURRENT)

#RT-Cadmium Definitions needed in order to use the real-time clock.
add_compile_definitions(RT_WIN)
add_compile_definitions(RT_DEVS)
#The value of this definition can be changed to anything other than -1.
add_compile_definitions(MISSED_DEADLINE_TOLERANCE=-10)

# These definitions are required to use Boost thread pools
add_compile_definitions(BOOST_THREAD_PROVIDES_FUTURE_CONTINUATION)
add_compile_definitions(BOOST_THREAD_PROVIDES_EXECUTORS)
add_compile_definitions(BOOST_THREAD_USES_MOVE)

# Setup dependancies
include(deps/cadmium.cmake)
include(deps/rt-cadmium.cmake)
include(deps/destimes.cmake)

configure_file("${CADMIUM_INCLUDE_DIR}/cadmium/basic_model/pdevs/iestream.hpp" "${RT_CADMIUM_INCLUDE_DIR}/cadmium/basic_model/pdevs/iestream.hpp" COPYONLY) # Used to copy a missing file to rt cadmium

# Setup boost
set(Boost_USE_STATIC_LIBS on)
find_package(
	Boost 1.65 REQUIRED
	COMPONENTS system thread regex
)

# Setup includes
set(rt_includes_list ${Boost_INCLUDE_DIRS} ${RT_CADMIUM_INCLUDE_DIR} ${DESTIMES_INCLUDE_DIR} "${CMAKE_SOURCE_DIR}/include")

# Create all tests
add_executable(td_udp_output            				"${CMAKE_SOURCE_DIR}/test/drivers/td_udp_output.cpp")
add_executable(td_udp_input             				"${CMAKE_SOURCE_DIR}/test/drivers/td_udp_input.cpp")
add_executable(td_udp_input_async						"${CMAKE_SOURCE_DIR}/test/drivers/td_udp_input_async.cpp")

target_include_directories(td_udp_output                PUBLIC ${rt_includes_list})
target_include_directories(td_udp_input                 PUBLIC ${rt_includes_list})
target_include_directories(td_udp_input_async			PUBLIC ${rt_includes_list})

target_link_libraries(td_udp_output                     ${Boost_LIBRARIES})
target_link_libraries(td_udp_input                      ${Boost_LIBRARIES})
target_link_libraries(td_udp_input_async				${Boost_LIBRARIES})
