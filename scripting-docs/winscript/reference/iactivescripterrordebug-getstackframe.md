---
title: "IActiveScriptErrorDebug::GetStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetStackFrame
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetStackFrame"
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetStackFrame
Stellt den Stapelrahmen bereit, der für Laufzeitfehler wirksam ist.  
  
## Syntax  
  
```  
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### Parameter  
 `ppdsf`  
 \[out\] Der Stapelrahmen für den Fehler.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode stellt den Stapelrahmen, der wirksam für Laufzeitfehler ist.  
  
## Siehe auch  
 [IActiveScriptErrorDebug\-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)