---
title: Scriptthreadid-Konstanten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575668"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID-Konstanten
Wird verwendet, um den Typ des Threads anzugeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xfffffffd|Der derzeit ausgeführte Thread.|  
|SCRIPTTHREADID_BASE|0xfffffffe|Der Basis Thread. Das heißt, der Thread, in dem die Skript-Engine instanziiert wurde.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Alle Threads.|  
  
## <a name="remarks"></a>Hinweise  
 Der `SCRIPTTHREADID` Typ wird von `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` und `IActiveScript::InterruptScriptThread` verwendet, aber die Konstanten können nur von `IActiveScript::GetScriptThreadState` und `IActiveScript::InterruptScriptThread` verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript:: getcurrentscriptthreadid](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)    
 [IActiveScript:: getscriptthreadid](../../winscript/reference/iactivescript-getscriptthreadid.md)    
 [IActiveScript:: getscriptthreadstate](../../winscript/reference/iactivescript-getscriptthreadstate.md) -   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)