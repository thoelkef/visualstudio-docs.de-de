---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714330"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Gibt die Flags für die Debugmodulinformationen an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Felder
 `MIF_NONE`\
 Initialisieren/Verwenden von keinem der Felder in der Struktur.

 `MIF_NAME`\
 Initialisieren/verwenden `m_bstrName` Sie das Feld in der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.

 `MIF_URL`\
 Initialisieren/verwenden `m_bstrUrl` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_VERSION`\
 Initialisieren/verwenden `m_bstrVersion` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_DEBUGMESSAGE`\
 Initialisieren/verwenden `m_bstrDebugMessage` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_LOADADDRESS`\
 Initialisieren/verwenden `m_addrLoadAddress` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_PREFFEREDADDRESS`\
 Initialisieren/verwenden `m_addrPreferredLoadAddress` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_SIZE`\
 Initialisieren/verwenden `m_dwSize` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_LOADORDER`\
 Initialisieren/verwenden `m_dwLoadOrder` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_TIMESTAMP`\
 Initialisieren/verwenden `m_TimeStamp` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_URLSYMBOLLOCATION`\
 Initialisieren/verwenden `m_bstrUrlSymbolLocation` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_FLAGS`\
 Initialisieren/verwenden `m_dwModuleFlags` Sie das `MODULE_INFO` Feld in der Struktur.

 `MIF_ALLFIELDS`\
 Initialisieren/Verwenden aller Felder in `MODULE_INFO` der Struktur.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden als Argument an die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) übergeben, um anzugeben, welche Felder der [MODULE_INFO-Struktur](../../../extensibility/debugger/reference/module-info.md) initialisiert werden sollen.

 Diese Werte werden auch `MODULE_INFO` in der Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem `OR`bitwise kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
