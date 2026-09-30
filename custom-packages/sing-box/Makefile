include $(TOPDIR)/rules.mk

PKG_NAME:=sing-box
PKG_VERSION:=1.8.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/SagerNet/sing-box/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=35db2a6953c04ea6301f242ba2d6c7ca7f6d52bae0b4927beca5255ee958b218

PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=D50-5G-HomeProxy

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/sagernet/sing-box
GO_PKG_BUILD_PKG:=$(GO_PKG)/cmd/sing-box
GO_PKG_LDFLAGS_X:=$(GO_PKG)/constant.Version=$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/sing-box
  TITLE:=The universal proxy platform
  SECTION:=net
  CATEGORY:=Network
  URL:=https://sing-box.sagernet.org
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle +kmod-inet-diag +kmod-tun
  USERID:=sing-box=5566:sing-box=5566
endef

define Package/sing-box/description
  Sing-box 1.8.7, pinned for the HomeProxy 2024031600 configuration format.
endef

GO_PKG_TAGS:=with_clash_api,with_ech,with_gvisor,with_quic,with_reality_server,with_utls,with_wireguard

define Package/sing-box/conffiles
/etc/config/sing-box
/etc/sing-box/
endef

define Package/sing-box/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(GO_PKG_BUILD_BIN_DIR)/sing-box $(1)/usr/bin/sing-box

	$(INSTALL_DIR) $(1)/etc/sing-box
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/release/config/config.json $(1)/etc/sing-box/config.json

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/sing-box.conf $(1)/etc/config/sing-box

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/sing-box.init $(1)/etc/init.d/sing-box
endef

$(eval $(call BuildPackage,sing-box))
