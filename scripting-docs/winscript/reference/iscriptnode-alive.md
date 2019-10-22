---
title: 'Iscriptnode:: Alive | Microsoft-Dokumentation'
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
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573628"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Gibt an, ob ein Objekt noch aktiv ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die-Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Skript Knoten ist noch aktiv.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Objekt nicht aktiv ist, gibt Component Object Model (com) einen Fehler vom marshallingproxy für Aufrufe dieser Methode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)