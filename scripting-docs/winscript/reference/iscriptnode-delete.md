---
title: Iscriptnode::D Elete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c3522e5543d333443de5b1287c994bf29de51c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576306"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Löscht diese Objektstruktur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die-Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Nachdem die `Delete`-Methode aufgerufen wurde, sollte die [iscriptnode:: Alive](../../winscript/reference/iscriptnode-alive.md) -Methode angeben, dass der Skript Knoten nicht aktiv ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)