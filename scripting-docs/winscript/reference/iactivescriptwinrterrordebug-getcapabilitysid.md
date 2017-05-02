---
title: "IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetCapabilitySid"
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetCapabilitySid
Gibt die Funktion SIDs für Windows Runtime\-Fehler zurück, sofern verfügbar.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug\-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### Parameter  
 `capabilitySid`  
 Die Funktion SID des Fehlers.  
  
## Siehe auch  
 [IActiveScriptWinRTErrorDebug\-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)