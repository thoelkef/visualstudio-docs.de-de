---
title: SCRIPTTHREADSTATE-Enumeration | Microsoft-Dokumentation
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
ms.openlocfilehash: 906a309b25a1fe606fb37f8cbab70040e5a4c46f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840186"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE-Enumeration
Gibt den Zustand eines Threads in einer Skript-Engine an. Diese Enumeration wird verwendet, durch die [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) Methode.  
  
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
|SCRIPTTHREADSTATE_NOTINSCRIPT|Angegebenen Thread ist derzeit nicht zum Warten einer skriptgesteuerten Ereignis Skripttext Verarbeitung, die sofort ausgeführt, oder ein Skript-Makro wurde ausgeführt.|  
|SCRIPTTHREADSTATE_RUNNING|Angegebenen Thread ist aktiv zum Warten einer skriptgesteuerten Ereignis Skripttext Verarbeitung, die sofort ausgeführt, oder ein Skript-Makro wurde ausgeführt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)