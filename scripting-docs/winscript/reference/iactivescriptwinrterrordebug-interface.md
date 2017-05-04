---
title: "IActiveScriptWinRTErrorDebug-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug-Schnittstelle"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug-Schnittstelle
Durch das JavaScript\-Modul, um erweiterte Windows Runtime\-Fehlerinformationen von einem [BREAKREASON\-Enumeration](../../winscript/reference/breakreason-enumeration.md)\-Ereignis bereitzustellen.  Sie können ein QueryInterface durchführen, um es von einem [IActiveScriptError](../../winscript/reference/iactivescripterror.md)\-Objekt abzurufen.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Die `IActiveScriptWinRTErrorDebug`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Gibt die Funktion SIDs für Windows Runtime\-Fehler zurück, sofern verfügbar.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Gibt die Windows Runtime eingeschränkte Fehlerbezugszeichenfolge zurück, sofern verfügbar.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Gibt die Windows Runtime eingeschränkte Fehlerzeichenfolge zurück, sofern verfügbar.|