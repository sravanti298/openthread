#
#  Copyright (c) 2019, The OpenThread Authors.
#  All rights reserved.
#
#  Redistribution and use in source and binary forms, with or without
#  modification, are permitted provided that the following conditions are met:
#  1. Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#  2. Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in the
#     documentation and/or other materials provided with the distribution.
#  3. Neither the name of the copyright holder nor the
#     names of its contributors may be used to endorse or promote products
#     derived from this software without specific prior written permission.
#
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
#  AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
#  IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
#  ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE
#  LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
#  CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
#  SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
#  INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
#  CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
#  ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
#  POSSIBILITY OF SUCH DAMAGE.
#

include $(abs_top_nlbuild_autotools_dir)/automake/pre.am

lib_LIBRARIES = libopenthread-efr32mg21.a

# Do not enable -Wconversion for rail
override CFLAGS   := $(filter-out -Wconversion,$(CFLAGS))
override CXXFLAGS := $(filter-out -Wconversion,$(CXXFLAGS))

# Do not enable -pedantic-errors for rail
override CFLAGS   := $(filter-out -pedantic-errors,$(CFLAGS))
override CXXFLAGS := $(filter-out -pedantic-errors,$(CXXFLAGS))

# Do not enable -Wundef for rail
override CFLAGS   := $(filter-out -Wundef,$(CFLAGS))
override CXXFLAGS := $(filter-out -Wundef,$(CXXFLAGS))

EFR32_BOARD_DIR = $(shell echo $(BOARD) | tr A-Z a-z)

SDK_SRC_DIR = $(top_srcdir)/third_party/silabs/gecko_sdk_suite/v2.7

libopenthread_efr32mg21_a_CPPFLAGS                                            = \
    -DEFR32_SERIES2_CONFIG1_MICRO                                               \
    -DNVIC_CONFIG=\"platform/base/hal/micro/cortexm3/efm32/nvic-config.h\"      \
    -DPLATFORM_HEADER=\"platform/base/hal/micro/cortexm3/compiler/gcc.h\"       \
    -Wno-sign-compare                                                           \
    -I$(top_srcdir)/examples/platforms                                          \
    -I$(top_srcdir)/examples/platforms/efr32mg21/$(EFR32_BOARD_DIR)             \
    -I$(top_srcdir)/include                                                     \
    -I$(top_srcdir)/src/core                                                    \
    -I$(top_srcdir)/third_party/silabs/rail_config                              \
    -I$(SDK_SRC_DIR)                                                            \
    -I$(SDK_SRC_DIR)/hardware/kit/common/bsp                                    \
    -I$(SDK_SRC_DIR)/hardware/kit/common/drivers                                \
    -I$(SDK_SRC_DIR)/hardware/kit/EFR32MG21_$(BOARD)/config                     \
    -I$(SDK_SRC_DIR)/platform/base/hal/micro/cortexm3/efm32                     \
    -I$(SDK_SRC_DIR)/platform/base/hal/micro/cortexm3/efm32/config              \
    -I$(SDK_SRC_DIR)/platform/common/inc                                        \
    -I$(SDK_SRC_DIR)/platform/CMSIS/Include                                     \
    -I$(SDK_SRC_DIR)/platform/Device/SiliconLabs/EFR32MG21P/Include             \
    -I$(SDK_SRC_DIR)/platform/emdrv/common/inc                                  \
    -I$(SDK_SRC_DIR)/platform/emdrv/gpiointerrupt/inc                           \
    -I$(SDK_SRC_DIR)/platform/emdrv/uartdrv/inc                                 \
    -I$(SDK_SRC_DIR)/platform/emdrv/uartdrv/config                              \
    -I$(SDK_SRC_DIR)/platform/emdrv/ustimer/inc                                 \
    -I$(SDK_SRC_DIR)/platform/emdrv/dmadrv/inc                                  \
    -I$(SDK_SRC_DIR)/platform/emdrv/dmadrv/config                               \
    -I$(SDK_SRC_DIR)/platform/emlib/inc                                         \
    -I$(SDK_SRC_DIR)/platform/halconfig/inc/hal-config                          \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/chip/efr32                         \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/chip/efr32/efr32xg2x               \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/chip/efr32/rf/common/cortex        \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/common                             \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/hal                                \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/hal/efr32                          \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/protocol/ieee802154                \
    -I$(SDK_SRC_DIR)/platform/radio/rail_lib/plugin/pa-conversions              \
    -I$(SDK_SRC_DIR)/platform/service/mpu/inc                                   \
    -I$(SDK_SRC_DIR)/platform/service/sleeptimer/config                         \
    -I$(SDK_SRC_DIR)/platform/service/sleeptimer/inc                            \
    -I$(SDK_SRC_DIR)/util/plugin/plugin-common/fem-control                      \
    -I$(SDK_SRC_DIR)/util/third_party/mbedtls/sl_crypto/include                 \
    -Wno-unused-parameter                                                       \
    -Wno-missing-field-initializers                                             \
    $(NULL)

PLATFORM_SOURCES                                                              = \
    alarm.c                                                                     \
    diag.c                                                                      \
    entropy.c                                                                   \
    fem-control.c                                                               \
    flash.c                                                                     \
    logging.c                                                                   \
    misc.c                                                                      \
    openthread-core-efr32-config.h                                              \
    platform-efr32.h                                                            \
    platform-band.h                                                             \
    radio.c                                                                     \
    rail_config.h                                                               \
    startup-gcc.c                                                               \
    system.c                                                                    \
    uart.c                                                                      \
    $(NULL)

noinst_HEADERS                                                                = \
    platform-efr32.h                                                            \
    platform-band.h                                                             \
    $(NULL)

libopenthread_efr32mg21_a_SOURCES                                             = \
    $(PLATFORM_SOURCES)                                                         \
    $(NULL)

Dash = -
libopenthread_efr32mg21_a_LIBADD                                                                     = \
    $(shell find $(top_builddir)/examples/platforms/utils $(Dash)type f $(Dash)name "*.o")             \
    $(shell find $(top_builddir)/third_party/jlink/SEGGER_RTT_V640/RTT $(Dash)type f $(Dash)name "*.o")

DIST_SUBDIRS                                                                  = \
    sleepy-demo                                                                 \
    $(NULL)

SUBDIRS                                                                       = \
    sleepy-demo                                                                 \
    $(NULL)

include $(abs_top_nlbuild_autotools_dir)/automake/post.am
