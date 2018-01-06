---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTY_FIELDS
helpviewer_keywords: THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9ff443fc655c18600ff90536d6e7ee5b8aa1ab7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Gibt an, welche Informationen über einen Thread abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 TPF_ID  
 Die Initialisierung/verwenden die `dwThreadId` Feld der [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Struktur.  
  
 TPF_SUSPENDCOUNT  
 Initialisieren/verwenden die `dwSuspendCount` Feld der `THREADPROPERTIE`S-Struktur.  
  
 TPF_STATE  
 Initialisieren/verwenden die `dwThreadState` Feld der `THREADPROPERTIE`S-Struktur.  
  
 TPF_PRIORITY  
 Initialisieren/verwenden die `bstrPriority` Feld der `THREADPROPERTIE`S-Struktur.  
  
 TPF_NAME  
 Initialisieren/verwenden die `bstrName` Feld der `THREADPROPERTIE`S-Struktur.  
  
 TPF_LOCATION  
 Initialisieren/verwenden die `bstrLocation` Feld der `THREADPROPERTIE`S-Struktur.  
  
 TPF_ALLFIELDS  
 Gibt alle Felder an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden als Argument übergeben der [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) Methode, um anzugeben, welche Felder von der [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch verwendet, `dwFields` Mitglied der `THREADPROPERTIES` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)