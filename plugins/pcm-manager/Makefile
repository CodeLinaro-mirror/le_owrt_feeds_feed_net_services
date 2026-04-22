# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling (version 2.40.6)
# WARNING: You should contribute changes to https://gitlab.com/prpl-foundation/components/core/plugins/tr181-pcm/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=pcm-manager
RAW_VERSION:=sah-next-4.1_v1.0.2
PKG_VERSION:=$(if $(filter v0% v1% v2% v3% v4% v5% v6% v7% v8% v9%,$(RAW_VERSION)),$(patsubst v%,%,$(RAW_VERSION)),$(RAW_VERSION))
SHORT_DESCRIPTION:=Upgrade Persistent Configuration Manager

PKG_SOURCE:=tr181-pcm-sah-next-4.1_v1.0.2.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-pcm/-/archive/sah-next-4.1_v1.0.2
PKG_HASH:=33a59950078f5769cd85b4dee780e8b1fe3c62a3ac4e0c44a12cb252186446e0
PKG_BUILD_DIR:=$(BUILD_DIR)/tr181-pcm-sah-next-4.1_v1.0.2
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=pcm-manager

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/S$(CONFIG_SAH_AMX_PCM_START_ORDER)$(COMPONENT)
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/K$(CONFIG_SAH_AMX_PCM_STOP_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=prpl Foundation
  SUBMENU:=TR-181 Managers
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/prpl-foundation/components/core/plugins/tr181-pcm
  DEPENDS += +amxrt
  DEPENDS += +libamxc
  DEPENDS += +libamxd
  DEPENDS += +libamxp
  DEPENDS += +libamxb
  DEPENDS += +libamxo
  DEPENDS += +libamxm
  DEPENDS += +libamxj
  DEPENDS += +libsahtrace
  DEPENDS += +mod-dmext
  DEPENDS += +mod-pcm-svc
  DEPENDS += +libxml2
  DEPENDS += +SAH_AMX_PCM_TARBALL:libarchive
  DEPENDS += +libopenssl
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	Upgrade Persistent Configuration Manager
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_AMX_PCM_START_ORDER=$(CONFIG_SAH_AMX_PCM_START_ORDER) CONFIG_SAH_AMX_PCM_STOP_ORDER=$(CONFIG_SAH_AMX_PCM_STOP_ORDER) CONFIG_SAH_AMX_PCM_TARBALL=$(CONFIG_SAH_AMX_PCM_TARBALL) CONFIG_SAH_AMX_PCM_RUN_AS_USER=$(CONFIG_SAH_AMX_PCM_RUN_AS_USER) CONFIG_SAH_AMX_PCM_RUN_AS_GROUP=$(CONFIG_SAH_AMX_PCM_RUN_AS_GROUP))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_AMX_PCM_START_ORDER=$(CONFIG_SAH_AMX_PCM_START_ORDER) CONFIG_SAH_AMX_PCM_STOP_ORDER=$(CONFIG_SAH_AMX_PCM_STOP_ORDER) CONFIG_SAH_AMX_PCM_TARBALL=$(CONFIG_SAH_AMX_PCM_TARBALL) CONFIG_SAH_AMX_PCM_RUN_AS_USER=$(CONFIG_SAH_AMX_PCM_RUN_AS_USER) CONFIG_SAH_AMX_PCM_RUN_AS_GROUP=$(CONFIG_SAH_AMX_PCM_RUN_AS_GROUP))

	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_AMX_PCM_START_ORDER=$(CONFIG_SAH_AMX_PCM_START_ORDER) CONFIG_SAH_AMX_PCM_STOP_ORDER=$(CONFIG_SAH_AMX_PCM_STOP_ORDER) CONFIG_SAH_AMX_PCM_TARBALL=$(CONFIG_SAH_AMX_PCM_TARBALL) CONFIG_SAH_AMX_PCM_RUN_AS_USER=$(CONFIG_SAH_AMX_PCM_RUN_AS_USER) CONFIG_SAH_AMX_PCM_RUN_AS_GROUP=$(CONFIG_SAH_AMX_PCM_RUN_AS_GROUP))
	$(call SAHInit/Install,$(STAGING_DIR))
endef

define Package/$(PKG_NAME)/install
	if [ -d $(PKG_INSTALL_DIR) ]; then \
		$(CP) $(PKG_INSTALL_DIR)/* $(1)/; \
	fi
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
