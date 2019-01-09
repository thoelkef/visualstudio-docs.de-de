---
title: IActiveScriptSite::OnLeaveScript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7d08d58fc788d2d10ed044808ca40a5f4ea929c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093157"
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