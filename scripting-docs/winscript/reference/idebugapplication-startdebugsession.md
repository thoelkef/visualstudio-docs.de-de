---
title: "IDebugApplication::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StartDebugSession
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StartDebugSession"
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StartDebugSession
Startet die standardmäßige Debuggerintegrierte Entwicklungsumgebung \(IDE\) und die fügt eine Debugsitzung zu dieser Anwendung, wenn nicht bereits angefügt wird.  
  
## Syntax  
  
```  
HRESULT StartDebugSession();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird verwendet, um das Just\-In\-Time\-Debuggen zu implementieren.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)