# Vulkan

## Vulkan for Raspberry Pi

```bash
$ sudo apt install mesa-vulkan-drivers
$ sudo apt install vulkan-tools
```

`mesa-vulkan-drivers`: Mesa Vulkan graphics drivers

- Vulkan is a low-overhead 3D graphics and compute API.
- This package includes Vulkan drivers provided by the Mesa project.

`vulkan-tools`: Miscellaneous Vulkan utilities

- This package provides utilities for Vulkan, including `vulkaninfo`.

```bash
$ vulkaninfo --summary
WARNING: v3dv is neither a complete nor a conformant Vulkan implementation. Testing use only.
WARNING: lavapipe is not a conformant vulkan implementation, testing use only.
==========
VULKANINFO
==========

Vulkan Instance Version: 1.2.162


Instance Extensions: count = 18
-------------------------------
VK_EXT_acquire_xlib_display            : extension revision 1
VK_EXT_debug_report                    : extension revision 9
VK_EXT_debug_utils                     : extension revision 2
VK_EXT_direct_mode_display             : extension revision 1
VK_EXT_display_surface_counter         : extension revision 1
VK_KHR_device_group_creation           : extension revision 1
VK_KHR_display                         : extension revision 23
VK_KHR_external_fence_capabilities     : extension revision 1
VK_KHR_external_memory_capabilities    : extension revision 1
VK_KHR_external_semaphore_capabilities : extension revision 1
VK_KHR_get_display_properties2         : extension revision 1
VK_KHR_get_physical_device_properties2 : extension revision 1
VK_KHR_get_surface_capabilities2       : extension revision 1
VK_KHR_surface                         : extension revision 25
VK_KHR_surface_protected_capabilities  : extension revision 1
VK_KHR_wayland_surface                 : extension revision 6
VK_KHR_xcb_surface                     : extension revision 6
VK_KHR_xlib_surface                    : extension revision 6

Instance Layers: count = 2
--------------------------
VK_LAYER_MESA_device_select Linux device selection layer 1.2.73  version 1
VK_LAYER_MESA_overlay       Mesa Overlay layer           1.1.73  version 1

Devices:
========
GPU0:
	apiVersion         = 4194459 (1.0.155)
	driverVersion      = 83898373 (0x5003005)
	vendorID           = 0x14e4
	deviceID           = 0x002a
	deviceType         = PHYSICAL_DEVICE_TYPE_INTEGRATED_GPU
	deviceName         = V3D 4.2
GPU1:
	apiVersion         = 4194306 (1.0.2)
	driverVersion      = 1 (0x0001)
	vendorID           = 0x10005
	deviceID           = 0x0000
	deviceType         = PHYSICAL_DEVICE_TYPE_CPU
	deviceName         = llvmpipe (LLVM 11.0.1, 128 bits)
	driverID           = DRIVER_ID_MESA_LLVMPIPE
	driverName         = llvmpipe
	driverInfo         = Mesa 20.3.5 (LLVM 11.0.1)
	conformanceVersion = 1.0.0.0
```
