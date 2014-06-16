include $(TOPDIR)/rules.mk

PKG_NAME:=shairport
PKG_VERSION:=1.0
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
#PKG_SOURCE_URL:=git://github.com/abrasive/shairport.git
PKG_SOURCE_URL:=git://github.com/plietar/shairport.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/shairport
  DEPENDS:= +libopenssl +alsa-lib
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=ShairPort
  URL:=http://mafipulation.org/
endef

define Package/shairport/description
ShairPort is server software that implements the RAOP protocol for
playback of music streamed from a compatible remote client.
endef

define Build/Configure
	(cd $(PKG_BUILD_DIR); \
	$(TARGET_CONFIGURE_OPTS) \
	CFLAGS="$(TARGET_CFLAGS) $(TARGET_CPPFLAGS)" \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	./configure \
	)
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) $(TARGET_CONFIGURE_OPTS)
endef

define Package/shairport/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config

	$(INSTALL_BIN) $(PKG_BUILD_DIR)/shairport $(1)/usr/bin/
	$(INSTALL_BIN) ./files/init.d/airplay $(1)/etc/init.d/
	$(INSTALL_DATA) ./files/config/airplay $(1)/etc/config/
endef

$(eval $(call BuildPackage,shairport))

