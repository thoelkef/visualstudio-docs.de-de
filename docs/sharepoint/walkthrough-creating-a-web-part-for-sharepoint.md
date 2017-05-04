---
title: "Exemplarische Vorgehensweise: Erstellen eines Webparts f&#252;r SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Erstellen"
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Entwerfen"
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Entwickeln"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Exemplarische Vorgehensweise: Erstellen eines Webparts f&#252;r SharePoint
  Mithilfe von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint\-Website direkt im Browser ändern.  In dieser exemplarischen Vorgehensweise wird erläutert, wie ein Webpart mit der Elementvorlage **Webpart** in Visual Studio 2010 erstellt wird.  
  
 Das Webpart zeigt Mitarbeiter in einem Datenraster an.  Der Benutzer gibt den Speicherort der Datei an, die die Mitarbeiterdaten enthält.  Außerdem kann der Benutzer das Datenraster filtern, damit nur Mitarbeiter, die Manager sind, in der Liste angezeigt werden.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Webparts mit der Visual Studio\-Elementvorlage **Webpart**.  
  
-   Erstellen einer Eigenschaft, die vom Benutzer des Webparts festgelegt werden kann.  Diese Eigenschaft gibt den Speicherort der Mitarbeiterdatendatei an.  
  
-   Rendern von Inhalt in einem Webpart durch Hinzufügen von Steuerelementen zur Webpart\-Steuerelementauflistung.  
  
-   Erstellen eines neuen, als *Verb* bezeichneten Menüelements, das im Verbmenü des gerenderten Webparts angezeigt wird.  Verben ermöglichen es dem Benutzer, die im Webpart angezeigten Daten zu ändern.  
  
-   Testen des Webparts in SharePoint.  
  
    > [!NOTE]  
    >  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die Elemente werden durch die verwendete Edition von Visual Studio und die gewählten Einstellungen bestimmt.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] oder eine Edition der Anwendungslebenszyklus\-Verwaltung \(Application Lifecycle Management, ALM\) von Visual Studio.  
  
## Erstellen eines leeren SharePoint\-Projekts  
 Erstellen Sie zunächst ein leeres SharePoint\-Projekt.  Später fügen Sie dem Projekt mit der Elementvorlage **Webpart** ein Webpart hinzu.  
  
#### So erstellen Sie ein leeres SharePoint\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit der Option **Als Administrator ausführen**.  
  
2.  Wählen Sie auf der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **SharePoint** unter der gewünschten Sprache, und wählen Sie anschließend den Knoten **2010** aus.  
  
4.  Im Bereich **Vorlagen** wählen Sie **SharePoint 2010\-Projekt**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.  
  
5.  Wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** aus, und klicken Sie dann auf die Schaltfläche **Fertig stellen**, um die standardmäßige lokale SharePoint\-Website zu übernehmen.  
  
## Hinzufügen eines Webparts zum Projekt  
 Fügen Sie dem Projekt ein Element **Webpart** hinzu.  Durch das Element **Webpart** wird die Codedatei für das Webpart hinzugefügt.  Später fügen Sie der Codedatei für das Webpart Code hinzu, um den Inhalt des Webparts zu rendern.  
  
#### So fügen Sie ein Webpart zum Projekt hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
2.  Erweitern Sie im Dialogfeld **Neues Element hinzufügen** im Bereich **Installierte Vorlagen** den Knoten **SharePoint**, und klicken Sie dann auf den Knoten **2010**.  
  
3.  Wählen Sie in der Liste der SharePoint\-Vorlagen die Vorlage **Webpart** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.  
  
     Das Element **Webpart** wird im **Projektmappen\-Explorer** angezeigt.  
  
## Rendern von Inhalt im Webpart  
 Sie können angeben, welche Steuerelemente im Webpart angezeigt werden, indem Sie diese der Steuerelementauflistung der Webpartklasse hinzufügen.  
  
#### So rendern Sie Inhalt im Webpart  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** "WebPart1.vb" \(in Visual Basic\) oder "WebPart1.cs" \(in C\#\).  
  
     Die Codedatei für das Webpart wird im Code\-Editor geöffnet.  
  
2.  Fügen Sie am Anfang der Codedatei für das Webpart die folgenden Anweisungen hinzu.  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  Fügen Sie der `WebPart1`\-Klasse folgenden Code hinzu.  Mit diesem Code werden die folgenden Felder deklariert:  
  
    -   Ein Datenraster, um Mitarbeiter im Webpart anzuzeigen.  
  
    -   Text, der auf dem Steuerelement angezeigt wird, das zum Filtern des Datenrasters verwendet wird.  
  
    -   Eine Bezeichnung, die einen Fehler anzeigt, wenn das Datenraster keine Daten anzeigen kann.  
  
    -   Eine Zeichenfolge, die den Pfad zur Mitarbeiterdatendatei enthält.  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  Fügen Sie der `WebPart1`\-Klasse folgenden Code hinzu.  In diesem Code wird dem Webpart eine benutzerdefinierte Eigenschaft mit dem Namen `DataFilePath` hinzugefügt.  Eine benutzerdefinierte Eigenschaft ist eine Eigenschaft, die vom Benutzer in SharePoint festgelegt werden kann.  Diese Eigenschaft ruft den Speicherort einer XML\-Datendatei ab, die zum Auffüllen des Datenrasters verwendet wird, und legt diesen Speicherort fest.  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  Ersetzen Sie die `CreateChildControls`\-Methode durch den folgenden Code.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Fügt das Datenraster und die Bezeichnung hinzu, die Sie im vorherigen Schritt deklariert haben.  
  
    -   Bindet das Datenraster an eine XML\-Datei, die Mitarbeiterdaten enthält.  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  Fügen Sie der `WebPart1`\-Klasse die folgende Methode hinzu.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Erstellt ein Verb, das im Verbmenü des gerenderten Webparts angezeigt wird.  
  
    -   Behandelt das Ereignis, das ausgelöst wird, wenn der Benutzer im Verbmenü das Verb auswählt.  In diesem Code wird die Liste der Mitarbeiter gefiltert, die im Datenraster angezeigt wird.  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## Testen des Webparts  
 Wenn Sie das Projekt ausführen, wird die SharePoint\-Website geöffnet.  Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt.  Sie können das Webpart jeder Webpartseite hinzufügen.  
  
#### So testen Sie das Webpart  
  
1.  Fügen Sie folgendes XML in eine Editor\-Datei ein.  Diese XML\-Datei enthält die Beispieldaten, die im Webpart angezeigt werden.  
  
    ```  
  
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
  
2.  Wählen Sie in Editor in der Menüleiste **Datei**, **Speichern unter** aus.  
  
3.  Wählen Sie im Dialogfeld **Speichern unter** in der Liste **Dateityp** die Option **Alle Dateien** aus.  
  
4.  Geben Sie im Feld **Dateiname** den Namen "data.xml" ein.  
  
5.  Wählen Sie über die Schaltfläche **Ordner durchsuchen** einen die oft ausgegebene Befehlszeilen  Ordner aus, und klicken Sie dann auf **Speichern**.  
  
6.  In Visual Studio drücken Sie die Taste **F5**.  
  
     Die SharePoint\-Website wird geöffnet.  
  
7.  Klicken Sie im Menü **Websiteaktionen** auf **Weitere Optionen**.  
  
8.  Auf der Seite **Erstellen** wählen Sie den Typ **Webpartseite** aus, und wählen Sie dann die Schaltfläche **Erstellen** aus.  
  
9. Geben Sie auf der Seite **Neue Webpartseite** den Namen **SampleWebPartPage.aspx** für die Seite an, und klicken Sie dann auf die Schaltfläche **Erstellen**.  
  
     Die Webpartseite wird angezeigt.  
  
10. Wählen Sie eine Zone auf der Webpartseite aus.  
  
11. Wählen Sie im oberen Bereich der Webpartseite die Registerkarte **Einfügen** aus, und klicken Sie dann auf die Schaltfläche **Webpart**.  
  
12. Wählen Sie im Bereich **Kategorien** den Ordner **Benutzerdefiniert** aus, wählen Sie das Webpart **WebPart1** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.  
  
     Das Webpart wird auf der Seite angezeigt.  
  
## Testen der benutzerdefinierten Eigenschaft  
 Um das im Webpart angezeigte Datenraster aufzufüllen, geben Sie den Pfad der XML\-Datei an, die Daten zu jedem Mitarbeiter enthält.  
  
#### So testen Sie die benutzerdefinierte Eigenschaft  
  
1.  Wählen Sie den Pfeil aus, der auf der rechten Seite des Webparts angezeigt wird, und wählen Sie dann im angezeigten Menü **Webpart bearbeiten** aus.  
  
     Ein Bereich, der Eigenschaften für das Webpart enthält, wird auf der rechten Seite der Seite angezeigt.  
  
2.  Erweitern Sie im Bereich den Knoten **Sonstiges**, geben Sie den Pfad zur XML\-Datei ein, die Sie zuvor erstellt haben, wählen Sie **Übernehmen** und dann **OK** aus.  
  
     Überprüfen Sie, ob eine Liste von Mitarbeitern im Webpart angezeigt wird.  
  
## Testen des Webpartverbs  
 Zeigen Sie Mitarbeiter an, die keine Manager sind, und blenden Sie diese aus, indem Sie auf ein Element klicken, das im Verbmenü des Webparts angezeigt wird.  
  
#### So testen Sie das Webpartverb  
  
1.  Wählen Sie den Pfeil aus, der auf der rechten Seite des Webparts angezeigt wird, und wählen Sie dann im angezeigten Menü **Nur Manager anzeigen** aus.  
  
     Nur Mitarbeiter, die Manager sind, werden im Webpart angezeigt.  
  
2.  Wählen Sie den Pfeil erneut aus, und wählen Sie dann im angezeigten Menü **Alle Mitarbeiter anzeigen** aus.  
  
     Alle Mitarbeiter werden im Webpart angezeigt.  
  
## Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Gewusst wie: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  