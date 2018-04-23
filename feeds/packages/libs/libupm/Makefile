#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libupm
PKG_VERSION:=1.5.0

PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/intel-iot-devkit/upm.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=4037ec517cc48ae922393fb66f9c80ba071c8628
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
CMAKE_INSTALL:=1

PKG_MAINTAINER:=John Crispin <blogic@openwrt.org>
PKG_LICENSE:=LGPL-2.1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

UPM_MODULES:= bmp280 ssd1351

CMAKE_OPTIONS=-DBUILDARCH=$(CONFIG_ARCH) \
	-DNODE_EXECUTABLE=$(STAGING_DIR_HOST)/bin/node \
	-DSWIG_DIR=$(STAGING_DIR_HOST)/bin

define Package/libupm
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libmraa +librt +libpthread
  TITLE:=Intel IoT sensor library - Full
endef


define Package/libupm/install
	$(INSTALL_DIR) $(1)/usr/lib/{node/,python2.7/site-packages}; \
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/; \
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/; \
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/jsupm_* $(1)/usr/lib/node/; \
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/python2.7/site-packages/upm/{pyupm_*.py,_pyupm_*.so} \
		$(1)/usr/lib/python2.7/site-packages/ ;
endef

$(eval $(call BuildPackage,libupm))
