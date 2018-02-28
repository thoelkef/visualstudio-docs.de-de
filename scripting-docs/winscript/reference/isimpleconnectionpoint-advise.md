---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Herstellen einer Verbindung zwischen der einfachen Verbindungspunktobjekt und der Client-Senke.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdisp`  
 [in] Zeiger auf die `IDispatch` Schnittstelle auf dem Client die advise-Senke. Die Senke des Clients empfängt die ausgehende Aufrufe vom einfachen Verbindungspunkt.  
  
 `pdwCookie`  
 [out] Ein Zeiger auf ein zurückgegebene Token, das diese Verbindung eindeutig identifiziert. Der Aufrufer verwendet dieses Token später löschen die Verbindung durch Übergabe an die `ISimpleConnectionPoint::Unadvise` Methode. Wenn die Verbindung nicht erfolgreich hergestellt wurde, ist dieser Wert 0 (null).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird eine Verbindung zwischen der einfachen Verbindungspunktobjekt und der Client-Senke.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)