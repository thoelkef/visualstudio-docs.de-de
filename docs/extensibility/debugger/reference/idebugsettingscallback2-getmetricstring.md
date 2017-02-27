---
title: "IDebugSettingsCallback2::GetMetricString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetMetricString"
  - "GetMetricString"
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetMetricString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Zeichenfolge des Werts von metrischen angegebene Name ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### Parameter  
 `pszType`  
 \[in\]  Typ der Metriken.  
  
 `guidSection`  
 \[in\]  Eindeutiger Bezeichner des Abschnitts.  
  
 `pszMetric`  
 \[in\]  Name der Metriken.  
  
 `pbstrValue`  
 \[out\]  Gibt die Zeichenfolge des Werts der Metriken zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)