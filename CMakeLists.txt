cmake_minimum_required(VERSION 3.21)
project(GenshinAchievementChecker LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(OpenCV CONFIG REQUIRED)
find_package(Tesseract CONFIG REQUIRED)
find_package(nlohmann_json CONFIG REQUIRED)

add_executable(GenshinAchievementChecker
  src/main.cpp
)

target_include_directories(GenshinAchievementChecker PRIVATE src)
target_link_libraries(GenshinAchievementChecker PRIVATE
  opencv_core
  opencv_imgproc
  opencv_imgcodecs
  Tesseract::libtesseract
  nlohmann_json::nlohmann_json
)

if(MSVC)
  target_compile_options(GenshinAchievementChecker PRIVATE /W4 /permissive-)
endif()
