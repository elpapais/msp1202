TARGETMCU	?= msp430g2553

CROSS		:= msp430-
CC		:= $(CROSS)gcc
MSPDEBUG	:= mspdebug
CFLAGS		:= -Os -Wall -Werror -g -mmcu=$(TARGETMCU)
CFLAGS += -fdata-sections -ffunction-sections -Wl,--gc-sections

SRCS			:= ste2007.c usci_spi.c chargen.c
TEST_TERMINAL		:= test_terminal.c

all:			test_terminal.elf

test_terminal.elf:	$(OBJS)
	$(CC) $(CFLAGS) -o test_terminal.elf $(SRCS) $(TEST_TERMINAL)

install:	test_terminal.elf
	mspdebug rf2500 "prog test_terminal.elf"

clean:
	-rm -f *.elf