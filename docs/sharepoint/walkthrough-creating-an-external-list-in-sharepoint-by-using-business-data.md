---
title: "Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Gesch&#228;ftsdaten"
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
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Geschäftsdaten in einem Webpart"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Externe Liste"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Geschäftsdaten in einer SharePoint-Liste"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Geschäftsdaten in einer SharePoint-Liste"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Geschäftsdaten in einem Webpart"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Gesicherte Entitätsliste"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Gesicherte Entitätsliste"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Externe Liste"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Gesch&#228;ftsdaten
  Der Business Data Connectivity \(BDC\)\-Dienst ermöglicht SharePoint das Anzeigen von Geschäftsdaten von Back\-End\-Serveranwendungen, Webdiensten und Datenbanken.  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie ein Modell für den BDC\-Dienst erstellt wird, das Informationen zu Kontakten in einer Beispieldatenbank zurückgibt.  Dann erstellen Sie unter Verwendung dieses Modells eine externe Liste in SharePoint.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Projekts.  
  
-   Hinzufügen einer Entität zum Modell.  
  
-   Hinzufügen einer Finder\-Methode.  
  
-   Hinzufügen einer spezifischen Finder\-Methode.  
  
-   Testen des Projekts  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] oder [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Zugriff auf die AdventureWorks\-Beispieldatenbank.  Weitere Informationen dazu, wie Sie die AdventureWorks\-Datenbank, finden Sie installiert [SQL Server\-Beispieldatenbanken](http://go.microsoft.com/fwlink/?LinkID=117483).  
  
## Erstellen eines Projekts, das ein BDC\-Modell enthält  
  
#### So erstellen Sie ein Projekt, das ein BDC\-Modell enthält  
  
1.  Wählen Sie in der Visual Studio\-Menüleiste **Datei**, **Neu** und **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie das Element **2010** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie **SharePoint 2010\-Projekt** aus, nennen Sie das Projekt "AdventureWorksTest", und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  In diesem Assistenten können Sie die Site angeben, die Sie verwenden, um das Projekt zu debuggen und die Vertrauensebene der Projektmappe ermöglicht.  
  
4.  Wählen Sie das Optionsfeld **Als Farmlösung bereitstellen**, um die Vertrauensebene festzulegen.  
  
5.  Klicken Sie auf die Schaltfläche **Fertig stellen**, um die standardmäßige lokale SharePoint\-Website zu übernehmen.  
  
6.  Wählen Sie im **Projektmappen\-Explorer** den SharePoint\-Projektknoten aus.  
  
7.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
8.  Im Bereich **Vorlagen** wählen Sie **Business Data Connectivity\-Modell \(nur Farmlösung\)** aus, nennen Sie das Projekt AdventureWorksContacts, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
## Hinzufügen von Datenzugriffsklassen zum Projekt  
  
#### So fügen Sie dem Projekt Datenzugriffsklassen hinzu  
  
1.  Wählen Sie in der Menüleiste **Mit Datenbank verbinden**, **Tools** aus.  
  
     Das Dialogfeld **Verbindung hinzufügen** wird geöffnet.  
  
2.  Fügen Sie der SQL Server\-Beispieldatenbank AdventureWorks eine Verbindung hinzu.  
  
     Weitere Informationen finden Sie unter [Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/de-de/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten aus.  
  
4.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
5.  Im Bereich **Installierte Vorlagen** wählen Sie den Knoten **Daten** aus.  
  
6.  Im Bereich **Vorlagen** wählen Sie **LINQ to SQL\-Klassen** aus.  
  
7.  Im Feld **Name** Geben Sie "AdventureWorks" an und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Dem Projekt wird eine DBML\-Datei hinzugefügt, und der Object Relational Designer \(O\/R\-Designer\) wird geöffnet.  
  
8.  Wählen Sie in der Menüleiste **Server\-Explorer**, **Ansicht** aus.  
  
9. Erweitern Sie in **Server\-Explorer** den Knoten, der die AdventureWorks\-Beispieldatenbank darstellt, und erweitern Sie dann den Knoten **Tabellen**.  
  
10. Fügen Sie der Tabelle **Kontakt \(Person\)** auf den O\/R\-Designer hinzu.  
  
     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt.  Die Entitätsklasse verfügt über Eigenschaften, die sich auf die Spalten in der Tabelle Contact \(Person\) beziehen.  
  
## Entfernen der Standardentität aus dem BDC\-Modell  
 Durch das Projekt vom Typ **Business Data Connectivity\-Modell** wird dem Modell eine Standardentität mit dem Namen Entity1 hinzugefügt.  Entfernen Sie diese Entität.  Später fügen Sie eine neue Entität hinzu.  Beginnen Sie mit einem leeren Modell, um die Anzahl der Schritte zu reduzieren, die für die Durchführung der exemplarischen Vorgehensweise erforderlich sind.  
  
#### So entfernen Sie die Standardentität aus dem Modell  
  
1.  Erweitern Sie in **Projektmappen\-Explorer** den Knoten **BdcModel1**, und öffnen Sie dann die BdcModel1.bdcm\-Datei.  
  
2.  Die Business Data Connectivity\-Modelldatei wird im BDC\-Designer geöffnet.  
  
3.  Im Designer öffnen Sie das Kontextmenü für **Entity1**, und wählen Sie dann **Löschen** aus.  
  
4.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für Entity1.vb \(in Visual Basic\) oder Entity1.cs \(in C\#\), und wählen Sie dann **Löschen** aus.  
  
5.  Öffnen Sie das Kontextmenü für Entity1Service.vb \(in Visual Basic\) oder Entity1Service.cs \(in C\#\), und wählen Sie dann **Löschen** aus.  
  
## Hinzufügen einer Entität zum Modell  
 Fügen Sie dem Modell eine Entität hinzu.  Sie können Entitäten von der **Werkzeugkasten** von Visual Studio auf den BDC\-Designer hinzufügen.  
  
#### So fügen Sie dem Modell eine Entität hinzu  
  
1.  Wählen Sie in der Menüleiste **Ansicht**, **Werkzeugkasten** aus.  
  
2.  Auf der Registerkarte **BusinessDataConnectivityWerkzeugkasten**, fügen Sie **Entität** auf den BDC\-Designer hinzu.  
  
     Die neue Entität wird im Designer angezeigt.  Visual Studio fügt eine Datei hinzu, die von EntityService.vb \(in Visual Basic\) bzw. EntityService.cs \(in C\#\) zum Projekt erstellt.  
  
3.  Klicken Sie auf der Menüleiste **Eigenschaften**, **Fenster**, **Ansicht** aus.  
  
4.  Im Fenster **Eigenschaften** legen Sie die Eigenschaft ENT50ENTs\-Wert auf Contact fest.  
  
5.  Klicken Sie im Designer öffnen Sie das Kontextmenü für die Entität, wählen Sie **Hinzufügen** und wählen Sie dann **Bezeichner** aus.  
  
     Ein neuer Bezeichner wird für die Entität angezeigt.  
  
6.  Ändern Sie im Fenster **Eigenschaften** den Namen des Bezeichners in ContactID.  
  
7.  In der Liste **Typname** wählen Sie **System.Int32** aus.  
  
## Hinzufügen einer spezifischen Finder\-Methode  
 Damit der BDC\-Dienst einen bestimmten Kontakt anzeigen kann, müssen Sie eine spezifische Finder\-Methode hinzufügen.  Der BDC\-Dienst ruft die spezifische Finder\-Methode auf, wenn ein Benutzer in einer Liste ein Element auswählt und dann die Schaltfläche **Element anzeigen** auf dem Menüband aus.  
  
 Fügen Sie der Contact\-Entität im Fenster **BDC\-Methodendetails** eine spezifische Finder\-Methode hinzu.  Um eine bestimmte Entität zurückzugeben, fügen Sie der Methode Code hinzu.  
  
#### So fügen Sie eine spezifische Finder\-Methode hinzu  
  
1.  Wählen Sie im BDC\-Designer die Entität **Kontakt** aus.  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster BDC\-Methodendetails wird geöffnet.  
  
3.  In der Liste **Methode hinzufügen** wählen Sie **Spezifische Finder\-Methode erstellen** aus.  
  
     Mit Visual Studio werden dem Modell die folgenden Elemente hinzugefügt.  Diese Elemente werden im Fenster **BDC\-Methodendetails** angezeigt.  
  
    -   Eine Methode mit dem Namen ReadItem.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Rückgabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für jeden Parameter.  
  
    -   Eine Methodeninstanz für die Methode.  
  
4.  Im Fenster **BDC\-Methodendetails** öffnen Sie die Liste, die für den Typdeskriptor **Kontakt** angezeigt wird, und wählen Sie dann **Bearbeiten** aus.  
  
     **BDC\-Explorer** wird geöffnet und stellt eine hierarchische Ansicht des Modells.  
  
5.  Im Fenster **Eigenschaften** öffnen Sie die Liste neben der Eigenschaft **TypeName**, wählen Sie die Registerkarte **Aktuelles Projekt**, und wählen Sie dann die Eigenschaft **Kontakt** aus.  
  
6.  In **BDC\-Explorer** öffnen Sie das Kontextmenü **Kontakt**, und wählen Sie dann **Typdeskriptor hinzufügen** aus.  
  
     Ein neuer Typdeskriptor des neuen Typs, der dem Namen **TypeDescriptor1**, im **BDC\-Explorer** angezeigt.  
  
7.  Legen Sie im Fenster **Eigenschaften** die Werteigenschaft **Name** auf **ContactID** fest.  
  
8.  Öffnen Sie die Liste neben der Eigenschaft **TypeName**, und wählen Sie dann **Int32** aus.  
  
9. Öffnen Sie die Liste neben der Eigenschaft **Bezeichner**, und wählen Sie dann **ContactID**.  
  
10. Wiederholen Sie Schritt 6, um einen Typdeskriptor für jedes der folgenden Felder zu erstellen.  
  
    |Name|Typname|  
    |----------|-------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Phone|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. Im BDC\-Designer unter der Entität **Kontakt**, öffnen Sie die **ReadItem**\-Methode.  
  
     Die Codedatei für den Contact\-Dienst wird im Code\-Editor geöffnet.  
  
12. Ersetzen Sie in der `ContactService`\-Klasse die `ReadItem`\-Methode durch folgenden Code.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft einen Datensatz aus der Tabelle Contact der AdventureWorks\-Datenbank ab.  
  
    -   Gibt eine Contact\-Entität an den BDC\-Dienst zurück.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Hinzufügen einer Finder\-Methode  
 Damit der BDC\-Dienst die Kontakte in einer Liste anzeigen kann, müssen Sie eine Finder\-Methode hinzufügen.  Fügen Sie der Contact\-Entität im Fenster **BDC\-Methodendetails** eine Finder\-Methode hinzu.  Um eine Auflistung von Entitäten an den BDC\-Dienst zurückzugeben, fügen Sie der Methode Code hinzu.  
  
#### So fügen Sie eine Finder\-Methode hinzu  
  
1.  Wählen Sie im BDC\-Designer die Entität **Kontakt** aus.  
  
2.  Im Fenster **BDC\-Methodendetails** reduzieren Sie den Knoten **ReadItem**.  
  
3.  In der Liste **Methode hinzufügen** unter der Methode **ReadList**, wählen Sie **Finder\-Methode erstellen** aus.  
  
     Visual Studio fügt eine Methode, einen Rückgabeparameter und einen Typdeskriptor hinzu.  
  
4.  Im BDC\-Designer unter der Entität **Kontakt**, öffnen Sie die **ReadList**\-Methode.  
  
     Die Codedatei für den Kontaktdienst wird im Code\-Editor geöffnet.  
  
5.  Ersetzen Sie in der `ContactService`\-Klasse die `ReadList`\-Methode durch folgenden Code.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft Daten aus der Tabelle Contacts der AdventureWorks\-Datenbank ab.  
  
    -   Gibt eine Liste von Contact\-Entitäten an den BDC\-Dienst zurück.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Testen des Projekts  
 Wenn Sie das Projekt ausführen, wird die SharePoint\-Site geöffnet, und Visual Studio fügt dem Business Data Connectivity\-Dienst das Modell hinzu.  Erstellen Sie eine externe Liste in SharePoint, die auf die Contact\-Entität verweist.  Die Daten für Kontakte in der AdventureWorks\-Datenbank werden in der Liste angezeigt.  
  
> [!NOTE]  
>  Möglicherweise müssen zunächst die Sicherheitseinstellungen in SharePoint geändert werden, damit Sie die Lösung debuggen können.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### So testen Sie das Projekt  
  
1.  Wählen Sie die Taste **F5** aus.  
  
     Die SharePoint\-Website wird geöffnet.  
  
2.  Klicken Sie im Menü **Websiteaktionen** wählen Sie den Befehl **Weitere Optionen** aus.  
  
3.  Auf der Seite **Erstellen** wählen Sie die Vorlage **Externe Liste** aus, und wählen Sie dann die Schaltfläche **Erstellen** aus.  
  
4.  Weisen Sie der benutzerdefinierten Liste den Namen Contacts zu.  
  
5.  Wählen Sie die Schaltfläche neben dem Feld **Externer Inhaltstyp** aus.  
  
6.  Im Dialogfeld **Auswahl für externen Inhaltstyp** wählen Sie das Element **AdventureWorksContacts.BdcModel1.Contact**, und wählen Sie dann die Schaltfläche **Erstellen** aus.  
  
     SharePoint erstellt eine externe Liste, welche Kontakte aus der AdventureWorks\-Beispieldatenbank enthält.  
  
7.  Um die spezifische Finder\-Methode zu testen, wählen Sie einen Kontakt in der Liste.  
  
8.  Klicken Sie im Menüband auf die Registerkarte **Elemente**, und dann den Befehl **Element anzeigen** aus.  
  
     Die Details Contact, den Sie ausgewählt haben, angezeigt.  
  
## Nächste Schritte  
 Weitere Informationen zum Entwerfen von Modellen für den BDC\-Dienst in SharePoint finden Sie in folgenden Themen:  
  
-   [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).  
  
## Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  