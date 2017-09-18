---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "BP_PASSCOUNT_STYLE-Struktur"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Bedingung an, die mit der Anzahl der haben Haltepunkt zugeordnet ist, die den Haltepunkt ausgelöst wird.  
  
## Syntax  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## Mitglieder  
 BP\_PASSCOUNT\_NONE  
 Gibt kein Haltepunkt übergaben\-Anzahl Format an.  
  
 BP\_PASSCOUNT\_EQUAL  
 Legt das übergaben\-Anzahl Haltepunkt fest, um zu entsprechen.  Die Haltepunkt ausgelöst wird, wenn die Häufigkeit der Haltepunkt erreicht gleichgestellte die Anzahl übergeben wird.  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 Legt das übergaben\-Anzahl Haltepunkt fest, um zu entsprechen oder höher.  Die Haltepunkt ausgelöst wird, wenn die Häufigkeit der Haltepunkt getroffen wird, ist gleich oder höher als die Anzahl übergeben.  
  
 BP\_PASSCOUNT\_MOD  
 Gibt eine Modulo\-Übergaben Anzahl an.  Wenn z. B. die Anzahl der vom Typ `BP_PASSCOUNT_MOD` übergeben wird und der gültige Zählwert 4 ist, die Haltepunkt ausgelöst, wenn die Trefferanzahl ein Vielfaches von 4 ist.  
  
## Hinweise  
 Wird für den `stylePassCount`\-Member der [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die wiederum Mitglied der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen ist.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)