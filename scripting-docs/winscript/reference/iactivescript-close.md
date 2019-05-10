---
title: IActiveScript::Close | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53b71471ada55751de301391fdcc70387c1bb6c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935678"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Bewirkt, dass die Skript-Engine alle aktuell geladenen Skripts abbrechen, verlieren den Zustand und release-Schnittstellenzeiger auf die sie für andere Objekte, also einen geschlossenen Zustand verfügt. Ereignissenken, sofort ausgeführten Skripttext und -Makroaufrufe, die bereits in Bearbeitung sind werden abgeschlossen, bevor die Änderungen des Ansichtszustands (verwenden Sie [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) , einen ausgeführten Skriptthread abzubrechen). Diese Methode muss durch den Host erstellen aufgerufen werden, bevor die Schnittstelle freigegeben wird, um zu verhindern, dass der Zirkelverweis Probleme.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine war bereits im Zustand "geschlossen").|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde in die Warteschlange erfolgreich, jedoch der Zustand noch nicht geändert wurde. Zustandsänderungen, wenn der Standort ist auf zurückgerufen werden die [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methode.|  
|`S_FALSE`|Die Methode erfolgreich ausgeführt, aber das Skript wurde bereits geschlossen.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)