---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
Informiert den Host, dass das Skriptmodul Zustände geändert hat.  
  
## Syntax  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### Parameter  
 `ssScriptState`  
 \[in\] Der Wert, das den neuen Skriptzustand angibt.  Siehe die [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)\-Methode für eine Beschreibung der Zustände.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK` zurückgegeben.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)