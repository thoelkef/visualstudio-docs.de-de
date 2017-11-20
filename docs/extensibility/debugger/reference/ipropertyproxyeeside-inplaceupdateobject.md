---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords: IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 723a24a0a0ce21c7817b5dfcef2680808f9319a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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