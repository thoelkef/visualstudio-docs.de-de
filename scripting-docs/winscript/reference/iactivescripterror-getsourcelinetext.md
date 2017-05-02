---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
Ruft die Zeile in der Quelldatei ab, in der ein Fehler aufgetreten ist, während ein Skriptmodul ein Skript ausführen.  
  
## Syntax  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## Parameter  
 `pbstrSourceLine`  
 \[out\] Adresse eines Puffers, der die Zeile des Quellcodes empfängt, in der der Fehler aufgetreten ist.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_FAIL`, wenn die Zeile in der Quelldatei nicht abgerufen wurde.  
  
## Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)