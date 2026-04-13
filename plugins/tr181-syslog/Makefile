# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling (version 2.40.3)
# WARNING: You should contribute changes to https://gitlab.com/prpl-foundation/components/core/plugins/tr181-syslog/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=tr181-syslog
RAW_VERSION:=sah-next-4.1_v1.0.2
PKG_VERSION:=$(if $(filter v0% v1% v2% v3% v4% v5% v6% v7% v8% v9%,$(RAW_VERSION)),$(patsubst v%,%,$(RAW_VERSION)),$(RAW_VERSION))
SHORT_DESCRIPTION:=TR-181 compatible syslog

PKG_SOURCE:=tr181-syslog-sah-next-4.1_v1.0.2.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-syslog/-/archive/sah-next-4.1_v1.0.2
PKG_HASH:=e9dfba030118e3c4a79d3af02d835e2d34c076663a72e326b2c72211e49a718f
PKG_BUILD_DIR:=$(BUILD_DIR)/tr181-syslog-sah-next-4.1_v1.0.2
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=tr181-syslog

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/S$(CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER)$(COMPONENT)
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/K$(CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=prpl Foundation
  SUBMENU:=Ambiorix
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-syslog
  DEPENDS += +libamxc
  DEPENDS += +libamxp
  DEPENDS += +libamxd
  DEPENDS += +libamxo
  DEPENDS += +libamxm
  DEPENDS += +libamxb
  DEPENDS += +libsahtrace
  DEPENDS += +libnetmodel
  DEPENDS += +amxrt
  DEPENDS += +mod-dmext
  DEPENDS += +libopenssl
  DEPENDS += +logrotate
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	TR-181 compatible syslog
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER=$(CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER) CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER) CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_USER) CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_GROUP))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER=$(CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER) CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER) CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_USER) CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_GROUP))

	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER=$(CONFIG_SAH_AMX_TR181_SYSLOG_START_ORDER) CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_SYSLOG_STOP_ORDER) CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_USER) CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_SYSLOG_RUN_AS_GROUP))
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
