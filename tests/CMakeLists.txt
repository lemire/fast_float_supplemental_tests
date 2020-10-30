
function(add_cpp_test TEST_NAME)
    add_executable(${TEST_NAME} ${TEST_NAME}.cpp)
    add_test(${TEST_NAME} ${TEST_NAME})
    target_compile_definitions(${TEST_NAME} PRIVATE DATA_DIR="${DATA_DIR}")
    target_link_libraries(${TEST_NAME}  PUBLIC fast_float)
endfunction(add_cpp_test)

add_cpp_test(basic_tests)
