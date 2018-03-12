---
title: IScriptEntry::GetRange | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Gibt die Startposition und Länge eines Eintrags an.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pichMin`  
 [out] Für `IScriptEntry` Objekte, die einen Skriptblock geben 0 zurück.  
  
 Für `IScriptEntry` Objekte, die angeben, ein Funktionsobjekt gibt die Startposition der Funktion im aktuellen Skriptblock.  
  
 Für `IScriptScriptlet` Objekte, wird 0 zurückgegeben.  
  
 `pcch`  
 [out] Für `IScriptEntry` Objekte, die einen Skriptblock angeben gibt die Länge des Texts zurück.  
  
 Für `IScriptEntry` Objekte, die angeben, ein Funktionsobjekt gibt die Länge der Definition der Funktion zurück.  
  
 Für `IScriptScriptlet` Objekte, gibt die Länge des Eintrags.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)