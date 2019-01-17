---
title: SCRIPTTHREADSTATE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2c66d078effd510b3f64cf1f443926984ff2e282
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347670"
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