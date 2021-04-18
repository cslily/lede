#
# Copyright (C) 2008-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=jme-eth-driver
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/jme
  SUBMENU:=Other modules
  TITLE:=JMicron(R) PCI-Express Gigabit Ethernet support
  DEPENDS:=@PCI_SUPPORT +kmod-mii
  KCONFIG:=
  FILES:=$(LINUX_DIR)/drivers/net/ethernet/jme.ko
  AUTOLOAD:=$(call AutoLoad,30,jme,1)
endef

define KernelPackage/jme/description
 Kernel modules for JMicron(R) PCI-Express Gigabit Ethernet adapters
endef

EXTRA_KCONFIG:= \
	CONFIG_JME=m

EXTRA_CFLAGS:= \
	$(patsubst CONFIG_%, -DCONFIG_%=1, $(patsubst %=m,%,$(filter %=m,$(EXTRA_KCONFIG)))) \
	$(patsubst CONFIG_%, -DCONFIG_%=1, $(patsubst %=y,%,$(filter %=y,$(EXTRA_KCONFIG)))) \

MAKE_OPTS:= \
	$(KERNEL_MAKE_FLAGS) \
	M="$(PKG_BUILD_DIR)" \
	EXTRA_CFLAGS="$(EXTRA_CFLAGS)" \
	$(EXTRA_KCONFIG)

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		$(MAKE_OPTS) \
		modules
endef

$(eval $(call KernelPackage,jme))
