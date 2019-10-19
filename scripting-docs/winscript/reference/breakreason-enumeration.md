---
title: Breakreason-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572622"
---
# <a name="breakreason-enumeration"></a>BREAKREASON-Enumeration
Gibt an, was die Unterbrechung verursacht hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|BREAKREASON_STEP|Die Sprach-Engine befindet sich im Schritt Modus.|  
|BREAKREASON_BREAKPOINT|In der Sprach-Engine ist ein expliziter Haltepunkt aufgetreten.|  
|BREAKREASON_DEBUGGER_BLOCK|Die Sprach-Engine hat einen debuggerblock in einem anderen Thread gefunden.|  
|BREAKREASON_HOST_INITIATED|Der Host hat eine Pause angefordert.|  
|BREAKREASON_LANGUAGE_INITIATED|Die Sprach-Engine hat eine Pause angefordert.|  
|BREAKREASON_DEBUGGER_HALT|Die Debugger-IDE forderte eine Pause an.|  
|BREAKREASON_ERROR|Ein Ausführungsfehler hat die Unterbrechung verursacht.|  
|BREAKREASON_JIT|Ursache beim Start des JIT-Debuggens.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)