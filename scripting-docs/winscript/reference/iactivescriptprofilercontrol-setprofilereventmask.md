---
title: 'Iactivescriptprofilercontrol:: setprofilereventmask | Microsoft-Dokumentation'
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
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571580"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Legt eine 4-Byte-Bitmaske fest, die die Ereignis Typen angibt, die die Skript-Engine ausgeben soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwEventMask`  
 in Eine 4-Byte-Bitmaske, die die Ereignis Typen angibt. Die Bits werden in der [PROFILER_EVENT_MASK-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md)definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die Profilerstellung ist nicht aktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)