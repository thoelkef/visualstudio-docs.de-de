---
title: "IActiveScriptErrorDebug::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetDocumentContext"
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetDocumentContext
Stellt den Dokumentenkontext für diesen Fehler.  
  
## Syntax  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### Parameter  
 `ppssc`  
 \[out\] Der Dokumentenkontext für diesen Fehler.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Dokumentenkontext\-Zeichenpositionsbereich sollte alle Zeichen entsprechend dem Fehler enthalten.  
  
## Siehe auch  
 [IActiveScriptErrorDebug\-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)