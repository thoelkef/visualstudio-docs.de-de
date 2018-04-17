---
title: 'Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09606f3ca61abd747451f92d4ecf8ee43010e669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten

Der Business Data Connectivity (BDC)-Dienst ermöglicht SharePoint, um Geschäftsdaten aus Back-End-serveranwendungen, Webdienste und Datenbanken anzuzeigen.

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein Modell für den BDC-Dienst zu erstellen, die Informationen zu Kontakten in einer Beispieldatenbank zurückgibt. Eine externe Liste erstellt in SharePoint durch dieses Modell verwenden.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Projekts.
- Hinzufügen einer Entität zum Modell.
- Hinzufügen einer Finder-Methode.
- Hinzufügen einer bestimmten Finder-Methode.
- Testen des Projekts.

## <a name="prerequisites"></a>Erforderliche Komponenten

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Zugriff auf die AdventureWorks-Beispieldatenbank. Weitere Informationen zum Installieren der AdventureWorks-Datenbank finden Sie unter [SQL Server-Beispieldatenbanken](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="creating-a-project-that-contains-a-bdc-model"></a>Erstellen eines Projekts, das ein BDC-Modell enthält

1. Wählen Sie in der Menüleiste in Visual Studio **Datei**, **neu**, **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Element.

3. In der **Vorlagen** Bereich auswählen **SharePoint 2010-Projekt**, nennen Sie das Projekt **AdventureWorksTest**, und wählen Sie dann die **OK** Schaltfläche .

     Die **Assistent zum Anpassen von SharePoint** angezeigt wird. Mit diesem Assistenten können Sie die Website angeben, die Sie zum Debuggen des Projekts, und legen Sie die Vertrauensebene der Projektmappe verwenden.

4. Wählen Sie die **als farmlösung bereitstellen** Optionsfeldes zum Festlegen der Vertrauensebene.

5. Wählen Sie die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu übernehmen.

6. In **Projektmappen-Explorer**, wählen Sie den SharePoint-Projektknoten.

7. Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

8. In der **Vorlagen** Bereich auswählen **Business Data Connectivity-Modell (nur Farmlösung)**, nennen Sie das Projekt **AdventureWorksContacts**, und wählen Sie dann die **Hinzufügen** Schaltfläche.

## <a name="adding-data-access-classes-to-the-project"></a>Hinzufügen von Datenzugriffsklassen zum Projekt

1. Wählen Sie in der Menüleiste **Tools**, **mit Datenbank verbinden**.

     Die **Verbindung hinzufügen** Dialogfeld wird geöffnet.

2. Fügen Sie eine Verbindung zu SQL Server AdventureWorks-Beispieldatenbank.

     Weitere Informationen finden Sie unter [Verbindung hinzufügen/ändern (Microsoft SQL Server)](http://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.

4. Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.

5. In der **installierte Vorlagen** Bereich, wählen Sie die **Daten** Knoten.

6. In der **Vorlagen** Bereich auswählen **LINQ to SQL-Klassen**.

7. In der **Namen** geben **AdventureWorks**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Eine DBML-Datei wird dem Projekt hinzugefügt, und der Object Relational Designer (O/R-Designer) wird geöffnet.

8. Wählen Sie in der Menüleiste **Ansicht**, **Server-Explorer**.

9. In **Server-Explorer**, erweitern Sie den Knoten, die AdventureWorks-Beispieldatenbank darstellt, und erweitern Sie dann die **Tabellen** Knoten.

10. Hinzufügen der **Contact (Person)** Tabelle in den O/R-Designer.

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitätsklasse verfügt über Eigenschaften, die den Spalten in der Tabelle Kontakt (Person) zuordnen.

## <a name="removing-the-default-entity-from-the-bdc-model"></a>Entfernen die Standardentität aus dem BDC-Modell

Die **Business Data Connectivity-Modell** Projekt fügt eine Standardentität mit dem Namen Entity1 für das Modell. Entfernen Sie diese Entität. Später fügen Sie eine neue Entität. Beginnend mit einem leeren Modell reduziert die Anzahl der erforderlichen Schritte zum Abschließen dieser exemplarischen Vorgehensweise.

1. In **Projektmappen-Explorer**, erweitern Sie die **BdcModel1** Knoten, und öffnen Sie dann die Datei BdcModel1.bdcm.

2. Business Data Connectivity-Modell-Datei wird im BDC-Designer geöffnet.

3. Öffnen Sie im Designer das Kontextmenü für **Entity1**, und wählen Sie dann **löschen**.

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für Entity1.vb (in Visual Basic) oder Entity1.cs (in c#), und wählen Sie dann **löschen**.

5. Öffnen Sie das Kontextmenü für Entity1Service.vb (in Visual Basic) oder Entity1Service.cs (in c#), und wählen Sie dann **löschen**.

## <a name="adding-an-entity-to-the-model"></a>Hinzufügen einer Entität zum Modell

Hinzufügen einer Entität zum Modell. Fügen Sie Entitäten aus der Visual Studio **Toolbox** im BDC-Designer.

1. Klicken Sie in der Menüleiste auf **Ansicht**, **Toolbox**.

2. Auf der **BusinessDataConnectivity** auf der Registerkarte die **Toolbox**, Hinzufügen einer **Entität** im BDC-Designer.

     Die neue Entität wird im Designer angezeigt. Visual Studio fügt eine Datei, die von benannten EntityService.vb (in Visual Basic) oder EntityService.cs (in c#) für das Projekt ist.

3. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaften**, **Fenster**.

4. In der **Eigenschaften** legen die **Name** Eigenschaftswert angibt, **Kontakt**.

5. Öffnen Sie im Designer das Kontextmenü für die Entität, wählen Sie **hinzufügen**, und wählen Sie dann **Bezeichner**.

     Ein neuer Bezeichner wird für die Entität angezeigt.

6. In der **Eigenschaften** Fenster, ändern Sie den Namen des Bezeichners zu **ContactID**.

7. In der **Typnamen** wählen **System. Int32**.

## <a name="adding-a-specific-finder-method"></a>Hinzufügen einer bestimmten Finder-Methode

Um den BDC-Dienst zum Anzeigen eines bestimmten Kontakts zu aktivieren, müssen Sie eine bestimmten Finder-Methode hinzufügen. Der BDC-Dienst Ruft die spezifischer Finder-Methode auf, wenn ein Benutzer ein Element in einer Liste auswählt und dann wählt die **Ansichtselement** Schaltfläche auf dem Menüband.

Hinzufügen eine bestimmten Finder-Methode für die Kontakt-Entität mithilfe der **BDC-Methodendetails** Fenster. Um eine bestimmte Entität zurückzugeben, fügen Sie Code zur Methode hinzu.

1. Wählen Sie in der BDC-Designer die **Kontakt** Entität.

2. Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **BDC-Methodendetails**.

     Das BDC-Methodendetails-Fenster wird geöffnet.

3. In der **Hinzufügen einer Methode** wählen **bestimmten Finder-Methode erstellen**.

     Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden der **BDC-Methodendetails** Fenster.

    - Eine Methode mit dem Namen ReadItem.

    - Ein Eingabeparameter für die Methode.

    - Ein Rückgabeparameter für die Methode.

    - Ein Typdeskriptor für jeden Parameter.

    - Methodeninstanz für die Methode.

4. In der **BDC-Methodendetails** Fenster, öffnen Sie die Liste, die für die **Kontakt** Typdeskriptor, und wählen Sie dann **bearbeiten**.

     Die **BDC-Explorer** wird geöffnet, und eine hierarchische Ansicht des Modells.

5. In der **Eigenschaften** Fenster öffnen Sie die Liste neben den **TypeName** -Eigenschaft, wählen Sie die **aktuelles Projekt** Registerkarte, und wählen Sie dann die **Kontakt**Eigenschaft.

6. In der **BDC-Explorer**, öffnen Sie im Kontextmenü des der **Kontakt**, und wählen Sie dann **Typdeskriptor hinzufügen**.

     Ein neuer Typdeskriptor mit dem Namen **TypeDescriptor1** wird angezeigt, der **BDC-Explorer**.

7. In der **Eigenschaften** legen die **Namen** Eigenschaftswert an **ContactID**.

8. Öffnen Sie die Liste neben den **TypeName** -Eigenschaft, und wählen Sie dann **Int32**.

9. Öffnen Sie die Liste neben den **Bezeichner** -Eigenschaft, und wählen Sie dann **ContactID**.

10. Wiederholen Sie Schritt 6, um ein Typdeskriptor für jedes der folgenden Felder zu erstellen.

    |name|Typname|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Telefon|System.String|
    |emailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Im BDC-Designer auf die **Kontakt** Entität, öffnen die **ReadItem** Methode.

     Die Kontakt-Service-Codedatei wird im Code-Editor geöffnet.

12. In der `ContactService` -Klasse, ersetzen Sie die `ReadItem` -Methode durch folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

    - Ruft einen Datensatz aus der Contact-Tabelle der AdventureWorks-Datenbank ab.

    - Eine Kontaktentität zurückgegeben an den BDC-Dienst.

    > [!NOTE]
    > Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="adding-a-finder-method"></a>Hinzufügen einer Finder-Methode

Damit kann den BDC-Dienst, um die Kontakte in einer Liste anzuzeigen, müssen Sie eine Finder-Methode hinzufügen. Hinzufügen eine Finder-Methode für die Kontakt-Entität mithilfe der **BDC-Methodendetails** Fenster. Um eine Auflistung von Entitäten an den BDC-Dienst zurückzugeben, fügen Sie Code zur Methode hinzu.

1. Wählen Sie im BDC-Designer die **Kontakt** Entität.

2. In der **BDC-Methodendetails** Fenster reduzieren die **ReadItem** Knoten.

3. In der **Hinzufügen einer Methode** Liste unter dem **ReadList** -Methode, wählen Sie **Finder-Methode erstellen**.

     Visual Studio fügt eine Methode, einen Rückgabeparameter und ein Typdeskriptor.

4. Im BDC-Designer auf die **Kontakt** Entität, öffnen die **ReadList** Methode.

     Die Codedatei für den Kontakt-Dienst wird im Code-Editor geöffnet.

5. In der `ContactService` -Klasse, ersetzen Sie die `ReadList` -Methode durch folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

    - Ruft Daten aus der Contacts-Tabelle der AdventureWorks-Datenbank ab.

    - Gibt eine Liste der Kontakt-Entitäten an den BDC-Dienst zurück.

    > [!NOTE]
    > Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="testing-the-project"></a>Testen des Projekts

Wenn Sie das Projekt ausführen, die SharePoint-Website wird geöffnet, und Visual Studio fügt das Modell mit dem Business Data Connectivity-Dienst. Erstellen Sie eine externe Liste in SharePoint, die die Contact-Entität verweist. Die Daten für Kontakte in der AdventureWorks-Datenbank, die in der Liste angezeigt werden.

> [!NOTE]
> Sie müssen möglicherweise die Sicherheitseinstellungen in SharePoint zu ändern, bevor Sie die Lösung Debuggen können. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Drücken Sie die Taste **F5**.

     Die SharePoint-Website wird geöffnet.

2. Auf der **Websiteaktionen** Menü Wählen Sie die **Weitere Optionen** Befehl.

3. Auf der **erstellen** Seite, und wählen Sie die **externe Liste** Vorlage, und wählen Sie dann die **erstellen** Schaltfläche.

4. Benennen Sie die benutzerdefinierte Liste **Kontakte**.

5. Wählen Sie die Schaltfläche zum Durchsuchen neben der **externe Inhaltstypen** Feld.

6. In der **externen Inhalt Typauswahl** Dialogfeld Wählen Sie die **AdventureWorksContacts.BdcModel1.Contact** -Element aus, und wählen Sie dann die **erstellen** Schaltfläche.

     SharePoint wird eine externe Liste mit Kontakten aus der AdventureWorks-Beispieldatenbank erstellt.

7. Um den bestimmten Finder-Methode zu testen, wählen Sie einen Kontakt in der Liste aus.

8. Wählen Sie auf dem Menüband der **Elemente** Registerkarte, und wählen Sie dann die **Ansichtselement** Befehl.

     Die Details des Kontakts, die Sie ausgewählt haben, die im Formular angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über das Entwerfen von Modellen für den BDC-Dienst in SharePoint in den folgenden Themen:

- [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).
- [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).
- [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Siehe auch

[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
[Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)  
[Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)  
[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
