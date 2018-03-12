---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Ermöglicht es einen Host, um anzugeben, dass ein Skript beendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Aufruf erfolgreich war, und der Host ermöglicht das Skript weiter ausgeführt werden.|  
|`S_FALSE`|Der Aufruf erfolgreich war und der Host-Anforderungen, die das Skript beendet.|  
  
## <a name="remarks"></a>Hinweise  
 Das gehostete Skript beendet werden sollen, es sei denn, der Rückgabewert von der `QueryContinue` Methode ist `S_OK`. Ein Rückgabewert von `S_FALSE` gibt an, dass der Host fordert explizit an, dass das Skript beendet.  
  
 Einen multithreaded-Host verwendet möglicherweise die `IActiveScript::InterruptScriptThread` Methode, um ein Skript zu beenden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteInterruptPoll-Schnittstelle](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)