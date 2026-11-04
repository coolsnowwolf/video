# SPDX-License-Identifier: GPL-2.0-only
include $(TOPDIR)/rules.mk

PKG_NAME:=libass
PKG_VERSION:=0.17.5
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/libass/libass/tar.gz/refs/tags/$(PKG_VERSION)?
PKG_HASH:=fa286fc9ee1ba3b932703a3df7b8474d01dc8abe29ec69b6fa68781dc4bf7acc
PKG_LICENSE:=ISC
PKG_LICENSE_FILES:=COPYING
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/libass
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=ASS/SSA subtitle renderer
  URL:=https://github.com/libass/libass
  DEPENDS:=+libfreetype +fribidi +harfbuzz +fontconfig
endef

MESON_ARGS += \
	-Ddefault_library=shared \
	-Dfontconfig=enabled \
	-Ddirectwrite=disabled \
	-Dcoretext=disabled \
	-Dlibunibreak=disabled \
	-Dtest=disabled \
	-Dcompare=disabled \
	-Dprofile=disabled \
	-Dfuzz=disabled \
	-Dcheckasm=disabled

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/ass $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/include/ass/*.h $(1)/usr/include/ass/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libass.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libass.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libass/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libass.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libass))
