---
title: IScriptNode::Alive | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159217"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Gibt an, ob ein Objekt noch aktiv ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Skriptknoten ist immer noch aktiv.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Objekt nicht aktiv ist, wird ein Fehler Component Object Model (COM) aus dem Marshalling Proxy für die Aufrufe dieser Methode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)