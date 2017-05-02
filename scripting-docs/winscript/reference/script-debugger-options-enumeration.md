---
title: "SCRIPT_DEBUGGER_OPTIONS-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS-Enumeration"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS-Enumeration
Gibt einen Satz von Optionen und\/oder Funktionen, die für den angefügten Debugger gelten.  Wird in [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) und in [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Diese Konstanten werden durch PDM v10.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|SDO\_NONE|0x00000000|Es sind keine Optionen festgelegt.|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|Gibt an, dass die Skriptlaufzeit BREAKREASON\_ERROR\-Ereignisse auslösen soll, wenn eine Ausnahme ausgelöst wird.  Diese Option wird durch den Debugger oder durch Benutzercode über `Debug.enableFirstChanceExceptions(<true&#124;false>)` festgelegt werden.|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|Gibt an, dass der Debugger Internet\-Worker unterstützt.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)