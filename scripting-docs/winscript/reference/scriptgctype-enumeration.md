---
title: "SCRIPTGCTYPE-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTGCTYPE-Enumeration
Der Typ der Garbage Collection auszuführen.  Wird in der [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md)\-Methode verwendet.  
  
## Syntax  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|Führen Sie die normale Garbage Collection.  Der ganzzahlige Wert ist 0.|  
|SCRIPTGCTYPE\_EXHAUSTIVE|Führen Sie vollständige Garbage Collection.  Der ganzzahlige Wert ist 1.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)