
target.o-y = \
	libhthread.o \
	libhthread-actual.o \
	libhthread-debug.o

target.so-y = \
	libhthread.so

libhthread.o_files-y = \
	libhthread-actual.o \
	libhthread-debug.o

libhthread.so_files-y = \
	libhthread.o

libhthread.so_ldflags-y = \
	-lpthread

ifeq ($(uname_S), Linux)
libhthread.so_ldflags-y = \
	-lrt
endif

libhthread-actual.o_files-y = \
	hthread.c

libhthread-actual.o_cflags-y = \
	-DHTHREAD_DEBUG=0
	
libhthread-debug.o_files-y = \
	hthread.c

libhthread-debug.o_cflags-y = \
	-DHTHREAD_DEBUG=1

ifeq (${HTHREAD_ENABLE_CALLSTACK}, 1)
libhthread-actual.o_cflags-y += \
	-DHTHREAD_ENABLE_CALLSTACK=${HTHREAD_ENABLE_CALLSTACK}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_ENABLE_CALLSTACK=${HTHREAD_ENABLE_CALLSTACK}

libhthread.so_ldflags-y = \
	-lbfd \
	-ldl
else ifeq (${HTHREAD_ENABLE_CALLSTACK}, 0)
libhthread-actual.o_cflags-y += \
	-DHTHREAD_ENABLE_CALLSTACK=0

libhthread-debug.o_cflags-y += \
	-DHTHREAD_ENABLE_CALLSTACK=0
endif

ifneq (${HTHREAD_REPORT_CALLSTACK}, )
libhthread-actual.o_cflags-y += \
	-DHTHREAD_REPORT_CALLSTACK=${HTHREAD_REPORT_CALLSTACK}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_REPORT_CALLSTACK=${HTHREAD_REPORT_CALLSTACK}
endif

ifneq (${HTHREAD_ASSERT_ON_ERROR}, )
libhthread-actual.o_cflags-y += \
	-DHTHREAD_ASSERT_ON_ERROR=${HTHREAD_ASSERT_ON_ERROR}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_ASSERT_ON_ERROR=${HTHREAD_ASSERT_ON_ERROR}
endif

ifneq (${HTHREAD_LOCK_THRESHOLD}, )
libhthread-actual.o_cflags-y += \
	-DHTHREAD_LOCK_THRESHOLD=${HTHREAD_LOCK_THRESHOLD}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_LOCK_THRESHOLD=${HTHREAD_LOCK_THRESHOLD}
endif

ifneq (${HTHREAD_LOCK_THRESHOLD_ASSERT}, )
libhthread-actual.o_cflags-y += \
	-DHTHREAD_LOCK_THRESHOLD_ASSERT=${HTHREAD_LOCK_THRESHOLD_ASSERT}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_LOCK_THRESHOLD_ASSERT=${HTHREAD_LOCK_THRESHOLD_ASSERT}
endif

ifneq (${HTHREAD_LOCK_TRY_THRESHOLD}, )
libhthread-actual.o_cflags-y += \
	-DHTHREAD_LOCK_TRY_THRESHOLD=${HTHREAD_LOCK_TRY_THRESHOLD}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_LOCK_TRY_THRESHOLD=${HTHREAD_LOCK_TRY_THRESHOLD}
endif

ifneq (${HTHREAD_LOCK_TRY_THRESHOLD_ASSERT}, )
libhthread-actual.o_cflags-y += \
	-DHTHREAD_LOCK_TRY_THRESHOLD_ASSERT=${HTHREAD_LOCK_TRY_THRESHOLD_ASSERT}

libhthread-debug.o_cflags-y += \
	-DHTHREAD_LOCK_TRY_THRESHOLD_ASSERT=${HTHREAD_LOCK_TRY_THRESHOLD_ASSERT}
endif

distdir = ../dist

dist.lib-y = \
	libhthread.so

dist.include-y = \
	hthread.h

include ../Makefile.lib
