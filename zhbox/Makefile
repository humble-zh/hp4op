include $(TOPDIR)/rules.mk

PKG_NAME:=zhbox
PKG_VERSION:=0.0.2
PKG_RELEASE=1
PKG_LICENSE:=MIT

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/humble-zh/zhbox.git
PKG_MIRROR_HASH:=9c26c920434fe06f99f2ecae569959be5c078b127213060bceeca729f5dec45a
PKG_SOURCE_VERSION:=989b4e9273dc977c2cec3a1ab39476e3b73d349d

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
  DEPENDS:=+libconfig +libevent2-core +libmosquitto-ssl
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
