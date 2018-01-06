---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_INFO_FIELDS
helpviewer_keywords: MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d96175501d0e75ee1949847c69909c23a3b08582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Gibt die Flags für die Debuginformationen für das Modul an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
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
public enum enum_MODULE_INFO_FIELDS {   
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
  
## <a name="members"></a>Member  
 MIF_NONE  
 Die Initialisierung/verwenden keines der Felder in der Struktur.  
  
 MIF_NAME  
 Initialisieren/verwenden die `m_bstrName` -Feld in der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.  
  
 MIF_URL  
 Initialisieren/verwenden die `m_bstrUrl` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_VERSION  
 Initialisieren/verwenden die `m_bstrVersion` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_DEBUGMESSAGE  
 Initialisieren/verwenden die `m_bstrDebugMessage` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_LOADADDRESS  
 Initialisieren/verwenden die `m_addrLoadAddress` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_PREFFEREDADDRESS  
 Initialisieren/verwenden die `m_addrPreferredLoadAddress` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_SIZE  
 Initialisieren/verwenden die `m_dwSize` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_LOADORDER  
 Initialisieren/verwenden die `m_dwLoadOrder` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_TIMESTAMP  
 Initialisieren/verwenden die `m_TimeStamp` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_URLSYMBOLLOCATION  
 Initialisieren/verwenden die `m_bstrUrlSymbolLocation` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_FLAGS  
 Initialisieren/verwenden die `m_dwModuleFlags` -Feld in der `MODULE_INFO` Struktur.  
  
 MIF_ALLFIELDS  
 Die Initialisierung/verwenden alle Felder in der `MODULE_INFO` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden als Argument übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) Methode, um anzugeben, welche Felder von der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch verwendet, der `MODULE_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)