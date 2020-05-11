---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714528"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Gibt an, welche Art von Informationen für einen bestimmten Computer abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Felder
 `MCIF_NAME`\
 Initialisieren/verwenden `bstrName` Sie das Feld in der Struktur.

 `MCIF_FLAGS`\
 Initialisieren/verwenden `Flags` Sie das Feld in der Struktur.

 `MIF_ALL`\
 Initialisieren/Verwenden aller Felder in der Struktur.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden an die [GetMachineInfo-Methode](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) übergeben, um anzugeben, welche Member der [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Struktur initialisiert werden sollen.

 Wird auch `Fields` im Element `MACHINE_INFO` der Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem `OR`bitwise kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
