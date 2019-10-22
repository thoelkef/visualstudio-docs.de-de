---
title: 'Iactivescriptsite:: onenterscript | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570363"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informiert den Host, dass die Skript-Engine mit der Ausführung des Skriptcodes begonnen hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine muss diese Methode für jeden Eintrag oder einen erneuten Eintrag in der Skript-Engine abrufen. Wenn das Skript z. b. ein Objekt aufruft, das ein Ereignis auslöst, das von der Skript-Engine behandelt wird, muss die Skript-Engine vor dem Ausführen des Ereignisses `IActiveScriptSite::OnEnterScript` aufrufen und die [iactivescriptsite:: onleavescript](../../winscript/reference/iactivescriptsite-onleavescript.md) -Methode aufrufen, nachdem das Ereignis ausgeführt wurde. vor dem zurückkehren zu dem Objekt, das das Ereignis ausgelöst hat. Aufrufe dieser Methode können eingebettet werden. Jeder Aufrufe dieser Methode erfordert einen entsprechenden-Aufruf`IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)