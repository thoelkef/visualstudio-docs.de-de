---
title: 'Iscriptnode:: GetParent | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572555"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Gibt das `IScriptNode` Objekt zurück, das dem-Objekt übergeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppsnParent`  
 vorgenommen Die Adresse einer Variablen, die einen Zeiger auf die `IScriptNode`-Schnittstelle der übergeordneten Instanz empfängt.  
  
 Wenn die-Klasse `IScriptEntry` oder `IScriptScriptlet` implementiert, wird ein `IScriptNode`-Objekt zurückgegeben.  
  
 Wenn die Klasse `IScriptNode` implementiert (die eine Webseite darstellt), wird NULL zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)