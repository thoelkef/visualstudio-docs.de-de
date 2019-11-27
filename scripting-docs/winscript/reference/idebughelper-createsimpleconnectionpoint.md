---
title: 'Idebughelper:: kreatesimpleconnectionpoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06324b0d10eb6d0d69b6426276d5df7f382d2abe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562455"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Gibt eine Ereignis Schnittstelle zurück, die ein angegebenes `IDispatch` Objekt umschließt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdisp`  
 in Das `IDispatch` zu Umbruch Ende-Objekt.  
  
 `ppscp`  
 vorgenommen Die Ereignis Schnittstelle, die `pdisp`umschließt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Gibt eine Ereignis Schnittstelle zurück, die die angegebene `IDispatch` umschließt (siehe [isimpleconnectionpoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Idebughelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)