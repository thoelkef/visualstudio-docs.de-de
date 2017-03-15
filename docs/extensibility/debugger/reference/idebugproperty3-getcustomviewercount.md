---
title: "IDebugProperty3::GetCustomViewerCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetCustomViewerCount"
helpviewer_keywords: 
  - "IDebugProperty3::GetCustomViewerCount"
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProperty3::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Anzahl der benutzerdefinierten Viewern ab, die möglicherweise für diese Eigenschaft verfügbar sind.  
  
## Syntax  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### Parameter  
 `pcelt`  
 \[out\]  Die Anzahl von benutzerdefinierten Viewern verfügbar für diese Eigenschaft.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um Typschnellansichten zu unterstützen, leitet diese Methode den Aufruf an die [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)\-Methode weiter.  Wenn die Ausdrucksauswertung auch benutzerdefinierte Viewer für den jeweiligen Typ der Eigenschaft unterstützt, fügt diese Methode die Anzahl von benutzerdefinierten Viewern den zurückgegebenen Wert hinzu.  
  
 Ausführliche Informationen zu den Unterschieden zwischen Typ und schnellansichten benutzerdefinierten Viewern finden Sie unter [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CProperty\-Objekt** implementiert, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle verfügbar macht.  
  
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
  
## Siehe auch  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)