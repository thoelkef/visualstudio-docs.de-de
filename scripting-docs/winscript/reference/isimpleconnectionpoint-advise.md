---
title: ISimpleConnectionPoint::Advise | Microsoft-Dokumentation
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
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786261"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Herstellen einer Verbindung zwischen der einfachen Verbindungspunktobjekt und die Senke des Clients.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdisp`  
 [in] Zeiger auf die `IDispatch` Schnittstelle auf dem Client der advise-Senke. Die Senke des Clients empfängt ausgehende Aufrufe von der einfachen Verbindungspunkt an.  
  
 `pdwCookie`  
 [out] Zeiger auf einen zurückgegebenen Token, der diese Verbindung eindeutig identifiziert. Der Aufrufer verwendet dieses Token später beim Löschen der Verbindung durch Übergeben an die `ISimpleConnectionPoint::Unadvise` Methode. Wenn die Verbindung nicht erfolgreich hergestellt wurde, ist dieser Wert 0 (null).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode stellt eine Verbindung zwischen der einfachen Verbindungspunktobjekt und die Senke des Clients her.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)