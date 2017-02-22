---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
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
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "THREADPROPERTY_FIELDS-enumeration"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält, welche Informationen über einen Thread abgerufen werden soll.  
  
## Syntax  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
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
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Mitglieder  
 TPF\_ID  
 Initialisieren Sie `dwThreadId` \/verwenden das Feld [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Struktur.  
  
 TPF\_SUSPENDCOUNT  
 Initialisieren Sie verwenden das\/ `dwSuspendCount` Feld der Struktur `THREADPROPERTIE`S.  
  
 TPF\_STATE  
 Initialisieren Sie verwenden das\/ `dwThreadState` Feld der Struktur `THREADPROPERTIE`S.  
  
 TPF\_PRIORITY  
 Initialisieren Sie verwenden das\/ `bstrPriority` Feld der Struktur `THREADPROPERTIE`S.  
  
 TPF\_NAME  
 Initialisieren Sie verwenden das\/ `bstrName` Feld der Struktur `THREADPROPERTIE`S.  
  
 TPF\_LOCATION  
 Initialisieren Sie verwenden das\/ `bstrLocation` Feld der Struktur `THREADPROPERTIE`S.  
  
 TPF\_ALLFIELDS  
 Gibt alle Felder angezeigt.  
  
## Hinweise  
 Diese Werte werden als Argument an die [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)\-Methode übergeben, um anzugeben, welche Felder der [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch in `dwFields`\-Member der `THREADPROPERTIES` Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)