---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft-Dokumentation
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
ms.openlocfilehash: ed69657823ac5e3ae821304aa6ffdbee55f39a70
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847616"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualisiert die Daten des Objekts mit dem angegebenen Objekt und gibt ein neues Datenobjekt, das neue Daten des Objekts darstellt.  
  
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
 [in] Ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, das die neuen Daten enthält.  
  
 `dataOut`  
 [out] Gibt eine neue `IEEDataStorage` -Objekt, das die ersetzten Daten enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird tatsächlich die Daten des Objekts aktualisiert. Die Daten in der zurückgegebenen [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt muss nicht identisch mit den Daten in der eingehenden werden `IEEDataStorage` -Objekt, aber das zurückgegebene Objekt muss der aktuelle Eigenschaftswert widerspiegeln.  
  
 Das eingehende Objekt ist in der Regel nicht von der EE implementiert. Das von dieser Methode zurückgegebene Objekt ist jedoch immer implementiert, von der EE, können Sie die EE implementieren die `IEEDataStorage` Schnittstelle für eine beliebige Klasse gewünscht wird.  
  
 Die [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) Methode wird ein Datenobjekt, das basierend auf dem eingehende Datenobjekt erstellt, sondern wirkt sich nicht auf die ursprünglichen Daten von der Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)