include $(TOPDIR)/rules.mk

PKG_NAME:=pptp-linux
PKG_VERSION:=1.10.0
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).orig.tar.gz
PKG_SOURCE_URL:=file://$(TOPDIR)/dl/
PKG_HASH:=skip

include $(INCLUDE_DIR)/package.mk

define Package/pptp-linux
  SECTION:=net
  CATEGORY:=Network
  TITLE:=PPTP Client for Linux
  DEPENDS:=+ppp-mod-pptp +kmod-pptp
endef

define Package/pptp-linux/description
  PPTP client implementation for Linux.
endef

define Build/Prepare
    $(call Build/Prepare/Default)
    tar -xzf $(DL_DIR)/$(PKG_SOURCE) -C $(PKG_BUILD_DIR)
endef

define Build/Compile
    $(MAKE) -C $(PKG_BUILD_DIR) \
        CC="$(TARGET_CC)" \
        CFLAGS="$(TARGET_CFLAGS)" \
        DESTDIR="$(PKG_INSTALL_DIR)" \
        install
endef

define Package/pptp-linux/install
    $(INSTALL_DIR) $(1)/usr/sbin
    $(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/pptp $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,pptp-linux))
