PROJECT_NAME = $(shell basename "$(realpath ./)")

APPLICATION_SRCS = $(notdir $(wildcard ./*.c))
APPLICATION_SRCS += bootloader.c
APPLICATION_SRCS += bootloader_util.c
APPLICATION_SRCS += bootloader_settings.c
APPLICATION_SRCS += crc16.c
APPLICATION_SRCS += dfu_single_bank.c
APPLICATION_SRCS += dfu_transport_ble.c
APPLICATION_SRCS += ble_dfu.c
APPLICATION_SRCS += dfu_init_template.c
APPLICATION_SRCS += hci_transport.c
APPLICATION_SRCS += hci_slip.c
APPLICATION_SRCS += hci_mem_pool.c
APPLICATION_SRCS += pstorage_raw.c
APPLICATION_SRCS += app_scheduler.c
APPLICATION_SRCS += app_uart.c
APPLICATION_SRCS += softdevice_handler.c
APPLICATION_SRCS += softdevice_handler_appsh.c
APPLICATION_SRCS += ble_advdata.c
APPLICATION_SRCS += ble_conn_params.c
APPLICATION_SRCS += app_timer.c
APPLICATION_SRCS += app_timer_appsh.c
APPLICATION_SRCS += app_error.c
APPLICATION_SRCS += ble_srv_common.c
APPLICATION_SRCS += app_util_platform.c
APPLICATION_SRCS += nrf_drv_common.c
APPLICATION_SRCS += nrf_delay.c
APPLICATION_SRCS += led.c
APPLICATION_SRCS += nrf_drv_uart.c 

LIBRARY_PATHS += ../include
LIBRARY_PATHS += .

SOURCE_PATHS += ../src

SDK_VERSION ?= 11
SOFTDEVICE_MODEL ?= s130
RAM_KB ?= 32
FLASH_KB ?= 256

LINKER_SCRIPT = ../make/ld/gcc_nrf51_s130_2.0.0_32_256_bootloader.ld

BOOTLOADER_REGION_START = $(addprefix 0x, $(shell echo "obase=16; (${FLASH_KB}-18)*1024" | bc ))
BOOTLOADER_SETTINGS_ADDRESS = $(addprefix 0x, $(shell echo "obase=16; (${FLASH_KB}-2)*1024" | bc))
CFLAGS += -DBOOTLOADER_REGION_START=$(BOOTLOADER_REGION_START)
CFLAGS += -DBOOTLOADER_SETTINGS_ADDRESS=$(BOOTLOADER_SETTINGS_ADDRESS)

LDFLAGS += --specs=nano.specs

NRF_BASE_PATH ?= ..
include $(NRF_BASE_PATH)/make/Makefile
