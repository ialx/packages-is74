include $(TOPDIR)/rules.mk

PKG_NAME:=speedtestcpp_is74
PKG_VERSION:=1.20.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/ialx/speedtestcpp_is74/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=9f5f5888320891329bb7395e086a189589e1170151b4cdf759c503f180c37ce4

PKG_MAINTAINER:=Alexander V. Ignatyev <ialx84@ya.ru>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/libspeedtestcpp_is74
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=library for ookla's speedtest
  DEPENDS:=+libcurl +libstdcpp
  URL:=https://github.com/ialx/speedtestcpp_is74
endef

define Package/libspeedtestcpp_is74/description
  Shared library that provides support for ookla's speedtest
endef

define Package/speedtestcpp_is74
  SECTION:=net
  CATEGORY:=Network
  TITLE:=SpeedTest++
  DEPENDS:=+libspeedtestcpp_is74 +libstdcpp
  URL:=https://github.com/ialx/speedtestcpp_is74
  PROVIDES:=speedtestpp_is74
endef

define Package/speedtestcpp_is74/description
  Yet another unofficial speedtest.net client cli interface
  forked from taganaka's SpeedTest with few improments and
  lesser depends.
endef

TARGET_CXXFLAGS += --std=c++23 -fPIC

define Build/Configure
endef

define Package/libspeedtestcpp_is74/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libspeedtestcpp.so* $(1)/usr/lib/
endef

define Package/speedtestcpp_is74/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/speedtest $(1)/usr/bin/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib $(1)/usr/include/speedtest
	$(CP) $(PKG_BUILD_DIR)/libspeedtestcpp.{so*,a} $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/include/speedtest/*.hpp $(1)/usr/include/speedtest/
endef

$(eval $(call BuildPackage,libspeedtestcpp_is74))
$(eval $(call BuildPackage,speedtestcpp_is74))
