---
UID: NI:winioctl.IOCTL_DISK_IS_WRITABLE
title: IOCTL_DISK_IS_WRITABLE
description: Determines whether the specified disk is writable.
old-location: fs\ioctl_disk_is_writable.htm
tech.root: FileIO
ms.assetid: 0b56ea0d-95ae-4306-9866-b4b5e985ed43
ms.date: 12/05/2018
ms.keywords: IOCTL_DISK_IS_WRITABLE, IOCTL_DISK_IS_WRITABLE control, IOCTL_DISK_IS_WRITABLE control code [Files], base.ioctl_disk_is_writable, fs.ioctl_disk_is_writable, winioctl/IOCTL_DISK_IS_WRITABLE
f1_keywords:
- winioctl/IOCTL_DISK_IS_WRITABLE
dev_langs:
- c++
req.header: winioctl.h
req.include-header: Windows.h
req.target-type: Windows
req.target-min-winverclnt: Windows XP [desktop apps only]
req.target-min-winversvr: Windows Server 2003 [desktop apps only]
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
- IOCTL_DISK_IS_WRITABLE
targetos: Windows
req.typenames: 
req.redist: 
---

# IOCTL_DISK_IS_WRITABLE IOCTL

## -description

Determines whether the specified disk is writable.

To perform this operation, call the [**DeviceIoControl**](../ioapiset/nf-ioapiset-deviceiocontrol.md) function with the following parameters.

```cpp
BOOL DeviceIoControl(
  (HANDLE) hDevice,               // handle to device
  IOCTL_DISK_IS_WRITABLE, // dwIoControlCode
  NULL,                           // lpInBuffer
  0,                              // nInBufferSize
  NULL ,                          // lpOutBuffer
  0 ,                             // nOutBufferSize
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

Use **IOCTL_DISK_IS_WRITABLE** for this operation.

### -param lpInBuffer [in, optional]

Not used with this operation. Set to **NULL**.

### -param nInBufferSize [in]

The size of the input buffer, in bytes. Set to 0 (zero).

### -param lpOutBuffer [out, optional]

Not used with this operation. Set to **NULL**.

### -param nOutBufferSize [in]

The size of the input buffer, in bytes. Set to 0 (zero).

### -param lpBytesReturned [out, optional]

A pointer to a variable that receives the size of the data stored in the output buffer, in bytes.

### -param lpOverlapped [in, out, optional]

A pointer to an [**OVERLAPPED**](../minwinbase/ns-minwinbase-overlapped.md) structure.

## -returns

If the operation completes successfully, the return value is nonzero.

If the operation fails or is pending, the return value is zero. To get extended error information, call [**GetLastError**](../errhandlingapi/nf-errhandlingapi-getlasterror.md).

## -see-also

[DeviceIoControl](../ioapiset/nf-ioapiset-deviceiocontrol.md), [Disk Management Control Codes](/windows/win32/FileIO/disk-management-control-codes)
