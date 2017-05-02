---
title: "IActiveScriptErrorDebug110-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110-Schnittstelle"
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptErrorDebug110-Schnittstelle
Fügt [IActiveScriptDebug\-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md) Funktionalität hinzu.  Diese Schnittstelle wird durch das JavaScript\-Modul implementiert, um zu bestimmen, warum ein BREAKREASON\_ERROR\-Ereignis aufgetreten ist.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert.  Gefunden in activdbg100.h.  
  
## Methoden  
 Die `IActiveScriptErrorDebug110`\-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Gibt die Ausnahmeart für eine ausgelöste Ausnahme zurück.|