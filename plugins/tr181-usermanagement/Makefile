# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling
# WARNING: You should contribute changes to https://gitlab.com/prpl-foundation/components/core/plugins/tr181-usermanagement/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=tr181-usermanagement
PKG_VERSION:=sah-next-4.1_v0.31.0
SHORT_DESCRIPTION:=tr181 user management plugin

PKG_SOURCE:=tr181-usermanagement-sah-next-4.1_v0.31.0.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-usermanagement/-/archive/sah-next-4.1_v0.31.0
PKG_HASH:=5780637fd63c1db2a5c824e50de7b04d1214e1da1a8731ae59199615c856e4ea
PKG_BUILD_DIR:=$(BUILD_DIR)/tr181-usermanagement-sah-next-4.1_v0.31.0
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=tr181-usermanagement

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/S$(CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER)$(COMPONENT)
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/K$(CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=prpl Foundation
  SUBMENU:=TR-181 Managers
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-usermanagement
  DEPENDS += +libamxc
  DEPENDS += +libamxd
  DEPENDS += +libamxo
  DEPENDS += +libamxb
  DEPENDS += +yajl
  DEPENDS += +libamxj
  DEPENDS += +libsahtrace
  DEPENDS += +libopenssl
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	tr181 user management plugin
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER=$(CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER) CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER=$(CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER) CONFIG_SAH_AMX_USERMANAGEMENT_DISABLE_SHA512=$(CONFIG_SAH_AMX_USERMANAGEMENT_DISABLE_SHA512))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(PKG_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER=$(CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER) CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER=$(CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER) CONFIG_SAH_AMX_USERMANAGEMENT_DISABLE_SHA512=$(CONFIG_SAH_AMX_USERMANAGEMENT_DISABLE_SHA512))

	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(PKG_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER=$(CONFIG_SAH_AMX_USERMANAGEMENT_START_ORDER) CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER=$(CONFIG_SAH_AMX_USERMANAGEMENT_STOP_ORDER) CONFIG_SAH_AMX_USERMANAGEMENT_DISABLE_SHA512=$(CONFIG_SAH_AMX_USERMANAGEMENT_DISABLE_SHA512))
	$(call SAHInit/Install,$(STAGING_DIR))
endef

define Package/$(PKG_NAME)/install
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
	if [ -d ./files ]; then \
		$(CP) ./files/* $(1)/; \
	fi
	find $(1) -name *.a -exec rm {} +;
	find $(1) -name *.h -exec rm {} +;
	find $(1) -name *.pc -exec rm {} +;
endef

define Package/$(PKG_NAME)/config
	source "$(SOURCE)/Config.in"
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
