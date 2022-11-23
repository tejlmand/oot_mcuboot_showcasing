cmake_minimum_required(VERSION 3.20)

project(oot_mcuboot LANGUAGES NONE)

find_package(Zephyr 3.2 REQUIRED HINTS $ENV{ZEPHYR_BASE} COMPONENTS west zephyr_module)

include(ExternalProject)
ExternalProject_Add(
    mcuboot
    SOURCE_DIR ${ZEPHYR_MCUBOOT_MODULE_DIR}/boot/zephyr
    INSTALL_COMMAND ""
    CMAKE_ARGS "-DBOARD=${BOARD}" "-DAPPLICATION_CONFIG_DIR=${CMAKE_CURRENT_LIST_DIR}"
)
