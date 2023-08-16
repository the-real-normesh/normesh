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
