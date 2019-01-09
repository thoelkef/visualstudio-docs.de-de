---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 40c527881c45a935344aa5444d7397ccdb6d99e4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092494"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Benachrichtigt den Profilerobjekt, das die Skript-Engine vor sich geht auf einen Funktionsaufruf (DOKUMENTOBJEKTMODELL) ausführen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pwszFunctionName`  
 [in] Der Name der Funktion, die die Skript-Engine ausführen soll.  
  
 `scriptType`  
 [in] Der Typ der Funktion. Beschreibungen der gültigen Werte finden Sie [PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Für DOM-Aufrufe, die Skript-Engine ruft diese Methode auf statt [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Dies ist aufgrund der großen Anzahl von eindeutigen Methoden und Eigenschaften im DOM.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)