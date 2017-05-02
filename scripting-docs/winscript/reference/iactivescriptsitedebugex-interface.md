---
title: "IActiveScriptSiteDebugEx-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx-Schnittstelle"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx-Schnittstelle
Implementieren Sie diese Schnittstelle zusammen mit der `IActiveScriptSiteDebug`\-Schnittstelle, wenn Sie einen Host schreiben, der eine Benachrichtigung eines Laufzeitfehlers in einer Anwendung und optional der Durchführen an die Anwendung für das Debuggen zugreifen muss.  Der Prozessdebug\-Manager stellt Benachrichtigung von `IActiveScriptDebug` bereit, wenn ein Just\-in\-Time\-Skriptdebugger auf dem Computer gefunden wird.  Wenn kein Just\-in\-Time\-Skriptdebugger gefunden wird, wird das PDM Benachrichtigung von `IActiveScriptDebugEx` stattdessen bereit.  
  
 Um eine Benachrichtigung eines Laufzeitfehlers abzurufen, muss der Host [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/de-de/cf7639f9-a699-4571-9f3a-82ef52c0b5f4) behandeln.  Auf Grundlage eine Benutzeraktion können Sie anschließend entscheiden, ob der internen Debugger und die Rückgabe anfügt oder Starten des Debuggers im Parameter OnScriptErrorDebug `pfEnterDebugger` zurückgibt.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informiert den Host über einen Skriptlaufzeitfehler, wenn der Prozessdebug\-Manager keinen externen Just\-in\-timedebugger sucht.|