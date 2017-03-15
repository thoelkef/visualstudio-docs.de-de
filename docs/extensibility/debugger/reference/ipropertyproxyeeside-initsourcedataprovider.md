---
title: "IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Initialisiert die Quelldaten für dieses Objekt und gibt ein Objekt zurück, das die ursprünglichen Daten enthält.  
  
## Syntax  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parameter  
 `dataOut`  
 \[out\]  Gibt ein Objekt zurück [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode hat, was erforderlich ist, um ein Objekt zu initialisieren, sodass es eine [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)\-Schnittstelle für Daten des Objekts zurückgeben kann.  Dies ermöglicht die von einer Typ schnellansicht angezeigt werden und darf, wenn es Daten des Objekts geändert.  
  
## Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)