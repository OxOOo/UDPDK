#
# Created by leoll2 on 9/25/20.
# Copyright (c) 2020 Leonardo Lai. All rights reserved.
#

ROOTDIR=../..
DEPSDIR=${ROOTDIR}/deps

ifeq ($(UDPDK_PATH),)
	UDPDK_PATH=${ROOTDIR}
endif

PKGCONF = pkg-config

# all source are stored in SRCS-y
SRCS= main.c

LIBS+= -L${UDPDK_PATH}/udpdk -Wl,--whole-archive,-ludpdk,--no-whole-archive
LIBS+= $(shell $(PKGCONF) --libs libdpdk)
LIBS+= -Wl,--no-whole-archive -lrt -lm -ldl -pthread

CFLAGS += $(WERROR_FLAGS) -O3

TARGET="pingpong"
all:
	cc -I${ROOTDIR}/udpdk -o ${TARGET} ${SRCS} ${LIBS}

.PHONY: clean
clean:
	rm -f *.o ${TARGET}
