---
title: "IDebugField::Equal | Microsoft Docs"
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
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "IDebugField::Equal-Methode"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode vergleicht dieses Feld mit dem angegebenen Feld auf Gleichheit.  
  
## Syntax  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### Parameter  
 `pField`  
 \[in\]  Das auf dieses Feld für den Vergleich.  
  
## Rückgabewert  
 Wenn die Felder identisch sind, gibt `S_OK`zurück.  Wenn die Felder unterschiedlich sind, gibt `S_FALSE.` andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)