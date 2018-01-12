---
title: "Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c4701cf7509b368c1264436d97d9fc95722e4aff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint
  Mithilfe von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website direkt im Browser ändern. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen eines Webparts mit der **Webpart** Elementvorlage in Visual Studio 2010.  
  
 Das Webpart zeigt Mitarbeiter in einem Datenraster an. Der Benutzer gibt den Speicherort der Datei an, die die Mitarbeiterdaten enthält. Außerdem kann der Benutzer das Datenraster filtern, damit nur Mitarbeiter, die Manager sind, in der Liste angezeigt werden.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Webparts mit Visual Studio **Webpart** Elementvorlage.  
  
-   Erstellen einer Eigenschaft, die vom Benutzer des Webparts festgelegt werden kann. Diese Eigenschaft gibt den Speicherort der Mitarbeiterdatendatei an.  
  
-   Rendern von Inhalt in einem Webpart durch Hinzufügen von Steuerelementen zur Webpart-Steuerelementauflistung.  
  
-   Erstellen ein neues Menüelement als bezeichnet eine *Verb,* , das im Verbmenü des gerenderten Webparts angezeigt wird. Verben ermöglichen es dem Benutzer, die im Webpart angezeigten Daten zu ändern.  
  
-   Testen des Webparts in SharePoint.  
  
    > [!NOTE]  
    >  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]oder eine Edition von Visual Studio Application Lifecycle Management (ALM).  
  
## <a name="creating-an-empty-sharepoint-project"></a>Erstellen eines leeren SharePoint-Projekts  
 Erstellen Sie zunächst ein leeres SharePoint-Projekt. Sie werden später ein Webpart zum Projekt hinzufügen, mit der **Webpart** Elementvorlage.  
  
#### <a name="to-create-an-empty-sharepoint-project"></a>So erstellen Sie ein leeres SharePoint-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der **als Administrator ausführen** Option.  
  
2.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt**.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten unter der Sprache, die Sie verwenden möchten, und wählen Sie dann die **2010** Knoten.  
  
4.  In der **Vorlagen** Bereich auswählen **SharePoint 2010-Projekt**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.  
  
5.  Wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu übernehmen.  
  
## <a name="adding-a-web-part-to-the-project"></a>Hinzufügen eines Webparts zum Projekt  
 Hinzufügen einer **Webpart** Element aus, um das Projekt. Die **Webpart** Element wird die Webpart-Codedatei hinzugefügt. Später fügen Sie der Codedatei für das Webpart Code hinzu, um den Inhalt des Webparts zu rendern.  
  
#### <a name="to-add-a-web-part-to-the-project"></a>So fügen Sie ein Webpart zum Projekt hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
2.  In der **neues Element hinzufügen** Dialogfeld die **installierte Vorlagen** Bereich, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
3.  Wählen Sie in der Liste der SharePoint-Vorlagen, die **Webpart** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **Webpart** Element wird in **Projektmappen-Explorer**.  
  
## <a name="rendering-content-in-the-web-part"></a>Rendern von Inhalt im Webpart  
 Sie können angeben, welche Steuerelemente im Webpart angezeigt werden, indem Sie diese der Steuerelementauflistung der Webpartklasse hinzufügen.  
  
#### <a name="to-render-content-in-the-web-part"></a>So rendern Sie Inhalt im Webpart  
  
1.  In **Projektmappen-Explorer**, öffnen Sie WebPart1.vb (in Visual Basic) oder WebPart1.cs (in c#).  
  
     Die Codedatei für das Webpart wird im Code-Editor geöffnet.  
  
2.  Fügen Sie am Anfang der Codedatei für das Webpart die folgenden Anweisungen hinzu.  
  
     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]  
  
3.  Fügen Sie der `WebPart1`-Klasse folgenden Code hinzu. Mit diesem Code werden die folgenden Felder deklariert:  
  
    -   Ein Datenraster, um Mitarbeiter im Webpart anzuzeigen.  
  
    -   Text, der auf dem Steuerelement angezeigt wird, das zum Filtern des Datenrasters verwendet wird.  
  
    -   Eine Bezeichnung, die einen Fehler anzeigt, wenn das Datenraster keine Daten anzeigen kann.  
  
    -   Eine Zeichenfolge, die den Pfad zur Mitarbeiterdatendatei enthält.  
  
     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]  
  
4.  Fügen Sie der `WebPart1`-Klasse folgenden Code hinzu. In diesem Code wird dem Webpart eine benutzerdefinierte Eigenschaft mit dem Namen `DataFilePath` hinzugefügt. Eine benutzerdefinierte Eigenschaft ist eine Eigenschaft, die vom Benutzer in SharePoint festgelegt werden kann. Diese Eigenschaft ruft den Speicherort einer XML-Datendatei ab, die zum Auffüllen des Datenrasters verwendet wird, und legt diesen Speicherort fest.  
  
     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]  
  
5.  Ersetzen Sie die `CreateChildControls`-Methode durch folgenden Code: Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Fügt das Datenraster und die Bezeichnung hinzu, die Sie im vorherigen Schritt deklariert haben.  
  
    -   Bindet das Datenraster an eine XML-Datei, die Mitarbeiterdaten enthält.  
  
     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]  
  
6.  Fügen Sie der `WebPart1`-Klasse die folgende Methode hinzu. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Erstellt ein Verb, das im Verbmenü des gerenderten Webparts angezeigt wird.  
  
    -   Behandelt das Ereignis, das ausgelöst wird, wenn der Benutzer im Verbmenü das Verb auswählt. In diesem Code wird die Liste der Mitarbeiter gefiltert, die im Datenraster angezeigt wird.  
  
     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]  
  
## <a name="testing-the-web-part"></a>Testen des Webparts  
 Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt. Sie können das Webpart jeder Webpartseite hinzufügen.  
  
#### <a name="to-test-the-web-part"></a>So testen Sie das Webpart  
  
1.  Fügen Sie folgendes XML in eine Editor-Datei ein. Diese XML-Datei enthält die Beispieldaten, die im Webpart angezeigt werden.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
           <employee>  
               <name>David Hamilton</name>  
               <hireDate>2001-05-11</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
           <employee>  
               <name>Karina Leal</name>  
               <hireDate>1999-04-01</hireDate>  
               <title>Manager</title>  
           </employee>  
           <employee>  
               <name>Nancy Davolio</name>  
               <hireDate>1992-05-01</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
           <employee>  
               <name>Steven Buchanan</name>  
               <hireDate>1955-03-04</hireDate>  
               <title>Manager</title>  
           </employee>  
           <employee>  
               <name>Suyama Michael</name>  
               <hireDate>1963-07-02</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
        </employees>  
    ```  
  
2.  Wählen Sie in Editor, in der Menüleiste **Datei**, **speichern unter**.  
  
3.  In der **speichern unter** Dialogfeld die **Dateityp** wählen **alle Dateien**.  
  
4.  In der **Dateiname** geben **data.xml**.  
  
5.  Wählen Sie einen beliebigen Ordner mithilfe der **Ordner durchsuchen** aus, und klicken Sie dann die **speichern** Schaltfläche.  
  
6.  Wählen Sie in Visual Studio die **F5** Schlüssel.  
  
     Die SharePoint-Website wird geöffnet.  
  
7.  Auf der **Websiteaktionen** Menü wählen **Weitere Optionen**.  
  
8.  In der **erstellen** Seite, und wählen Sie die **Webpartseite** geben, und wählen Sie dann die **erstellen** Schaltfläche.  
  
9. In der **neue Webpartseite** Seite, nennen Sie die Seite **SampleWebPartPage.aspx**, und wählen Sie dann die **erstellen** Schaltfläche.  
  
     Die Webpartseite wird angezeigt.  
  
10. Wählen Sie eine Zone auf der Webpartseite aus.  
  
11. Wählen Sie am oberen Rand der Seite, die **einfügen** Registerkarte, und wählen Sie dann die **Webpart** Schaltfläche.  
  
12. In der **Kategorien** Bereich, wählen Sie die **benutzerdefinierte** Ordner, wählen Sie die **WebPart1** -Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Das Webpart wird auf der Seite angezeigt.  
  
## <a name="testing-the-custom-property"></a>Testen der benutzerdefinierten Eigenschaft  
 Um das im Webpart angezeigte Datenraster aufzufüllen, geben Sie den Pfad der XML-Datei an, die Daten zu jedem Mitarbeiter enthält.  
  
#### <a name="to-test-the-custom-property"></a>So testen Sie die benutzerdefinierte Eigenschaft  
  
1.  Wählen Sie den Pfeil, der auf der rechten Seite des Webparts angezeigt wird, und wählen Sie dann **Webpart bearbeiten** aus dem angezeigten Menü aus.  
  
     Ein Bereich, der Eigenschaften für das Webpart enthält, wird auf der rechten Seite der Seite angezeigt.  
  
2.  Erweitern Sie im Bereich der **Sonstiges** Knoten, geben Sie den Pfad der XML-Datei, die Sie zuvor erstellt haben, wählen Sie die **übernehmen** aus, und klicken Sie dann die **OK** Schaltfläche.  
  
     Überprüfen Sie, ob eine Liste von Mitarbeitern im Webpart angezeigt wird.  
  
## <a name="testing-the-web-part-verb"></a>Testen des Webpartverbs  
 Zeigen Sie Mitarbeiter an, die keine Manager sind, und blenden Sie diese aus, indem Sie auf ein Element klicken, das im Verbmenü des Webparts angezeigt wird.  
  
#### <a name="to-test-the-web-part-verb"></a>So testen Sie das Webpartverb  
  
1.  Wählen Sie den Pfeil, der auf der rechten Seite des Webparts angezeigt wird, und wählen Sie dann **nur Manager anzeigen** aus dem angezeigten Menü aus.  
  
     Nur Mitarbeiter, die Manager sind, werden im Webpart angezeigt.  
  
2.  Wählen Sie den Pfeil erneut aus, und wählen Sie dann **alle Mitarbeiter anzeigen** aus dem angezeigten Menü aus.  
  
     Alle Mitarbeiter werden im Webpart angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Vorgehensweise: erstellen ein SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  