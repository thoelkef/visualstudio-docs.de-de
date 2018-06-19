---
title: BREAKPOINT_STATE-Enumeration | Microsoft Docs
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
ms.openlocfilehash: 881598b39625b02651a4d57456904db60ace80c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640770"
---
# <a name="breakpointstate-enumeration"></a>BREAKPOINT_STATE-Enumeration
Gibt den Zustand eines Haltepunkts an.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Der Breakpoint nicht mehr vorhanden, aber es sind noch darauf verwiesen wird.|  
|BREAKPOINT_DISABLED|Der Haltepunkt vorhanden, aber deaktiviert.|  
|BREAKPOINT_ENABLED|Der Haltepunkt vorhanden und aktiviert ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)