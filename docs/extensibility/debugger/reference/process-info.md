---
title: "PROCESS_INFO | Microsoft Docs"
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
  - "PROCESS_INFO"
helpviewer_keywords: 
  - "PROCESS_INFO-Struktur"
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# PROCESS_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält Informationen über einen Prozess.  
  
## Syntax  
  
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
  
```c#  
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
  
## Mitglieder  
 Felder  
 Eine Kombination von Flags aus der [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)\-Enumeration, die angeben, welche Felder geändert werden.  
  
 bstrFileName  
 Der vollständige Pfadname des Prozesses.  Entspricht dem Aufruf der [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)\-Methode auf, wobei der Parameter `GN_FILENAME`.  
  
 bstrBaseName  
 Der Dateiname und die Erweiterung des Prozesses.  Entspricht dem Aufruf der `IDebugProcess2::Getname`\-Methode auf, wobei der Parameter `GN_BASENAME`.  
  
 bstrTitle  
 Der Titel des Prozesses, sofern vorhanden.  Entspricht dem Aufruf der `IDebugProcess2::Getname`\-Methode auf, wobei der Parameter `GN_TITLE`.  
  
 ProcessId  
 Die [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die den Vorgang identifiziert.  Entspricht dem Aufruf der [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)\-Methode.  
  
 dwSessionId  
 Der Bezeichner der Debugsitzung, in dem Prozess ausgeführt wird.  
  
 bstrAttachedSessionName  
 Der angefügte Name der Sitzung.  Entspricht dem Aufruf der [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)\-Methode.  
  
 CreationTime  
 Die Uhrzeit, zu der der Prozess erstellt wurde.  
  
 Flags  
 Eine Kombination von Flags aus der [PROCESS\_INFO\_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)\-Enumeration, die die Eigenschaften des Prozesses angeben.  
  
## Hinweise  
 Diese Struktur wird auf die [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)\-Methode übergeben, in der er eingetragen wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS\_INFO\_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)