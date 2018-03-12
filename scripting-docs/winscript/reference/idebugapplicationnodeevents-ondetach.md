---
title: IDebugApplicationNodeEvents::onDetach | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onDetach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b5f1ccc35e83f4fa016b5ff3dae8fac867bb8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Behandelt ein Ereignis gibt an, dass das Debug-Anwendungsobjekt Knoten von einem übergeordneten Knoten getrennt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode behandelt ein Ereignis gibt an, dass das Debug-Anwendungsobjekt Knoten von einem übergeordneten Knoten getrennt wurde.  
  
 Implementierer der `IDebugApplicationNode` Schnittstelle dieses Ereignis auslösen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNodeEvents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)   
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)