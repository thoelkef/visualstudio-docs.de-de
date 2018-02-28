---
title: ISimpleConnectionPoint::GetEventCount | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.GetEventCount
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::GetEventCount
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 523748112d99f000d2eb88a7a64c88b60d5ea44f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointgeteventcount"></a>ISimpleConnectionPoint::GetEventCount
Gibt die Anzahl der Ereignisse, die für diese Schnittstelle verfügbar gemacht werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pulCount`  
 [out] Anzahl der Ereignisse, die für die Anzahl dieser Schnittstelle verfügbar gemacht werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt die Anzahl der Ereignisse, die für diese Schnittstelle verfügbar gemacht werden.  
  
## <a name="see-also"></a>Siehe auch  
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)