---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714310"
---
# <a name="module_info"></a>MODULE_INFO
Beschreibt ein bestimmtes Modul (DLL, EXE oder Assembly).

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Member
 `dwValidFields`\
 Eine Kombination von [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Flags aus der MODULE_INFO_FIELDS-Enumeration, die angibt, welche Felder ausgefüllt werden.

 `m_bstrName`\
 Der Modulname.

 `m_bstrUrl`\
 Die Modul-URL.

 `m_bstrVersion`\
 Die Modulversion.

 `m_bstrDebugMessage`\
 Eine optionale Meldung zum Modul, z. B. "Symbole können nicht geladen werden."

 `m_addrLoadAddress`\
 Die Ladeadresse des Moduls.

 `m_addrPreferredLoadAddress`\
 Die bevorzugte Ladeadresse des Moduls.

 `m_dwSize`\
 Die Modulgröße.

 `m_dwLoadOrder`\
 Die Modulladereihenfolge.

 `m_TimeStamp`\
 Der Zeitpunkt, zu dem die Symboldatei zuletzt geändert wurde.

 `m_bstrUrlSymbolLocation`\
 Der Speicherort der Symboldatei (z.\\B. ". ") im Modul angegeben. Wird als Startposition verwendet, um Symbole für ein Modul zu finden.

 `m_dwModuleFlags`\
 Eine Kombination von [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) Flags aus der MODULE_FLAGS-Enumeration, die das Modul beschreibt.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) übergeben, bei der sie ausgefüllt wird.

 Diese Struktur entspricht jedem Modul, das im **Fenster Module aufgeführt** ist.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
