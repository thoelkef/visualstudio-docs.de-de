---
title: Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 30
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7ab8ce7199fec306a0f50344619200266a2261b8
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI
Durch das Einbeziehen von Tests der programmierten UI in einer SharePoint-Anwendung können Sie sicherstellen, dass die gesamte Anwendung, einschließlich der zugehörigen Benutzeroberflächen-Steuerelemente, richtig funktioniert. Tests der programmierten UI können zudem Werte und Logik auf der Benutzeroberfläche validieren .  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Was sollte ich sonst noch über Tests der codierten UI wissen?  
 Weitere Informationen zu den Vorteilen der Verwendung von Tests der programmierten UI finden Sie unter [Use UI Automation To Test Your Code (Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes)](../test/use-ui-automation-to-test-your-code.md) und [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 5 Automating System Tests (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 5 Automatisieren von Systemtests)](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Notizen**  
  
-   ![Erforderliche Komponente](../test/media/prereq.png "Prereq") Tests der programmierten UI für SharePoint-Anwendungen werden nur mit SharePoint 2010 unterstützt.  
  
-   ![Erforderliche Komponente](../test/media/prereq.png "Prereq") Die Unterstützung für Visio- und PowerPoint 2010-Steuerelement in Ihrer SharePoint-Anwendung wird nicht unterstützt.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Erstellen eines Tests der codierten UI für die SharePoint-App  
 Das[Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) für Ihre SharePoint 2010-Anwendungen entspricht dem Erstellen von Tests für andere Anwendungstypen. Die Aufzeichnung und Wiedergabe wird für alle Steuerelemente in der Webbearbeitungsschnittstelle unterstützt. Bei der Schnittstelle für das Auswählen von Kategorien und Webparts handelt es sich um standardmäßige Websteuerelemente.  
  
 ![SharePoint-Webparts](../test/media/cuit_sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Wenn Sie Aktionen aufzeichnen, überprüfen Sie die Aktionen vor dem Generieren von Code. Da mehrere Verhaltensweisen Mauszeigerbewegungen zugeordnet sind, ist es standardmäßig aktiviert. Achten Sie darauf, dass Sie redundante Bewegungen des Mauszeigers aus Tests der programmierten UI entfernen. Sie erreichen dies durch Bearbeiten des Codes für den Test oder mithilfe des [Test-Editors für codierte UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Einschließen von Tests der Office 2010-Steuerelemente innerhalb der SharePoint-App  
 Um die Automatisierung für einige Office 2010-Webparts in der SharePoint-App zu aktivieren, müssen Sie einige geringfügige Codeänderungen vornehmen.  
  
> [!WARNING]
>  Visio- und PowerPoint 2010-Steuerelemente werden nicht unterstützt.  
  
### <a name="excel-2010-cell-controls"></a>Steuerelemente für Excel 2010-Zellen  
 Zum Einbeziehen von Excel-Zellensteuerelementen müssen Sie einige Änderungen im Code des Tests der programmierten UI vornehmen.  
  
> [!WARNING]
>  Das Eingeben von Text in einer Excel-Zelle, gefolgt von einer Aktion mit einer PFEILTASTE wird nicht richtig aufgezeichnet. Verwenden Sie die Maus, um Zellen auszuwählen.  
  
 Wenn Sie Aktionen in einer leeren Zelle aufzeichnen, müssen Sie den Code ändern, indem Sie in die Zelle doppelklicken und anschließend einen „set text“-Vorgang ausführen. Dies ist erforderlich, da durch das Klicken in eine Zelle, gefolgt von einer Tastaturaktion der `textarea` in der Zelle aktiviert wird. Das einfache Aufzeichnen eines `setvalue` in der leeren Zelle würde zu einer Suche nach `editbox` führen, welches nicht vorhanden ist, bis in die Zelle geklickt wurde. Zum Beispiel:  
  
```c#  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Wenn Sie Aktionen in einer nicht leeren Zelle aufzeichnen, wird die Aufzeichnung etwas komplizierter, da im Augenblick, wenn Sie einer Zelle Text hinzufügen, ein neues \<div>-Steuerelement als untergeordnetes Element der Zelle hinzugefügt wird. Das neue \<div>-Steuerelement enthält den von Ihnen soeben eingegebenen Text. Die Aufzeichnung muss die Aktionen im neuen \<div>-Steuerelement aufzeichnen. Es ist jedoch dazu nicht in der Lage, da das neue \<div>-Steuerelement erst vorhanden ist, nachdem der Test eingegeben wurde. Sie müssen die folgenden Codeänderungen manuell vornehmen, um dieses Problem zu beheben.  
  
1.  Wechseln Sie zur Initialisierung der Zelle, und legen Sie `RowIndex` und `ColumnIndex` als primäre Eigenschaften fest:  
  
    ```c#  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Suchen Sie nach dem untergeordneten `HtmlDiv` -Element der Zelle:  
  
    ```c#  
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
  
3.  Fügen Sie in `HtmlDiv`Code für eine Mausdoppelklickaktion hinzu:  
  
    ```c#  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Fügen Sie Code hinzu, um Text für `TextArea`festzulegen:  
  
    ```c#  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Aktivieren von Tests der codierten UI von Silverlight-Webparts in der SharePoint 2010-App  
 Silverlight-Tests werden in Visual Studio 2012 und höher nicht unterstützt. Wenn Sie die Silverlight-Webparts in Ihrer SharePoint 2010-App jedoch testen möchten, können Sie ein separates Silverlight-Plug-In aus Visual Studio Gallery installieren.  
  
#### <a name="setting-up-your-machine"></a>Einrichten des Computers  
  
1.  Stellen Sie sicher, dass Visual Studio 2012.1 oder höher installiert ist.  
  
2.  Installieren Sie das [Microsoft Visual Studio UI Test Plugin for Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3.  Installieren Sie [Fiddler](http://www.fiddler2.com/fiddler2/). Hierbei handelt es sich um ein einfaches Tool, das den HTTP-Datenverkehr erfasst und protokolliert.  
  
4.  Laden Sie das [fiddlerXap-Projekt](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip)herunter. Entpacken Sie es, erstellen Sie es, und führen Sie das Skript „CopySLHelper.bat“ aus, um die Helper DLL zu installieren, die für das Testen von Silverlight-Webparts erforderlich ist, wenn Sie das Fiddler-Tool verwenden.  
  
 Befolgen Sie nach dem Einrichten Ihres Computers zum Starten des Tests Ihrer SharePoint 2010-App mit Silverlight-Webparts die folgenden Schritte:  
  
#### <a name="testing-silverlight-web-parts"></a>Testen von Silverlight-Webparts  
  
1.  Starten Sie Fiddler.  
  
2.  Löschen Sie den Browsercache. Dies ist erforderlich, da die XAP-Datei, die die Silverlight UI Automation Helper DLL enthält, für gewöhnlich zwischengespeichert wird. Wir müssen sicherstellen, dass die geänderte XAP-Datei abgerufen wird, daher löschen wir den Browsercache.  
  
3.  Öffnen Sie die Webseite.  
  
4.  Starten Sie die Aufzeichnung, und generieren Sie den Code so, als würden Sie ihn für einen gewöhnlichen Webanwendungstest generieren.  
  
5.  Sie sollten sicherstellen, dass der generierte Code die „Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll“ referenziert.  
  
     Weitere Informationen finden Sie unter [UI-Tests für SharePoint 2010 in Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx).  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="blogs"></a>Blogs  
 [UI-Tests für SharePoint 2010 in Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Grundlegendes zur Suchlogik für Silverlight-Steuerelemente im Test der programmmierten UI](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Abrufen der Eigenschaft eines Silverlight-Steuerelements](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Inhaltsindex für den Test der programmierten UI](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Empfehlungen  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 5 Automating System Tests (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 5 Automatisieren von Systemtests)](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Forum  
 [Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Webleistungs- und Auslastungstests in SharePoint 2010- und SharePoint 2013-Anwendungen](/devops-test-docs/test/web-performance-and-load-testing-sharepoint-2010-and-2013-applications)   
 [Erstellen von SharePoint-Lösungen](/office-dev/office-dev/create-sharepoint-solutions)   
 [Überprüfen und Debuggen von SharePoint-Code](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)   
 [Erstellen und Debuggen von SharePoint-Lösungen](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)   
 [Profilerstellung für die Leistung von SharePoint-Anwendungen](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)

