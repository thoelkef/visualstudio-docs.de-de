---
title: Isimpleconnectionpoint::D escribeevents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571820"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Gibt die DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `iEvent`  
 in Der Index des ersten Ereignisses, das abgerufen werden soll.  
  
 `cEvents`  
 in Anzahl der abzurufenden Ereignisse.  
  
 `prgid`  
 vorgenommen Array von Ereignis-DISPID-Werten.  
  
 `prgbstr`  
 vorgenommen Array von Ereignis Namen.  
  
 `pcEventsFetched`  
 vorgenommen Die tatsächliche Anzahl von abgerufenen Ereignissen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Es wurden weitere Ereignisse angefordert, als verfügbar waren. Nicht verfügbare Ereignisse werden mit DISPID_NULL und einem NULL BSTR dargestellt.|  
|`E_INVALIDARG`|Es konnten keine Elemente abgerufen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt die DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)