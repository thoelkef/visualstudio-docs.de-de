---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft-Dokumentation
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
ms.openlocfilehash: 1b5824f945ad25f177fc169b58157377bf53bcce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786418"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
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
 [in] Der Index des ersten Ereignisses abrufen.  
  
 `cEvents`  
 [in] Anzahl der Ereignisse abgerufen.  
  
 `prgid`  
 [out] Array von DISPID Ereigniswerten.  
  
 `prgbstr`  
 [out] Array von Namen von Ereignissen.  
  
 `pcEventsFetched`  
 [out] Die tatsächliche Anzahl der Ereignisse abgerufen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Weitere Ereignisse, die angefordert wurden, als verfügbar waren. Nicht verfügbar-Ereignisse werden mit DISPID_NULL und null BSTR dargestellt.|  
|`E_INVALIDARG`|Es konnte keine Elemente abgerufen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen an.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)