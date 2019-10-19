---
title: 'Iactivescriptprofilercallback:: Initialize | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576445"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Wird aufgerufen, um das profilerobjekt zu initialisieren, wenn die Profilerstellung für eine Skript-Engine gestartet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwContext`  
 in Ein 4-Byte-Wert, der an [iactivescriptprofilercontrol:: startprofiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)übermittelt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Methode das Profiler-Objekt nicht initialisieren kann, sollte ein Fehler-HRESULT zurückgegeben werden, um die Skript-Engine zu benachrichtigen. In diesem Fall sollte die Skript-Engine [iactivescriptprofilercallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)direkt aufrufen, das HRESULT im-Parameter übergeben und dann das Profiler-Objekt freigeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)