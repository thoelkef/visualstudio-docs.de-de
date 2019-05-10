---
title: IDebugAsyncOperation::GetResult | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49cf761c85fce3f8fc2f6705d114ab042e0c2ecd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822044"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Stellt den Rückgabewert und ein Rückgabeobjekt-Parameter aus der synchronen Debugvorgang.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 [out] Wenn der Vorgang abgeschlossen ist, ist `phrResult` ist der Rückgabewert von `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Wenn der Vorgang abgeschlossen ist, ist `ppunkResult` ist der Objektparameter, die vom Vorgang zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang wurde nicht abgeschlossen.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Vorgang abgeschlossen ist, gibt diese Methode die `HRESULT` und-Objektparameter aus `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)