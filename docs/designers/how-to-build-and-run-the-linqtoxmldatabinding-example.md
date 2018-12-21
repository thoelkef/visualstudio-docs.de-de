---
title: 'Vorgehensweise: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d8bc9ece20867e96f0ae0ee6d6ceb9ad2e3952
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159775"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Vorgehensweise: Erstellen und Ausführen des LinqToXmlDataBinding-Beispiels

In diesem Thema wird gezeigt, wie Sie das Visual Studio-<legacyBold>LinqToXmlDataBinding</legacyBold>-Projekt erstellen und das resultierende WPF-<legacyBold>LinqToXmlDataBinding</legacyBold>-Beispielprogramm ausführen können.

Weitere Informationen zu Visual Studio finden Sie unter [Überblick über die Visual Studio-IDE](../get-started/visual-studio-ide.md).

## <a name="create-and-populate-the-project"></a>Erstellen und Auffüllen des Projekts

### <a name="to-create-the-starting-project"></a>So erstellen Sie das Startprojekt

1. Starten Sie Visual Studio, und erstellen Sie eine C#-WPF-Anwendung mit dem Namen <legacyBold>LinqToXmlDataBinding</legacyBold>. Das Projekt muss .NET Framework 3.5 (oder höher) verwenden.

1. Sofern nicht bereits vorhanden, fügen Sie Projektverweise für die folgenden .NET-Assemblys hinzu:

    - <legacyBold>System.Data</legacyBold>

    - <legacyBold>System.Data.DataSetExtensions</legacyBold>

    - System.Xml

    - System.Xml.Linq

1. Erstellen Sie die Projektmappe, indem Sie **STRG**+**UMSCHALTTASTE**+**B** drücken, und führen Sie sie dann mit **F5** aus. Das Projekt sollte ohne Fehler kompiliert und als generische WPF-Anwendung ausgeführt werden.

### <a name="to-add-custom-code-to-the-project"></a>So fügen Sie dem Projekt benutzerdefinierten Code hinzu

1. Benennen Sie im Projektmappen-Explorer die Quelldatei **Window1.xaml** in **L2XDBForm.xaml** um. Die abhängige Quelldatei **Window1.xaml.cs** sollte automatisch in **L2XDBForm.xaml.cs** umbenannt werden.

1. Ersetzen Sie den Quellcode in der Datei **L2XDBForm.xaml** durch den Codeabschnitt aus dem Artikel [L2DBForm.xaml-Quellcode](../designers/l2dbform-xaml-source-code.md). Verwenden Sie zum Arbeiten mit dieser Datei die XAML-Quellansicht.

1. Ersetzen Sie den Quellcode in der Datei **L2XDBForm.xaml.cs** durch den Codeabschnitt aus dem Artikel [L2DBForm.xaml.cs-Quellcode](../designers/l2dbform-xaml-cs-source-code.md).

1. Ersetzen Sie in der Datei **App.xaml** alle Vorkommen der Zeichenfolge `Window1.xaml` durch `L2XDBForm.xaml`.

1. Erstellen Sie die Projektmappe, indem Sie **STRG**+**UMSCHALTTASTE**+**B** drücken.

## <a name="run-the-program"></a>Ausführen des Programms

Das <legacyBold>LinqToXmlDataBinding</legacyBold>-Programm ermöglicht es dem Benutzer, eine Liste von Büchern anzuzeigen und zu bearbeiten, die als eingebettetes XML-Element gespeichert ist.

### <a name="to-run-the-program-and-view-the-book-list"></a>So führen Sie das Programm aus und zeigen die Buchliste an

- Führen Sie LinqToXmlDataBinding aus, indem Sie **F5** (**Debuggen starten**) oder **STRG**+**F5** (**Starten ohne Debuggen**) drücken.

   Daraufhin wird ein Programmfenster mit dem Titel **WPF-Datenbindung mit LINQ to XML** angezeigt.

- Achten Sie auf den obersten Abschnitt der Benutzeroberfläche. Dort wird das unformatierte **XML** angezeigt, das die Buchliste darstellt. Die Anzeige erfolgt unter Verwendung eines WPF-<xref:System.Windows.Controls.TextBlock>-Steuerelements, das keine Interaktion mithilfe von Maus oder Tastatur zulässt.

- Im zweiten vertikalen Abschnitt mit der Bezeichnung **Book List** (Buchliste) werden die Bücher als geordnete Nur-Text-Liste angezeigt. Dazu wird ein <xref:System.Windows.Controls.ListBox>-Steuerelement verwendet, das die Auswahl über Maus oder Tastatur zulässt.

### <a name="to-add-and-delete-books-from-the-list"></a>So fügen Sie der Liste Bücher hinzu und löschen Bücher daraus

- Wenn Sie der Liste ein neues Buch hinzufügen möchten, geben Sie in die <xref:System.Windows.Controls.TextBox>-Steuerelemente **ID** und **Value** im letzten Abschnitt, **Add New Book**, Werte ein, und klicken Sie dann auf **Add Book**. Das Buch wird sowohl der Buchliste als auch der XML-Auflistung angefügt. Das Programm prüft die Eingabewerte nicht auf ihre Gültigkeit.

- Wenn Sie ein vorhandenes Buch aus der Liste löschen möchten, wählen Sie es im Abschnitt **Book List** aus, und klicken Sie dann auf die Schaltfläche **Remove Selected Book**. Der Bucheintrag wird daraufhin sowohl aus der Buchliste als auch aus der unformatierten XML-Quellauflistung entfernt.

### <a name="to-edit-an-existing-book-entry"></a>So bearbeiten Sie einen vorhandenen Bucheintrag

1. Wählen Sie den Bucheintrag im zweiten Abschnitt, **Book List**, aus. Die aktuellen Werte des Bucheintrags sollten im dritten Abschnitt, **Edit Selected Book** (Ausgewähltes Buch bearbeiten), angezeigt werden.

1. Bearbeiten Sie die Werte mit der Tastatur. Sobald Sie zu einem anderen <xref:System.Windows.Controls.TextBox>-Steuerelement wechseln, werden die Änderungen automatisch in die XML-Auflistung und in die Buchliste übernommen.

## <a name="see-also"></a>Siehe auch

- [Beispiel für die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Exemplarische Vorgehensweise: LinqToXmlDataBinding-Beispiel](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Übersicht über die Visual Studio-IDE](../get-started/visual-studio-ide.md)