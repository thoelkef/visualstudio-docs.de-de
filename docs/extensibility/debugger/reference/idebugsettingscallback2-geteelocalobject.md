---
title: "IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEELocalObject"
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSettingsCallback2::GetEELocalObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft ein lokales angegebenes Objekt des Ausdrucksauswerters der metrische Name ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetEELocalObject(  
   REFGUID     guidLang,  
   REFGUID     guidVendor,  
   LPCWSTR     pszMetric,  
   IUnknown ** ppUnk  
);  
```  
  
```c#  
private int GetEELocalObject(  
   ref Guid          guidLang,  
   ref Guid          guidVendor,  
   string            pszMetric,  
   out System.Object ppUnk  
);  
```  
  
#### Parameter  
 `guidLang`  
 \[in\]  Eindeutiger Bezeichner der Programmiersprache.  
  
 `guidVendor`  
 \[in\]  Eindeutiger Bezeichner des Anbieters.  
  
 `pszMetric`  
 \[in\]  Name der Metriken.  
  
 `ppUnk`  
 \[out\]  Gibt das Objekt die Ausdrucksauswertung lokalen Variablen zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)