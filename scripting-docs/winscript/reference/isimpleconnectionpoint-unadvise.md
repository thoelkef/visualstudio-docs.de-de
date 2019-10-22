---
title: 'Isimpleconnectionpoint:: unempfehlung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571753"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Beendet eine Beratungs Verbindung, die zuvor über `ISimpleConnectionPoint::Advise` hergestellt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCookie`  
 in Das Token der zu beendenden Verbindung, wie von `ISimpleConnectionPoint::Advise` zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Beratungs Verbindung beendet wird, ruft der Verbindungspunkt die `Release`-Methode für den Zeiger auf, der während der `ISimpleConnectionPoint::Advise` Methode für die Verbindung gespeichert wurde. Dieser Aufruf kehrt die `AddRef` um, die während der `ISimpleConnectionPoint::Advise` ausgeführt wurden, wenn der Verbindungspunkt die `QueryInterface` der Beratungs Senke aufruft.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)