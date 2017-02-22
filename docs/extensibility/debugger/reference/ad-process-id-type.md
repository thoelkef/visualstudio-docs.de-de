---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
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
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "AD_PROCESS_ID_TYPE-enumeration"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, wie eine Prozess\-ID in der [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur interpretiert.  
  
## Syntax  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## Mitglieder  
 AD\_PROCESS\_ID\_SYSTEM  
 Prozess\-ID handelt es sich um einen Systembezeichner.  Verwenden Sie das `ProcessId.dwProcessId` Feld der [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.  
  
 AD\_PROCESS\_ID\_GUID  
 Prozess\-ID ist eine GUID.  Verwenden Sie das `ProcessId.guidProcessId` Feld der `AD_PROCESS_ID` Struktur.  
  
## Hinweise  
 Wird für den `ProcessIdType`\-Member der [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur verwendet, um den Typ der Prozesses\-ID zu identifizieren, die in der Struktur enthalten ist.  Bestimmt, wie die `ProcessId` Union in der Struktur interpretiert.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)