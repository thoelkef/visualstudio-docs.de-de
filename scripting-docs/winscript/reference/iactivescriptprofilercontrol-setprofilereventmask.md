---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01e55d793d174f550e33e18558eccc19d417c80b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149293"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Legt eine 4-Byte-Bitmaske, die die Typen von Ereignissen gibt an, die die Skript-Engine auslösen soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwEventMask`  
 [in] Eine 4-Byte-Bitmaske, die die Ereignistypen angibt. Die Bits sind definiert, [PROFILER_EVENT_MASK-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die profilerstellung ist nicht aktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)