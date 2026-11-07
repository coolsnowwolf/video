# SPDX-License-Identifier: GPL-2.0-only
include $(TOPDIR)/rules.mk

PKG_NAME:=accel-support
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define Package/accel-support
  SECTION:=hardware
  CATEGORY:=Hardware support
  TITLE:=Render and compute device support
  DEPENDS:=+procd
  PKGARCH:=all
  USERID:=:render=43
endef

define Package/accel-support/description
 Allocates the render group and grants it access to GPU render and compute
 devices, using hotplug scripts supported by this procd version.
endef

define Build/Compile
endef

define Package/accel-support/install
	$(INSTALL_DIR) $(1)/etc/hotplug.d/drm $(1)/etc/hotplug.d/accel $(1)/etc/hotplug.d/kfd
	$(INSTALL_DATA) ./files/30-render $(1)/etc/hotplug.d/drm/30-render
	$(INSTALL_DATA) ./files/30-render $(1)/etc/hotplug.d/accel/30-render
	$(INSTALL_DATA) ./files/30-render $(1)/etc/hotplug.d/kfd/30-render
endef

$(eval $(call BuildPackage,accel-support))
