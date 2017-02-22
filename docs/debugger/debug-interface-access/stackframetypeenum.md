---
title: "StackFrameTypeEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StackFrameTypeEnum-Enumeration"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Typ der Stapelrahmen an.  
  
## Syntax  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elements  
 `FrameTypeFPO`  
 Framezeiger ausgelassen. FPO\-verfügbare Informationszwecken.  
  
 `FrameTypeTrap`  
 Kernel\-Blockier Skinframes.  
  
 `FrameTypeTSS`  
 Kernel\-Blockier Skinframes.  
  
 `FrameTypeStandard`  
 Standard\-EBP\-Stapelrahmen.  
  
 `FrameTypeFrameData`  
 Framezeiger ausgelassen. Feld bezugspunkt verfügbaren Informationen.  
  
 `FrameTypeUnknown`  
 Felder, die keine Debuginformationen verfügt.  
  
## Hinweise  
 Die Werte in dieser Enumeration werden von einem Aufruf der [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)