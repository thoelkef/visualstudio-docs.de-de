---
title: Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0ec4c0a9594202b6755500d683c426238264aec3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586978"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch das Einbeziehen von Tests der programmierten UI in einer SharePoint-Anwendung können Sie sicherstellen, dass die gesamte Anwendung, einschließlich der zugehörigen Benutzeroberflächen-Steuerelemente, richtig funktioniert. Tests der programmierten UI können zudem Werte und Logik auf der Benutzeroberfläche validieren .

 **Anforderungen**

- Visual Studio Enterprise

## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Was sollte ich sonst noch über Tests der codierten UI wissen?
 Weitere Informationen zu den Vorteilen der Verwendung von Tests der programmierten UI finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md) und [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 5 Automatisieren von Systemtests](https://msdn.microsoft.com/library/jj159335.aspx).

 **Notizen**

- ![Prerequsite](../test/media/prereq.png "Prereq") Coded UI-Tests für SharePoint-Anwendungen werden nur mit SharePoint 2010 unterstützt.

- ![Prerequsite](../test/media/prereq.png "Prereq") Unterstützung für Visio-und PowerPoint 2010-Steuerelemente in Ihrer SharePoint-Anwendung wird nicht unterstützt.

## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Erstellen eines Tests der codierten UI für die SharePoint-App
 Das[Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) für Ihre SharePoint 2010-Anwendungen entspricht dem Erstellen von Tests für andere Anwendungstypen. Die Aufzeichnung und Wiedergabe wird für alle Steuerelemente in der Webbearbeitungsschnittstelle unterstützt. Bei der Schnittstelle für das Auswählen von Kategorien und Webparts handelt es sich um standardmäßige Websteuerelemente.

 ![SharePoint-Webparts](../test/media/cuit-sharepoint.png "CUIT_SharePoint")

> [!NOTE]
> Wenn Sie Aktionen aufzeichnen, überprüfen Sie die Aktionen vor dem Generieren von Code. Da mehrere Verhaltensweisen Mauszeigerbewegungen zugeordnet sind, ist es standardmäßig aktiviert. Achten Sie darauf, dass Sie redundante Bewegungen des Mauszeigers aus Tests der programmierten UI entfernen. Sie erreichen dies durch Bearbeiten des Codes für den Test oder mithilfe des [Test-Editors für codierte UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Einschließen von Tests der Office 2010-Steuerelemente innerhalb der SharePoint-App
 Um die Automatisierung für einige Office 2010-Webparts in der SharePoint-App zu aktivieren, müssen Sie einige geringfügige Codeänderungen vornehmen.

> [!WARNING]
> Visio- und PowerPoint 2010-Steuerelemente werden nicht unterstützt.

### <a name="excel-2010-cell-controls"></a>Steuerelemente für Excel 2010-Zellen
 Zum Einbeziehen von Excel-Zellensteuerelementen müssen Sie einige Änderungen im Code des Tests der programmierten UI vornehmen.

> [!WARNING]
> Das Eingeben von Text in einer Excel-Zelle, gefolgt von einer Aktion mit einer PFEILTASTE wird nicht richtig aufgezeichnet. Verwenden Sie die Maus, um Zellen auszuwählen.

 Wenn Sie Aktionen in einer leeren Zelle aufzeichnen, müssen Sie den Code ändern, indem Sie in die Zelle doppelklicken und anschließend einen „set text“-Vorgang ausführen. Dies ist erforderlich, da durch das Klicken in eine Zelle, gefolgt von einer Tastaturaktion der `textarea` in der Zelle aktiviert wird. Das einfache Aufzeichnen eines `setvalue` in der leeren Zelle würde zu einer Suche nach `editbox` führen, welches nicht vorhanden ist, bis in die Zelle geklickt wurde. Beispiel:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

 Wenn Sie Aktionen in einer nicht leeren Zelle aufzeichnen, wird die Aufzeichnung etwas komplizierter, da der Moment, in dem Sie einer Zelle Text hinzufügen, ein neues Steuerelement als untergeordnetes Element \<div> der Zelle hinzugefügt wird. Das neue \<div> Steuerelement enthält den Text, den Sie soeben eingegeben haben. Der Recorder muss Aktionen für das neue Steuerelement aufzeichnen \<div> . Dies kann jedoch nicht der Fall sein, da das neue \<div> Steuerelement erst vorhanden ist, nachdem der Test eingegeben wurde. Sie müssen die folgenden Codeänderungen manuell vornehmen, um dieses Problem zu beheben.

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
    ```

## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Aktivieren von Tests der codierten UI von Silverlight-Webparts in der SharePoint 2010-App
 Silverlight-Tests werden in Visual Studio 2012 und höher nicht unterstützt. Wenn Sie die Silverlight-Webparts in Ihrer SharePoint 2010-App jedoch testen möchten, können Sie ein separates Silverlight-Plug-In aus Visual Studio Gallery installieren.

#### <a name="setting-up-your-machine"></a>Einrichten des Computers

1. Stellen Sie sicher, dass Visual Studio 2012.1 oder höher installiert ist.

2. Installieren Sie das [Microsoft Visual Studio UI Test Plugin for Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudioUITestPluginforSilverlight).

3. Installieren Sie [Fiddler](http://www.fiddler2.com/fiddler2/). Hierbei handelt es sich um ein einfaches Tool, das den HTTP-Datenverkehr erfasst und protokolliert.

4. Laden Sie das [fiddlerXap-Projekt](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip)herunter. Entpacken Sie es, erstellen Sie es, und führen Sie das Skript „CopySLHelper.bat“ aus, um die Helper DLL zu installieren, die für das Testen von Silverlight-Webparts erforderlich ist, wenn Sie das Fiddler-Tool verwenden.

   Befolgen Sie nach dem Einrichten Ihres Computers zum Starten des Tests Ihrer SharePoint 2010-App mit Silverlight-Webparts die folgenden Schritte:

#### <a name="testing-silverlight-web-parts"></a>Testen von Silverlight-Webparts

1. Starten Sie Fiddler.

2. Löschen Sie den Browsercache. Dies ist erforderlich, da die XAP-Datei, die die Silverlight UI Automation Helper DLL enthält, für gewöhnlich zwischengespeichert wird. Wir müssen sicherstellen, dass die geänderte XAP-Datei abgerufen wird, daher löschen wir den Browsercache.

3. Öffnen Sie die Webseite.

4. Starten Sie die Aufzeichnung, und generieren Sie den Code so, als würden Sie ihn für einen gewöhnlichen Webanwendungstest generieren.

5. Sie sollten sicherstellen, dass der generierte Code die „Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll“ referenziert.

     Weitere Informationen finden Sie unter [UI-Tests für SharePoint 2010 in Visual Studio 2012](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/).

## <a name="external-resources"></a>Externe Ressourcen

### <a name="blogs"></a>Blogs
 [UI-Tests für SharePoint 2010 in Visual Studio 2012](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

 [Grundlegendes zur Suchlogik für Silverlight-Steuerelemente im Test der programmmierten UI](https://tapas-techsnips.blogspot.com/)

 [Abrufen der Eigenschaft eines Silverlight-Steuerelements](https://tapas-techsnips.blogspot.com/)

 [Inhaltsindex für den Test der programmierten UI](https://blogs.msdn.microsoft.com/mathew_aniyan/2013/02/18/content-index-for-coded-ui-test/)

### <a name="guidance"></a>Anleitungen
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 5 Automatisieren von Systemtests](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="forum"></a>Forum
 [Visual Studio ALM + Team Foundation Server Blog](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)

## <a name="see-also"></a>Weitere Informationen
 [Verwenden von Benutzeroberflächen Automatisierung zum Testen Ihres](../test/use-ui-automation-to-test-your-code.md) [codewebleistungs-und Auslastungs Tests SharePoint 2010-und 2013-Anwendungen](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [Erstellen](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) von SharePoint-Lösungen über [prüfen und Debuggen](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c) von SharePoint-Code erstellen [und Debuggen](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [von](https://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8) SharePoint-Lösungen erstellen und
