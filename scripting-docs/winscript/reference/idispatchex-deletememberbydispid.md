---
title: IDispatchEx::D eletemembership bydispid | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ead33fb51caff1103ca9abe6bc01f3e0aa6aa3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576635"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Löscht einen Member durch DISPID.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 Elementbezeichner Verwendet `GetDispID` oder `GetNextDispID`, um den Dispatchbezeichner abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Der Member ist vorhanden, kann aber nicht gelöscht werden.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Member gelöscht wird, muss die DISPID für `GetNextDispID`gültig bleiben.  
  
 Wenn ein Element mit einem bestimmten Namen gelöscht und später ein Member mit demselben Namen neu erstellt wird, sollte die DISPID identisch sein. (Unabhängig davon, ob die Elementnamen, die sich nur durch die Groß-/Kleinschreibung unterscheiden, vom Objekt abhängig sind.)  
  
## <a name="example"></a>Beispiel  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)