# Copyright 1996-2018 Cyberbotics Ltd.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Webots Makefile system
#
# You may add some variable definitions hereafter to customize the build process
# See documentation in $(WEBOTS_HOME_PATH)/resources/Makefile.include

space :=
space +=
WEBOTS_HOME_PATH=$(subst $(space),\ ,$(strip $(subst \,/,$(WEBOTS_HOME))))

include $(WEBOTS_HOME_PATH)/resources/Makefile.os.include

CXX_SOURCES = entry_points.cpp Viewer.cpp TransferWidget.cpp SSH.cpp ZIP.cpp
HPP_FILES_TO_MOC = TransferWidget.hpp SSH.hpp

QT = core gui widgets concurrent
USE_C_API = true

QT_UTILS = $(WEBOTS_HOME)/resources/projects/libraries/qt_utils
LIBRARIES = -L"$(QT_UTILS)" -lqt_utils -L"$(WEBOTS_HOME)/lib" -lssh
INCLUDE = -I"$(QT_UTILS)"

ifeq ($(OSTYPE),windows)
LIBRARIES += -lpthread -lzip
INCLUDE += -I"$(WEBOTS_HOME)/msys64/mingw64/include" -I"$(WEBOTS_HOME)/msys64/mingw64/lib/libzip/include"
else
INCLUDE += -I"$(WEBOTS_HOME)/include/libzip" -I"$(WEBOTS_HOME)/include/libssh"
endif

ifeq ($(OSTYPE),darwin)
LIBRARIES += -lnihzip
endif

ifeq ($(OSTYPE),linux)
LIBRARIES += -lzip
endif

include $(WEBOTS_HOME_PATH)/resources/Makefile.include
