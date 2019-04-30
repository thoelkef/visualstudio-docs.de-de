---
title: MODULE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3a11e368b6260d00f3f6ed0b19d94aa26bd31a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865465"
---
# <a name="moduleinfo"></a>MODULE_INFO
Beschreibt ein bestimmtes Modul (DLL, EXE-Datei oder Assembly).

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
 DwValidFields eine Kombination von Flags aus der [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Enumeration, der angibt, welche Felder ausgefüllt sind.

 M_bstrName den Namen des Moduls.

 M_bstrUrl die Modul-URL.

 M_bstrVersion die Modulversion.

 M_bstrDebugMessage eine optionale Nachricht, die über das Modul, z. B. "Symbole geladen werden nicht möglich."

 M_addrLoadAddress die Ladeadresse des Moduls.

 M_addrPreferredLoadAddress die bevorzugte Ladeadresse des Moduls.

 M_dwSize die Modulgröße.

 M_dwLoadOrder die Ladereihenfolge Modul.

 M_TimeStamp die Zeit, die Symboldatei zuletzt geändert wurde.

 M_bstrUrlSymbolLocation den Speicherort der Symboldatei (z. B. ".\\") im Modul angegeben. Zum Suchen von Symbolen für ein Modul als einen Startort anzugeben.

 M_dwModuleFlags eine Kombination von Flags aus der [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) -Enumeration, die diesem Modul erläutert.

## <a name="remarks"></a>Hinweise
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) Methode, in denen es ausgefüllt wird.

 Jedes Modul aufgeführt, die dieser Struktur entspricht dem **Module** Fenster.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)