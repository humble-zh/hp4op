include $(TOPDIR)/rules.mk

PKG_NAME:=zhbox
PKG_VERSION:=0.0.2
PKG_RELEASE=1
PKG_LICENSE:=GPL-3.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/humble-zh/zhbox.git
PKG_MIRROR_HASH:=8579cf3ae11077c0594682d6866cfdd93d2e238bb9dab1f24e9b9cf4fd26cadc
PKG_SOURCE_VERSION:=8eadee9aa5f7befa8ff8070d13306af8d0270f48

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  TITLE:=zhbox just syslog a string helloworld
  URL:=
  DEPENDS:=+libevent2-core
endef

define Package/$(PKG_NAME)/description
zhbox just syslog a string helloworld
endef

CMAKE_SOURCE_DIR=$(PKG_BUILD_DIR)
CMAKE_OPTIONS+=

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
