---
title: MODULE_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 6e28756873339d504efba417d9e2fe2cc00000b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126715"
---
# <a name="moduleinfo"></a>MODULE_INFO
Beschreibt ein bestimmtes Modul (DLL, EXE-Datei oder Assembly) an.  
  
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
 Eine Kombination aus Flags aus der [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) -Enumeration, der angibt, welche Felder ausgefüllt sind.  
  
 m_bstrName  
 Der Modulname.  
  
 m_bstrUrl  
 Die Modul-URL.  
  
 m_bstrVersion  
 Die Version des Moduls.  
  
 m_bstrDebugMessage  
 Eine optionale Meldung, die zum Modul, z. B. "Symbole geladen werden nicht möglich."  
  
 m_addrLoadAddress  
 Adresse des Moduls.  
  
 m_addrPreferredLoadAddress  
 Die bevorzugte Adresse des Moduls.  
  
 m_dwSize  
 Die Modulgröße.  
  
 m_dwLoadOrder  
 Die Ladereihenfolge von Modul.  
  
 m_TimeStamp  
 Die Uhrzeit, die letzten der Symboldatei Änderung.  
  
 m_bstrUrlSymbolLocation  
 Der Speicherort, der die Symboldatei (z. B. ".\\") im Modul angegeben. Als Anfangsposition verwendet, um die Symbole für ein Modul zu suchen.  
  
 m_dwModuleFlags  
 Eine Kombination aus Flags aus der [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) -Enumeration, die das Modul beschreibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) Methode, wo in gefüllt.  
  
 Diese Struktur entspricht jedes Modul aufgeführt, die der **Module** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)