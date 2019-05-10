---
title: IScriptNode::GetChild | Microsoft-Dokumentation
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
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787129"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Gibt das untergeordnete Element, das am angegebenen Index in der Knoten ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `isn`  
 [in] Der Index des untergeordneten Elements im übergeordneten Element.  
  
 `ppsn`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptNode` Schnittstelle die untergeordnete Instanz.  
  
 Für `IScriptNode` Objekte, die eine Webseite darstellen, gibt dieser Parameter ein Objekt, das einen Skriptblock enthält.  
  
 Für `IScriptEntry` Objekte, die einen Skriptblock angeben, gibt dieser Parameter ein Objekt, eine Funktion angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Für `IScriptEntry` Objekte, die angeben, ein Funktionsobjekt und `IScriptScriptlet` Objekten, die diese Methode schlägt fehl, da keine untergeordneten Einträge vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)