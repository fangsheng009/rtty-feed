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
PKG_SOURCE_VERSION:=10a371a10377aefa5d6db303152addc9fd50b1e8
PKG_MIRROR_HASH:=f51e314278903e349fecba76d889431f32246b094d46fd47bc102c37f56c72dc

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

PKG_MAINTAINER:=Jianhui Zhao <jianhuizhao329@gmail.com>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/xttyd
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Terminal
  TITLE:=Share your terminal over the web
  DEPENDS:=+libuwsc-nossl +libblobmsg-json
endef

define Package/xttyd/description
  Share your terminal over the web. Unlike ttyd, xTTYD consists of two parts of the client and the server.
  xTTYD can share the shell of your device based on the MAC address you specify.
endef

define Package/xttyd/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/xttyd $(1)/usr/sbin
	$(INSTALL_BIN) ./files/xttyd.init $(1)/etc/init.d/xttyd
	$(INSTALL_CONF) ./files/xttyd.config $(1)/etc/config/xttyd
endef

$(eval $(call BuildPackage,xttyd))
