---
title: MODULE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 989b5c24fc3d99c99f8a979ded2994f767a1e1bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910843"
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
 dwValidFields  
 Eine Kombination von Flags aus der [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Enumeration, der angibt, welche Felder ausgefüllt sind.  
  
 m_bstrName  
 Der Modulname.  
  
 m_bstrUrl  
 Die Modul-URL.  
  
 m_bstrVersion  
 Die Modulversion.  
  
 m_bstrDebugMessage  
 Eine optionale Nachricht, die über das Modul, z. B. "Symbole geladen werden nicht möglich."  
  
 m_addrLoadAddress  
 Die Ladeadresse des Moduls.  
  
 m_addrPreferredLoadAddress  
 Die bevorzugte Ladeadresse des Moduls.  
  
 m_dwSize  
 Die Modulgröße.  
  
 m_dwLoadOrder  
 Die Modul-Load-Reihenfolge.  
  
 m_TimeStamp  
 Die Zeit, die Symboldatei zuletzt geändert wurde.  
  
 m_bstrUrlSymbolLocation  
 Der Speicherort der Symboldatei (z. B. ".\\") im Modul angegeben. Zum Suchen von Symbolen für ein Modul als einen Startort anzugeben.  
  
 m_dwModuleFlags  
 Eine Kombination von Flags aus der [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) -Enumeration, die diesem Modul erläutert.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) Methode, in denen es ausgefüllt wird.  
  
 Jedes Modul aufgeführt, die dieser Struktur entspricht dem **Module** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)