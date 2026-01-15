# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling
# WARNING: You should contribute changes to https://gitlab.com/prpl-foundation/components/core/plugins/tr181-dnssd/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=tr181-dnssd
PKG_VERSION:=sah-next_v1.3.1
SHORT_DESCRIPTION:=dns service discovery plugin

PKG_SOURCE:=tr181-dnssd-sah-next_v1.3.1.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-dnssd/-/archive/sah-next_v1.3.1
PKG_HASH:=6c0ceda1c4462f6e18115aa629cbeffa2f57fc07e90a9ddc06244d40ba98b479
PKG_BUILD_DIR:=$(BUILD_DIR)/tr181-dnssd-sah-next_v1.3.1
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=tr181-dnssd

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/S$(CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER)$(COMPONENT)
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/K$(CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=prpl Foundation
  SUBMENU:=Ambiorix
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-dnssd
  DEPENDS += +libamxb
  DEPENDS += +libamxc
  DEPENDS += +libamxd
  DEPENDS += +libamxo
  DEPENDS += +libamxp
  DEPENDS += +libamxm
  DEPENDS += +libamxj
  DEPENDS += +libsahtrace
  DEPENDS += +libnetmodel
  DEPENDS += +umdns
  DEPENDS += +rpcd
  DEPENDS += +mod-dmext
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	dns service discovery plugin
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER=$(CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER) CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER) CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_USER) CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_GROUP))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(PKG_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER=$(CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER) CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER) CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_USER) CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_GROUP))

	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(PKG_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER=$(CONFIG_SAH_AMX_TR181_DNSSD_START_ORDER) CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_DNSSD_STOP_ORDER) CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_USER) CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_DNSSD_RUN_AS_GROUP))
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
