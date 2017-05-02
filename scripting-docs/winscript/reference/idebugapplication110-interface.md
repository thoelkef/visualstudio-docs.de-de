---
title: "IDebugApplication110-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110-Schnittstelle"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110-Schnittstelle
Die `IDebugApplication110`\-Schnittstelle erweitert die Funktionalität [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md).  Sie können eine Instanz dieser Schnittstelle abrufen, indem Sie entweder QueryInterface auf einer Implementierung von [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md) aufrufen.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Die `IDebugApplication110`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Führt einen synchronen Aufruf im Hauptausführungsthread auf.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Führt einen asynchronen Aufruf im Hauptausführungsthread auf.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Wartung eines der angegebenen Handles beim Ermöglichen des den threadübergreifenden zu diesem Thread zu sendende Aufrufen signalisiert wird.  Diese Methode muss vom Debuggerthread aufgerufen werden.|