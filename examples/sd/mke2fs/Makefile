# KallistiOS ##version##
#
# examples/dreamcast/sd/mke2fs/Makefile
#

TARGET = mke2fs.elf
OBJS = mke2fs.o

# We need the private headers from libkosext2fs, since we're not using the
# facilities of fs_ext2 here.
KOS_CFLAGS += -I$(KOS_BASE)/addons/libkosext2fs -Werror -W -std=gnu99

all: rm-elf $(TARGET)

include $(KOS_BASE)/Makefile.rules

clean:
	-rm -f $(TARGET) $(OBJS) romdisk.*

rm-elf:
	-rm -f $(TARGET) romdisk.*

$(TARGET): $(OBJS)
	kos-cc -o $(TARGET) $(OBJS)

run: $(TARGET)
	$(KOS_LOADER) $(TARGET)

dist:
	rm -f $(OBJS) romdisk.o romdisk.img
	$(KOS_STRIP) $(TARGET)
