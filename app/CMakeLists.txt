cmake_minimum_required(VERSION 3.4.1)

add_library( native-lib
             SHARED
             src/main/cpp/native-lib.cpp )

add_library( jpegbither
             SHARED
             IMPORTED)
set_target_properties( jpegbither
                       PROPERTIES IMPORTED_LOCATION
                       ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libjpegbither.so
                       )

find_library( log-lib log )

include_directories(src/main/cpp/jpeg/)


target_link_libraries(  native-lib jpegbither jnigraphics
                       ${log-lib} )