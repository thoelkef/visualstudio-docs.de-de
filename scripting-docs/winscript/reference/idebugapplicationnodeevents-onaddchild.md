---
title: 'Idebugapplicationnodeevents:: onaddchild | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052fe47f1ddf2d20e7486a95a9dd79bc388f7ebc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574706"
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Behandelt das-Ereignis, wenn einem Debug-Anwendungs Knoten Objekt ein untergeordneter Knoten hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `prddpChild`  
 in Der untergeordnete debuganwendungsknoten, der hinzugefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode behandelt das-Ereignis, wenn einem Debug-Anwendungs Knoten Objekt ein untergeordneter Knoten hinzugefügt wird.  
  
 Implementierer der `IDebugApplicationNode`-Schnittstelle gibt dieses Ereignis aus  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplicationnodeevents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)