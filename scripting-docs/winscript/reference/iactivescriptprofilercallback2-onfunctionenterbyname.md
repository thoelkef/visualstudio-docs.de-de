---
title: 'IActiveScriptProfilerCallback2:: onfunctionenterbyname | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571639"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Benachrichtigt das Profiler-Objekt, dass die Skript-Engine einen Dokumentobjektmodell (DOM)-Funktionsaufrufen ausführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pwszFunctionName`  
 in Der Name der Funktion, die von der Skript-Engine ausgeführt wird.  
  
 `scriptType`  
 in Der Typ der Funktion. Beschreibungen gültiger Werte finden Sie unter [PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Bei Dom-aufrufen Ruft die Skript-Engine diese Methode auf, anstatt [iactivescriptprofilercallback:: onfunctionenter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)aufzurufen. Dies liegt an der großen Anzahl von eindeutigen Methoden und Eigenschaften im Dom.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)