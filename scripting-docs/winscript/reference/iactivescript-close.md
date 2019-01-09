---
title: IActiveScript::Close | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 886ab1c4c39cf7c64571862bfd28f2fbd1062694
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097044"
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