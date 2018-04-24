---
title: Testen von SharePoint-Anwendungen mit Tests der programmierten UI in Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0ed08d82e186f83b71a01dab0b267410fde7267d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Testen von SharePoint-Anwendungen mit Tests der programmierten UI

Durch das Einbeziehen von Tests der programmierten UI in einer SharePoint-Anwendung können Sie sicherstellen, dass die gesamte Anwendung, einschließlich der zugehörigen Benutzeroberflächen-Steuerelemente, richtig funktioniert. Tests der programmierten UI können zudem Werte und Logik auf der Benutzeroberfläche validieren .

Weitere Informationen über die Vorteile von Tests der programmierten UI finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md).

**Anforderungen**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Erstellen eines Tests der programmierten UI für die SharePoint-App

Das [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md) für Ihre SharePoint-Anwendungen entspricht dem Erstellen von Tests für andere Anwendungstypen. Die Aufzeichnung und Wiedergabe wird für alle Steuerelemente in der Webbearbeitungsschnittstelle unterstützt. Bei der Schnittstelle für das Auswählen von Kategorien und Webparts handelt es sich um standardmäßige Websteuerelemente.

![SharePoint-Webparts](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Wenn Sie Aktionen aufzeichnen, überprüfen Sie die Aktionen vor dem Generieren von Code. Da mehrere Verhaltensweisen Mauszeigerbewegungen zugeordnet sind, ist es standardmäßig aktiviert. Achten Sie darauf, dass Sie redundante Bewegungen des Mauszeigers aus Tests der programmierten UI entfernen. Sie erreichen dies durch Bearbeiten des Codes für den Test oder mithilfe des [Test-Editors für codierte UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Testen von Office-Steuerelementen in einer SharePoint-App

Zum Aktivieren der Automatisierung für einige Office-Webparts in der SharePoint-App, müssen Sie einige geringfügige Codeänderungen vornehmen.

> [!NOTE]
> Das Testen von Visio- und PowerPoint-Steuerelementen in einer SharePoint-Anwendung wird nicht unterstützt.

### <a name="excel-cell-controls"></a>Excel-Zellensteuerelemente

Zum Einbeziehen von Excel-Zellensteuerelementen müssen Sie einige Änderungen im Code des Tests der programmierten UI vornehmen.

> [!WARNING]
> Das Eingeben von Text in einer Excel-Zelle, gefolgt von einer Aktion mit einer PFEILTASTE wird nicht richtig aufgezeichnet. Verwenden Sie die Maus, um Zellen auszuwählen.

Wenn Sie Aktionen in einer leeren Zelle aufzeichnen, müssen Sie den Code ändern, indem Sie in die Zelle doppelklicken und anschließend einen „set text“-Vorgang ausführen. Dies ist erforderlich, da durch das Klicken in eine Zelle, gefolgt von einer Tastaturaktion `textarea` in der Zelle aktiviert wird. Das einfache Aufzeichnen eines `setvalue` in der leeren Zelle würde zu einer Suche nach `editbox` führen, welches nicht vorhanden ist, bis in die Zelle geklickt wurde. Zum Beispiel:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Wenn Sie Aktionen in einer nicht leeren Zelle aufzeichnen, wird die Aufzeichnung etwas komplizierter, da im Augenblick, wenn Sie einer Zelle Text hinzufügen, ein neues \<div>-Steuerelement als untergeordnetes Element der Zelle hinzugefügt wird. Das neue \<div>-Steuerelement enthält den von Ihnen soeben eingegebenen Text. Die Aufzeichnung muss die Aktionen im neuen \<div>-Steuerelement aufzeichnen. Es ist jedoch dazu nicht in der Lage, da das neue \<div>-Steuerelement erst vorhanden ist, nachdem der Test eingegeben wurde. Sie müssen die folgenden Codeänderungen manuell vornehmen, um dieses Problem zu beheben.

1. Wechseln Sie zur Initialisierung der Zelle, und legen Sie `RowIndex` und `ColumnIndex` als primäre Eigenschaften fest:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Suchen Sie nach dem untergeordneten `HtmlDiv` -Element der Zelle:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Fügen Sie in `HtmlDiv`Code für eine Mausdoppelklickaktion hinzu:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Fügen Sie Code hinzu, um Text für `TextArea`festzulegen:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI Automation To Test Your Code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint Solutions](/office-dev/office-dev/create-sharepoint-solutions)
- [Verifying and Debugging SharePoint Code](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)
- [Building and Debugging SharePoint Solutions](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)
- [Profiling the Performance of SharePoint Applications](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
