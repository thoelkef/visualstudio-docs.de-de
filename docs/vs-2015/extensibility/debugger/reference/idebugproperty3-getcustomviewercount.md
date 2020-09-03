---
title: 'IDebugProperty3:: getcustomviewercount | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193417"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Anzahl der benutzerdefinierten Viewer ab, die möglicherweise für diese Eigenschaft verfügbar sind.  
  
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
 vorgenommen Die Anzahl der für diese Eigenschaft verfügbaren benutzerdefinierten Viewer.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Zur Unterstützung von typvisualisierungen leitet diese Methode den-Befehl an die [getcustomviewercount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) -Methode weiter. Wenn die Ausdrucks Auswertung auch benutzerdefinierte Viewer für diesen Eigenschaftentyp unterstützt, fügt diese Methode die Anzahl der benutzerdefinierten Viewer dem zurückgegebenen Wert hinzu.  
  
 Ausführliche Informationen zu den Unterschieden zwischen typvisualisierungen und benutzerdefinierten Viewern finden Sie unter [typvisualizer und Custom Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cproperty** -Objekt implementiert wird, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle verfügbar macht.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Getcustomviewercount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
