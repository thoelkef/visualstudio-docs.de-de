---
title: IScriptNode::GetParent | Microsoft-Dokumentation
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
ms.openlocfilehash: 1c990b5ba5c3d03d319e0eeced282c92cfbb5281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786855"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Gibt die `IScriptNode` -Objekt, das das übergeordnete Element eines Objekts ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppsnParent`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptNode` Schnittstelle der übergeordneten Instanz.  
  
 Wenn die Klasse implementiert `IScriptEntry` oder `IScriptScriptlet`, `IScriptNode` Objekt zurückgegeben.  
  
 Wenn die Klasse implementiert `IScriptNode` (für eine Webseite), wird NULL zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)