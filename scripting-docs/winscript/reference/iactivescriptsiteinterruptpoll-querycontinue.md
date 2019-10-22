---
title: 'Iactivescriptsiteinterruptabruf:: querycontinue | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572233"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Ermöglicht einem Host, anzugeben, dass ein Skript beendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der-Befehl wurde erfolgreich ausgeführt, und der Host kann die Ausführung des Skripts fortsetzen.|  
|`S_FALSE`|Der-Befehl war erfolgreich, und der Host fordert an, dass das Skript beendet wird.|  
  
## <a name="remarks"></a>Hinweise  
 Das gehostete Skript sollte beendet werden, es sei denn, der Rückgabewert der `QueryContinue`-Methode ist `S_OK`. Der Rückgabewert `S_FALSE` gibt an, dass der Host explizit anfordert, dass das Skript beendet wird.  
  
 Ein Multithread-Host kann die `IActiveScript::InterruptScriptThread`-Methode verwenden, um ein Skript zu beenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptsiteinterruptabruf-Schnittstelle](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)    
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)