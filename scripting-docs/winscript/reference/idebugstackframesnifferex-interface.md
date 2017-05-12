---
title: "IDebugStackFrameSnifferEx-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx-Schnittstelle"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx-Schnittstelle
Stellt eine Methode bereit, die logischen Stapelrahmen aufzulisten, die durch eine Komponente bezeichnet werden.  Skriptmodule implementieren normalerweise diese Schnittstelle.  Der Debug\- ProzessManager verwendet diese Schnittstelle, um alle Stapelrahmen zu suchen, die mit einem angegebenen Thread zugeordnet werden.  
  
> [!NOTE]
>  Diese Schnittstelle wird aus dem Thread relevante bezeichnet.  Die Schnittstellenimplementierung muss den aktuellen Thread identifizieren und einen entsprechenden Enumerator zurückgeben.  
  
 Zusätzlich zu den von `IDebugStackFrameSniffer` geerbten Methoden macht die `IDebugStackFrameSnifferEx`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Gibt einen Enumerator von Stapelrahmen für den aktuellen Thread zurück.|