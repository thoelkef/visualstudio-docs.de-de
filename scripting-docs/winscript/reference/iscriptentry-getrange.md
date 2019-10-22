---
title: 'Iscriptentry:: GetRange | Microsoft-Dokumentation'
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
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575436"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Gibt die Startposition und die Länge eines Eintrags zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pichMin`  
 vorgenommen Bei `IScriptEntry` Objekten, die einen Skriptblock angeben, wird 0 zurückgegeben.  
  
 Bei `IScriptEntry` Objekten, die ein Funktions Objekt angeben, wird die Startposition der Funktion im aktuellen Skriptblock zurückgegeben.  
  
 Bei `IScriptScriptlet`-Objekten wird 0 zurückgegeben.  
  
 `pcch`  
 vorgenommen Bei `IScriptEntry` Objekten, die einen Skriptblock angeben, wird die Länge des Texts zurückgegeben.  
  
 Gibt die Länge der Funktionsdefinition für `IScriptEntry` Objekte zurück, die ein Funktions Objekt angeben.  
  
 Gibt für `IScriptScriptlet`-Objekte die Länge des Eintrags zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)