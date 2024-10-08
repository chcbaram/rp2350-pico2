file(GLOB SRC_FILES 
  bsp/*.c
  hw/*.c
)

file(GLOB_RECURSE SRC_FILES_RECURSE
  ap/*.cpp
  ap/*.c
  common/*.c 
  hw/*.c
)

add_executable(
  ${PRJ_NAME}
  
  main.cpp

  ${SRC_FILES}
  ${SRC_FILES_RECURSE}
)

target_include_directories(${PRJ_NAME} PUBLIC 
  ap
  bsp
  common 
  common/core
  common/hw/include 
  hw
  lib
)

target_link_libraries(${PRJ_NAME} 
  pico_stdlib
  hardware_spi
  hardware_dma
  hardware_irq
  hardware_i2c
  pico_multicore
  )

pico_add_extra_outputs(${PRJ_NAME})
pico_enable_stdio_usb(${PRJ_NAME}  1)
pico_enable_stdio_uart(${PRJ_NAME} 0)

set_target_properties(${PRJ_NAME} PROPERTIES SUFFIX ".elf")


