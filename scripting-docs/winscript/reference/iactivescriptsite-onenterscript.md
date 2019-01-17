---
title: IActiveScriptSite::OnEnterScript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccef1b2bf63c4421843d3a33cab2e4f471a48251
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346513"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informiert den Host, dass die Skript-Engine begonnen hat, den Skriptcode ausführen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine muss diese Methode für jeden Eintrag oder Reentranz in die Skript-Engine aufrufen. Z. B. wenn das Skript ein Objekt aufruft, dann ein Ereignis, das von der Skript-Engine verarbeitet löst, die Skript-Engine muss Aufrufen `IActiveScriptSite::OnEnterScript` vor dem Ausführen des Ereignisses und müssen die [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) die Methode nach dem Ausführen des Ereignisses, aber vor der Rückgabe an das Objekt, das das Ereignis ausgelöst hat. Aufrufe dieser Methode können geschachtelt werden. Jeder Aufruf dieser Methode muss einen zugehörigen Aufruf an `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)