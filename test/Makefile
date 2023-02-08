CC=gcc
CFLAGS=-g -Wall -Wextra -pedantic -I../include -fprofile-arcs -ftest-coverage
LDFLAGS=-g -L../build/src -L../build/test --coverage
LDLIBS=
RM=rm
BUILD_DIR=../build

.PHONY: all
all: $(BUILD_DIR)/test/test_gc

$(BUILD_DIR)/test/%.o: %.c
		mkdir -p $(@D)
		$(CC) $(CFLAGS) -MMD -c $< -o $@

SRCS=test_gc.c ../src/log.c
OBJS=$(SRCS:%.c=$(BUILD_DIR)/test/%.o)
DEPS=$(OBJS:%.o=%.d)

$(BUILD_DIR)/test/test_gc: $(OBJS)
		mkdir -p $(@D)
		$(CC) $(LDFLAGS) $(LDLIBS) $^ -o $@

.PHONY: clean
clean:
	$(RM) -f $(OBJS) $(DEPS)

distclean: clean
	$(RM) -f $(BUILD_DIR)/test/test_gc
	$(RM) -f $(BUILD_DIR)/test/*gcda
	$(RM) -f $(BUILD_DIR)/test/*gcno
