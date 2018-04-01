---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b5c52e78359b4cce4a92717801cce65f183578d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Initialisiert die Quelldaten für dieses Objekt und gibt ein Objekt, das die ursprünglichen Daten enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dataOut`  
 [out] Gibt eine [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode führt nach Belieben ist erforderlich, um ein Objekt zu initialisieren, damit es zurückgeben kann ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle auf die Daten des Objekts. Dadurch können Daten angezeigt und, wenn zugelassen wird, geändert werden, indem eine Schnellansicht Typ des Objekts.  
  
## <a name="see-also"></a>Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)