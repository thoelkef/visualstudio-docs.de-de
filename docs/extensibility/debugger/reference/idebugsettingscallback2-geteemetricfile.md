---
title: "IDebugSettingsCallback2::GetEEMetricFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricFile"
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das metrische angegebene Datei des Ausdrucksauswerters der Name oder die Metrik ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricFile(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### Parameter  
 `guidLang`  
 \[in\]  Eindeutiger Bezeichner der Programmiersprache.  
  
 `guidVendor`  
 \[in\]  Eindeutiger Bezeichner des Anbieters.  
  
 `pszMetric`  
 \[in\]  Name der Metriken.  
  
 `pbstrValue`  
 \[out\]  Gibt den Inhalt der Datei metrischen als Zeichenfolge zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)