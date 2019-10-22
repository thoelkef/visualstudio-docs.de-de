---
title: 'IActiveScript:: Close | Microsoft-Dokumentation'
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
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575779"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Bewirkt, dass die Skript-Engine alle zurzeit geladenen Skripts abschließt, den Zustand verliert und alle Schnittstellen Zeiger freigibt, die es für andere Objekte gibt, sodass ein geschlossener Zustand eintritt. Ereignis senken, sofort ausgeführte Skript Text und Makro Aufrufe, die bereits ausgeführt werden, werden abgeschlossen, bevor der Status geändert wird (verwenden Sie [IActiveScript:: interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) , um einen ausgeführten Skript Thread abzubrechen). Diese Methode muss vom erstellenden Host aufgerufen werden, bevor die-Schnittstelle freigegeben wird, um Zirkel Verweis Probleme zu vermeiden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. befindet sich die Skript-Engine bereits im geschlossenen Zustand).|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde erfolgreich in die Warteschlange eingereiht, aber der Zustand wurde noch nicht geändert. Wenn sich der Status ändert, muss die Website auf der [iactivescriptsite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) -Methode zurück aufgerufen werden.|  
|`S_FALSE`|Die Methode war erfolgreich, das Skript wurde jedoch bereits geschlossen.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)