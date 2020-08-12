---
title: IDispatchEx::D eletemitgliedbyname | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf62972b192d73bd130d15066d79ea70fe24beb8
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144596"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Löscht einen Member nach dem Namen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 Der Name des zu löschenden Members.  
  
 `grfdex`  
 Bestimmt, ob der Elementname die Groß-/Kleinschreibung beachtet. Mögliche Werte:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexnamecasesensitive|Fordert an, dass die Namenssuche nach Groß-/Kleinschreibung durchgeführt wird. Kann von einem Objekt ignoriert werden, das die Suche nach Groß-und Kleinschreibung nicht unterstützt.|  
|fdexnamecaseinsensitive|Fordert an, dass die Namenssuche ohne Berücksichtigung der Groß-/Kleinschreibung erfolgt. Kann von einem Objekt ignoriert werden, das die Suche ohne Beachtung der Groß-und Kleinschreibung nicht unterstützt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Wert|Bedeutung|
|-|-|  
|`S_OK`|Erfolg.|  
|`S_FALSE`|Der Member ist vorhanden, kann aber nicht gelöscht werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Member gelöscht wird, muss die DISPID für gültig bleiben `GetNextDispID` .  
  
 Wenn ein Element mit einem bestimmten Namen gelöscht und später ein Member mit demselben Namen neu erstellt wird, sollte die DISPID identisch sein. (Unabhängig davon, ob Elemente, die sich nur durch die Groß-/Kleinschreibung unterscheiden, sind Objekt abhängig.)  
  
## <a name="example"></a>Beispiel  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)