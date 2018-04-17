---
title: PROCESS_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d35b94b6153b65672453ed8b4e7d2c0d9c2bd5eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="processinfo"></a>PROCESS_INFO
Enthält Informationen zu einem Prozess.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Member  
 Felder  
 Eine Kombination aus Flags aus der [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) -Enumeration, die angeben, welche Felder ausgefüllt sind.  
  
 bstrFileName  
 Der vollständige Pfadname des Prozesses. Entspricht dem Aufrufen der [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) Methode mit dem Parameter `GN_FILENAME`.  
  
 bstrBaseName  
 Der Dateiname und Erweiterung des Prozesses. Entspricht dem Aufrufen der `IDebugProcess2::Getname` Methode mit dem Parameter `GN_BASENAME`.  
  
 bstrTitle  
 Der Titel des Prozesses, falls vorhanden. Entspricht dem Aufrufen der `IDebugProcess2::Getname` Methode mit dem Parameter `GN_TITLE`.  
  
 ProcessId  
 Die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die den Prozess bezeichnet. Entspricht dem Aufrufen der [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) Methode.  
  
 dwSessionId  
 Der Bezeichner der Debugsitzung, die diesen Prozess ausgeführt wird.  
  
 bstrAttachedSessionName  
 Der Name der angefügten Sitzung. Entspricht dem Aufrufen der [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) Methode.  
  
 CreationTime  
 Der Zeitpunkt, an der Prozess erstellt wurde.  
  
 Flags  
 Eine Kombination aus Flags aus der [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) -Enumeration, die Eigenschaften des Prozesses an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) Methode, wo in gefüllt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [getName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)