---
title: BREAKREASON-Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641020"
---
# <a name="breakreason-enumeration"></a>BREAKREASON-Enumeration
Gibt an, was die Unterbrechung verursacht hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|BREAKREASON_STEP|Das Sprachmodul befindet sich im schrittweisen Modus.|  
|BREAKREASON_BREAKPOINT|Das Sprachmodul hat einen expliziten Haltepunkt festgestellt.|  
|BREAKREASON_DEBUGGER_BLOCK|Das Sprachmodul hat einen Debugger-Block in einem anderen Thread festgestellt.|  
|BREAKREASON_HOST_INITIATED|Der Host hat eine Unterbrechung angefordert.|  
|BREAKREASON_LANGUAGE_INITIATED|Das Sprachmodul angefordert eine Unterbrechung an.|  
|BREAKREASON_DEBUGGER_HALT|Der Debugger IDE angefordert eine Unterbrechung an.|  
|BREAKREASON_ERROR|Ein Ausführungsfehler verursacht die Unterbrechung an.|  
|BREAKREASON_JIT|Durch den JIT-Debuggen starten verursacht.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)