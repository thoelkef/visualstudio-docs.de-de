---
title: 'Isimpleconnectionpoint:: Rat | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571828"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Stellt eine Verbindung zwischen dem einfachen Verbindungspunkt Objekt und der Senke des Clients her.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdisp`  
 in Ein Zeiger auf die `IDispatch`-Schnittstelle in der Benachrichtigungs Senke des Clients. Die Senke des Clients empfängt ausgehende Aufrufe vom einfachen Verbindungspunkt.  
  
 `pdwCookie`  
 vorgenommen Zeiger auf ein zurück gegebenes Token, das diese Verbindung eindeutig identifiziert. Der Aufrufer verwendet dieses Token später, um die Verbindung zu löschen, indem Sie an die `ISimpleConnectionPoint::Unadvise`-Methode übergeben wird. Wenn die Verbindung nicht erfolgreich hergestellt wurde, ist dieser Wert 0 (null).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode stellt eine Verbindung zwischen dem einfachen Verbindungspunkt Objekt und der Senke des Clients her.  
  
## <a name="see-also"></a>Siehe auch  
 [Isimpleconnectionpoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)    
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)