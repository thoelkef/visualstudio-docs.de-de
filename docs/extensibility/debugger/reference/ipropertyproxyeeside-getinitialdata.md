---
title: "IPropertyProxyEESide::GetInitialData | Microsoft Docs"
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
  - "IPropertyProxyEESide::GetInitialData"
helpviewer_keywords: 
  - "IPropertyProxyEESide::GetInitialData"
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::GetInitialData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die ursprünglichen Daten für dieses Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetInitialData(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int GetInitialData(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parameter  
 `dataOut`  
 \[out\]  Gibt ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)\-Objekt zurück, das die ursprünglichen Daten dieses Objekts enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)