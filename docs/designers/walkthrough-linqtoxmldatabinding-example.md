---
title: 'Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiel'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 567b03f9f0441e7f5eb38f4ca0e0b3a1d64cec91
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081191"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiel
In dieser exemplarischen Vorgehensweise wird das Beispiel „LinqToXmlDataBinding“ beschrieben, und es werden einige wichtige Aspekte seiner beiden primären Quelldateien *L2DBForm.xaml* und *L2DBForm.xaml.cs* erläutert.

## <a name="prerequisites"></a>Erforderliche Komponenten
 Bevor Sie sich diese exemplarische Vorgehensweise durchlesen, wird dringend empfohlen, das LinqToXmlDataBinding-Programm wie in [Vorgehensweise: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md) beschrieben zu erstellen und auszuführen.

## <a name="remarks"></a>Hinweise
 Das <legacyBold>LinqToXmlDataBinding</legacyBold>-Programm ist eine WPF-Anwendung (Windows Presentation Foundation), die aus C#- und XAML-Quelldateien besteht. Es enthält ein eingebettetes XML-Dokument, das eine Liste von Büchern definiert. Das Programm versetzt den Benutzer in die Lage, diese Einträge anzuzeigen, hinzuzufügen, zu löschen und zu bearbeiten. Das Programm setzt sich aus den folgenden beiden primären Quelldateien zusammen:

-   *L2DBForm.xaml* enthält den XAML-Deklarationscode für die Benutzeroberfläche des Hauptfensters. Außerdem enthält die Datei den Abschnitt <legacyBold>Window.Resources</legacyBold>, in dem ein Datenanbieter und ein eingebettetes XML-Dokument für die Bücherlisten definiert sind.

-   *L2DBForm.xaml.cs* enthält die Initialisierungs- und Ereignisbehandlungsmethoden, die der Benutzeroberfläche zugeordnet sind.

 Das Hauptfenster ist in die folgenden vier vertikalen Benutzeroberflächenabschnitte unterteilt:

-   **XML**: Zeigt die unformatierte XML-Quelle der eingebetteten Bücherliste an.

-   **Book List** (Bücherliste): Zeigt die Bucheinträge als Standardtext an, und versetzt den Benutzer in die Lage, einzelne Einträge auszuwählen und zu löschen.

-   **Edit Selected Book** (Ausgewähltes Buch bearbeiten): Ermöglicht es dem Benutzer, die dem aktuell ausgewählten Bucheintrag zugeordneten Werte zu bearbeiten.

-   **Add New Book** (Neues Buch hinzufügen): Ermöglicht das Erstellen eines neuen Bucheintrags anhand der vom Benutzer eingegebenen Werte.

## <a name="in-this-section"></a>In diesem Abschnitt

|Thema|Beschreibung |
|-----------|-----------------|
|[L2DBForm.xaml-Quellcode](../designers/l2dbform-xaml-source-code.md)|Enthält den Inhalt und die Beschreibung des XAML-Codes in der Datei <legacyBold>L2DBForm.xaml</legacyBold>.|
|[L2DBForm.xaml.cs-Quellcode](../designers/l2dbform-xaml-cs-source-code.md)|Enthält den Inhalt und die Beschreibung des C#-Quellcodes in der Datei <legacyBold>L2DBForm.xaml.cs</legacyBold>.|

## <a name="see-also"></a>Siehe auch

- [Beispiel für die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Vorgehensweise: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)