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

define Package/$(PKG_NAME)/Default
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=ZHBox
  URL:=
endef


define Package/$(PKG_NAME)
  $(call Package/$(PKG_NAME)/Default)
  TITLE:=iot-edge to hold the connection between Cloud and Subdevice
  DEPENDS:=+libconfig +libevent2-core +libmosquitto-ssl +open62541 +openssl-util
endef

define Package/$(PKG_NAME)/description
an iot-edge program hold the connection between Cloud and Subdevice
endef

define Package/$(PKG_NAME)_n_aliyun
  $(call Package/$(PKG_NAME)/Default)
  TITLE:=northbound plugin connected to aliyun with MQTT
  DEPENDS:= @$(PKG_NAME)
endef

define Package/$(PKG_NAME)_n_huaweicloud
  $(call Package/$(PKG_NAME)/Default)
  TITLE:=northbound plugin connected to huaweicloud with MQTT
  DEPENDS:= @$(PKG_NAME)
endef

define Package/$(PKG_NAME)_s_modbus
  $(call Package/$(PKG_NAME)/Default)
  TITLE:=southbound plugin connected to Modbus Slave
  DEPENDS:= @$(PKG_NAME)
endef

define Package/$(PKG_NAME)_s_opcua
  $(call Package/$(PKG_NAME)/Default)
  TITLE:=southbound plugin connected to OPCUA Server
  DEPENDS:= @$(PKG_NAME)
endef


CMAKE_SOURCE_DIR=$(PKG_BUILD_DIR)
CMAKE_OPTIONS+=

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/
endef

define Package/$(PKG_NAME)_n_aliyun/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME)_n_aliyun $(1)/usr/bin/
endef

define Package/$(PKG_NAME)_n_huaweicloud/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME)_n_huaweicloud $(1)/usr/bin/
endef

define Package/$(PKG_NAME)_s_modbus/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME)_s_modbus $(1)/usr/bin/
endef

define Package/$(PKG_NAME)_s_opcua/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME)_s_opcua $(1)/usr/bin/
endef


$(eval $(call BuildPackage,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)_n_aliyun))
$(eval $(call BuildPackage,$(PKG_NAME)_n_huaweicloud))
$(eval $(call BuildPackage,$(PKG_NAME)_s_modbus))
$(eval $(call BuildPackage,$(PKG_NAME)_s_opcua))
