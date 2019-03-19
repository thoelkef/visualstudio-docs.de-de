---
title: IActiveScriptSite::OnLeaveScript | Microsoft-Dokumentation
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
ms.openlocfilehash: da39058a8f069c4799835108372d11849d86444e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160744"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informiert, dass die Skript-Engine, vom Ausführen von Skriptcode zurückgegeben hat des Hosts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine muss diese Methode aufrufen, vor dem Zurückgeben der Steuerung an eine aufrufende Anwendung, die die Skript-Engine eingegeben. Z. B. wenn das Skript ein Objekt aufruft, dann ein Ereignis, das von der Skript-Engine verarbeitet löst, die Skript-Engine muss Aufrufen der [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) Methode vor dem Ausführen des Ereignisses und aufrufenmuss`IActiveScriptSite::OnLeaveScript`nach dem Ausführen des Ereignisses vor der Rückgabe an das Objekt, das das Ereignis ausgelöst hat. Aufrufe dieser Methode können geschachtelt werden. Für jeden Aufruf `IActiveScriptSite::OnEnterScript` einen zugehörigen Aufruf an diese Methode erfordert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)