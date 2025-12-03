# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling
# WARNING: You should contribute changes to https://gitlab.com/prpl-foundation/components/core/plugins/tr181-mqtt/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=tr181-mqtt
PKG_VERSION:=sah-next_v3.11.8
SHORT_DESCRIPTION:=TR-181 compatible MQTT client

PKG_SOURCE:=tr181-mqtt-sah-next_v3.11.8.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-mqtt/-/archive/sah-next_v3.11.8
PKG_HASH:=6e6c5e7a451a9444127cadd447d7e7ef549c316b645ecfa7edf5b66acc095306
PKG_BUILD_DIR:=$(BUILD_DIR)/tr181-mqtt-sah-next_v3.11.8
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=tr181-mqtt

PKG_RELEASE:=1

define SAHInit/Install
	install -d ${PKG_INSTALL_DIR}/etc/rc.d/
	ln -sfr ${PKG_INSTALL_DIR}/etc/init.d/$(COMPONENT) ${PKG_INSTALL_DIR}/etc/rc.d/S$(CONFIG_SAH_AMX_TR181_MQTT_START_ORDER)$(COMPONENT)
	ln -sfr ${PKG_INSTALL_DIR}/etc/init.d/$(COMPONENT) ${PKG_INSTALL_DIR}/etc/rc.d/K$(CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=prpl Foundation
  SUBMENU:=Ambiorix
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-mqtt
  DEPENDS += +libamxc
  DEPENDS += +libamxj
  DEPENDS += +libamxp
  DEPENDS += +libamxd
  DEPENDS += +libamxb
  DEPENDS += +libamxo
  DEPENDS += +libsahtrace
  DEPENDS += +libimtp
  DEPENDS += +libmosquitto
  DEPENDS += +mod-dmext
  DEPENDS += +libnetmodel
  DEPENDS += +libcares
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	TR-181 compatible MQTT client
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_TR181_MQTT_START_ORDER=$(CONFIG_SAH_AMX_TR181_MQTT_START_ORDER) CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER) CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_USER) CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_GROUP) CONFIG_DEFAULT_CIPHER_SUITE_LIST=$(CONFIG_DEFAULT_CIPHER_SUITE_LIST))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(PKG_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_TR181_MQTT_START_ORDER=$(CONFIG_SAH_AMX_TR181_MQTT_START_ORDER) CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER) CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_USER) CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_GROUP) CONFIG_DEFAULT_CIPHER_SUITE_LIST=$(CONFIG_DEFAULT_CIPHER_SUITE_LIST))

	$(call SAHInit/Install)
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(PKG_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(PKG_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include CONFIG_SAH_AMX_TR181_MQTT_START_ORDER=$(CONFIG_SAH_AMX_TR181_MQTT_START_ORDER) CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER=$(CONFIG_SAH_AMX_TR181_MQTT_STOP_ORDER) CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_USER=$(CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_USER) CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_GROUP=$(CONFIG_SAH_AMX_TR181_MQTT_RUN_AS_GROUP) CONFIG_DEFAULT_CIPHER_SUITE_LIST=$(CONFIG_DEFAULT_CIPHER_SUITE_LIST))
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
