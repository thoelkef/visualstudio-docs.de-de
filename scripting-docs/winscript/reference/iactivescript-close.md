---
title: IActiveScript::Close | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Bewirkt, dass das Skriptmodul in verwerfen Sie alle derzeit geladenes Skript, verlieren den Zustand, und lassen Sie alle Schnittstellenzeiger er für andere Objekte, daher eingeben Zustand "geschlossen" aufweist. Ereignissenken, sofort ausgeführte Skripttext und -Makroaufrufe, die bereits in Bearbeitung sind werden abgeschlossen, bevor die statusänderungen (verwenden Sie [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) zu einen ausgeführten Skriptthread "Abbrechen"). Diese Methode muss durch den Host erstellen aufgerufen werden, bevor die Schnittstelle freigegeben wird, um Zirkelverweis Problemen vorzubeugen.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde bereits im Zustand "abgeschlossen").|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde in die Warteschlange wurde erfolgreich, jedoch der Zustand noch nicht geändert wurde. Wenn die statusänderungen der Standort ist, wieder aufgerufen werden der [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methode.|  
|`S_FALSE`|Die Methode war erfolgreich, aber das Skript bereits geschlossen wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)