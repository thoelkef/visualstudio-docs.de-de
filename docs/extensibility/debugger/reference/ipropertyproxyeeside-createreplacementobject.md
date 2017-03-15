---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt eine Kopie eines Datenobjekts in den spezifischen Ausdrucksauswertung \(EE\).  
  
## Syntax  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parameter  
 `dataIn`  
 \[in\]  Ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)\-Objekt, das die zu kopierenden Daten enthält.  
  
 `dataOut`  
 \[out\]  Gibt ein neues `IEEDataStorage`\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ist ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) angegebene Objekt, das ein Bytearray darstellt.  Dieses eingehende Datenobjekt wird normalerweise nicht von der EE implementiert.  Allerdings ist das Objekt, das von dieser Methode zurückgegeben wird, immer von der EE implementiert, der die EE implementieren lässt die `IEEDataStorage`\-Schnittstelle für die Klasse erforderlich ist.  
  
 Beachten Sie, dass die Daten, die vom eingehenden `IEEDataStorage`\-Objekt angegeben werden, die gleichen Daten in ausgehenden `IEEDataStorage`\-Objekt sein müssen.  
  
## Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)