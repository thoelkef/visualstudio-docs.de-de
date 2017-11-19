---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Löscht ein Element anhand des Namens an.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 Name des Elements gelöscht werden soll.  
  
 `grfdex`  
 Bestimmt, ob der Elementname Groß-/Kleinschreibung beachtet wird. Dies kann einer der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexNameCaseSensitive|Anforderungen, die die Namenssuche die Groß-und Kleinschreibung ausgeführt werden. Kann vom Objekt ignoriert werden, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
|fdexNameCaseInsensitive|Anforderungen, die unter Beachtung der Namenssuche ausgeführt werden. Kann vom Objekt ignoriert werden, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Element vorhanden ist, aber es kann nicht gelöscht werden.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Element gelöscht wird, muss die DISPID für gültig bleibt `GetNextDispID`.  
  
 Wenn ein Element mit einem angegebenen Namen wird gelöscht, und später ein Element mit dem gleichen Namen neu erstellt, sollte die DISPID identisch sein. (Ist, ob Elemente, die sich nur durch '-Fällen zu unterscheiden sind "identisch" Objekt abhängig.)  
  
## <a name="example"></a>Beispiel  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)