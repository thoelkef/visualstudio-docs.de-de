---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
Ruft eine Zeichenfolge ab, die Host\-definierte eindeutig die Version des aktuellen Dokuments identifiziert.  Wenn das zugehörige Dokument außerhalb des Bereichs des Windows Scripts \(wie im Fall einer HTML\-Seite, die mit Editor bearbeitet wird\) geändert wurde, kann das Skriptmodul dieses zusammen mit dem gespeicherten Zustand speichern und einen Kompilieren Sie erzwingen, beim nächsten das Skript geladen wird.  
  
## Syntax  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### Parameter  
 `pstrVersionString`  
 \[out\] Adresse der Host\-definierten Dokumentenversionszeichenfolge.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_NOTIMPL`, wenn diese Methode nicht unterstützt wird.  
  
## Hinweise  
 Wenn `E_NOTIMPL` zurückgegeben wird, sollte das Skriptmodul davon ausgehen, dass das Skript mit dem Dokument ist.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)