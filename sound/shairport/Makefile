#
# Copyright (C) 2011 OpenWrt.org  
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
# updated to work with latest source from abrasive
#

include $(TOPDIR)/rules.mk

PKG_NAME:=shairport_new
PKG_VERSION:=0.08
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/sm3rt/shairport.git
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz


PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk


define Package/shairport_new/Default
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=ShairPort_new
  URL:=http://mafipulation.org/
endef


define Package/shairport_new
  $(Package/shairport_new/Default)
#  DEPENDS:= +libpthread +libopenssl +alsa-lib +libavahi-client +avahi-utils +libao
   DEPENDS:= +libpthread +libopenssl +alsa-lib +libavahi-client
endef

define Package/shairport_new/description
  ShairPort is server software that implements the RAOP protocol for
  playback of music streamed from a compatible remote client.
endef


define Package/shairport_new/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/shairport $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) ./files/init.d/airplay $(1)/etc/init.d/
	$(INSTALL_DATA) ./files/config/airplay $(1)/etc/config/
	$(INSTALL_DATA) ./files/asound.conf $(1)/etc/
	$(INSTALL_DATA) ./files/libao.conf $(1)/etc/
endef


$(eval $(call BuildPackage,shairport_new))
