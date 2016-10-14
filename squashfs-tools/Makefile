INSTALL_DIR = /usr/local/bin

INCLUDEDIR = .

CFLAGS := -I$(INCLUDEDIR) -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -O2

all: mksquashfs3 unsquashfs3

mksquashfs3: mksquashfs.o read_fs.o sort.o
	$(CC) mksquashfs.o read_fs.o sort.o -lz -lpthread -lm -o $@

mksquashfs.o: mksquashfs.c squashfs_fs.h mksquashfs.h global.h sort.h

read_fs.o: read_fs.c squashfs_fs.h read_fs.h global.h

sort.o: sort.c squashfs_fs.h global.h sort.h

unsquashfs3: unsquashfs.o
	$(CC) unsquashfs.o -lz -lpthread -lm -o $@

unsquashfs.o: unsquashfs.c squashfs_fs.h read_fs.h global.h

clean:
	-rm -f *.o mksquashfs3 unsquashfs3

install: mksquashfs3 unsquashfs3
	mkdir -p $(INSTALL_DIR)
	cp mksquashfs3 unsquashfs3 $(INSTALL_DIR)
