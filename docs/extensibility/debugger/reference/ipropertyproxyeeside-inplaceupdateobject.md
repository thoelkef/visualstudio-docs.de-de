---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf62b75fb421cdfb6ad323fbdd12958f93991254
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualisiert die Daten des Objekts mit dem angegebenen Objekt und gibt ein neues Datenobjekt, das das Objekt neue Daten darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dataIn`  
 [in] Ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt, das die neuen Daten enthält.  
  
 `dataOut`  
 [out] Gibt eine neue `IEEDataStorage` Objekt, das die ersetzten Daten enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird tatsächlich Daten für das Objekt aktualisiert. Die Daten in der zurückgegebenen [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt muss nicht mit den Daten in der eingehenden identisch sein `IEEDataStorage` Objekt, aber das zurückgegebene Objekt muss aktuellen Wert der Eigenschaft entsprechen.  
  
 Das eingehende Datenobjekt wird normalerweise nicht von der EE implementiert. Das von dieser Methode zurückgegebene Objekt ist jedoch immer implementiert, von der EE, letztere die EE implementieren die `IEEDataStorage` Schnittstelle auf beliebige Klasse gewünscht wird.  
  
 Die [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) Methode kann ein Datenobjekt basierend auf der eingehenden Datenobjekt erstellt, sondern wirkt sich nicht auf die ursprünglichen Daten für die Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)