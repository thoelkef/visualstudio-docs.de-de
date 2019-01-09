---
title: BREAKRESUMEACTION-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3186ac39353d11f327f7940ae5fc03ae2238ddd9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090467"
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