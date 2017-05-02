---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
Ruft den Speicherort im Quellcode ab, in dem ein Fehler aufgetreten ist, während das Skriptmodul ein Skript ausführen.  
  
## Syntax  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### Parameter  
 `pdwSourceContext`  
 \[out\] Adresse einer Variablen, die ein Cookie empfängt, das den Kontext identifiziert.  Die Darstellung dieses Parameters hängt von der Hostanwendung.  
  
 `pulLineNumber`  
 \[out\] Adresse einer Variable, die die Zeilennummer in der Quelldatei empfängt, in der der Fehler aufgetreten ist.  
  
 `pichCharPosition`  
 \[out\] Adresse einer Variablen, die die Zeichenposition in der Zeile empfängt, in der der Fehler aufgetreten ist.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_FAIL`, wenn der Speicherort nicht abgerufen wurde.  
  
## Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)