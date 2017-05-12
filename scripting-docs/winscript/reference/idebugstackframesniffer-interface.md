---
title: "IDebugStackFrameSniffer-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer-Schnittstelle"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer-Schnittstelle
Stellt eine Methode bereit, die logischen Stapelrahmen aufzulisten, die durch eine Komponente bezeichnet werden.  Skriptmodule implementieren normalerweise diese Schnittstelle.  Der Debug\- ProzessManager verwendet diese Schnittstelle, um alle Stapelrahmen zu suchen, die mit einem angegebenen Thread zugeordnet werden.  
  
> [!NOTE]
>  Der Debugger ruft diese Schnittstelle aus dem Thread relevante an.  Das Skriptmodul muss den aktuellen Thread identifizieren und einen entsprechenden Enumerator zurückgeben.  
  
## Methoden  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugStackFrameSniffer`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Gibt einen Enumerator von Stapelrahmen für den aktuellen Thread zurück.|