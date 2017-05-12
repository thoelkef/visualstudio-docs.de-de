---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByDispID-Methode"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
Löscht einen Member durch DISPID.  
  
## Syntax  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### Parameter  
 `id`  
 Memberbezeichner.  Verwendung `GetDispID` oder `GetNextDispID`, in der Dispatchbezeichner.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Member vorhanden ist, aber nicht gelöscht werden kann.|  
  
## Hinweise  
 Wenn der Member gelöscht wird, muss das DISPID für `GetNextDispID` gültig bleiben.  
  
 Wenn ein Member mit einem angegebenen Namen gelöscht wird und später ein Member mit dem gleichen Namen neu erstellt wird, sollte das DISPID das identisch sein.  Ob \(Membernamen, die nur durch die Groß\-\/Kleinschreibung unterscheiden, sind "," identisch ist Objektabhängiges Element.\)  
  
## Beispiel  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)