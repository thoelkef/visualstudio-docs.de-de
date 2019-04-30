---
title: APPBREAKFLAGS-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0862e6fc670be6cd3d3ca9fbf67f453aa0772a90
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009770"
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
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Sprach-Engine sollte sofort für alle Threads mit BREAKREASON_DEBUGGER_BLOCK unterbrochen.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Sprach-Engine durch BREAKREASON_DEBUGGER_HALT sollte sofort nicht mehr ausgeführt.|  
|APPBREAKFLAG_STEP|0x00010000|Sprach-Engine sollten sofort in der schrittweisen Ausführung Thread mit BREAKREASON_STEP unterbrochen.|  
|APPBREAKFLAG_NESTED|0x00020000|Die Anwendung ist in der verschachtelten Ausführung an einem Haltepunkt.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Der Debugger wird auf der Ebene der Datenquelle schrittweise ausführen.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Der Debugger wird auf der Byteebene für den Code schrittweise ausführen.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Der Debugger wird auf der Computerebene schrittweise ausführen.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maske zum Ausklammern von den Typen.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Ein Haltepunkt ist in Bearbeitung.|  
  
## <a name="remarks"></a>Hinweise  
 Einige Kennzeichen angeben, dass die Sprach-Engines bei nächster Gelegenheit, umgebrochen werden soll, während andere Flags Geben Sie die schrittweisen Modus des Debuggers.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Debugger-Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)