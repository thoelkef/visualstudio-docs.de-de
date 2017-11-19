---
title: APPBREAKFLAGS-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS-Enumeration
Geben den aktuellen Debugzustand für Anwendungen und Threads an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Sprachmodul sollten sofort auf alle Threads mit BREAKREASON_DEBUGGER_BLOCK unterbrechen.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Sprachmodul sollte mit BREAKREASON_DEBUGGER_HALT sofort unterbrechen.|  
|APPBREAKFLAG_STEP|0x00010000|Sprachmodul sollte in der schrittweisen Thread mit BREAKREASON_STEP sofort unterbrechen.|  
|APPBREAKFLAG_NESTED|0x00020000|Die Anwendung ist in der verschachtelten Ausführung an einem Haltepunkt.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Der Debugger wird auf der Ebene der Datenquelle ausführen in Einzelschritten.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Der Debugger wird auf der Ebene der Byte-Code schrittweise durchlaufen.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Der Debugger wird auf Computerebene ausführen in Einzelschritten.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maske für Ausklammern die Schritttypen.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Ein Haltepunkt ist in Bearbeitung.|  
  
## <a name="remarks"></a>Hinweise  
 Einige Kennzeichen angeben, dass die Sprache-Module bei nächster Gelegenheit umgebrochen werden soll, während andere Flags die schrittweise Ausführung des Debuggers angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Debugger-Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)