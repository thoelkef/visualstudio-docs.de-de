---
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb1c2c5478bb24f80646dcaacf64a9e6efb2e425
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988323"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Erstellt eine Kopie eines Datenobjekts für die ausdrucksauswertung (EE).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dataIn`  
 [in] Ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt, das die zu kopierenden Daten enthält.  
  
 `dataOut`  
 [out] Gibt eine neue `IEEDataStorage` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erhält eine [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt, das ein Array von Bytes darstellt. Dieses Datenobjekt der eingehenden ist in der Regel nicht von der EE implementiert. Das von dieser Methode zurückgegebene Objekt ist jedoch immer implementiert, von der EE, können Sie die EE implementieren die `IEEDataStorage` Schnittstelle für eine beliebige Klasse gewünscht wird.  
  
 Beachten Sie, dass die Daten von der eingehenden bereitgestellten `IEEDataStorage` Objekt muss die gleichen Daten in den ausgehenden `IEEDataStorage` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)