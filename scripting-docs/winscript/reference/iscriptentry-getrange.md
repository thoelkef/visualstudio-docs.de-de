---
title: IScriptEntry::GetRange | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7baa284be4fa7f45f247df7f4b3d140869f254b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787736"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Gibt die Startposition und Länge eines Eintrags.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pichMin`  
 [out] Für `IScriptEntry` Objekte, die einen Skriptblock angeben, wird 0 zurückgegeben.  
  
 Für `IScriptEntry` Objekte, die angeben, ein Funktionsobjekt, gibt die Anfangsposition der Funktion im aktuellen Skriptblock.  
  
 Für `IScriptScriptlet` Objekte, wird 0 zurückgegeben.  
  
 `pcch`  
 [out] Für `IScriptEntry` Objekte, die angeben, einen Skriptblock, gibt die Länge des Texts zurück.  
  
 Für `IScriptEntry` Objekte, die angeben, ein Funktionsobjekt, gibt die Länge der Definition der Funktion zurück.  
  
 Für `IScriptScriptlet` Objekte, gibt die Länge des Eintrags zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)