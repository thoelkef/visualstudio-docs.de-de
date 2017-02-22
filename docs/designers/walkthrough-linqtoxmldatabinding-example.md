---
title: "Exemplarische Vorgehensweise: &#39;LinqToXmlDataBinding&#39;-Beispiel | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: &#39;LinqToXmlDataBinding&#39;-Beispiel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird das **LinqToXmlDataBinding**\-Beispiel beschrieben, und es werden einige wichtige Aspekte seiner beiden primären Quelldateien **L2DBForm.xaml** und **L2DBForm.xaml.cs** erläutert.  
  
## Vorbereitungsmaßnahmen  
 Bevor Sie sich diese exemplarische Vorgehensweise durchlesen, empfehlen wir dringend, das unter [Vorgehensweise: Erstellen und Ausführen des 'LinqToXmlDataBinding'\-Beispiels](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md) beschriebene **LinqToXmlDataBinding**\-Programm zu kompilieren und auszuführen.  
  
## Hinweise  
 Das **LinqToXmlDataBinding**\-Programm ist eine WPF\-Anwendung \(Windows Presentation Foundation\), die aus C\#\- und XAML\-Quelldateien besteht.Es enthält ein eingebettetes XML\-Dokument, das eine Liste von Büchern definiert. Das Programm versetzt den Benutzer in die Lage, diese Einträge anzuzeigen, hinzuzufügen, zu löschen und zu bearbeiten.Das Programm setzt sich aus den folgenden beiden primären Quelldateien zusammen:  
  
-   **L2DBForm.xaml** enthält den XAML\-Deklarationscode für die Benutzeroberfläche des Hauptfensters.Außerdem enthält die Datei den Abschnitt **Window.Resources**, in dem ein Datenanbieter und ein eingebettetes XML\-Dokument für die Bücherlisten definiert sind.  
  
-   **L2DBForm.xaml.cs** enthält die Initialisierungs\- und Ereignishandlingmethoden, die der Benutzeroberfläche zugeordnet sind.  
  
 Das Hauptfenster ist in die folgenden vier vertikalen Benutzeroberflächenabschnitte unterteilt:  
  
-   **XML**: Zeigt die unformatierte XML\-Quelle der eingebetteten Bücherliste an.  
  
-   **Book List**: Zeigt die Bucheinträge als Standardtext an und versetzt den Benutzer in die Lage, einzelne Einträge auszuwählen und zu löschen.  
  
-   **Edit Selected Book**: Ermöglicht es dem Benutzer, die dem aktuell ausgewählten Bucheintrag zugeordneten Werte zu bearbeiten.  
  
-   **Add New Book**: Ermöglicht das Erstellen eines neuen Bucheintrags anhand der vom Benutzer eingegebenen Werte.  
  
## Inhalt dieses Abschnitts  
  
|Thema|Beschreibung|  
|-----------|------------------|  
|[L2DBForm.xaml\-Quellcode](../designers/l2dbform-xaml-source-code.md)|Enthält den Inhalt und die Beschreibung des XAML\-Codes in der Datei **L2DBForm.xaml**.|  
|[Quellcode in der Datei 'L2DBForm.xaml.cs'](../designers/l2dbform-xaml-cs-source-code.md)|Enthält den Inhalt und die Beschreibung des C\#\-Quellcodes in der Datei **L2DBForm.xaml.cs**.|  
  
## Siehe auch  
 [Beispiel für die WPF\-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Vorgehensweise: Erstellen und Ausführen des 'LinqToXmlDataBinding'\-Beispiels](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)