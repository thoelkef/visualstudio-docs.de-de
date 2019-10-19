---
title: Breakresumeaction-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572606"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTIONS-Enumeration
Beschreibt, wie der Vorgang von einem Haltepunkt aus fortgesetzt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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