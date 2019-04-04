---
title: IDebugProperty3::GetCustomViewerCount | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: adce7ad5813afc9c002ec9439326c12f3b2c8e6c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961015"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Anzahl der benutzerdefinierten Viewer, die für diese Eigenschaft verfügbar sein können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcelt`  
 [out] Die Anzahl der benutzerdefinierten Viewer für diese Eigenschaft verfügbar.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Um Typ-Schnellansichten unterstützen, diese Methode den Aufruf leitet das [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Methode. Wenn die ausdrucksauswertung benutzerdefinierten Viewer ebenfalls für den Typ dieser Eigenschaft unterstützt, wird der zurückgegebene Wert von dieser Methode die Anzahl der benutzerdefinierten Viewer hinzugefügt.  
  
 Ausführliche Informationen zu den Unterschieden zwischen typschnellansichten und benutzerdefinierten Viewer finden Sie unter [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CProperty** -Objekt, das macht die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle.  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
