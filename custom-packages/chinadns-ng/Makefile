include $(TOPDIR)/rules.mk

PKG_NAME:=chinadns-ng
PKG_VERSION:=2025.08.09
PKG_RELEASE:=1

ifeq ($(ARCH),aarch64)
  ifeq ($(BOARD),rockchip)
    PKG_ARCH:=chinadns-ng+wolfssl@aarch64-linux-musl@generic+v8a@fast+lto
    PKG_HASH:=3fe0217615dd7060b7287d2b6b31d2a0b364137398bfb335a03bead322eac716
  else
    PKG_ARCH:=chinadns-ng+wolfssl_noasm@aarch64-linux-musl@generic+v8a@fast+lto
    PKG_HASH:=42ddd494200ec6d88b35902927688d316bc23e06e6c08d9e01eb2412196ab845
  endif
else
  PKG_ARCH:=chinadns-ng+wolfssl_noasm@aarch64-linux-musl@generic+v8a@fast+lto
  PKG_HASH:=42ddd494200ec6d88b35902927688d316bc23e06c08d9e01eb2412196ab845
endif

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(ARCH_PACKAGES)
PKG_SOURCE_URL:=https://github.com/zfl9/chinadns-ng/releases/download/$(PKG_VERSION)/$(PKG_ARCH)?
UNPACK_CMD=$(CP) $(DL_DIR)/$(PKG_SOURCE) $(PKG_BUILD_DIR)/$(PKG_NAME)

PKG_LICENSE:=AGPL-3.0-only
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=D50-5G-HomeProxy

include $(INCLUDE_DIR)/package.mk

define Package/chinadns-ng
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  TITLE:=ChinaDNS next generation
  URL:=https://github.com/zfl9/chinadns-ng
  DEPENDS:=@(aarch64||arm||i386||mips||mipsel||mips64||mips64el||x86_64||riscv64)
endef

define Build/Compile
endef

define Package/chinadns-ng/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/chinadns-ng $(1)/usr/bin/
endef

$(eval $(call BuildPackage,chinadns-ng))
