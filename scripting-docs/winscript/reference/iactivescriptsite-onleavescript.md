---
title: 'Iactivescriptsite:: onleavescript | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570320"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Benachrichtigt den Host, dass die Skript-Engine von der Ausführung von Skriptcode zurückgegeben hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine muss diese Methode aufrufen, bevor die Steuerung an eine aufrufende Anwendung zurückgegeben wird, die die Skript-Engine eingegeben hat Wenn das Skript z. b. ein Objekt aufruft, das ein Ereignis auslöst, das von der Skript-Engine behandelt wird, muss die Skript-Engine vor dem Ausführen des Ereignisses die [iactivescriptsite:: onenterscript](../../winscript/reference/iactivescriptsite-onenterscript.md) -Methode aufrufen und `IActiveScriptSite::OnLeaveScript` nach dem Ausführen des Ereignisses aufrufen. vor dem zurückkehren zu dem Objekt, das das Ereignis ausgelöst hat. Aufrufe dieser Methode können eingebettet werden. Jeder `IActiveScriptSite::OnEnterScript` Aufrufe erfordert einen entsprechenden-Rückruf für diese Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)