---
title: 'Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiels | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 379c95e4de7831c833d8d82d48643a9da10be323
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757367"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird das <legacyBold>LinqToXmlDataBinding</legacyBold>-Beispiel beschrieben, und es werden einige wichtige Aspekte seiner beiden primären Quelldateien <legacyBold>L2DBForm.xaml</legacyBold> und <legacyBold>L2DBForm.xaml.cs</legacyBold> erläutert.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie sich diese exemplarische Vorgehensweise durchlesen, wird dringend empfohlen, das LinqToXmlDataBinding-Programm, wie in [Vorgehensweise: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md) beschrieben, zu erstellen und auszuführen.  
  
## <a name="remarks"></a>Hinweise  
 Das <legacyBold>LinqToXmlDataBinding</legacyBold>-Programm ist eine WPF-Anwendung (Windows Presentation Foundation), die aus C#- und XAML-Quelldateien besteht. Es enthält ein eingebettetes XML-Dokument, das eine Liste von Büchern definiert. Das Programm versetzt den Benutzer in die Lage, diese Einträge anzuzeigen, hinzuzufügen, zu löschen und zu bearbeiten. Das Programm setzt sich aus den folgenden beiden primären Quelldateien zusammen:  
  
- <legacyBold>L2DBForm.xaml</legacyBold> enthält den XAML-Deklarationscode für die Benutzeroberfläche des Hauptfensters. Außerdem enthält die Datei den Abschnitt <legacyBold>Window.Resources</legacyBold>, in dem ein Datenanbieter und ein eingebettetes XML-Dokument für die Bücherlisten definiert sind.  
  
- <legacyBold>L2DBForm.xaml.cs</legacyBold> enthält die Initialisierungs- und Ereignishandlingmethoden, die der Benutzeroberfläche zugeordnet sind.  
  
  Das Hauptfenster ist in die folgenden vier vertikalen Benutzeroberflächenabschnitte unterteilt:  
  
- **XML**: Zeigt die unformatierte XML-Quelle der eingebetteten Bücherliste an.  
  
- **Book List** (Bücherliste): Zeigt die Bucheinträge als Standardtext an, und versetzt den Benutzer in die Lage, einzelne Einträge auszuwählen und zu löschen.  
  
- **Edit Selected Book** (Ausgewähltes Buch bearbeiten): Ermöglicht es dem Benutzer, die dem aktuell ausgewählten Bucheintrag zugeordneten Werte zu bearbeiten.  
  
- **Add New Book** (Neues Buch hinzufügen): Ermöglicht das Erstellen eines neuen Bucheintrags anhand der vom Benutzer eingegebenen Werte.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[L2DBForm.xaml-Quellcode](../designers/l2dbform-xaml-source-code.md)|Enthält den Inhalt und die Beschreibung des XAML-Codes in der Datei <legacyBold>L2DBForm.xaml</legacyBold>.|  
|[L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md)|Enthält den Inhalt und die Beschreibung des C#-Quellcodes in der Datei <legacyBold>L2DBForm.xaml.cs</legacyBold>.|  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Gewusst wie: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
