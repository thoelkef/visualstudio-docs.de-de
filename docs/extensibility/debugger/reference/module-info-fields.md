---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
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
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "MODULE_INFO_FIELDS-enumeration"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Flags mit der Modul Debuggen Informationen an.  
  
## Syntax  
  
```cpp#  
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
  
```c#  
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
  
## Mitglieder  
 MIF\_NONE  
 Initialisieren Sie\/Verwendung keiner der Felder in der Struktur.  
  
 MIF\_NAME  
 Initialisieren Sie verwenden das\/ `m_bstrName` Feld in der [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.  
  
 MIF\_URL  
 Initialisieren Sie verwenden das\/ `m_bstrUrl` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_VERSION  
 Initialisieren Sie verwenden das\/ `m_bstrVersion` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_DEBUGMESSAGE  
 Initialisieren Sie verwenden das\/ `m_bstrDebugMessage` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_LOADADDRESS  
 Initialisieren Sie verwenden das\/ `m_addrLoadAddress` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_PREFFEREDADDRESS  
 Initialisieren Sie verwenden das\/ `m_addrPreferredLoadAddress` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_SIZE  
 Initialisieren Sie verwenden das\/ `m_dwSize` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_LOADORDER  
 Initialisieren Sie verwenden das\/ `m_dwLoadOrder` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_TIMESTAMP  
 Initialisieren Sie verwenden das\/ `m_TimeStamp` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_URLSYMBOLLOCATION  
 Initialisieren Sie verwenden das\/ `m_bstrUrlSymbolLocation` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_FLAGS  
 Initialisieren Sie verwenden das\/ `m_dwModuleFlags` Feld in der `MODULE_INFO` Struktur.  
  
 MIF\_ALLFIELDS  
 Initialisieren Sie\/verwenden alle Felder in der `MODULE_INFO` Struktur.  
  
## Hinweise  
 Diese Werte werden als Argument an die [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)\-Methode übergeben, um anzugeben, welche Felder der [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch in der `MODULE_INFO` Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)