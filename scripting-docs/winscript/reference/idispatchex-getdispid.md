---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729050"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Ordnet Mitgliedsname für eine einzelnes seiner entsprechenden DISPID, die dann bei nachfolgenden Aufrufen verwendet werden kann `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Syntax  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 Übergeben im Namen zugeordnet werden sollen.  
  
 `grfdex`  
 Bestimmt die Optionen zum Abrufen von den Elementbezeichner. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexNameCaseSensitive|Anforderungen, die die Namenssuche die Groß-und Kleinschreibung ausgeführt werden. Kann vom Objekt ignoriert werden sollen, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
|fdexNameEnsure|Fordert an, dass das Element erstellt werden, wenn sie nicht bereits vorhanden ist. Das neue Element erstellt werden sollten, mit dem Wert `VT_EMPTY`.|  
|fdexNameImplicit|Gibt an, dass der Aufrufer Objekt(e) für ein Element von einem bestimmten Namen suchen wird, wenn das Basisobjekt nicht explizit angegeben ist.|  
|fdexNameCaseInsensitive|Anforderungen, die unter Beachtung der Namenssuche ausgeführt werden. Kann vom Objekt ignoriert werden sollen, die Groß-/Kleinschreibung Suche nicht unterstützt.|  
  
 `pid`  
 Zeiger auf vom Aufrufer reservierten Speicherort um DISPID Ergebnis zu erhalten. Wenn ein Fehler auftritt, `pid` enthält u. DISPID_UNKNOWN lauten.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`E_OUTOFMEMORY`|Nicht genügend Arbeitsspeicher.|  
|`DISP_E_UNKNOWNNAME`|Der Name wurde nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 `GetDispID`kann verwendet werden, anstelle von `GetIDsOfNames` , die die DISPID für ein angegebenes Element zu erhalten.  
  
 Da `IDispatchEx` ermöglicht das Hinzufügen und Löschen von Elementen, die den Satz von DISPIDs bleibt nicht Konstanten für die Lebensdauer eines Objekts.  
  
 Der nicht verwendeten `riid` im Parameters `IDispatch::GetIDsOfNames` entfernt wurde.  
  
## <a name="example"></a>Beispiel  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)