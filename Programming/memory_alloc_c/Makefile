CC=gcc
CFLAGS=-Wall -Wextra -fPIC -g
LDFLAGS=-shared
TARGET_LIB=liballocator.so
TARGET_RUNME=runme

all: $(TARGET_LIB) $(TARGET_RUNME)

$(TARGET_LIB): allocator.o
	$(CC) $(LDFLAGS) -o $@ $<

allocator.o: allocator.c allocator.h
	$(CC) $(CFLAGS) -c allocator.c

$(TARGET_RUNME): runme.o allocator.o
	$(CC) $(CFLAGS) -o $@ runme.o allocator.o

runme.o: runme.c allocator.h
	$(CC) $(CFLAGS) -c runme.c

test:
	@echo "No tests yet."

clean:
	rm -f *.o $(TARGET_LIB) $(TARGET_RUNME)
