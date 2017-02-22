---
title: "IDebugProperty3::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
helpviewer_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste mit den benutzerdefinierten Viewern ab, die dieser Eigenschaft zugeordnet sind.  
  
## Syntax  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### Parameter  
 `celtSkip`  
 \[in\]  Die Anzahl der zu überspringenden Viewern zu.  
  
 `celtRequested`  
 \[in\]  Die Anzahl der abzurufenden Viewern \(gibt außerdem die Größe des Arrays `rgViewers` \).  
  
 `rgViewers`  
 \[in, out\]  Array von Strukturen, [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Die tatsächliche Anzahl von Viewern zurückgegeben.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um Typschnellansichten zu unterstützen, leitet diese Methode den Aufruf an die [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)\-Methode weiter.  Wenn die Ausdrucksauswertung auch benutzerdefinierte Viewer für den jeweiligen Typ der Eigenschaft unterstützt, kann diese Methode die entsprechenden benutzerdefinierten Viewer an die Liste angefügt werden.  
  
 Weitere Informationen finden Sie unter [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Einzelheiten über die Unterschiede zwischen Typ und schnellansichten benutzerdefinierten Viewern.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CProperty\-Objekt** implementiert, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## Siehe auch  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)