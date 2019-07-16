---
title: MODULE_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 04a8756fd7eb2a4b938ebcd2d5f4754509b704e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205219"
---
# <a name="moduleinfo"></a>MODULE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt ein bestimmtes Modul (DLL, EXE-Datei oder Assembly).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
