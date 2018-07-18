---
title: IDebugAsyncOperation::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726160"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Stellt den Rückgabewert und Rückgabeobjekt Parameter aus dem synchronen Debugvorgang.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 [out] Wenn der Vorgang abgeschlossen ist, `phrResult` ist der Rückgabewert der `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Wenn der Vorgang abgeschlossen ist, wird `ppunkResult` der Objektparameter, die vom Vorgang zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang wurde nicht abgeschlossen.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Vorgang abgeschlossen ist, gibt diese Methode die `HRESULT` und-Objektparameters aus `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)