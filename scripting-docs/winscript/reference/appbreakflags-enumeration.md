---
title: Appbreakflags-Enumeration | Microsoft-Dokumentation
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
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572662"
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
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Die Sprach-Engine sollte sofort für alle Threads mit BREAKREASON_DEBUGGER_BLOCK unterbrechen.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Die Sprach-Engine sollte sofort mit BREAKREASON_DEBUGGER_HALT unterbrechen.|  
|APPBREAKFLAG_STEP|0x00010000|Die Sprach-Engine sollte sofort im Schritt Thread mit BREAKREASON_STEP unterbrechen.|  
|APPBREAKFLAG_NESTED|0x00020000|Die Anwendung befindet sich an einem Haltepunkt in der genetzten Ausführung.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Der Debugger läuft auf Quell Ebene ab.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Der Debugger läuft auf der Byte Code Ebene ab.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Der Debugger läuft auf Computer Ebene ab.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00f 00000|Maske zum Gestalten der Schritt Typen.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Ein Haltepunkt wird gerade ausgeführt.|  
  
## <a name="remarks"></a>Hinweise  
 Einige Flags geben an, dass Sprachmodule bei der nächsten Gelegenheit unterbrechen werden sollen, während andere Flags den Schritt Modus des Debuggers angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)    
 [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)