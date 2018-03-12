---
title: IDebugApplicationNode::Close | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationNode.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Close
ms.assetid: ea8db480-2344-4c7b-960c-4fa97fa6c1b7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d50d1e9a22c3d64d65847922090dfab0c33ab32
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeclose"></a>IDebugApplicationNode::Close
Bewirkt, dass diese Anwendung alle Verweise freigeben, und geben einen inaktiven Status.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel ruft der Besitzer einer Anwendung diese Methode beim Beenden der Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)