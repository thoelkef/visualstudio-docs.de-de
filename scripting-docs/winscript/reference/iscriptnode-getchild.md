---
title: IScriptNode::GetChild | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086592"
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