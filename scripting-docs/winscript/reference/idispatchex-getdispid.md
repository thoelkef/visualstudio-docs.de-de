---
title: 'IDispatchEx:: GetDispID | Microsoft-Dokumentation'
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
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576601"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Ordnet der entsprechenden DISPID einen einzelnen Elementnamen zu, der dann bei nachfolgenden Aufrufen von `IDispatchEx::InvokeEx` verwendet werden kann.  
  
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
 Der Name, der zugeordnet werden soll.  
  
 `grfdex`  
 Bestimmt die Optionen zum Abrufen des Element Bezeichners. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexnamecasesensitive|Fordert an, dass die Namenssuche nach Groß-/Kleinschreibung durchgeführt wird. Kann von einem Objekt ignoriert werden, das die Suche nach Groß-und Kleinschreibung nicht unterstützt.|  
|f-namesicher|Fordert an, dass der Member erstellt wird, wenn er nicht bereits vorhanden ist. Der neue Member sollte mit dem Wert `VT_EMPTY` erstellt werden.|  
|"f-nameimplicit"|Gibt an, dass der Aufrufer Objekte nach einem Member eines bestimmten namens durchsucht, wenn das Basisobjekt nicht explizit angegeben wird.|  
|fdexnamecaseinsensitive|Fordert an, dass die Namenssuche ohne Berücksichtigung der Groß-/Kleinschreibung erfolgt. Kann von einem Objekt ignoriert werden, das die Suche ohne Beachtung der Groß-und Kleinschreibung nicht unterstützt.|  
  
 `pid`  
 Zeiger auf den vom Aufrufer zugewiesenen Speicherort zum Empfangen des DISPID-Ergebnisses. Wenn ein Fehler auftritt, enthält `pid` DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`E_OUTOFMEMORY`|Nicht genügend Arbeitsspeicher.|  
|`DISP_E_UNKNOWNNAME`|Der Name war nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 `GetDispID` können anstelle von `GetIDsOfNames` verwendet werden, um die DISPID für ein bestimmtes Element abzurufen.  
  
 Da `IDispatchEx` das Hinzufügen und Löschen von Membern ermöglicht, bleibt der Satz von DISPIDs für die Lebensdauer eines Objekts konstant.  
  
 Der nicht verwendete `riid` Parameter in `IDispatch::GetIDsOfNames` wurde entfernt.  
  
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