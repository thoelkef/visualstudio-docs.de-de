---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
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
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "PROCESS_INFO_FIELDS-enumeration"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche Art von Informationen für einen Prozess zu erhalten.  
  
## Syntax  
  
```cpp#  
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
  
```c#  
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
  
## Mitglieder  
 PIF\_FILE\_NAME  
 Initialisieren Sie `bstrFileName` \/verwenden das Feld [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.  
  
 PIF\_BASE\_NAME  
 Initialisieren Sie `bstrBaseName` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_TITLE  
 Initialisieren Sie `bstrTitle` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_PROCESS\_ID  
 Initialisieren Sie `ProcessId` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_SESSION\_ID  
 Initialisieren Sie `dwSessionId` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 Initialisieren Sie `bstrAttachedSessionName` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_CREATION\_TIME  
 Initialisieren Sie `CreationTime` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_FLAGS  
 Initialisieren Sie `Flags` \/verwenden das Feld `PROCESS_INFO` Struktur.  
  
 PIF\_ALL  
 Ergänzt alle Felder.  
  
## Hinweise  
 So [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) die Methode übergeben, um anzugeben, welche Felder der [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur initialisiert werden sollen.  
  
 Außerdem wird ein `Fields` Feld der `PROCESS_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)