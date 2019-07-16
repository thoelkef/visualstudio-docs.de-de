---
title: Erstellen Sie externe Liste in SharePoint mithilfe von Geschäftsdaten
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf9c7d13e6aaac85d3bac4254247a3c07b39b5c3
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401070"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Exemplarische Vorgehensweise: Erstellen Sie eine externe Liste in SharePoint mithilfe von Geschäftsdaten

Der Business Data Connectivity (BDC)-Dienst ermöglicht SharePoint zum Anzeigen von Geschäftsdaten aus Back-End-Server-Anwendungen, Webdienste und Datenbanken.

Diese exemplarische Vorgehensweise veranschaulicht das Erstellen eines Modells für den BDC-Dienst, der Informationen zu Kontakten in einer Beispieldatenbank zurückgibt. Klicken Sie dann erstellen eine externe Liste in SharePoint Sie mithilfe des Modells.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Projekts.
- Hinzufügen einer Entitätstyps zum Modell.
- Hinzufügen einer Finder-Methode.
- Hinzufügen einer bestimmten Finder-Methode.
- Testen des Projekts an.

## <a name="prerequisites"></a>Vorraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Windows und SharePoint.

- Zugriff auf die AdventureWorks-Beispieldatenbank. Weitere Informationen zum Installieren der AdventureWorks-Datenbank finden Sie unter [SQL Server-Beispieldatenbanken](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Erstellen Sie ein Projekt, das ein BDC-Modell enthält.

1. Wählen Sie auf der Menüleiste in Visual Studio **Datei** > **neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Element.

3. In der **Vorlagen** Bereich wählen **SharePoint 2010-Projekt**, nennen Sie das Projekt **AdventureWorksTest**, und wählen Sie dann die **OK** Schaltfläche .

     Die **SharePoint Customization Wizard** angezeigt wird. Mit diesem Assistenten können Sie den Standort angeben, den Sie zum Debuggen des Projekts, und legen Sie die Vertrauensebene der Projektmappe verwenden.

4. Wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, um die Vertrauensebene festgelegt.

5. Wählen Sie die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu akzeptieren.

6. In **Projektmappen-Explorer**, wählen Sie die SharePoint-Projektknoten.

7. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

8. In der **Vorlagen** Bereich wählen **Business Data Connectivity-Modell (nur Farmlösung)** , nennen Sie das Projekt **AdventureWorksContacts**, und wählen Sie dann die **Hinzufügen** Schaltfläche.

## <a name="add-data-access-classes-to-the-project"></a>Hinzufügen von Datenzugriffsklassen zum Projekt

1. Wählen Sie auf der Menüleiste **Tools** > **Herstellen einer Verbindung mit Datenbank**.

     Das Dialogfeld **Verbindung hinzufügen** wird geöffnet.

2. Fügen Sie eine Verbindung mit der SQL Server AdventureWorks-Beispieldatenbank hinzu.

     Weitere Informationen finden Sie unter [Verbindung hinzufügen/ändern (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.

4. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

5. In der **installierte Vorlagen** Bereich, wählen Sie die **Daten** Knoten.

6. In der **Vorlagen** Bereich wählen **LINQ to SQL-Klassen**.

7. In der **Namen** geben **AdventureWorks**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Eine DBML-Datei wird dem Projekt hinzugefügt, und der Object Relational Designer (O/R Designer) geöffnet wird.

8. Wählen Sie auf der Menüleiste **Ansicht** > **Server-Explorer**.

9. In **Server-Explorer**, erweitern Sie den Knoten, die AdventureWorks-Beispieldatenbank darstellt, und erweitern Sie dann die **Tabellen** Knoten.

10. Hinzufügen der **Kontakt (Person)** Tabelle in den O/R-Designer.

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitätsklasse verfügt über Eigenschaften, die die Spalten in der Tabelle Kontakt (Person) zugeordnet.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Entfernen Sie die Standardentität aus dem BDC-Modell

Die **Business Data Connectivity-Modells** Projekt wird eine Standardentität mit dem Namen ' Entity1 ' für das Modell. Entfernen Sie diese Entität. Später fügen Sie eine neue Entität. Beginnen mit einem leeren Modell reduziert die Anzahl der erforderlichen Schritte zum Abschließen dieser exemplarischen Vorgehensweise.

1. In **Projektmappen-Explorer**, erweitern Sie die **BdcModel1** Knoten, und öffnen Sie die *BdcModel1.bdcm* Datei.

2. Die Business Data Connectivity-Modell-Datei, die im BDC-Designer wird geöffnet.

3. Öffnen Sie im Designer das Kontextmenü für **' Entity1 '** , und wählen Sie dann **löschen**.

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für *Entity1.vb* (in Visual Basic) oder *Entity1.cs* (in c#), und wählen Sie dann **löschen** .

5. Öffnen Sie das Kontextmenü für *Entity1Service.vb* (in Visual Basic) oder *Entity1Service.cs* (in c#), und wählen Sie dann **löschen**.

## <a name="add-an-entity-to-the-model"></a>Eine Entität zum Modell hinzuzufügen.

Eine Entität zum Modell hinzuzufügen. Sie können Entitäten hinzufügen, von Visual Studio **Toolbox** im BDC-Designer.

1. Wählen Sie in der Menüleiste **Ansicht** > **Toolbox** aus.

2. Auf der **BusinessDataConnectivity** Registerkarte die **Toolbox**, Hinzufügen einer **Entität** im BDC-Designer.

     Die neue Entität wird im Designer angezeigt. Visual Studio fügt eine Datei mit dem Namen *von EntityService.vb* (in Visual Basic) oder *EntityService.cs* (in C#)) auf das Projekt.

3. Wählen Sie auf der Menüleiste **Ansicht** > **Eigenschaften** > **Fenster**.

4. In der **Eigenschaften** legen die **Namen** Eigenschaftswert **wenden Sie sich an**.

5. Öffnen Sie im Designer das Kontextmenü für die Entität, und wählen **hinzufügen**, und wählen Sie dann **Bezeichner**.

     Ein neuer Bezeichner wird für die Entität angezeigt.

6. In der **Eigenschaften** Fenster, ändern Sie den Namen des Bezeichners zu **ContactID**.

7. In der **Typnamen** wählen **System. Int32**.

## <a name="add-a-specific-finder-method"></a>Fügen Sie eine spezifische Finder-Methode

Um den BDC-Dienst zum Anzeigen eines bestimmten Kontakts zu aktivieren, müssen Sie eine spezifische Finder-Methode hinzufügen. Der BDC-Dienst Ruft die spezifische Finder-Methode auf, wenn ein Benutzer ein Element in einer Liste und dann wählt die **Ansichtselement** Schaltfläche auf dem Menüband.

Die Entität "Contact" eine bestimmten Finder-Methode hinzugefügt, mit der **BDC-Methodendetails** Fenster. Fügen Sie Code an die Methode, um eine bestimmte Entität zurückzugeben.

1. Wählen Sie in der BDC-Designer die **wenden Sie sich an** Entität.

2. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails**.

     Das BDC-Methodendetails-Fenster wird geöffnet.

3. In der **Hinzufügen einer Methode** wählen **spezifische Finder-Methode erstellen**.

     Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden angezeigt, der **BDC-Methodendetails** Fenster.

    - Eine Methode, mit dem Namen "ReadItem".

    - Ein Eingabeparameter für die Methode.

    - Ein Rückgabeparameter für die Methode.

    - Ein Typdeskriptor für jeden Parameter.

    - Eine Methodeninstanz für die Methode.

4. In der **BDC-Methodendetails** Fenster öffnen Sie die für die angezeigte Liste der **wenden Sie sich an** Typdeskriptor, und wählen Sie dann **bearbeiten**.

     Die **BDC-Explorer** wird geöffnet und enthält eine hierarchische Ansicht des Modells.

5. In der **Eigenschaften** Fenster öffnen Sie die Liste neben der **TypeName** -Eigenschaft, wählen Sie die **aktuelles Projekt** Registerkarte, und wählen Sie dann die **Kontakt**Eigenschaft.

6. In der **BDC-Explorer**, öffnen Sie im Kontextmenü des der **wenden Sie sich an**, und wählen Sie dann **Typdeskriptor hinzufügen**.

     Ein neuer Typdeskriptor, mit dem Namen **TypeDescriptor1** wird in der **BDC-Explorer**.

7. In der **Eigenschaften** legen die **Namen** Eigenschaftswert **ContactID**.

8. Öffnen Sie die Liste neben der **TypeName** -Eigenschaft, und wählen Sie dann **Int32**.

9. Öffnen Sie die Liste neben der **Bezeichner** -Eigenschaft, und wählen Sie dann **ContactID**.

10. Wiederholen Sie Schritt 6, um einen Typdeskriptor für jedes der folgenden Felder zu erstellen.

    |name|Typname|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Phone|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Im BDC-Designer auf die **wenden Sie sich an** öffnen Entität die **"ReadItem"** Methode.

     Wenden Sie sich an Authentifizierungsdienst-Codedatei wird im Code-Editor geöffnet.

12. In der `ContactService` -Klasse, ersetzen Sie die `ReadItem` Methode durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

    - Ruft einen Datensatz aus der Contact-Tabelle der AdventureWorks-Datenbank.

    - Gibt eine Entität "Contact" mit dem BDC-Dienst zurück.

    > [!NOTE]
    > Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Hinzufügen einer Finder-Methode

Um die Kontakte in einer Liste anzuzeigen. der BDC-Dienst zu aktivieren, müssen Sie eine Finder-Methode hinzufügen. Hinzufügen eine Finder-Methode, die Entität "Contact" mithilfe der **BDC-Methodendetails** Fenster. Um eine Auflistung von Entitäten mit dem BDC-Dienst zurückzugeben, fügen Sie der Methode Code hinzu.

1. Wählen Sie in der BDC-Designer die **wenden Sie sich an** Entität.

2. In der **BDC-Methodendetails** Fenster reduzieren die **"ReadItem"** Knoten.

3. In der **Hinzufügen einer Methode** Liste unter der **"ReadList"** Methode wählen **Finder-Methode erstellen**.

     Visual Studio fügt eine Methode, einen Rückgabeparameter und ein Typdeskriptor.

4. Im BDC-Designer auf die **wenden Sie sich an** öffnen Entität die **"ReadList"** Methode.

     Die Codedatei für den Kontakt-Dienst wird im Code-Editor geöffnet.

5. In der `ContactService` -Klasse, ersetzen Sie die `ReadList` Methode durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

   - Ruft Daten aus der Contacts-Tabelle der AdventureWorks-Datenbank ab.

   - Gibt eine Liste der Kontakt-Entitäten mit dem BDC-Dienst zurück.

     > [!NOTE]
     > Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Testen Sie das Projekt

Wenn Sie das Projekt ausführen, wird die SharePoint-Website wird geöffnet, und Visual Studio fügt das Modell mit dem Business Data Connectivity-Dienst. Erstellen Sie eine externe Liste in SharePoint, die die Entität "Contact" verweist. Die Daten für Kontakte in der AdventureWorks-Datenbank, die in der Liste angezeigt werden.

> [!NOTE]
> Sie müssen möglicherweise die Sicherheitseinstellungen in SharePoint zu ändern, bevor Sie Ihre Lösung Debuggen können. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Drücken Sie die Taste **F5**.

     Die SharePoint-Website wird geöffnet.

2. Auf der **Websiteaktionen** Menü Wählen Sie die **Weitere Optionen** Befehl.

3. Auf der **erstellen** Seite die **externe Liste** Vorlage, und wählen Sie dann die **erstellen** Schaltfläche.

4. Nennen Sie die benutzerdefinierte Liste **Kontakte**.

5. Wählen Sie die Schaltfläche zum Durchsuchen neben dem **External Content Type** Feld.

6. In der **Auswahl für externen Inhaltstyp** Dialogfeld auf die **AdventureWorksContacts.BdcModel1.Contact** Element aus, und wählen Sie dann die **erstellen** Schaltfläche.

     SharePoint erstellt eine externe Liste, die Kontakte aus der AdventureWorks-Beispieldatenbank enthält.

7. Um die spezifische Finder-Methode zu testen, wählen Sie einen Kontakt in der Liste aus.

8. Wählen Sie auf dem Menüband der **Elemente** Registerkarte, und wählen Sie dann die **Ansichtselement** Befehl.

     Die Details des Kontakts, die Sie ausgewählt haben, die auf einem Formular angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über das Entwerfen von Modellen für den BDC-Dienst in SharePoint in den folgenden Themen:

- [Vorgehensweise: Hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).
- [Vorgehensweise: Hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).
- [Vorgehensweise: Hinzufügen eine Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Siehe auch

[Entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
[erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
[BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md) 
 [ Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
