---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56c97e9fc7e5505578533c9e7b958a73dc8d2380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102586"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Diese Methode gibt einen angeforderten Dienst zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `vendor`  
 [in] `GUID` von einem Anbieter (ein null-Wert ist akzeptabel).  
  
 `language`  
 [in] `GUID` einer Sprache (ein null-Wert ist akzeptabel).  
  
 `iid`  
 [in] `IID` des abzurufenden Diensts.  
  
 `ppService`  
 [out] Eine Schnittstelle für den angeforderten Dienst.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben Sie die `IID` für die [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) Schnittstelle (`IID_IEEVisualizerServiceProvider`) zu überprüfen, ob der Typ Schnellansicht-Dienst verfügbar ist. Wenn also die ausdrucksauswertung erhalten Sie bei der [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Schnittstelle, um die Typ-Schnellansichten unterstützen. Finden Sie unter [Visualizing und Anzeige von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) für Details.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)