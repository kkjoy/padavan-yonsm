SRC_NAME = AdGuardHome_linux_mipsle_softfloat.tar.gz
SRC_TAG = v0.107.54
SRC_URL = https://github.com/AdguardTeam/AdGuardHome/releases/download/$(SRC_TAG)/AdGuardHome_linux_mipsle_softfloat.tar.gz
THISDIR = $(shell pwd)

all: download_test extract_test
	
download_test:
	( if [ ! -f $(SRC_NAME).tar.gz ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).tar.gz $(SRC_URL); \
	fi )
	
extract_test:
	( if [ ! -d $(SRC_NAME) ]; then \
		tar zxf $(SRC_NAME).tar.gz ; \
	fi )


romfs:
	$(ROMFSINST) -p +x $(THISDIR)/AdGuardHome/AdGuardHome /usr/bin/AdGuardHome
	$(ROMFSINST) -p +x $(THISDIR)/adguardhome.sh /usr/bin/adguardhome.sh
