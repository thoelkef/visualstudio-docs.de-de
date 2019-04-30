---
title: IDispatchEx::GetDispID | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95ab1d72e5b2f608c51ac6e56be1986df8945ec2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000862"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Ordnet einen Namen für die einzelnen Member der entsprechenden DISPID, die dann bei nachfolgenden Aufrufen verwendet werden kann `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 Übergeben Namen zugeordnet werden soll.  
  
 `grfdex`  
 Bestimmt die Optionen zum Abrufen von der Memberbezeichner. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexNameCaseSensitive|Fordert an, denen die Namenssuche die Groß-und Kleinschreibung ausgeführt werden. Kann vom Objekt ignoriert werden, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
|fdexNameEnsure|Fordert an, dass das Element erstellt werden, wenn es nicht bereits vorhanden ist. Das neue Element erstellt werden soll, mit dem Wert `VT_EMPTY`.|  
|fdexNameImplicit|Gibt an, dass der Aufrufer Objekte für ein Element mit einem bestimmten Namen suchen, wird das Basisobjekt nicht explizit angegeben ist.|  
|fdexNameCaseInsensitive|Fordert an, denen die Namenssuche Groß-und Kleinschreibung ausgeführt werden. Kann vom Objekt ignoriert werden, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
  
 `pid`  
 Zeiger auf vom Aufrufer reservierten Speicherort um DISPID Ergebnis zu erhalten. Wenn ein Fehler auftritt, `pid` DISPID_UNKNOWN enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`E_OUTOFMEMORY`|Nicht genügend Arbeitsspeicher.|  
|`DISP_E_UNKNOWNNAME`|Der Name wurde nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 `GetDispID` kann verwendet werden, anstelle von `GetIDsOfNames` um die DISPID für ein bestimmtes Element abzurufen.  
  
 Da `IDispatchEx` ermöglicht das Hinzufügen und Löschen von Elementen, die den Satz von DISPIDs bleibt nicht Konstanten für die Lebensdauer eines Objekts.  
  
 Der nicht verwendeten `riid` Parameter im `IDispatch::GetIDsOfNames` wurde entfernt.  
  
## <a name="example"></a>Beispiel  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)