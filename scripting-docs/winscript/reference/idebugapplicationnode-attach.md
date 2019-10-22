---
title: 'Idebugapplicationnode:: Attach | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574782"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Fügt den Anwendungs Knoten der angegebenen Projektstruktur hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdanParent`  
 in Die Projektstruktur, in der dieser Anwendungs Knoten hinzugefügt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode fügt diesen Anwendungs Knoten der Projektstruktur hinzu, wobei `pdanParent` als übergeordnetes Element verwendet wird. Wenn `pdanParent` `NULL` ist, wird dieser Anwendungs Knoten als Knoten der obersten Ebene verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplicationnode::D Etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)