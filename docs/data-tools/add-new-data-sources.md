---
title: "&#220;bersicht &#252;ber Datenquellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Datenquellen"
  - "Datenquellen"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#220;bersicht &#252;ber Datenquellen
Datenquellen stellen die für die Anwendung verfügbaren Daten dar.  Genauer gesagt handelt es sich bei Datenquellen um die Daten, mit denen Sie in der Anwendung arbeiten möchten.  Datenquellen können aus Datenbanken \(einschließlich lokaler Datenbankdateien\), Diensten und Objekten abgerufen werden.  
  
 Die Datenquellen, die Sie dem Projekt hinzufügen, werden im Datenquellenfenster angezeigt.  In vielen Fällen können Sie Datenquellen in die Windows Forms\-, WPF\- und Silverlight\-Designer ziehen, um Steuerelemente zu erstellen, die an die zugrunde liegenden Daten gebunden werden.  Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Visual Studio enthält Tools zum Erstellen und Bearbeiten von Datenquellen in der Anwendung.  Datenquellen in Visual Studio\-Projekten werden als Entity Data Models, Datasets, von einem Dienst zurückgegebene Proxyobjekte oder als andere Objekttypen dargestellt, und zwar abhängig von den Objekten, die vom zugrunde liegenden Datenspeicher zurückgegeben werden.  
  
 Sie können Datenquellen mit dem **Assistent zum Konfigurieren von Datenquellen** erstellen und bearbeiten.  
  
## Aus Datenbanken erstellte Datenquellen  
 Sie können eine Datenquelle aus einer Datenbank erstellen, indem Sie den **Assistenten zum Konfigurieren von Datenquellen** ausführen und den Datenquellentyp **Datenbank** auswählen.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
 Wenn Sie eine Datenquelle aus einer Datenbank erstellen, generiert Visual Studio ein *Datenmodell* und fügt es dem Projekt hinzu.  Ein Datenmodell ist eine stark typisierte, programmierbare Ansicht der zugrunde liegenden Daten in der Datenbank.  Sie können die folgenden Typen von Datenmodellen mithilfe von Visual Studio erstellen:  
  
-   Ein konzeptionelles Modell basiert auf dem [Entity Data Model](../Topic/Entity%20Data%20Model.md).  Dieser Typ von Modell kann vom Entity Framework oder von WCF Data Services verwendet werden.  Weitere Informationen finden Sie unter [Übersicht über das Entity Framework](../Topic/Entity%20Framework%20Overview.md) und [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).  
  
-   Typisiertes Dataset.  Weitere Informationen finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   LINQ to SQL\-Klassen.  Weitere Informationen finden Sie unter [LINQ to SQL](../Topic/LINQ%20to%20SQL.md).  
  
    > [!NOTE]
    >  Im Gegensatz zu Datasets und konzeptionellen Modellen, die auf dem Entity Data Model basieren, können LINQ to SQL\-Klassen nicht mit dem **Assistenten zum Konfigurieren von Datenquellen** erstellt werden.  Sie werden auch nicht im Datenquellenfenster angezeigt und können daher nicht in einen Designer gezogen werden, um datengebundene Steuerelemente zu erstellen.  Sie können jedoch eine Objektdatenquelle erstellen, die auf LINQ to SQL\-Klassen basiert und diese Objekte in den Designer ziehen.  Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL\-Klassen, die Tabellen und Ansichten \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
### Aus lokalen Datenbankdateien erstellte Datenquellen  
 Sie können auch Datenquellen aus den folgenden Datenbankdateitypen erstellen: Access \(MDB\-Dateien\), SQL Server Express LocalDB \(MDF\-Dateien\) und SQL Server Express \(MDF\-Dateien\).  Wenn Sie Datenquellen aus diesen Datenbankdateien erstellen, können Sie dem Projekt direkt die Datenbankdateien hinzufügen.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Übersicht über lokale Daten](../data-tools/local-data-overview.md)  
  
-   [Gewusst wie: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## Aus Diensten erstellte Datenquellen  
 Sie können eine Datenquelle mit einem Dienst erstellen, indem Sie den **Assistenten zum Konfigurieren von Datenquellen** ausführen und den Datenquellentyp **Dienst** auswählen.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
 Wenn Sie eine Datenquelle mit einem Dienst erstellen, fügt Visual Studio einen Dienstverweis auf das Projekt hinzu.  Visual Studio erstellt auch Proxyobjekte, die den Objekten entsprechen, die vom Dienst zurückgegeben werden.  Zum Beispiel wird ein Dienst, der ein Dataset zurückgibt, im Projekt als Dataset dargestellt. Ein Dienst, der einen bestimmten Typ zurückgibt, wird in dem Projekt als der zurückgegebene Typ dargestellt.  
  
 Sie können eine Datenquelle mit den folgenden Diensttypen erstellen:  
  
-   WCF Data Services.  Weitere Informationen finden Sie unter [Übersicht](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Windows Communication Foundation \(WCF\)\-Dienste.  Weitere Informationen finden Sie unter [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Webdienste.  Weitere Informationen finden Sie unter [Not in Build: Introduction to Programming Web Services in Managed Code](http://msdn.microsoft.com/de-de/bd8861f3-39e1-4c06-995e-677e007eb961).  
  
    > [!NOTE]
    >  Die im Datenquellenfenster angezeigten Elemente hängen von den vom Dienst zurückgegebenen Daten ab.  Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann.  Wenn der Dienst beispielsweise ein nicht typisiertes Dataset zurückgibt, werden beim Beenden des Assistenten im Datenquellenfenster keine Elemente angezeigt.  Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen und der Assistent daher nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.  
  
## Aus Objekten erstellte Datenquellen  
 Sie können eine Datenquelle mit jedem Objekt erstellen, das mindestens eine öffentliche Eigenschaft durch Ausführen des **Assistenten zum Konfigurieren von Datenquellen** und anschließendes Auswählen des Datenquellentyps **Objekt** verfügbar macht.  Alle öffentlichen Eigenschaften eines Objekts werden im Datenquellenfenster angezeigt.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Weitere Informationen zum Binden an Objekte finden Sie unter [Objektbindung in Visual Studio](../data-tools/bind-objects-in-visual-studio.md).  
  
## Aus SharePoint\-Listen erstellte Datenquellen  
 Sie können eine Datenquelle aus einer SharePoint\-Liste erstellen, indem Sie den **Assistenten zum Konfigurieren von Datenquellen** ausführen und den Datenquellentyp **SharePoint** auswählen.  SharePoint macht Daten über [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] verfügbar, sodass die Erstellung einer SharePoint\-Datenquelle dem Erstellen einer Datenquelle mit einem Dienst entspricht.  Durch Auswahl des **SharePoint**\-Elements im **Assistenten zum Konfigurieren von Datenquellen** wird das Dialogfeld **Dienstverweis hinzufügen** geöffnet, in dem Sie durch Zeigen auf den SharePoint\-Server eine Verbindung mit dem SharePoint\-Datendienst herstellen.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Siehe auch  
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)