---
title: 'Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f2c851659d09cc118f8f54b6e82bb3b806d7e34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944284"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint

Mithilfe von Webparts können Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website direkt im Browser ändern. In dieser exemplarischen Vorgehensweise erfahren Sie, wie ein Webpart zu erstellen, indem Sie mit der **Webpart** Item-Vorlage in Visual Studio 2010.

Das Webpart zeigt Mitarbeiter in einem Datenraster an. Der Benutzer gibt den Speicherort der Datei an, die die Mitarbeiterdaten enthält. Außerdem kann der Benutzer das Datenraster filtern, damit nur Mitarbeiter, die Manager sind, in der Liste angezeigt werden.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Webparts mit Visual Studio **Webpart** Elementvorlage.

- Erstellen einer Eigenschaft, die vom Benutzer des Webparts festgelegt werden kann. Diese Eigenschaft gibt den Speicherort der Mitarbeiterdatendatei an.

- Rendern von Inhalt in einem Webpart durch Hinzufügen von Steuerelementen zur Webpart-Steuerelementauflistung.

- Erstellen ein neues Menüelement als bezeichnet ein *-Verb,* , das im Verbmenü des gerenderten Webparts angezeigt wird. Verben ermöglichen es dem Benutzer, die im Webpart angezeigten Daten zu ändern.

- Testen des Webparts in SharePoint.

    > [!NOTE]
    > Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- Visual Studio 2017 oder Azure DevOps-Dienste.

## <a name="create-an-empty-sharepoint-project"></a>Erstellen Sie ein leeres SharePoint-Projekt

Erstellen Sie zunächst ein leeres SharePoint-Projekt. Sie werden später ein Webpart zum Projekt hinzufügen, mit der **Webpart** Elementvorlage.

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der **als Administrator ausführen** Option.

2. Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt**.

3. In der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten unter der Sprache, die Sie verwenden möchten, und wählen Sie dann die **2010** Knoten.

4. In der **Vorlagen** Bereich wählen **SharePoint 2010-Projekt**, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.

5. Wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu akzeptieren.

## <a name="add-a-web-part-to-the-project"></a>Hinzufügen eines Webparts zum Projekt

Hinzufügen einer **Webpart** Elements zum Projekt. Die **Webpart** Element wird der Webpart-Codedatei hinzugefügt. Später fügen Sie der Codedatei für das Webpart Code hinzu, um den Inhalt des Webparts zu rendern.

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

2. In der **neues Element hinzufügen** Dialogfeld die **installierte Vorlagen** Bereich erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

3. Wählen Sie in der Liste der SharePoint-Vorlagen, die **Webpart** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Die **Webpart** Element angezeigt wird, im **Projektmappen-Explorer**.

## <a name="rendering-content-in-the-web-part"></a>Rendern von Inhalt im Webpart

Sie können angeben, welche Steuerelemente im Webpart angezeigt werden, indem Sie diese der Steuerelementauflistung der Webpartklasse hinzufügen.

1. In **Projektmappen-Explorer**öffnen *WebPart1.vb* (in Visual Basic) oder *WebPart1.cs* (in C# -Referenz).

     Die Codedatei für das Webpart wird im Code-Editor geöffnet.

2. Fügen Sie am Anfang der Codedatei für das Webpart die folgenden Anweisungen hinzu.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Fügen Sie der `WebPart1` -Klasse folgenden Code hinzu. Mit diesem Code werden die folgenden Felder deklariert:

   - Ein Datenraster, um Mitarbeiter im Webpart anzuzeigen.

   - Text, der auf dem Steuerelement angezeigt wird, das zum Filtern des Datenrasters verwendet wird.

   - Eine Bezeichnung, die einen Fehler anzeigt, wenn das Datenraster keine Daten anzeigen kann.

   - Eine Zeichenfolge, die den Pfad zur Mitarbeiterdatendatei enthält.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Fügen Sie der `WebPart1` -Klasse folgenden Code hinzu. In diesem Code wird dem Webpart eine benutzerdefinierte Eigenschaft mit dem Namen `DataFilePath` hinzugefügt. Eine benutzerdefinierte Eigenschaft ist eine Eigenschaft, die vom Benutzer in SharePoint festgelegt werden kann. Diese Eigenschaft ruft den Speicherort einer XML-Datendatei ab, die zum Auffüllen des Datenrasters verwendet wird, und legt diesen Speicherort fest.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Ersetzen Sie die `CreateChildControls` -Methode durch folgenden Code: Mit diesem Code werden die folgenden Aufgaben ausgeführt:

   - Fügt das Datenraster und die Bezeichnung hinzu, die Sie im vorherigen Schritt deklariert haben.

   - Bindet das Datenraster an eine XML-Datei, die Mitarbeiterdaten enthält.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Fügen Sie der `WebPart1` -Klasse die folgende Methode hinzu. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

   - Erstellt ein Verb, das im Verbmenü des gerenderten Webparts angezeigt wird.

   - Behandelt das Ereignis, das ausgelöst wird, wenn der Benutzer im Verbmenü das Verb auswählt. In diesem Code wird die Liste der Mitarbeiter gefiltert, die im Datenraster angezeigt wird.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testen Sie das Webpart

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt. Sie können das Webpart jeder Webpartseite hinzufügen.

1. Fügen Sie folgendes XML in eine Editor-Datei ein. Diese XML-Datei enthält die Beispieldaten, die im Webpart angezeigt werden.

    ```xml
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

2. Wählen Sie im Editor auf der Menüleiste **Datei** > **speichern**.

3. In der **speichern** Dialogfeld die **Dateityp** wählen **alle Dateien**.

4. In der **Dateiname** geben **data.xml**.

5. Wählen Sie einen Ordner mit den **Ordner durchsuchen** Schaltfläche, und wählen Sie dann die **speichern** Schaltfläche.

6. Wählen Sie in Visual Studio die **F5** Schlüssel.

     Die SharePoint-Website wird geöffnet.

7. Auf der **Websiteaktionen** Menü wählen **Weitere Optionen**.

8. In der **erstellen** Seite die **Webpartseite** geben, und wählen Sie dann die **erstellen** Schaltfläche.

9. In der **neue Webpartseite** Seite, nennen Sie die Seite **SampleWebPartPage.aspx**, und wählen Sie dann die **erstellen** Schaltfläche.

     Die Webpartseite wird angezeigt.

10. Wählen Sie eine Zone auf der Webpartseite aus.

11. Klicken Sie oben auf der Seite auf die **einfügen** Registerkarte, und wählen Sie dann die **Webpart** Schaltfläche.

12. In der **Kategorien** Bereich Wählen Sie die **benutzerdefinierte** Ordner, wählen Sie die **WebPart1** -Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Das Webpart wird auf der Seite angezeigt.

## <a name="test-the-custom-property"></a>Testen der benutzerdefinierten Eigenschaft

Um das im Webpart angezeigte Datenraster aufzufüllen, geben Sie den Pfad der XML-Datei an, die Daten zu jedem Mitarbeiter enthält.

1. Wählen Sie den Pfeil, der auf der rechten Seite des Webparts angezeigt wird, und wählen Sie dann **Webpart bearbeiten** aus dem Menü, das angezeigt wird.

     Ein Bereich, der Eigenschaften für das Webpart enthält, wird auf der rechten Seite der Seite angezeigt.

2. Erweitern Sie im Bereich der **Sonstiges** Knoten, geben Sie den Pfad der XML-Datei, die Sie zuvor erstellt haben, wählen Sie die **übernehmen** Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.

     Überprüfen Sie, ob eine Liste von Mitarbeitern im Webpart angezeigt wird.

## <a name="test-the-web-part-verb"></a>Testen des Webpartverbs

Zeigen Sie Mitarbeiter an, die keine Manager sind, und blenden Sie diese aus, indem Sie auf ein Element klicken, das im Verbmenü des Webparts angezeigt wird.

1. Wählen Sie den Pfeil, der auf der rechten Seite des Webparts angezeigt wird, und wählen Sie dann **nur Manager anzeigen** aus dem Menü, das angezeigt wird.

     Nur Mitarbeiter, die Manager sind, werden im Webpart angezeigt.

2. Wählen Sie den Pfeil erneut aus, und wählen Sie dann **Show All Employees** aus dem Menü, das angezeigt wird.

     Alle Mitarbeiter werden im Webpart angezeigt.

## <a name="see-also"></a>Siehe auch

[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Vorgehensweise: Erstellen Sie einen SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
