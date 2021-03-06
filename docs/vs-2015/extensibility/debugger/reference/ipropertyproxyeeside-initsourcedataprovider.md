---
title: 'Ipropertyproxyeeside:: initsourcedataprovider | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5e067a0b93656eecd1fe47d5b192c70916b672d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199505"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Initialisiert die Quelldaten für dieses-Objekt und gibt ein-Objekt zurück, das die Anfangsdaten enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 vorgenommen Gibt ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode übernimmt alle Elemente, die zum Initialisieren eines Objekts erforderlich sind, damit eine [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Schnittstelle für die Daten des Objekts zurückgegeben werden kann. Dadurch können die Daten des Objekts angezeigt und, falls zulässig, von einer typschnell Ansicht geändert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
