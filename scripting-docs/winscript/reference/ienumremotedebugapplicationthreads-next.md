---
title: 'Ienumremotedebugapplicationthreads:: Next | Microsoft-Dokumentation'
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
ms.openlocfilehash: 36d24ffaca05b64c05815124358024d3b88b0d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575175"
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
Die `Next`-Methode ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.  
  
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
 in Die Anzahl der abzurufenden Segmente.  
  
 `pprdat`  
 vorgenommen Gibt ein Array von `IRemoteDebugApplicationThread`-Schnittstellen zurück, die die abgerufenen Segmente darstellen.  
  
 `pceltFetched`  
 vorgenommen Die tatsächliche Anzahl der Segmente, die vom Enumerator abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumRemoteDebugApplicationThreads-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)