---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
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
ms.openlocfilehash: 63ce45c0973d65d240136d7b42aef0c078b00c9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992298"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Können Sie einen Host aus, um anzugeben, dass es sich bei einem Skript musste beendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Aufruf erfolgreich war, und der Host ermöglicht das Skript weiter ausgeführt werden.|  
|`S_FALSE`|Der Aufruf erfolgreich war und die Host-Anforderungen, die das Skript zu beenden.|  
  
## <a name="remarks"></a>Hinweise  
 Das gehostete Skript sollte beendet werden, wenn der Rückgabewert von der `QueryContinue` Methode `S_OK`. Der Rückgabewert `S_FALSE` gibt an, dass der Host fordert explizit an, dass das Skript zu beenden.  
  
 Ein Multithread-Host können Sie die `IActiveScript::InterruptScriptThread` Methode, um einem Skript musste beendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteInterruptPoll-Schnittstelle](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)