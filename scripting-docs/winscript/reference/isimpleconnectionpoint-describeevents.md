---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734020"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Index des ersten Ereignisses abgerufen.  
  
 `cEvents`  
 [in] Anzahl der Ereignisse abgerufen.  
  
 `prgid`  
 [out] Ereignis Wertearray DISPID.  
  
 `prgbstr`  
 [out] Array von Ereignisnamen.  
  
 `pcEventsFetched`  
 [out] Die tatsächliche Anzahl von Ereignissen, die abgerufen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Weitere Ereignisse, die angefordert wurden, als verfügbar waren. Mit DISPID_NULL und null BSTR werden Ereignisse nicht verfügbar dargestellt.|  
|`E_INVALIDARG`|Es konnte keine Elemente abgerufen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)