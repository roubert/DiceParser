set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -fno-permissive -pedantic -Wall -Wextra")
set(CMAKE_AUTOMOC ON)
find_package(Qt5 ${QT_REQUIRED_VERSION} CONFIG REQUIRED COMPONENTS Core Gui Svg Test)

set(test_source testnode.cpp tst_dice.cpp)

add_executable(test_dice ${test_source})

target_include_directories(test_dice PRIVATE ../../include ../../ ../../node ../../result)

find_library(DICEPARSER_LIBRARY diceparser HINTS ${CMAKE_CURRENT_BINARY_DIR}/../../)

target_link_libraries(test_dice PUBLIC Qt5::Core Qt5::Gui Qt5::Test diceparser_shared)
add_test(tst_diceparser test_dice)
