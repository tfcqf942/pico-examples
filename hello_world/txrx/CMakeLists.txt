if (TARGET tinyusb_device)
    add_executable(txrx
            txrx.c
            )

    # pull in common dependencies
    target_link_libraries(txrx pico_stdlib)

    # enable usb output, disable uart output
    pico_enable_stdio_usb(txrx 1)
    pico_enable_stdio_uart(txrx 0)

    # create map/bin/hex/uf2 file etc.
    pico_add_extra_outputs(txrx)

    # add url via pico_set_program_url
    example_auto_set_url(txrx)
elseif(PICO_ON_DEVICE)
    message(WARNING "not building txrx because TinyUSB submodule is not initialized in the SDK")
endif()
