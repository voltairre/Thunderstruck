cmake_minimum_required(VERSION 4.1.2)

project(Thunderstruck VERSION 1.0 LANGUAGES CXX)

find_package(Qt6 REQUIRED COMPONENTS Quick)

qt_standard_project_setup(REQUIRES 6.11.1)

qt_add_executable(Thunderstruck
    main.cpp
)

qt_add_qml_module(Thunderstruck
    URI Thunderstruck
    QML_FILES
    Main.qml
    CoatOfArms.qml

    RESOURCES
    assets/blur_full_green_energy.jpg
)

target_link_libraries(Thunderstruck PRIVATE
    Qt6::Quick
)

target_compile_options(Thunderstruck PRIVATE
    -Os
    -flto
)

target_link_options(Thunderstruck PRIVATE
    -flto
    -O0
    -sWASM_BIGINT
    -sMAX_WEBGL_VERSION=2
    -sWEBGL2_BACKWARDS_COMPATIBILITY_EMULATION
)
