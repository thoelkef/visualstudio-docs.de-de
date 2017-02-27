---
title: "BP_COND_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "BP_COND_STYLE-enumeration"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt das Format für die anstehende zustands Haltepunkt und gebundenen Haltepunkte an.  
  
## Syntax  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## Mitglieder  
 BP\_COND\_NONE  
 Löst den Haltepunkt aus, wenn sich die Position des Haltepunkts unterbrochen wird.  Eine Haltepunktbedingung angegeben.  
  
 BP\_COND\_WHEN\_TRUE  
 Löst den Haltepunkt nur ausgeführt, wenn der bedingte Ausdruck, der mit dem Haltepunkt zugeordnet ist, `true`ergibt.  
  
 BP\_COND\_WHEN\_CHANGED  
 Löst den Haltepunkt nur ausgeführt, wenn sich der Wert des bedingten Ausdrucks, der dem Haltepunkt zugeordnet ist, aus der vorherigen Auswertung geändert hat.  
  
## Hinweise  
 Wird für den `styleCondition`\-Member der [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)