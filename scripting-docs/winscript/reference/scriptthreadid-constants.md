---
title: SCRIPTTHREADID-Konstanten | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID-Konstanten
Zur Angabe des Threads verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Den gerade ausgeführten Thread.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Die Basis-Thread. d. h. wurde der Thread, in dem das Skript-engine-instanziiert.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Alle Threads.|  
  
## <a name="remarks"></a>Hinweise  
 Die `SCRIPTTHREADID` Typ werden vom `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, und `IActiveScript::InterruptScriptThread`, aber die Konstanten können nur verwendet werden, indem `IActiveScript::GetScriptThreadState` und `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)