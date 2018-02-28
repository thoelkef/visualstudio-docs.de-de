---
title: SCRIPTTHREADSTATE-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE-Enumeration
Gibt den Zustand eines Threads in einem Skriptmodul. Diese Enumeration wird verwendet, durch die [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Angegebenen Thread ist derzeit nicht Wartung einer skriptgesteuerten Ereignis Skripttext Verarbeitung sofort ausgeführt, oder ein Skript-Makro ausgeführt.|  
|SCRIPTTHREADSTATE_RUNNING|Angegebenen Thread ist aktiv Wartung einer skriptgesteuerten Ereignis Skripttext Verarbeitung sofort ausgeführt, oder ein Skript-Makro ausgeführt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)