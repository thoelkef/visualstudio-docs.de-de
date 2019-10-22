---
title: 'Idebugapplicationnodeevents:: onremovechild | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ff7b28f14c26029d64197ba919cc97c90a856c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574668"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Behandelt das-Ereignis, wenn ein untergeordneter Knoten aus einem Debug-Anwendungs Knoten Objekt entfernt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `prddpChild`  
 in Der untergeordnete Anwendungs Knoten, der entfernt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode behandelt das-Ereignis, wenn ein untergeordneter Knoten aus einem Debug-Anwendungs Knoten Objekt entfernt wird.  
  
 Implementierer der `IDebugApplicationNode`-Schnittstelle gibt dieses Ereignis aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplicationnodeevents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)    
 [Idebugapplicationnodeevents:: onaddchild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)    
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)