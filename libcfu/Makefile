include $(TOPDIR)/rules.mk

PKG_NAME:=libcfu
PKG_VERSION:=0.03
PKG_RELEASE:=1
PKG_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/humble-zh/libcfu.git
PKG_MIRROR_HASH:=54b67e4c681d4ca68e687e4273923145895413cd4e6ca1b82ff62ea8891df48a
PKG_SOURCE_VERSION:=a5914e2d576875036db1ca6d7ac30d5b624968cd

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=a library of thread-safe functions and data structure
  URL:=http://libcfu.sourceforge.net/
  DEPENDS:=+libpthread
endef

define Package/$(PKG_NAME)/description
Libcfu is a library of tools that I have found useful, particularly when developing multithreaded software. It currently includes a hash table, a linked list, self-extending strings, a configuration file parser, a simple timer, and a thread queue.
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcfu.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
