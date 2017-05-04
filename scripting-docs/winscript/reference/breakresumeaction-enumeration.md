---
title: "BREAKRESUMEACTION-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION-Enumeration"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKRESUMEACTION-Enumeration
Beschreibt, wie der Vorgang von einem Haltepunkt aus fortgesetzt wird.  
  
## Syntax  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Mitglieder  
  
|Member|Beschreibung|  
|------------|------------------|  
|BREAKRESUMEACTION\_ABORT|Die Anwendung wird abgebrochen.|  
|BREAKRESUMEACTION\_CONTINUE|Wird weiterhin ausgeführt.|  
|BREAKRESUMEACTION\_STEP\_INTO|Schritte in einer Prozedur.|  
|BREAKRESUMEACTION\_STEP\_OVER|Überspringt über einer Prozedur.|  
|BREAKRESUMEACTION\_STEP\_OUT|Schritte aus der aktuellen Prozedur.|  
|BREAKRESUMEACTION\_IGNORE|Weiter mit Status.|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|Schritte zum nächsten Dokument.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)