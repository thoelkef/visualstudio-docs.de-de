---
title: IEnumRemoteDebugApplicationThreads::Next | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bde09e2c8372e0bb7e73fabfbd1ad4d9aa6467e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146759"
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
Die `Next` Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl von Segmenten abgerufen werden soll.  
  
 `pprdat`  
 [out] Gibt ein Array von `IRemoteDebugApplicationThread` Schnittstellen, die die Segmente, die abgerufen werden darstellt.  
  
 `pceltFetched`  
 [out] Die tatsächliche Anzahl von Segmenten, die vom Enumerator abgerufen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumRemoteDebugApplicationThreads-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)