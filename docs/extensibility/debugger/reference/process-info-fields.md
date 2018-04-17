---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3376db379e4e911bcaa8e865a16c63d1251229f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Angegeben, welche Art von Informationen für einen Prozess abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Member  
 PIF_FILE_NAME  
 Die Initialisierung/verwenden die `bstrFileName` Feld der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.  
  
 PIF_BASE_NAME  
 Die Initialisierung/verwenden die `bstrBaseName` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_TITLE  
 Die Initialisierung/verwenden die `bstrTitle` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_PROCESS_ID  
 Die Initialisierung/verwenden die `ProcessId` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_SESSION_ID  
 Die Initialisierung/verwenden die `dwSessionId` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_ATTACHED_SESSION_NAME  
 Die Initialisierung/verwenden die `bstrAttachedSessionName` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_CREATION_TIME  
 Die Initialisierung/verwenden die `CreationTime` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_FLAGS  
 Die Initialisierung/verwenden die `Flags` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_ALL  
 Füllt alle Felder ein.  
  
## <a name="remarks"></a>Hinweise  
 Zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) Methode, um anzugeben, welche Felder der der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur initialisiert werden sollen.  
  
 Auch in verwendet `Fields` Feld der `PROCESS_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)