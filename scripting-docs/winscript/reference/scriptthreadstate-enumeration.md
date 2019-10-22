---
title: Scriptthreadstate-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575655"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE-Enumeration
Gibt den Status eines Threads in einer Skript-Engine an. Diese Enumeration wird von der [IActiveScript:: getscriptthreadstate](../../winscript/reference/iactivescript-getscriptthreadstate.md) -Methode verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Der angegebene Thread verarbeitet zurzeit kein Skript Ereignis, verarbeitet sofort ausgeführten Skript Text oder führt ein Skript Makro aus.|  
|SCRIPTTHREADSTATE_RUNNING|Der angegebene Thread verarbeitet aktiv ein Skript Ereignis, verarbeitet sofort ausgeführten Skript Text und führt ein Skript Makro aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)