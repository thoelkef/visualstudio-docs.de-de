---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName-Methode"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
Löscht einen Member über den Namen.  
  
## Syntax  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### Parameter  
 `bstrName`  
 Name des zu löschenden Members.  
  
 `grfdex`  
 Bestimmt, ob der Membername die Groß\-\/Kleinschreibung beachtet wird.  Dieser kann einer der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|fdexNameCaseSensitive|Die diese Anforderungen die Namenssuche sind in einer Groß\-\/Kleinschreibung Weise ausgeführt.  Die kann durch Objekt ignoriert werden, das die Groß\-\/Kleinschreibung nicht beachtet Suche unterstützt.|  
|fdexNameCaseInsensitive|Die diese Anforderungen die Namenssuche sind in einer Kleinschreibung Weise ausgeführt.  Die kann durch Objekt ignoriert werden, das nicht Groß\-\/Kleinschreibung keine Suche unterstützt.|  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Member vorhanden ist, aber nicht gelöscht werden kann.|  
  
## Hinweise  
 Wenn der Member gelöscht wird, muss das DISPID für `GetNextDispID` gültig bleiben.  
  
 Wenn ein Member mit einem angegebenen Namen gelöscht wird und später ein Member mit dem gleichen Namen neu erstellt wird, sollte das DISPID das identisch sein.  Ob \(Member, die nur durch die Groß\-\/Kleinschreibung unterscheiden, sind "," identisch ist Objektabhängiges Element.\)  
  
## Beispiel  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)