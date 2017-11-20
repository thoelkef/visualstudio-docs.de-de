---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Gibt das untergeordnete Element, das am angegebenen Index im Knoten "" ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `isn`  
 [in] Der Index des untergeordneten Elements in der übergeordneten Tabelle.  
  
 `ppsn`  
 [out] Die Adresse einer Variablen, die einen Zeiger auf empfängt die `IScriptNode` Schnittstelle der untergeordneten Instanz.  
  
 Für `IScriptNode` Objekte, die eine Webseite darstellen, dieser Parameter gibt ein Objekt, das einen Skriptblock enthält.  
  
 Für `IScriptEntry` Objekte, die einen Skriptblock angeben, gibt dieser Parameter ein Objekt, eine Funktion angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Für `IScriptEntry` Objekten, die ein Funktionsobjekt angeben und für `IScriptScriptlet` Objekte aufweist, diese Methode schlägt fehl, da keine untergeordneten Einträge vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)