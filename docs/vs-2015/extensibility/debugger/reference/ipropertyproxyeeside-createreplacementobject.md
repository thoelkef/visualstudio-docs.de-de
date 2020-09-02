---
title: 'Ipropertyproxyeeside:: kreatereplacementobject | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3a21e640d6661f8066609bdc344299ccbd63d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147497"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt eine Kopie eines Datenobjekts, das spezifisch für die-Ausdrucks Auswertung (EE) ist.  
  
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
 in Ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, das die zu kopierenden Daten enthält.  
  
 `dataOut`  
 [out] Gibt ein neues `IEEDataStorage`-Objekt zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode erhält ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, das ein Bytearray darstellt. Dieses eingehende Datenobjekt wird in der Regel nicht von EE implementiert. Allerdings wird das von dieser Methode zurückgegebene-Objekt immer von der EE implementiert, sodass das EE die- `IEEDataStorage` Schnittstelle für jede gewünschte Klasse implementieren kann.  
  
 Beachten Sie, dass die vom eingehenden Objekt bereitgestellten Daten `IEEDataStorage` die gleichen Daten im ausgehenden Objekt sein müssen `IEEDataStorage` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
