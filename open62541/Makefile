include $(TOPDIR)/rules.mk

PKG_NAME:=open62541
PKG_VERSION:=1.0.6
PKG_RELEASE:=1
PKG_LICENSE:=MPL-2.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/open62541/open62541.git
PKG_MIRROR_HASH:=f2c289b8a2b57bb6c5c957db8bd13a8e1b8d6deb0a0ae859bb1ec65cbedeeb03
PKG_SOURCE_VERSION:=982f07963af7a0676ef30ea10a96acdd60e4d3f9

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Open source implementation of OPC UA
  URL:=http://open62541.org/
  DEPENDS:=+libc +libpthread
endef

define Package/$(PKG_NAME)/description
Open source implementation of OPC UA (OPC Unified Architecture) aka IEC 62541 licensed under Mozilla Public License v2.0
endef

CMAKE_SOURCE_DIR=$(PKG_BUILD_DIR)
CMAKE_OPTIONS+= -DBUILD_SHARED_LIBS=ON \
	-DCMAKE_BUILD_TYPE=MinSizeRel

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/open62541/ $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/*.pc $(1)/usr/lib/pkgconfig/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopen62541.so* $(1)/usr/lib/
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopen62541.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
