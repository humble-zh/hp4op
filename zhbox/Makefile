include $(TOPDIR)/rules.mk

PKG_NAME:=zhbox
PKG_VERSION:=0.0.3
PKG_RELEASE=1
PKG_LICENSE:=MIT

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/humble-zh/zhbox.git
PKG_MIRROR_HASH:=437a20005cc8bbcb74656993790550cd665dfed53ab257858e5e63d7a002984c
PKG_SOURCE_VERSION:=c857b9a174942330f4baaf06992df70421953998

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  TITLE:=an iot-edge program connected to the cloud with MQTT
  URL:=
  DEPENDS:=+libconfig +libevent2-core +libmosquitto-ssl +open62541 +openssl-util
endef

define Package/$(PKG_NAME)/description
an iot-edge program connected to the cloud with MQTT
endef

CMAKE_SOURCE_DIR=$(PKG_BUILD_DIR)
CMAKE_OPTIONS+=

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
