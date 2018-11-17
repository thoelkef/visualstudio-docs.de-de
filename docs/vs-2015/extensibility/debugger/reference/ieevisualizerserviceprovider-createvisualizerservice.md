---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4cc37f31de5e616dbc7497cb23f9f14b73610038
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807633"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode erstellt einen schnellansichtsdienst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `binder`  
 [in] Die [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt übergeben, um [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] Die [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt übergeben, um `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] Die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt übergeben, um `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Ein Objekt, das die [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Schnittstelle (bereitgestellt von der ausdrucksauswertung).  
  
 `ppService`  
 [out] Der erstellte Dienst.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die `binder`, `pSymProv`, und `pAddress` Parameter wurden zum Übergeben der `IDebugParsedExpression::EvaluateSync` Methode. `CreateVisualizerService` nur aus aufgerufen werden soll `IDebugParsedExpression::EvaluateSync` als Teil einer ausdrucksauswertung-Unterstützung für Typ-Schnellansichten.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

