---
title: "Der Wert &quot;System.Runtime.InteropServices.DispIdAttribute&quot; kann nicht auf &quot;&lt;Typname&gt;&quot; angewendet werden, da &quot;Microsoft.VisualBasic.ComClassAttribute&quot; Werte reserviert, die kleiner als 0 (null) sind | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32506"
  - "vbc32506"
helpviewer_keywords: 
  - "BC32506"
ms.assetid: c6f52e1d-45d8-45cb-9ecb-a2f23b3ca779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Wert &quot;System.Runtime.InteropServices.DispIdAttribute&quot; kann nicht auf &quot;&lt;Typname&gt;&quot; angewendet werden, da &quot;Microsoft.VisualBasic.ComClassAttribute&quot; Werte reserviert, die kleiner als 0 (null) sind
Ein <xref:System.Runtime.InteropServices.DispIdAttribute>\-Attributblock gibt einen DISPID\-Wert an, der kleiner als 0 \(null\) ist. Dieser ist von `COMClassAttribute` für Sonderfunktionen für die Klasse reserviert, auf die der Wert angewendet wird.  
  
 Die Dispatch\-ID \(DISPID\) wird in COM als Argument für die `IDispatch:Invoke`\-Methode verwendet, um auf die Eigenschaften und Methoden zuzugreifen, die von einem COM\-Objekt verfügbar gemacht werden.  
  
 **Fehler\-ID:** BC32506  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie in `DispIdAttribute` einen DISPID\-Wert größer als 0 \(null\) an.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute\-Klasse](http://msdn.microsoft.com/de-de/5c2f0835-9210-47dc-bc59-5c1769953574)