cmake_minimum_required(VERSION 3.27)

project(VulkanTutorial)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

if (MSVC)
    add_compile_options("/wd4819")
endif()

find_package(Vulkan REQUIRED)

add_subdirectory(ThirdParty)

set(DESCRIPTOR_LAYOUT_AND_BUFFER_PATH "3.1.Descriptor layout and buffer")
set(DESCRIPTOR_POOL_AND_SETS_PATH "3.2.Descriptor pool and sets")

set(DESCRIPTOR_LAYOUT_AND_BUFFER "3.1.DescriptorLayoutAndBuffer")
set(DESCRIPTOR_POOL_AND_SETS "3.2.DescriptorPoolAndSets")

add_subdirectory(${DESCRIPTOR_LAYOUT_AND_BUFFER_PATH})
add_subdirectory(${DESCRIPTOR_POOL_AND_SETS_PATH})

set_target_properties(
    ${DESCRIPTOR_LAYOUT_AND_BUFFER}
    ${DESCRIPTOR_POOL_AND_SETS}
    PROPERTIES FOLDER "3. Uniform buffers"
)