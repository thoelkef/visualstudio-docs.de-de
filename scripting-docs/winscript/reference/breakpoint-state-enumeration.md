---
title: "BREAKPOINT_STATE-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKPOINT_STATE-Enumeration"
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKPOINT_STATE-Enumeration
Gibt den Zustand eines Haltepunkts an.  
  
## Syntax  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## Mitglieder  
  
|Member|Description|  
|------------|-----------------|  
|BREAKPOINT\_DELETED|Der Haltepunkt nicht mehr vorhanden ist, gibt es immer noch verweist darauf.|  
|BREAKPOINT\_DISABLED|Der Haltepunkt vorhanden, jedoch ist deaktiviert.|  
|BREAKPOINT\_ENABLED|Der Haltepunkt vorhanden und ist aktiviert.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)