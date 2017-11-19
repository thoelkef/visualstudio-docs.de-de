---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Benachrichtigt den Host, dass das Skriptmodul begonnen hat den Skriptcode ausführen.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Das Skriptmodul muss diese Methode bei jedem eintritt oder Wiedereintritt in das Skriptmodul aufrufen. Beispielsweise, wenn das Skript ein Objekt, das ruft Sie ein Ereignis, das vom Skriptmodul verarbeitet löst, das Skriptmodul muss rufen `IActiveScriptSite::OnEnterScript` vor dem Ausführen des Ereignisses, und rufen Sie die muss die [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) die Methode nach der Ausführung des Ereignisses jedoch vor der Rückgabe auf das Objekt, das das Ereignis ausgelöst hat. Aufrufe dieser Methode können geschachtelt werden. Jeder Aufruf dieser Methode muss einen entsprechenden Aufruf von `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)