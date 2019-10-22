---
title: 'IActiveScriptProfilerCallback2:: onfunctionexitbyname | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571621"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Benachrichtigt das Profiler-Objekt, dass die Skript-Engine die Ausführung eines Dokumentobjektmodell (DOM)-Funktions Aufrufes beendet hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `pwszFunctionName`  
 in Der Name der Funktion, die die Skript-Engine ausgeführt hat.  
  
 `scriptType`  
 in Der Typ der Funktion. Beschreibungen gültiger Werte finden Sie unter [PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Bei Dom-aufrufen Ruft die Skript-Engine diese Methode auf, anstatt [iactivescriptprofilercallback:: onfunctionexit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)aufzurufen. Dies liegt an der großen Anzahl von eindeutigen Methoden und Eigenschaften im Dom.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback2:: onfunctionenterbyname](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)