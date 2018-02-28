---
title: BREAKRESUMEACTIONS-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTIONS-Enumeration
Beschreibt, wie der Vorgang von einem Haltepunkt aus fortgesetzt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Die Anwendung wird abgebrochen.|  
|BREAKRESUMEACTION_CONTINUE|Wird weiterhin ausgeführt.|  
|BREAKRESUMEACTION_STEP_INTO|Schritte in einer Prozedur.|  
|BREAKRESUMEACTION_STEP_OVER|Überspringt über einer Prozedur.|  
|BREAKRESUMEACTION_STEP_OUT|Schritte aus der aktuellen Prozedur.|  
|BREAKRESUMEACTION_IGNORE|Weiter mit Status.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Schritte zum nächsten Dokument.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)