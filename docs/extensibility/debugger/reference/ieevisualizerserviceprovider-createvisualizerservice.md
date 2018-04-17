---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f59d86e94be5c0295786b747f6b57753aa087b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Diese Methode erstellt einen schnellansichtsdienst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `binder`  
 [in] Die [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) an übergebene Objekt [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] Die [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) an übergebene Objekt `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] Die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) an übergebene Objekt `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Ein Objekt, durch die [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Schnittstelle (bereitgestellt von der ausdrucksauswertung).  
  
 `ppService`  
 [out] Der erstellte Dienst.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die `binder`, `pSymProv`, und `pAddress` Parameter wurden zum Übergeben der `IDebugParsedExpression::EvaluateSync` Methode. `CreateVisualizerService` nur aus aufgerufen werden soll `IDebugParsedExpression::EvaluateSync` als Teil einer ausdrucksauswertung-Unterstützung für die Typ-Schnellansichten.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)