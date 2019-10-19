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
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576609"
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
 Bestimmt, ob der Elementname die Groß-/Kleinschreibung beachtet. Dies kann einer der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexnamecasesensitive|Fordert an, dass die Namenssuche nach Groß-/Kleinschreibung durchgeführt wird. Kann von einem Objekt ignoriert werden, das die Suche nach Groß-und Kleinschreibung nicht unterstützt.|  
|fdexnamecaseinsensitive|Fordert an, dass die Namenssuche ohne Berücksichtigung der Groß-/Kleinschreibung erfolgt. Kann von einem Objekt ignoriert werden, das die Suche ohne Beachtung der Groß-und Kleinschreibung nicht unterstützt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Der Member ist vorhanden, kann aber nicht gelöscht werden.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Member gelöscht wird, muss die DISPID für `GetNextDispID` gültig bleiben.  
  
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