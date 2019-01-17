---
title: BREAKPOINT_STATE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bb0a1fabc90eea86f440ebca97a9adb1328c401
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348632"
---
# <a name="breakpointstate-enumeration"></a>BREAKPOINT_STATE-Enumeration
Gibt den Zustand eines Haltepunkts an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Der Haltepunkt nicht mehr vorhanden ist, aber es gibt immer noch darauf verwiesen wird.|  
|BREAKPOINT_DISABLED|Der Haltepunkt vorhanden, aber deaktiviert.|  
|BREAKPOINT_ENABLED|Der Haltepunkt vorhanden und aktiviert ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)