---
title: 'Ieevisualizerservice:: getcustomviewerlist | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2ee2682b04b03b2b0bb04e0ba9ef5d9a2df8a35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192067"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt eine Liste von typvisualisierungen zurück, die dieser Dienst kennt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celtSkip`  
 in Anzahl der Visualisierungen, die übersprungen werden sollen.  
  
 `celRequested`  
 in Anzahl der abzurufenden Visualisierungen (gibt auch die Größe des `rgViewers` Arrays an).  
  
 `rgViewers`  
 [in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen, die ausgefüllt werden sollen.  
  
 `pceltFetched`  
 vorgenommen Anzahl von Visualisierungen, die tatsächlich abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 [Getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) übergibt die Anforderung als Teil der Unterstützung für typvisualisierungen an diese Methode. Wenn die Ausdrucks Auswertung auch benutzerdefinierte Viewer für denselben Typ bereitstellt, kann Sie entsprechend ausgefüllte [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen für diese benutzerdefinierten Viewer an die Liste anfügen. Stellen Sie sicher, dass [getcustomviewercount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) diese zusätzlichen Viewer widerspiegelt.  
  
 Ausführliche Informationen zu den Unterschieden zwischen Visualisierungen und Viewern finden Sie unter [typschnell Ansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ieevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [Getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Getcustomviewercount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
