---
UID: NI:winioctl.IOCTL_DISK_GET_DISK_ATTRIBUTES
title: IOCTL_DISK_GET_DISK_ATTRIBUTES
description: Retrieves the attributes of the specified disk device.
old-location: fs\ioctl_disk_get_disk_attributes.htm
tech.root: FileIO
ms.assetid: 3fa9fabb-91ef-4306-90b6-c3dd17f3e298
ms.date: 12/05/2018
ms.keywords: IOCTL_DISK_GET_DISK_ATTRIBUTES, IOCTL_DISK_GET_DISK_ATTRIBUTES control, IOCTL_DISK_GET_DISK_ATTRIBUTES control code [Files], fs.ioctl_disk_get_disk_attributes, winioctl/IOCTL_DISK_GET_DISK_ATTRIBUTES
f1_keywords:
- winioctl/IOCTL_DISK_GET_DISK_ATTRIBUTES
dev_langs:
- c++
req.header: winioctl.h
req.include-header: Windows.h
req.target-type: Windows
req.target-min-winverclnt: Windows 7 [desktop apps only]
req.target-min-winversvr: Windows Server 2008 R2 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
topic_type:
- APIRef
- kbSyntax
api_type:
- HeaderDef
api_location:
- WinIoCtl.h
api_name:
- IOCTL_DISK_GET_DISK_ATTRIBUTES
targetos: Windows
req.typenames: 
req.redist: 
---

# IOCTL_DISK_GET_DISK_ATTRIBUTES IOCTL

## -description

Retrieves the attributes of the specified disk device.

To perform this operation, call the [**DeviceIoControl**](../ioapiset/nf-ioapiset-deviceiocontrol.md) function with the following parameters.

```cpp
BOOL DeviceIoControl(
  (HANDLE) hDevice,               // handle to device
  IOCTL_DISK_GET_DISK_ATTRIBUTES, // dwIoControlCode
  NULL,                           // lpInBuffer
  0,                              // nInBufferSize
  (LPVOID) lpOutBuffer,           // output buffer
  (DWORD) nOutBufferSize,         // size of output buffer
  (LPDWORD) lpBytesReturned,      // number of bytes returned
  (LPOVERLAPPED) lpOverlapped     // OVERLAPPED structure
);
```

## -parameters

### -param hDevice [in]

A handle to the disk.

To retrieve a device handle, call the [**CreateFile**](../fileapi/nf-fileapi-createfilew.md) function.

### -param dwIoControlCode [in]

The control code for the operation.

Use **IOCTL_DISK_GET_DISK_ATTRIBUTES** for this operation.

### -param lpInBuffer [in, optional]

Not used with this operation. Set to **NULL**.

### -param nInBufferSize [in]

The size of the input buffer, in bytes. Set to 0 (zero).

### -param lpOutBuffer [out, optional]

A pointer to the output buffer that is to receive the [**GET_DISK_ATTRIBUTES**](ns-winioctl-get_disk_attributes.md) data returned by the operation.

If the output buffer is not large enough to store the data, the function returns **FALSE** and [**GetLastError**](../errhandlingapi/nf-errhandlingapi-getlasterror.md) returns **ERROR_INSUFFICIENT_BUFFER**.

### -param nOutBufferSize [in]

The size of the output buffer, in bytes. It must be >= **sizeof**(GET_DISK_ATTRIBUTES).

### -param lpBytesReturned [out, optional]

A pointer to a variable that receives the size of the data stored in the output buffer, in bytes.

### -param lpOverlapped [in, out, optional]

A pointer to an [**OVERLAPPED**](../minwinbase/ns-minwinbase-overlapped.md) structure.

## -returns

If the operation completes successfully, the return value is nonzero.

If the operation fails or is pending, the return value is zero. To get extended error information, call [**GetLastError**](../errhandlingapi/nf-errhandlingapi-getlasterror.md).

## -see-also

[DeviceIoControl](../ioapiset/nf-ioapiset-deviceiocontrol.md), [Disk Management Control Codes](/windows/win32/FileIO/disk-management-control-codes), [GET_DISK_ATTRIBUTES](ns-winioctl-get_disk_attributes.md), [IOCTL_DISK_SET_DISK_ATTRIBUTES](ni-winioctl-ioctl_disk_set_disk_attributes)
