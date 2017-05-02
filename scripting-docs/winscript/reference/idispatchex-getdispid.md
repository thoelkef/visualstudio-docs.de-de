---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID-Methode"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
Ordnet einen einzelnen Membernamen den entsprechenden DISPID zu, das bei nachfolgenden Aufrufen von `IDispatchEx::InvokeEx` dann verwendet werden kann.  
  
## Syntax  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### Parameter  
 `bstrName`  
 Übergeben in den Namen zugeordnet werden.  
  
 `grfdex`  
 Bestimmt die Optionen zum Abrufen der Memberbezeichner.  Diese kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|fdexNameCaseSensitive|Die diese Anforderungen die Namenssuche sind in einer Groß\-\/Kleinschreibung Weise ausgeführt.  Die kann durch Objekt ignoriert werden, das die Groß\-\/Kleinschreibung nicht beachtet Suche unterstützt.|  
|fdexNameEnsure|Anforderungen, die dem Member erstellt wird, wenn sie nicht bereits vorhanden ist.  Der neue Member sollte mit dem Wert `VT_EMPTY` erstellt werden.|  
|fdexNameImplicit|Gibt an, dass der Aufrufer Objekte für ein Member eines bestimmten Namens findet, wenn das Basisobjekt nicht explizit angegeben wird.|  
|fdexNameCaseInsensitive|Die diese Anforderungen die Namenssuche sind in einer Kleinschreibung Weise ausgeführt.  Die kann durch Objekt ignoriert werden, das nicht Groß\-\/Kleinschreibung keine Suche unterstützt.|  
  
 `pid`  
 Zeiger auf den vom Aufrufer reservierten Position, an der DISPID\-Ergebnis zu empfangen.  Wenn ein Fehler auftritt, enthält `pid` DISPID\_UNKNOWN.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`E_OUTOFMEMORY`|Nicht genügend Arbeitsspeicher.|  
|`DISP_E_UNKNOWNNAME`|Der Name ist nicht bekannt.|  
  
## Hinweise  
 `GetDispID` kann anstelle `GetIDsOfNames` verwendet werden, erhält das DISPID für einen angegebenen Member.  
  
 Da `IDispatchEx` das Hinzufügen und Löschen von Member zulässig ist, bleibt der Satz von DISPID nicht während der Lebensdauer eines Objekts konstant.  
  
 Der nicht verwendete `riid`\-Parameter in `IDispatch::GetIDsOfNames` wurde entfernt.  
  
## Beispiel  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)