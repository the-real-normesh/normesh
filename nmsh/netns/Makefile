#   nmsh-netns Makefile
#   Copyright (C) 2023  Nathan Eric Norman
#
#   This program is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <https://www.gnu.org/licenses/>.

.PHONY: all install uninstall

LIBDIR ?= /usr/lib

all:

install:
	install --directory $(DESTDIR)/$(LIBDIR)/systemd/system $(DESTDIR)/etc/nmsh/netns $(DESTDIR)/usr/bin
	install --owner=root --group=root --mode=644 service/nmsh-netns@.service $(DESTDIR)/$(LIBDIR)/systemd/system/
	install --owner=root --group=root --mode=644 service/nmsh-netns-setup@.service $(DESTDIR)/$(LIBDIR)/systemd/system/
	install --owner=root --group=root --mode=755 tool/nmsh-netns $(DESTDIR)/usr/bin/
	systemctl daemon-reload || true

uninstall:
	systemctl disable --now "nmsh-netns-setup@*" || true
	systemctl disable --now "nmsh-netns@*" || true
	rm -f $(DESTDIR)/$(LIBDIR)/systemd/system/nmsh-netns@.service
	rm -f $(DESTDIR)/$(LIBDIR)/systemd/system/nmsh-netns-setup@.service
	rm -f $(DESTDIR)/usr/bin/nmsh-netns
