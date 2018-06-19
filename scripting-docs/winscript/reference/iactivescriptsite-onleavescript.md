---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
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
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725170"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Benachrichtigt den Host, dass das Skriptmodul von Skriptcode ausführen zurückgegeben hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Das Skriptmodul muss diese Methode aufrufen, vor dem Zurückgeben der Steuerung an eine aufrufende Anwendung, die das Skriptmodul eingegeben haben. Beispielsweise, wenn das Skript ein Objekt, das ruft Sie ein Ereignis, das vom Skriptmodul verarbeitet löst, das Skriptmodul muss rufen die [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) -Methode vor dem Ausführen des Ereignisses und aufrufenmuss`IActiveScriptSite::OnLeaveScript`nach der Ausführung des Ereignisses vor der Rückgabe auf das Objekt, das das Ereignis ausgelöst hat. Aufrufe dieser Methode können geschachtelt werden. Jeder Aufruf `IActiveScriptSite::OnEnterScript` erfordert einen entsprechenden Aufruf dieser Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)