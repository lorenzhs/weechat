#
# Copyright (C) 2014 Sébastien Helleu <flashcode@flashtux.org>
#
# This file is part of WeeChat, the extensible chat client.
#
# WeeChat is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# WeeChat is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with WeeChat.  If not, see <http://www.gnu.org/licenses/>.
#

AM_CPPFLAGS = -DLOCALEDIR=\"$(datadir)/locale\" $(CPPUTEST_CFLAGS)

noinst_LIBRARIES = lib_ncurses_fake.a lib_weechat_unit_tests.a

lib_ncurses_fake_a_SOURCES = ncurses-fake.c

lib_weechat_unit_tests_a_SOURCES = unit/core/test-eval.cpp \
                                   unit/core/test-hashtable.cpp \
                                   unit/core/test-hdata.cpp \
                                   unit/core/test-infolist.cpp \
                                   unit/core/test-list.cpp \
                                   unit/core/test-string.cpp \
                                   unit/core/test-url.cpp \
                                   unit/core/test-utf8.cpp \
                                   unit/core/test-util.cpp

bin_PROGRAMS = tests

# Because of a linker bug, we have to link 2 times with lib_weechat_core.a
# (and it must be 2 different path/names to be kept by linker)
tests_LDADD = ./../src/core/lib_weechat_core.a \
              ../src/plugins/lib_weechat_plugins.a \
              ../src/gui/lib_weechat_gui_common.a \
              ../src/gui/curses/lib_weechat_gui_curses.a \
              ../src/core/lib_weechat_core.a \
              lib_ncurses_fake.a \
              lib_weechat_unit_tests.a \
              $(PLUGINS_LFLAGS) \
              $(GCRYPT_LFLAGS) \
              $(GNUTLS_LFLAGS) \
              $(CURL_LFLAGS) \
              $(CPPUTEST_LFLAGS) \
              -lm

tests_SOURCES = tests.cpp

EXTRA_DIST = CMakeLists.txt
