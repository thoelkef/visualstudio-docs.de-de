---
title: 'Iactivescriptprofilercontrol:: startprofiling | Microsoft-Dokumentation'
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
ms.openlocfilehash: cfc59dd43ac3eed433f92af2cdd0aefe40392c4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571570"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Startet die Profilerstellung für die Skript-Engine. Die Skript-Engine erstellt eine Instanz des Profiler-Objekts, indem [cokreateinstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)aufgerufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `clsidProfilerObject`  
 in Klassen Bezeichner (CLSID) des Profiler-Objekts, das erstellt werden soll.  
  
 `dwEventMask`  
 in Eine 4-Byte-Bitmaske, die die Ereignis Typen angibt. Die Bits werden in der [PROFILER_EVENT_MASK-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md)definiert.  
  
 `dwContext`  
 in Ein 4-Byte-Wert, der an das Profiler-Objekt übermittelt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Die Profilerstellung ist bereits aktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)