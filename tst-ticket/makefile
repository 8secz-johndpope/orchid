# Orchid - WebRTC P2P VPN Market (on Ethereum)
# Copyright (C) 2017-2019  The Orchid Authors

# GNU Affero General Public License, Version 3 {{{ */
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU Affero General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Affero General Public License for more details.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
# }}}


include env/target.mk

args := 0x264930d4c83496ebe0ef1615d6d500c1c1f0aee37160b17cf548e7f8cefb0121

.PHONY: all
all: $(output)/$(default)/ticket$(exe)

.PHONY: test
test: $(output)/$(default)/ticket$(exe)
	$< $(args)

.PHONY: debug
debug: $(output)/$(default)/ticket$(exe)
	lldb -o 'run $(args)' $<

$(call include,p2p/target.mk)

source += $(wildcard source/*.cpp)

include env/output.mk

$(output)/%/ticket$(exe): $(patsubst %,$(output)/$$*/%,$(object) $(linked))
	@echo [LD] $@
	@set -o pipefail; $(cxx) $(more/$*) $(wflags) -o $@ $(filter %.o,$^) $(filter %.a,$^) $(filter %.lib,$^) $(lflags) 2>&1 | nl
	@ls -la $@
