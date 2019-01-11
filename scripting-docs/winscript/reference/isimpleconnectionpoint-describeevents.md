---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft-Dokumentation
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
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088503"
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