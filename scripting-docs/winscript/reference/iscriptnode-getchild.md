---
title: 'Iscriptnode:: GetChild | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573557"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Gibt das untergeordnete Element zurück, das sich am angegebenen Index im Knoten befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `isn`  
 in Der Index des untergeordneten Elements in der übergeordneten.  
  
 `ppsn`  
 vorgenommen Die Adresse einer Variablen, die einen Zeiger auf die `IScriptNode`-Schnittstelle der untergeordneten Instanz empfängt.  
  
 Bei `IScriptNode` Objekten, die eine Webseite darstellen, gibt dieser Parameter ein Objekt zurück, das einen Skriptblock enthält.  
  
 Bei `IScriptEntry` Objekten, die einen Skriptblock angeben, gibt dieser Parameter ein Objekt zurück, das eine Funktion angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Bei `IScriptEntry` Objekten, die ein Funktions Objekt und für `IScriptScriptlet` Objekte angeben, schlägt diese Methode fehl, da keine untergeordneten Einträge vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)