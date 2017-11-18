---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Wird aufgerufen, um das Profilerobjekt zu informieren, wenn für ein Skriptmodul der profilerstellung beenden. Auf diese Weise kann das Profilerobjekt seine Routinen Cleanup aufrufen, wenn erforderlich. Diese Methode wird auch vom Skriptmodul aufgerufen, wenn das Skriptmodul heruntergefahren wird oder wenn ein Aufruf von [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ein Fehler auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hrReason`  
 [in] Der Grund für das Herunterfahren. Wenn das Skriptmodul heruntergefahren wird, `S_OK` übergeben wird. Wenn der Aufruf von [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) gibt einen HRESULT-Fehler zurück, das HRESULT übergeben wird. Andernfalls wird dieser Wert abgerufen, von [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird vom Skriptmodul ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)