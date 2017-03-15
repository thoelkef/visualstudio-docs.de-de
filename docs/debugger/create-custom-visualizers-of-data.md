---
title: "Schnellansichten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Schnellansichten"
  - "Schnellansichten"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Schnellansichten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schnellansichten sind Komponenten der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Debuggerbenutzeroberfläche.  Eine *Schnellansicht* erstellt ein Dialogfeld oder eine weitere Benutzeroberfläche, um eine Variable oder ein Objekt auf eine dem Datentyp entsprechende Art und Weise anzuzeigen.  So interpretiert zum Beispiel eine HTML\-Schnellansicht eine HTML\-Zeichenfolge und stellt das Ergebnis so dar, wie es in einem Browserfenster angezeigt würde, eine Bitmapschnellansicht interpretiert eine Bitmapstruktur und zeigt die in der Bitmapdatei enthaltene Grafik an.  Bei einigen Schnellansichten können Sie die Daten nicht nur anzeigen lassen, sondern auch bearbeiten.  
  
 Der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Debugger beinhaltet sechs Standardschnellansichten.  Dies sind die Schnellansichten für Text, HTML, XML und JSON, die alle auf Zeichenfolgenobjekten basieren, die WPF\-Strukturschnellansicht zum Anzeigen der visuellen Struktur eines WPF\-Objekts sowie die Datasetschnellansicht, die für die Verarbeitung von DataSet\-Objekten, DataView\-Objekten und DataTable\-Objekten zuständig ist.  Weitere Schnellansichten stehen möglicherweise in Zukunft zum Download von der Microsoft Corporation zur Verfügung und werden von Dritten und der Community zur Verfügung.  Außerdem können Sie eigene Schnellansichten schreiben und sie im [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Debugger installieren.  
  
> [!NOTE]
>  In **Speicher**\-Anwendungen werden nur die Schnellansichten Standardtext, HTML, XML und JSON unterstützt.  Benutzerdefinierte \(von Benutzern erstellte\) Schnellansichten werden nicht unterstützt.  
  
 Schnellansichten werden im Debugger durch ein Lupensymbol dargestellt.  Wenn Sie in **DataTip**, in einem Debuggervariablenfenster oder im Dialogfeld **Schnellüberwachung** ein Lupensymbol sehen, können Sie auf das Lupensymbol klicken, um eine Schnellansicht auszuwählen, die zum Datentyp des entsprechenden Objekts passt.  
  
 Schnellansichten werden in Compact Framework nicht unterstützt.  
  
> [!NOTE]
>  Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden.  Schnellansichten werden deshalb nicht geladen, wenn die Ausführung in Code mit partieller Vertrauensstellung unterbrochen wurde.  Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
## In diesem Abschnitt  
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)  
  
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)  
  
 [Gewusst wie: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenz zur Schnellansicht\-API](../debugger/visualizer-api-reference.md)  
  
## Verwandte Abschnitte  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)