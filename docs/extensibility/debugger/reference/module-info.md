---
title: "MODULE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO"
helpviewer_keywords: 
  - "MODULE_INFO-Struktur"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt ein bestimmtes Modul \(EXE oder DLL\) \- Assembly.  
  
## Syntax  
  
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
  
```c#  
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
  
## Mitglieder  
 dwValidFields  
 Eine Kombination von Flags aus der [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)\-Enumeration, die angibt, welche Felder geändert werden.  
  
 m\_bstrName  
 Der Modulname.  
  
 m\_bstrUrl  
 Das Modul URL.  
  
 m\_bstrVersion  
 Die Modulversion.  
  
 m\_bstrDebugMessage  
 Eine optionale Nachricht über das Modul z. B. „Symbole kann nicht geladen werden“.  
  
 m\_addrLoadAddress  
 Die adresse Laden von Modulen unterdrücken.  
  
 m\_addrPreferredLoadAddress  
 Die bevorzugten Ladeadresse des Moduls.  
  
 m\_dwSize  
 Die Größe des Moduls.  
  
 m\_dwLoadOrder  
 Das Modul ladereihenfolge.  
  
 m\_TimeStamp  
 Die Uhrzeit, wann die Symboldateien zuletzt geändert wurde.  
  
 m\_bstrUrlSymbolLocation  
 Der Speicherort der Symboldatei \(beispielsweise „.  \\ "\) im Modul.  Wird als Anfangsposition, an dem der Symbole für ein Modul zu suchen.  
  
 m\_dwModuleFlags  
 Eine Kombination von Flags aus der [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)\-Enumeration, der das Modul beschreibt.  
  
## Hinweise  
 Diese Struktur wird auf die [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)\-Methode übergeben, in der er eingetragen wird.  
  
 Diese Struktur ist für jedes Modul, das im **Module** Fenster aufgelistet ist.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)