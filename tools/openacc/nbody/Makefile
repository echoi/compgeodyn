################################################################################
#
# Copyright 2014 NVIDIA Corporation.  All rights reserved.
#
# Please refer to the NVIDIA end user license agreement (EULA) associated
# with this source code for terms and conditions that govern your use of
# this software. Any use, reproduction, disclosure, or distribution of
# this software and related documentation outside the terms of the EULA
# is strictly prohibited.
#
################################################################################

PREC     = FP64
CC       = pgcc
OBJ     = o
EXE	= out
RUN     =
UNAME := $(shell uname -a)
ifeq ($(findstring CYGWIN_NT, $(UNAME)), CYGWIN_NT)
OBJ     = obj
EXE	= exe
endif

CCFLAGS  = -D$(PREC) -fast -Minline
ACCFLAGS = -Minfo -acc

all: build run verify

build: nbodyacc.c check.c
	$(CC) -c $(CCFLAGS) check.c
	$(CC) $(CCFLAGS) $(ACCFLAGS) -o nbody.$(EXE) nbodyacc.c check.$(OBJ)

run: nbody.$(EXE)
	$(RUN) ./nbody.$(EXE)

verify:


clean:
	@echo 'Cleaning up...'
	@rm -rf *.$(EXE) *.$(OBJ) *.dwf *.pdb prof
