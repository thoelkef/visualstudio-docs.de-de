---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
Veranlasst den Host, sein Hauptfenster sowie alle nicht modale Dialogfelder zu aktivieren oder zu deaktivieren.  
  
## Syntax  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### Parameter  
 `fEnable`  
 \[in\] Der Funktion, das, wenn `TRUE`, das Hauptfenster und die nicht modalen Dialogfelder oder, wenn `FALSE` aktiviert, sie deaktiviert.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_FAIL`, wenn ein Fehler aufgetreten ist.  
  
## Hinweise  
 Diese Methode ist zur `IOleInPlaceFrame::EnableModeless`\-Methode identisch.  
  
 Aufrufe dieser Methode können geschachtelt werden.  
  
## Siehe auch  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)