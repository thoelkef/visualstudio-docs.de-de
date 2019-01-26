---
title: PROCESS_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 995b4cda0cc1520871f55d3c4b57899754a05c3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937859"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Angegeben, welche Art von Informationen für einen Prozess abrufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
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
public enum enum_PROCESS_INFO_FIELDS {   
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
 Initialisieren und Verwenden der `bstrFileName` Feld der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.  
  
 PIF_BASE_NAME  
 Initialisieren und Verwenden der `bstrBaseName` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_TITLE  
 Initialisieren und Verwenden der `bstrTitle` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_PROCESS_ID  
 Initialisieren und Verwenden der `ProcessId` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_SESSION_ID  
 Initialisieren und Verwenden der `dwSessionId` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_ATTACHED_SESSION_NAME  
 Initialisieren und Verwenden der `bstrAttachedSessionName` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_CREATION_TIME  
 Initialisieren und Verwenden der `CreationTime` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_FLAGS  
 Initialisieren und Verwenden der `Flags` Feld der `PROCESS_INFO` Struktur.  
  
 PIF_ALL  
 Füllt alle Felder ein.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) Methode an, welche Felder der der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) sind, dass die Struktur initialisiert werden.  
  
 Auch in verwendet `Fields` Feld der `PROCESS_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)