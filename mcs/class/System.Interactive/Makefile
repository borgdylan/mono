thisdir = class/System.Interactive
SUBDIRS = 
include ../../build/rules.make

LIBRARY = System.Interactive.dll
LIB_REFS = System System.Core
LIB_MCS_FLAGS = @more_build_args

ifeq (2.1, $(FRAMEWORK_VERSION))
LIB_MCS_FLAGS += -d:NO_TASK_DELAY -d:HAS_AWAIT
endif

NET_4_5 := $(filter 4.5, $(FRAMEWORK_VERSION))
ifdef NET_4_5
LIB_MCS_FLAGS += -d:HAS_EDI -d:PREFERASYNC -d:PREFER_ASYNC -d:HAS_AWAIT
endif

TEST_MCS_FLAGS = $(LIB_MCS_FLAGS)

EXTRA_DISTFILES = more_build_args

VALID_PROFILE := $(filter monotouch monotouch_watch monodroid xammac mobile mobile_static net_4_5, $(PROFILE))
ifndef VALID_PROFILE
LIBRARY_NAME = dummy-System.System.Interactive.dll
NO_SIGN_ASSEMBLY = yes
endif

INSTALL_PROFILE := $(filter net_4_5, $(PROFILE))
ifndef INSTALL_PROFILE
NO_INSTALL = yes
endif

NO_TEST = yes

include ../../build/library.make
