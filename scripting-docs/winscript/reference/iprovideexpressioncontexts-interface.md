---
title: "IProvideExpressionContexts-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts-Schnittstelle"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts-Schnittstelle
Stellt eine Methode bereit, die Ausdruckskontexte aufzulisten, die von einer bestimmten Komponente bezeichnet werden.  Skriptmodule implementieren normalerweise diese Schnittstelle.  
  
 Der Debug\- ProzessManager verwendet diese Schnittstelle, um alle globalen Ausdruckskontexte zu suchen, die mit einem angegebenen Thread zugeordnet werden.  
  
> [!NOTE]
>  Diese Schnittstelle wird aus dem Thread relevante bezeichnet.  Sie ist von der Implementierung, um des aktuellen Threads ermitteln und eines entsprechenden Enumerators zurückzugeben.  
  
## Methoden  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IProvideExpressionContexts`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Gibt einen Enumerator von den Ausdruckskontexten zurück, die von dieser Komponente bezeichnet werden.|