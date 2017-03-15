---
title: "Erweitern von Toolfenstern | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenster [Visual Studio SDK], Tool"
  - "Dokumentfenster"
  - "Toolfenster"
  - "Fenster [Visual Studio SDK], Dokument"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# Erweitern von Toolfenstern
Die Toolfenster von Visual Studio sind im Allgemeinen schreibgeschützte Fenster, die nicht dateibasiert sind. Darin unterscheiden sie sich von Dokumentfenstern, in denen die Dateien im Modus mit Lese\- und Schreibzugriff angezeigt werden. Die Fenster **Toolbox**, **Projektmappen\-Explorer**, **Eigenschaften** und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Alle Toolfenster in Visual Studio 2010 und höheren Versionen basieren auf WPF. In Versionen vor Visual Studio 2010 basieren die Toolfenster auf Windows Forms. Auf Windows Forms basierende Fenster werden weiterhin angezeigt, aber neue Toolfenster müssen auf WPF basieren.  
  
## Grundlegendes zu Toolfenstern  
 Wenn Sie ein Toolfenster bereitstellen möchten, müssen Sie es mit Visual Studio registrieren und sein Standardformat sowie den Speicherort angeben. Weitere Informationen finden Sie unter [Toolfenster in der Registrierung](../extensibility/tool-windows-in-the-registry.md).  
  
 Toolfenster werden in der Regel durch Klicken auf einen Menübefehl erstellt oder geöffnet. Weitere Informationen zum programmgesteuerten Erstellen eines Toolfensters finden Sie unter [Programmgesteuertes Öffnen eines Toolfensters](../misc/opening-a-tool-window-programmatically.md).  
  
 Toolfenster sind standardmäßig Einzelinstanzen, d. h. nur eine Instanz des Toolfensters kann jeweils geöffnet sein. Nachdem ein Einzelinstanz\-Toolfenster geöffnet wurde, bleibt es geöffnet, bis die IDE geschlossen wird. Wenn Sie bei einem Einzelinstanz\-Toolfenster auf die Schaltfläche „Schließen“ klicken, verändert sich nur seine Sichtbarkeit. Sie können auch Toolfenster mit mehreren Instanzen erstellen, sodass mehrere Instanzen des Fensters gleichzeitig geöffnet sein können. Weitere Informationen finden Sie unter [Erstellen eines Toolfensters mit mehreren Instanzen](../extensibility/creating-a-multi-instance-tool-window.md).  
  
 Toolfenster können im Dokumentrahmen angedockt oder unverankert sein bzw. das Registerkartenformat aufweisen. Der Toolfensterrahmen wird von der IDE bereitgestellt und dazu verwendet, um das Format, die Position, den Andockzustand und andere permanente Eigenschaften zu steuern. Der Toolfensterbereich zeigt die Inhalte an. Das Standardformat und die Standardposition gelten nur beim ersten Öffnen des Toolfensters. Anschließend wird der Toolfensterzustand beibehalten.  
  
 Toolfensterbereiche können WPF\-Benutzersteuerelemente hosten und Symbolleisten unterstützen. Sie können die <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>\-Eigenschaft außer Kraft setzen, um das Handle des gehosteten Steuerelements zurückzugeben.  
  
 Toolfenster können *dynamisch* sein \(auch als *automatisch sichtbar* bezeichnet\). Dynamische Toolfenster werden angezeigt, wenn ihr zugehöriger Benutzeroberflächenkontext gilt. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit hinsichtlich der Fenster in der IDE verbessern. Weitere Informationen finden Sie unter [Öffnen ein dynamisches Tool\-Fenster](../extensibility/opening-a-dynamic-tool-window.md).  
  
 VSPackages stellen nicht die einzige Möglichkeit zum Erstellen von Toolfenstern dar. Add\-Ins können mithilfe des Visual Studio\-Automatisierungsmodells ein Toolfenster erstellen. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen und Steuern von Toolfenstern](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md).  
  
## Siehe auch  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [Dokumentfenster](../extensibility/internals/document-windows.md)   
 [Hinzufügen von Suchfunktionen zu einem Toolfenster](../extensibility/adding-search-to-a-tool-window.md)