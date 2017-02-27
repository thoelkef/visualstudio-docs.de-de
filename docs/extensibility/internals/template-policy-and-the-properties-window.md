---
title: "Die Richtlinie f&#252;r Vorlagen und im Eigenschaftenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Im Eigenschaftenfenster für Richtlinie"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Die Richtlinie f&#252;r Vorlagen und im Eigenschaftenfenster
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn ein Projekt innerhalb eines Enterprise\-Vorlagenprojekts enthalten ist, kann dieses Enterprise\-Vorlagenprojekt Richtlinie erzwingen.  Richtlinie für Vorlagen wird ein einschränkendes System, das verwendet werden kann, um Standardwerte für Eigenschaften ausblenden, Eigenschaften festzulegen usw. Eigenschaften hinzufügen.  
  
 Verwenden von Vorlagen, die Richtlinie für die Anzeige von Informationen im Fenster hat **Eigenschaften** steuern zu dem Implementieren von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>unterschiedlich.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> behandelt Objekteigenschaften aufgeführt, während der Ebene der Komponenten Richtlinie für Vorlagen verwendet werden kann, um Objekteigenschaften an der Projektmappe oder Projektebene zu beschränken.  Anders ausgedrückt  
  
-   Implementieren Sie die Methoden für <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> , um zu bestimmen, was im Fenster **Eigenschaften** für bestimmte Objekte angezeigt wird  
  
-   Verwenden von Vorlagen an der Projektmappe Richtlinie und Projektebene, um zu bestimmen, was im Fenster **Eigenschaften** zuvor angegebene Objekte angezeigt wird  
  
 Verwenden von Vorlagen bestimmte Richtlinie für die Eigenschaften im Fenster **Eigenschaften** selektiv kann eingeschränkt werden, wenn ein Projektelement eines angegebenen Typs in **Projektmappen\-Explorer** ausgewählt ist, an alle Mitglieder des Entwicklungsteams hilfreich sein, die an einem Projekt arbeiten.  Beispielsweise Richtlinie mithilfe von Vorlagen können Sie alle Informationen zur Verbindungszeichenfolge in einer Datenbank für Entwickler installieren und die Verbindungszeichenfolge schreibgeschützt machen.  Auf diese Weise können Sie eine einfache Möglichkeit zur Verfügung stellen, sicherstellen, dass jeder Entwickler den richtigen Pfad für den Datenzugriff verwenden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)