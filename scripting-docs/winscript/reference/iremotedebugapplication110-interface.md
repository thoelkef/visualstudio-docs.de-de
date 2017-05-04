---
title: "IRemoteDebugApplication110-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110-Schnittstelle"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110-Schnittstelle
Wird verwendet, um neue Funktionen bereitzustellen, die von den Skriptdebuggern und von den prozessinternen Aufrufern aufgerufen werden können.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Die `IRemoteDebugApplication110`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Description|  
|-------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Wird aufgerufen, um Debuggeroptionen zu aktualisieren.  Der Optionsstandard auf 0 \(SDO\_NONE\).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Gibt den aktuellen zurück, der von den Optionen festgelegt, die aktiviert werden.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Gibt den Hauptthread für Hosts zurück, die SetSite aufrufen.|