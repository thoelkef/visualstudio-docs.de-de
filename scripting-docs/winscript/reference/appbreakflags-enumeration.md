---
title: "APPBREAKFLAGS-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS-Konstanten"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# APPBREAKFLAGS-Enumeration
Geben Sie das aktuelle debuggen Zustand für Anwendungen und Threads an.  
  
## Syntax  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|Sprachmodul sollte sofort auf allen Threads mit BREAKREASON\_DEBUGGER\_BLOCK unterbrechen.|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|Sprachmodul sollte mit BREAKREASON\_DEBUGGER\_HALT sofort unterbrechen.|  
|APPBREAKFLAG\_STEP|0x00010000|Sprachmodul sollte sofort den Tretenthread mit BREAKREASON\_STEP einlaufen.|  
|APPBREAKFLAG\_NESTED|0x00020000|Die Anwendung ist in geschachtelter Ausführung auf einem Haltepunkt.|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|Der Debugger tritt auf der Quellcodeebene.|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|Der Debugger tritt auf der Bytecodeebene.|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|Der Debugger durchläuft auf Computerebene.|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|Masken Faktor darstellen zerlegen Schritttypen out darstellen.|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|Ein Haltepunkt ausgeführt wird.|  
  
## Hinweise  
 Einige Flags geben an, dass Sprachmodule an der folgenden Möglichkeit unterbrechen sollen, während andere Flags den Tretenmodus des Debuggers angeben.  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON\-Enumeration](../../winscript/reference/breakreason-enumeration.md)