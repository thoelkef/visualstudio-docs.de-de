---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091ccc30f16081fdca8f10778efec208ef5ccb16
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154451"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Wird aufgerufen, um das Profilerobjekt zu informieren, wenn auf eine Skript-Engine die profilerstellung beendet wird. Auf diese Weise kann das Profilerobjekt seine Bereinigungsroutinen aufrufen, wenn erforderlich. Diese Methode wird auch von der Skript-Engine aufgerufen, wenn die Skript-Engine heruntergefahren wird oder wenn ein Aufruf von [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ein Fehler auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hrReason`  
 [in] Der Grund für das Herunterfahren. Wenn die Skript-Engine heruntergefahren wird, `S_OK` übergeben wird. Wenn der Aufruf von [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) einen HRESULT-Fehler zurückgibt, der HRESULT-Wert übergeben wird. Andernfalls wird dieser Wert abgerufen, von [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)