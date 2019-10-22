---
title: 'Iscriptentry:: setbody | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575384"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Legt den Text fest, der im Hauptteil eines `IScriptEntry` Skript Blocks oder eines `IScriptScriptlet` Scriptlets liegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psz`  
 in Bei einem `IScriptEntry` Skriptblock ist `psz` der Text, der in den Skript Tags eingeschlossen ist.  
  
 Bei einem `IScriptEntry`-Funktionsblock ist `psz` der Funktions Rumpf.  
  
 Bei einem `IScriptScriptlet` Objekt (das von `IScriptEntry` abgeleitet ist) ist `psz` der Skript Text des Scriptlets.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iscriptentry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)