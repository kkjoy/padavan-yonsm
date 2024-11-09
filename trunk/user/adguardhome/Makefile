SRC_NAME = AdGuardHome_linux_mipsle_softfloat.tar.gz
SRC_TAG = v0.107.54
SRC_URL = https://github.com/AdguardTeam/AdGuardHome/releases/download/$(SRC_TAG)/AdGuardHome_linux_mipsle_softfloat.tar.gz
THISDIR = $(shell pwd)
TAG
all: download_test extract_test config_test
	$(MAKE) -C $(SRC_NAME)
	
download_test:
	( if [ ! -f $(SRC_NAME).tar.gz ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).tar.gz $(SRC_URL); \
	fi )
	
extract_test:
	( if [ ! -d $(SRC_NAME) ]; then \
		tar zxf $(SRC_NAME).tar.gz ; \
	fi )

config_test:
	( if [ -f ./config_done ]; then \
		echo "the same configuration"; \
	else \
		touch config_done; \
	fi )

clean:
	if [ -f $(SRC_NAME)/Makefile ] ; then \
		$(MAKE) -C $(SRC_NAME) clean ; \
	fi ; \
	rm -f config_done

romfs:
	$(ROMFSINST) -p +x $(THISDIR)/$(SRC_NAME)/AdGuardHome/AdGuardHome /usr/bin/AdGuardHome
	$(ROMFSINST) -p +x $(THISDIR)/adguardhome.sh /usr/bin/adguardhome.sh
