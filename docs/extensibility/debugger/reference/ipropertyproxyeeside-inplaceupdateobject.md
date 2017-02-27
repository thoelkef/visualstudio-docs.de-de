---
title: "IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::InPlaceUpdateObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InPlaceUpdateObject"
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktualisiert die Objektdaten mit dem angegebenen Datenobjekt und gibt ein neues Datenobjekt zurück, das die neuen Daten des Objekts darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parameter  
 `dataIn`  
 \[in\]  Ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)\-Objekt, das die neuen Daten enthält.  
  
 `dataOut`  
 \[out\]  Gibt ein neues `IEEDataStorage`\-Objekt zurück, das die ersetzten Daten enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode aktualisiert dann die Daten des Objekts.  Die Daten im zurückgegebenen [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)\-Objekt muss nicht identisch sein, die die Daten im eingehenden `IEEDataStorage`\-Objekt, aber das zurückgegebene Objekt den aktuellen Wert der Eigenschaft reflektieren müssen.  
  
 Das eingehende Datenobjekt wird in der Regel nicht von der EE implementiert.  Allerdings ist das Objekt, das von dieser Methode zurückgegeben wird, immer von der EE implementiert, der die EE implementieren lässt die `IEEDataStorage`\-Schnittstelle für die Klasse erforderlich ist.  
  
 Die [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)\-Methode erstellt, ein Datenobjekt auf Grundlage des eingehenden Datenobjekt wirkt sich jedoch nicht auf die ursprünglichen Daten der Eigenschaft.  
  
## Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)