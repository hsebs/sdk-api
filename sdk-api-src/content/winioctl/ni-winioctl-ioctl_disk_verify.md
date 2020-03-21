---
UID: NI:winioctl.IOCTL_DISK_VERIFY
title: IOCTL_DISK_VERIFY
description: Verifies the specified extent on a fixed disk.
old-location: fs\ioctl_disk_verify.htm
tech.root: FileIO
ms.assetid: 156b217d-6cdc-4802-b711-8845934e277b
ms.date: 12/05/2018
ms.keywords: IOCTL_DISK_VERIFY, IOCTL_DISK_VERIFY control, IOCTL_DISK_VERIFY control code [Files], _win32_ioctl_disk_verify, base.ioctl_disk_verify, fs.ioctl_disk_verify, winioctl/IOCTL_DISK_VERIFY
f1_keywords:
- winioctl/IOCTL_DISK_VERIFY
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
- IOCTL_DISK_VERIFY
targetos: Windows
req.typenames: 
req.redist: 
---

# IOCTL_DISK_VERIFY IOCTL

## -description

Verifies the specified extent on a fixed disk.

To perform this operation, call the [**DeviceIoControl**](../ioapiset/nf-ioapiset-deviceiocontrol.md) function with the following parameters.

```cpp
BOOL DeviceIoControl(
  (HANDLE) hDevice,                // handle to device
  IOCTL_DISK_VERIFY,               // dwIoControlCode
  (LPVOID) lpInBuffer,             // input buffer
  (DWORD) nInBufferSize,           // size of input buffer
  NULL,                            // lpOutBuffer
  0,                               // nOutBufferSize
  (LPDWORD) lpBytesReturned,       // number of bytes returned
  (LPOVERLAPPED) lpOverlapped      // OVERLAPPED structure
);
```

## -parameters

### -param hDevice [in]

A handle to the disk.

To retrieve a device handle, call the [**CreateFile**](../fileapi/nf-fileapi-createfilew.md) function.

### -param dwIoControlCode [in]

The control code for the operation.

Use **IOCTL_DISK_VERIFY** for this operation.

### -param lpInBuffer [in, optional]

A pointer to the input buffer that contains the [**VERIFY_INFORMATION**](ns-winioctl-verify_information.md) data to be set.

### -param nInBufferSize [in]

The size of the input buffer, in bytes. It must be >= **sizeof**(VERIFY_INFORMATION).

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

 [DeviceIoControl](../ioapiset/nf-ioapiset-deviceiocontrol.md), [Disk Management Control Codes](/windows/win32/FileIO/disk-management-control-codes), [VERIFY_INFORMATION](ns-winioctl-verify_information.md)