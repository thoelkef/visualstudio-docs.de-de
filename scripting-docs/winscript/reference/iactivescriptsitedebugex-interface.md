---
title: IActiveScriptSiteDebugEx-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx-Schnittstelle
Implementieren Sie diese Schnittstelle zusammen mit der `IActiveScriptSiteDebug` Schnittstelle, wenn Sie einen Host schreiben, die muss eine Benachrichtigung über einen Laufzeitfehler in einer Anwendung abrufen und optional an die Anwendung zum Debuggen anzufügen. Der Debug-Prozess-Manager stellt eine Benachrichtigung über bereit `IActiveScriptDebug` Wenn Skript für eine Just-In-Time-Debugger ist auf dem Computer gefunden. Wenn keine Just-in-Time-Skriptdebugger wird gefunden, die PDM stellt die Benachrichtigung über `IActiveScriptDebugEx` stattdessen.  
  
 Um eine Benachrichtigung über einen Laufzeitfehler zu erhalten, muss der Host behandeln [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). Basierend auf eine Benutzeraktion, Sie können dann entscheiden, ob die internen Debugger und die Rückgabetypen anfügen oder zurückzugeben, das Starten des Debuggers in der OnScriptErrorDebug `pfEnterDebugger` Parameter.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informiert, dass der Host über ein Skript zur Laufzeit Fehler beim Debuggen die Prozess-Manager einen externen nur Just-in-Time-Debugger nicht finden kann.|