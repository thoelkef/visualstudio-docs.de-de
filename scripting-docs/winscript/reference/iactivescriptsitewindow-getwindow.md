---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
Ruft das Handle für ein Fenster ab, das als der Besitzer eines Popupfensters auftreten kann, das das Skriptmodul anzeigen muss.  
  
## Syntax  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### Parameter  
 `phwnd`  
 \[out\] Adresse einer Variablen, die das Fensterhandle empfängt.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_FAIL`, wenn ein Fehler aufgetreten ist.  
  
## Hinweise  
 Diese Methode ist mit der `IOleWindow::GetWindow`\-Methode vergleichbar.  
  
## Siehe auch  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)