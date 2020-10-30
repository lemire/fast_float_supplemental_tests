

set(DATA_DIR ${CMAKE_CURRENT_BINARY_DIR} PARENT_SCOPE)


# Copy static files to the build dir so they live alongside the generated ones
file(GLOB_RECURSE example_files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.txt)
foreach(example_file ${example_files})
  configure_file(${example_file} ${example_file} COPYONLY)
endforeach(example_file)
