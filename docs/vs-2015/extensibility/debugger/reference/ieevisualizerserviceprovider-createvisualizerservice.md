---
title: 'Ieevisualizerserviceprovider:: kreatevisualizerservice | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155080"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode erstellt einen schnell Ansichts Dienst.  
  
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
 in Das an [evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)über gegebene [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt.  
  
 `pSymProv`  
 in Das [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt, das an übergeben wird `IDebugParsedExpression::EvaluateSync` .  
  
 `pAddress`  
 in Das [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das an übergeben wird `IDebugParsedExression::EvaluateSync` .  
  
 `dataProvider`  
 in Ein Objekt, das die [ieevisualizerdataprovider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle implementiert (von der Ausdrucks Auswertung bereitgestellt).  
  
 `ppService`  
 vorgenommen Der erstellte Dienst.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die `binder` `pSymProv` Parameter, und `pAddress` wurden alle an die-Methode übermittelt `IDebugParsedExpression::EvaluateSync` . `CreateVisualizerService` muss nur aus `IDebugParsedExpression::EvaluateSync` als Teil der Unterstützung für typvisualisierungen eines Ausdrucks Auswerters aufgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ieevisualizerserviceprovider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [Idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
