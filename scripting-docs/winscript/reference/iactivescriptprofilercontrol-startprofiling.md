---
title: IActiveScriptProfilerControl::StartProfiling | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 780886e4ca21abbe11580992244cee0d6a28b134
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149194"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Startet die profilerstellung auf die Skript-Engine. Die Skript-Engine erstellt eine Instanz des Profiler-Objekts, indem einen Aufruf von [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `clsidProfilerObject`  
 [in] Klassen Sie-ID (CLSID) des Profiler-Objekts erstellt werden.  
  
 `dwEventMask`  
 [in] Eine 4-Byte-Bitmaske, die die Ereignistypen angibt. Die Bits sind definiert, [PROFILER_EVENT_MASK-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] Ein 4-Byte-Wert, der mit dem Profilerobjekt übergeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Die profilerstellung ist bereits aktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)