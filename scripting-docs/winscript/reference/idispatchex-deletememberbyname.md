---
title: IDispatchEx::DeleteMemberByName | Microsoft-Dokumentation
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000891"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Löscht ein Element anhand des Namens an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 Name des Elements gelöscht werden soll.  
  
 `grfdex`  
 Bestimmt, ob der Membername Groß-/Kleinschreibung beachtet wird. Dies kann einen der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexNameCaseSensitive|Fordert an, denen die Namenssuche die Groß-und Kleinschreibung ausgeführt werden. Kann vom Objekt ignoriert werden, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
|fdexNameCaseInsensitive|Fordert an, denen die Namenssuche Groß-und Kleinschreibung ausgeführt werden. Kann vom Objekt ignoriert werden, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Element vorhanden ist, aber es kann nicht gelöscht werden.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Element gelöscht wird, muss die DISPID gültig bleiben `GetNextDispID`.  
  
 Wenn ein Element mit einem bestimmten Namen gelöscht wird, und später ein Element mit dem gleichen Namen neu erstellt wird, sollte die DISPID identisch sein. (Ist, ob die Elemente, die nur durch Fall unterscheiden, die "gleich" sind Objekt abhängig.)  
  
## <a name="example"></a>Beispiel  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)