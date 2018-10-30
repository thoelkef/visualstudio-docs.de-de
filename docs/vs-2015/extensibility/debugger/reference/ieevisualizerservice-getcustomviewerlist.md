---
title: IEEVisualizerService::GetCustomViewerList | Microsoft-Dokumentation
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
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 514dd657930fd55520ac58d70956d56dc086a51b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818184"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt eine Liste der Typ-Schnellansichten, denen diesen Dienst bekannt sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celtSkip`  
 [in] Die Anzahl von Schnellansichten, zu überspringen.  
  
 `celRequested`  
 [in] Anzahl von Schnellansichten abrufen (gibt auch die Größe der an die `rgViewers` Array).  
  
 `rgViewers`  
 [in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen gefüllt werden soll.  
  
 `pceltFetched`  
 [out] Die Anzahl von Schnellansichten, die tatsächlich abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) übergibt die Anforderung an diese Methode als Teil der Unterstützung für Typ-Schnellansichten. Wenn die ausdrucksauswertung auch benutzerdefinierten Viewer für den gleichen Typ bereitstellt, können sie entsprechend ausgefüllte Anfügen [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen für diesen benutzerdefinierten Viewer zur Liste. Stellen Sie sicher, dass [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) diese zusätzliche Viewer widerspiegelt.  
  
 Finden Sie unter [Typschnellansicht und benutzerdefinierte Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Weitere Informationen zu den Unterschieden zwischen Schnellansichten und -Viewer.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

