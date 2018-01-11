#
# Copyright (C) 2014-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xttyd
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/zhaojh329/xttyd.git
PKG_SOURCE_DATE:=2018-1-11
PKG_SOURCE_VERSION:=039d1de7884d3ddfdb8cc53ed72dfb40546b0bb4
#PKG_MIRROR_HASH:=

PKG_BUILD_DIR=$(BUILD_DIR)/$(PKG_NAME)-$(BUILD_VARIANT)/$(PKG_SOURCE_SUBDIR)

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

PKG_MAINTAINER:=Jianhui Zhao <jianhuizhao329@gmail.com>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/xttyd/default
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Terminal
  TITLE:=xTTYD
  DEPENDS:=+libuwsc
endef

define Package/xttyd-nossl
  $(Package/xttyd/default)
  TITLE += (NO SSL)
  DEPENDS += +libuwsc-nossl
  VARIANT:=nossl
endef

define Package/xttyd-openssl
  $(Package/xttyd/default)
  TITLE += (openssl)
  DEPENDS += +libuwsc-openssl
  VARIANT:=openssl
endef

define Package/xttyd-wolfssl
  $(Package/xttyd/default)
  TITLE += (wolfssl)
  DEPENDS += +libuwsc-wolfssl
  VARIANT:=wolfssl
endef

define Package/xttyd-mbedtls
  $(Package/xttyd/default)
  TITLE += (mbedtls)
  DEPENDS += +libuwsc-mbedtls
  VARIANT:=mbedtls
endef

define Package/xttyd/default/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/xttyd $(1)/usr/sbin
	$(INSTALL_BIN) ./files/xttyd.init $(1)/etc/init.d/xttyd
	$(INSTALL_CONF) ./files/xttyd.config $(1)/etc/config/xttyd
endef

Package/xttyd-nossl/install = $(Package/xttyd/default/install)
Package/xttyd-openssl/install = $(Package/xttyd/default/install)
Package/xttyd-wolfssl/install = $(Package/xttyd/default/install)
Package/xttyd-mbedtls/install = $(Package/xttyd/default/install)

$(eval $(call BuildPackage,xttyd-nossl))
$(eval $(call BuildPackage,xttyd-mbedtls))
$(eval $(call BuildPackage,xttyd-wolfssl))
$(eval $(call BuildPackage,xttyd-openssl))
