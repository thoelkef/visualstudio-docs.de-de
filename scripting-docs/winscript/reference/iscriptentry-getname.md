---
title: 'Iscriptentry:: GetName | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c99cda48a20efb41b2535645ccdb50be8bb6d6bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575448"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Gibt für Einträge, die ein einzelnes Objekt (z. b. eine Funktion) darstellen, den Namen des Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstr`  
 vorgenommen Der Name des Objekts, das durch den `IScriptEntry` Skriptblock dargestellt wird. Wenn ein Eintrag kein einzelnes Objekt darstellt, wird NULL zurückgegeben.  
  
 Untergeordnete Einträge stellen ein einzelnes Funktions Objekt dar.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Iscriptentry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)