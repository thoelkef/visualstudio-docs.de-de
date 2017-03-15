---
title: "Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Verbinden mit Datenbanken"
  - "Datenquellen, Erstellen"
  - "Datenquellen, Datenbanken"
  - "Datenbankverbindungen"
  - "Datenbanken, Verbinden mit"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank
Sie können die Anwendung mithilfe von Visual Studio mit einer Datenbank verbinden.  Nach dem Erstellen der Datenverbindung erstellt Visual Studio ein Datenmodell, mit dem die Anwendung mit den Daten in der Datenbank interagiert.  Die Objekte im Datenmodell werden im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) angezeigt.  Sie können dann die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf die Designoberfläche ziehen.  Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Dieses Thema enthält Anweisungen zum Herstellen einer Verbindung mit einer Datenbank und Erstellen der folgenden Datenmodelltypen:  
  
-   DataSet  
  
-   Entity Data Model \(EDM\)  
  
> [!NOTE]
>  Sie können mit Visual Studio LINQ to SQL\-Klassen aus einer Datenbank erstellen.  LINQ to SQL\-Klassen werden jedoch nicht im **Datenquellenfenster** angezeigt und können daher nicht direkt in einen Designer gezogen werden, um datengebundene Steuerelemente zu erstellen.  Weitere Informationen zum Erstellen von LINQ to SQL\-Klassen aus einer Datenbank finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL\-Klassen, die Tabellen und Ansichten \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> Herstellen einer Verbindung mit einer Datenbank und Erstellen eines Datasets  
 Wenn Sie ein auf einer Datenbank basiertes Dataset erstellen, erstellt Visual Studio einen Satz von Klassen, die eine programmierbare Ansicht der Daten darstellen.  Die Hauptklasse wird als *typisiertes Dataset* bezeichnet.  Das typisierte Dataset enthält Datentabellenobjekte, die Tabellen in der Datenbank darstellen.  Weitere Informationen zu typisierten Datasets finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Nachdem Sie ein Dataset erstellt haben, können Sie datengebundene WPF\- oder Windows Forms\-Steuerelemente erstellen, indem Sie Datasetobjekte aus dem Datenquellenfenster in den WPF\- oder Windows Forms\-Designer ziehen.  
  
#### So verbinden Sie die Anwendung und erstellen ein Dataset  
  
1.  Öffnen Sie ein vorhandenes Projekt in Visual Studio, oder erstellen Sie ein neues Projekt.  
  
2.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Wählen Sie ein Datenbankmodell aus** die Option **DataSet** aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** eine Datenverbindung in der Liste der verfügbaren Verbindungen aus, und klicken Sie anschließend auf **Weiter**.  
  
     Wenn die gewünschte Datenverbindung nicht verfügbar ist, erstellen Sie eine neue Verbindung, indem Sie die Schritte in [Erstellen von Datenbankverbindungen](#CreatingDataConnection) ausführen.  
  
6.  Deaktivieren Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** optional das Kontrollkästchen **Ja, Verbindung speichern unter**, wenn Sie die Verbindungszeichenfolge in der kompilierten Anwendung direkt speichern möchten.  Standardmäßig wird die Verbindung in der Anwendungskonfigurationsdatei gespeichert.  Weitere Informationen finden Sie unter [Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
7.  Wählen Sie auf der Seite **Datenbankobjekte auswählen** die Datenbankobjekte aus, die Sie in der Anwendung verwenden möchten.  Sie können auch den standardmäßigen **DataSet\-Namen** ersetzen.  
  
8.  Klicken Sie auf **Fertig stellen**.  Das soeben erstellte Dataset ist jetzt im **Datenquellenfenster** verfügbar.  
  
    > [!NOTE]
    >  Wenn das **Datenquellenfenster** nicht geöffnet ist, klicken Sie zum Öffnen des Fensters im Menü **Daten** auf **Datenquellen anzeigen**.  
  
9. Sie können jetzt Elemente aus dem **Datenquellenfenster** in den WPF\-Designer, den Windows Forms\-Designer oder den [Component Designer](../Topic/Component%20Designer.md) ziehen, um datengebundene Steuerelemente zu erstellen.  Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Herstellen einer Verbindung mit einer Datenbank und Erstellen eines Entity Data Models  
 Wenn Sie ein auf einer Datenbank basiertes Entity Data Model erstellen, erstellt Visual Studio einen Satz von Klassen, die eine programmierbare Ansicht der Daten darstellen.  Weitere Informationen über Entity Data Models und ADO.NET Entity Framework finden Sie unter [Übersicht über das Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
 Nachdem Sie ein Entity Data Model erstellt haben, können Sie datengebundene WPF\-Steuerelemente erstellen, indem Sie Entitätsobjekte aus dem Datenquellenfenster in den WPF\-Designer ziehen.  
  
#### So stellen Sie eine Verbindung zwischen der Anwendung und einer Datenbank her und erstellen ein Entity Data Model  
  
1.  Öffnen Sie ein vorhandenes Projekt in Visual Studio, oder erstellen Sie ein neues Projekt.  
  
2.  Folgen Sie den Anweisungen im **Assistent für Entity Data Model**, um eine Verbindung mit einer Datenbank herzustellen und den Inhalt des Modells anzugeben.  Weitere Informationen finden Sie unter [How to: Create a New .edmx File](http://msdn.microsoft.com/de-de/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Nachdem Sie den **Assistent für Entity Data Model** abgeschlossen haben, wird das erstellte Entity Data Model im Entity Data Model\-Designer geöffnet, und die Datenobjekte sind im **Datenquellenfenster** verfügbar.  
  
    > [!NOTE]
    >  Wenn das **Datenquellenfenster** nicht geöffnet ist, klicken Sie zum Öffnen des Fensters im Menü **Daten** auf **Datenquellen anzeigen**.  
  
4.  Wenn der WPF\-Designer geöffnet ist, können Sie Elemente aus dem **Datenquellenfenster** in den Designer ziehen, um Steuerelemente zu erstellen, die an das Entity Data Model gebunden sind.  Weitere Informationen finden Sie unter [Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Wenn der Windows Forms\-Designer geöffnet ist, können Sie keine Elemente aus den **Datenquellen** in den Designer ziehen.  Zum Erstellen von an das Entity Data Model gebundenen Steuerelementen erstellen Sie das Projekt, fügen Sie eine neue auf dem Entity Data Model basierte Objektdatenquelle hinzu und ziehen anschließend die Objekte in den Designer.  
  
##  <a name="CreatingDataConnection"></a> Erstellen von Datenbankverbindungen  
 Wenn Sie den **Assistent zum Konfigurieren von Datenquellen** oder den **Assistent für Entity Data Model** verwenden, müssen Sie eine Verbindung zur Datenbank angeben, die Sie verwenden möchten.  Wenn Sie noch keine Verbindung zur Datenbank hergestellt haben, führen Sie die folgenden Schritte aus, um die Verbindung zu herzustellen.  
  
 Diese Anweisungen gehen davon aus, dass der **Assistent zum Konfigurieren von Datenquellen** oder der **Assistent für Entity Data Model**, wie unter [Herstellen einer Verbindung mit einer Datenbank und Erstellen eines Datasets](#dataset) und [Herstellen einer Verbindung mit einer Datenbank und Erstellen eines Entity Data Models](#edm) beschrieben, bereits geöffnet ist.  
  
#### So erstellen Sie eine Datenbankverbindung  
  
1.  Klicken Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** des **Assistenten zum Konfigurieren von Datenquellen** oder des **Assistenten für Entity Data Model** auf **Neue Verbindung**.  
  
     Eine der folgenden Aktionen wird ausgeführt:  
  
    -   Wenn Sie bereits eine Datenverbindung in Visual Studio erstellt haben, wird das Dialogfeld **Verbindung hinzufügen** geöffnet.  
  
    -   Wenn dies die erste in Visual Studio erstellte Datenverbindung ist, wird das Dialogfeld **Datenquelle auswählen** angezeigt.  Wählen Sie den Typ der Datenbank aus, mit dem Sie eine Verbindung herstellen möchten, und klicken Sie dann auf **OK**, um das Dialogfeld **Verbindung hinzufügen** anzuzeigen.  
  
2.  Geben Sie im Dialogfeld **Verbindung hinzufügen** die erforderlichen Informationen ein.  Das Dialogfeld **Verbindung hinzufügen** variiert je nach Typ des Datenanbieters.  
  
    > [!NOTE]
    >  Wenn die ausgewählte **Datenquelle** im Dialogfeld **Verbindung hinzufügen** nicht die Datenquelle ist, zu der Sie eine Verbindung herstellen möchten, klicken Sie auf **Ändern**, um das Dialogfeld **Datenquelle wechseln** zu öffnen, und wählen Sie eine andere Datenquelle aus.  
  
3.  Klicken Sie im Dialogfeld **Verbindung hinzufügen** auf **OK**.  
  
     Sie kehren anschließend zur Seite **Wählen Sie Ihre Datenverbindung aus** des **Assistenten zum Konfigurieren von Datenquellen** oder des **Assistenten für Entity Data Model** zurück.  
  
4.  Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** die neue Datenverbindung aus, und klicken Sie dann auf **Weiter**.  
  
5.  Führen Sie die verbleibenden Schritte im **Assistent zum Konfigurieren von Datenquellen** oder dem **Assistent für Entity Data Model** aus.  
  
## .NET Framework-Sicherheit  
 Das Speichern vertraulicher Informationen \(z. B. ein Kennwort\) kann sich auf die Sicherheit der Anwendung auswirken.  Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows\-Authentifizierung \(wird auch als integrierte Sicherheit bezeichnet\) sicherer steuern.  Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](../Topic/Protecting%20Connection%20Information.md).  
  
## Siehe auch  
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Aufbauen der Verbindung zu einer Datenquelle](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)