---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference"
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
Gibt den Windows Runtime eingeschränkten Bezugsfehler zurück, sofern verfügbar.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug\-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### Parameter  
 `referenceString`  
 \[out\] Die Bezugsfehlerzeichenfolge.  
  
## Siehe auch  
 [IActiveScriptWinRTErrorDebug\-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)