---
title: 'Idebugapplicationnodeevents:: onattach | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574690"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Behandelt ein Ereignis, das signalisiert, dass das debuganwendungsobjekt an einen übergeordneten Knoten angefügt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `prddpParent`  
 in Der debuganwendungsknoten, der diesem Knoten übergeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode behandelt ein Ereignis, das Kenn spricht, dass das Objekt zum debuggingknoten an einen übergeordneten Knoten angefügt wurde.  
  
 Implementierer der `IDebugApplicationNode`-Schnittstelle gibt dieses Ereignis aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplicationnodeevents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)    
 [Idebugapplicationnodeevents:: ondetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md) -   
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)