---
title: PROCESS_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205022"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enthält Informationen zu einem Prozess.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Eine Kombination von Flags aus der [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Enumeration, die angeben, welche Felder ausgefüllt werden.  
  
 bstrFileName  
 Der vollständige Pfadname des Prozesses. Äquivalent zum Aufrufen der [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) -Methode mit dem-Parameter `GN_FILENAME` .  
  
 bstraubasename  
 Der Dateiname und die Erweiterung des Prozesses. Äquivalent zum Aufrufen der- `IDebugProcess2::Getname` Methode mit dem-Parameter `GN_BASENAME` .  
  
 bstrintitle  
 Der Titel des Prozesses, wenn ein solcher vorhanden ist. Äquivalent zum Aufrufen der- `IDebugProcess2::Getname` Methode mit dem-Parameter `GN_TITLE` .  
  
 ProcessId  
 Die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) -Struktur, die den Prozess identifiziert. Äquivalent zum Aufrufen der [getphysicalprocessid-](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) Methode.  
  
 dwsessionid  
 Der Bezeichner der Debugsitzung, in der dieser Prozess ausgeführt wird.  
  
 bstrattachedsessionname  
 Der Name der angefügten Sitzung. Äquivalent zum Aufrufen der [getattachedsessionname](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) -Methode.  
  
 CreationTime  
 Der Zeitpunkt, zu dem der Prozess erstellt wurde.  
  
 Flags  
 Eine Kombination von Flags aus der [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Enumeration, die Eigenschaften des Prozesses angeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird an die [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) -Methode, in der Sie ausgefüllt ist, übermittelt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [Getphysicalprocessid](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
