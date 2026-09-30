include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-homeproxy
PKG_VERSION:=2024031600
PKG_RELEASE:=1
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/douglarek/luci-app-homeproxy.git
PKG_SOURCE_VERSION:=2dce4439b4ef671314d42c449b3af1aeba6580a
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_LICENSE:=GPL-2.0-only
PKG_MAINTAINER:=D50-5G-HomeProxy

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-homeproxy
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:=HomeProxy legacy 2024031600
  PKGARCH:=all
  DEPENDS:=+luci-base +sing-box +chinadns-ng +firewall4 +kmod-nft-tproxy +unzip
endef

define Package/luci-app-homeproxy/description
  Exact HomeProxy source at release 2024031600 (commit 2dce443).
endef

define Package/luci-app-homeproxy/conffiles
/etc/config/homeproxy
/etc/homeproxy/certs/
/etc/homeproxy/ruleset/
/etc/homeproxy/resources/geoip.db
/etc/homeproxy/resources/geoip.ver
/etc/homeproxy/resources/geosite.db
/etc/homeproxy/resources/geosite.ver
/etc/homeproxy/resources/direct_list.txt
/etc/homeproxy/resources/proxy_list.txt
endef

define Build/Compile
endef

define Package/luci-app-homeproxy/install
	$(CP) $(PKG_BUILD_DIR)/root/* $(1)/
	$(INSTALL_DIR) $(1)/www
	$(CP) $(PKG_BUILD_DIR)/htdocs/* $(1)/www/
endef

$(eval $(call BuildPackage,luci-app-homeproxy))
