---
title: "Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "System.Data.SqlClient.SqlConnection"
  - "System.Data.Odbc.OdbcConnection"
  - "System.Data.OleDb.OleDbConnection"
  - "System.Data.OracleClient.OracleConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Verbinden mit Datenbanken, ADO.NET-Verbindungen"
  - "Verbindungsobjekte"
  - "Verbindungsobjekte, Tools für den Umgang"
  - "Verbindungsobjekte, Typen"
  - "Verbindungspooling, ADO.NET-Verbindungen"
  - "Verbindungszeichenfolgen [Visual Studio], ADO.NET"
  - "Verbindungen, Informationen über Verbindungen"
  - "Verbindungen, Entwurfszeit"
  - "Daten [Visual Studio], Verbindung herstellen"
  - "Datenadapter, Verbindungen"
  - "Datenbankverbindungen [Visual Studio], ADO.NET"
  - "Datenbanken [Visual Studio], Verbinden mit"
  - "Entwurfszeitverbindungen"
  - "Dynamische Eigenschaften, ADO.NET-Verbindungen"
  - "OleDbConnection-Klasse, ADO.NET-Verbindungsobjekte"
  - "SqlConnection-Klasse, ADO.NET-Verbindungsobjekte"
  - "TableAdapters, Verbindungen"
  - "Transaktionen, ADO.NET"
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet Tools, mit der Sie Ihre Anwendung mit Daten aus vielen unterschiedlichen Quellen wie Datenbanken, Webdiensten und Objekten verbinden können.  Wenn Sie Datenentwurfstools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden, müssen Sie häufig nicht explizit ein Datenverbindungsobjekt für das Formular oder die Komponente erstellen.  Das Verbindungsobjekt wird typischerweise erstellt, wenn Sie einen der Daten\-Assistenten durchlaufen haben oder Datenobjekte auf das Formular ziehen.  Um die Anwendung mit Daten aus einer Datenbank, einem Webdienst oder Objekt zu verbinden, führen Sie [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) aus, indem Sie **Neue Datenquelle hinzufügen** aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auswählen.  
  
 Das folgende Diagramm zeigt den standardmäßigen Ablauf der Vorgänge beim Verbinden von Daten mittels der Durchführung einer TableAdapter\-Abfrage für das Abrufen von Daten und deren Anzeige im Formular in einer Windows\-Anwendung.  
  
 ![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 In manchen Situationen ist es praktisch, ein Verbindungsobjekt ohne die Unterstützung durch irgendein Datenentwurfstool zu erstellen.  Informationen zum Erstellen programmgesteuerter Verbindungen finden Sie unter [Aufbauen der Verbindung zu einer Datenquelle](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md).  
  
> [!NOTE]
>  Informationen zur Verbindung von Webanwendungen mit Daten finden Sie unter [ASP.NET Data Access Content Map](http://msdn.microsoft.com/de-de/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## Exemplarische Vorgehensweisen für das Verbinden von Windows Forms\-Anwendungen mit Daten  
 Die folgenden exemplarischen Vorgehensweisen enthalten Vorgehensweisen für das Verbinden von Daten mit Windows Forms\-Anwendungen:  
  
-   [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Datenbank \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)  
  
-   [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Webdienst \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Web%20Service%20\(Windows%20Forms\).md)  
  
-   [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in Objekten \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)  
  
-   [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Access\-Datenbank \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## Verbindungen erstellen  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden Verbindungen mithilfe des Dialogfelds **Verbindung hinzufügen\/ändern** konfiguriert.  Das Dialogfeld **Verbindung hinzufügen** wird angezeigt, wenn Sie Verbindungen in einem der Daten\-Assistenten bearbeiten oder erstellen, in [Server\-Explorer\/Datenbank\-Explorer](../Topic/Server%20Explorer.md) oder beim Bearbeiten von Verbindungseigenschaften im Fenster **Eigenschaften**.  
  
 Datenverbindungen werden automatisch konfiguriert, wenn Sie eine der folgenden Aktionen durchführen.  
  
|Aktion|Beschreibung|  
|------------|------------------|  
|Ausführen von [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).|Verbindungen werden konfiguriert, wenn der Datenbankpfad im **Assistenten zum Konfigurieren von Datenquellen** ausgewählt wurde.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Ausführen von [TableAdapter\-Konfigurations\-Assistent](../Topic/TableAdapter%20Configuration%20Wizard.md).|Verbindungen werden im **TableAdapter\-Konfigurations\-Assistent** erstellt.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Ausführen von [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md).|Verbindungen werden im **Konfigurations\-Assistent für TableAdapter\-Abfragen** erstellt.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).|  
|Ziehen Sie Elemente vom [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auf ein Formular oder den [Component Designer](../Topic/Component%20Designer.md).|Verbindungsobjekte werden erstellt, wenn man Objekte vom **Datenquellenfenster** auf den **Windows Forms\-Designer** oder den **Komponenten\-Designer** zieht.  Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Hinzufügen einer neuen Datenverbindung zum [Server\-Explorer\/Datenbank\-Explorer](../Topic/Server%20Explorer.md).|Datenverbindungen im **Server\-Explorer\/Datenbank\-Explorer** werden in der Liste der verfügbaren Verbindungen im Daten\-Assistenten angezeigt|  
  
## Verbindungszeichenfolgen  
 Verbindungszeichenfolgen können in der kompilierten Anwendung oder in einer Anwendungskonfigurationsdatei gespeichert werden.  Weitere Informationen finden Sie unter [Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
## Verbindungsinformationen und Sicherheit  
 Weil das Öffnen einer Verbindung den Zugriff auf eine wichtige Ressource – eine Datenbank – beinhaltet, treten häufig Sicherheitsprobleme beim Konfigurieren und Arbeiten mit einer Verbindung auf.  
  
 Wie Sie die Anwendung und ihren Zugriff auf die Datenquelle sichern, hängt von der Architektur des Systems ab.  In einer webbasierten Anwendung beispielsweise erhalten Benutzer üblicherweise anonymen Zugriff auf die Internetinformationsdienste \(IIS\) und geben deshalb keine Sicherheitsanmeldeinformationen an.  In diesem Fall unterhält die Anwendung eigene Anmeldeinformationen und verwendet diese statt irgendwelcher spezifischer Benutzerinformationen für die Verbindung und den Zugriff auf die Datenbank.  
  
> [!IMPORTANT]
>  Das Speichern von Informationen über Verbindungszeichenfolgen wie z. B. das Kennwort kann die Sicherheit einer Anwendung beeinträchtigen.  Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank.  Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](../Topic/Protecting%20Connection%20Information.md).  
  
 Im Intranet oder in Anwendungen mit mehreren Ebenen können Sie die integrierte Sicherheitsoption nutzen, die von Windows, IIS und SQL Server bereitgestellt wird.  In diesem Modell werden die Authentifizierungsanmeldedaten für das lokale Netzwerk ebenfalls für den Zugriff auf Datenbankressourcen verwendet und in der Verbindungszeichenfolge kein ausdrücklicher Benutzername oder Kennwort gebraucht.  Typischerweise werden Berechtigungen auf dem Datenbankservercomputer mithilfe von Gruppen ermöglicht, sodass man keine individuelle Berechtigung für jeden Benutzer braucht, der auf die Datenbank zuzugreifen kann.  In diesem Modell müssen überhaupt keine Anmeldeinformationen gespeichert werden und es sind keine zusätzlichen Schritte erforderlich, um die Informationen der Verbindungszeichenfolge zu schützen.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Sichern von ADO.NET\-Anwendungen](../Topic/Securing%20ADO.NET%20Applications.md)  
  
-   [Mehr Sicherheit beim Datei\- und Datenzugriff in Windows Forms](../Topic/More%20Secure%20File%20and%20Data%20Access%20in%20Windows%20Forms.md)  
  
## Entwurfszeitverbindungen in Server\-Explorer\/Datenbank\-Explorer  
 **Server\-Explorer\/Datenbank\-Explorer** bietet eine Möglichkeit zum Erstellen von Entwurfszeitverbindungen zu Datenquellen.  Damit können Sie verfügbare Datenquellen durchsuchen; Informationen über die Tabellen, Spalten und andere Elemente anzeigen, die sie enthalten; und Datenbankelemente bearbeiten und erstellen.  
  
 Die Anwendung verwendet nicht direkt die Verbindungen, die in **Server\-Explorer\/Datenbank\-Explorer** verfügbar sind.  Diese Verbindungen werden von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für die Arbeit an der Datenbank zur Entwurfszeit verwendet.  Weitere Informationen finden Sie unter [Visual Database Tools](http://msdn.microsoft.com/de-de/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Sie verwenden zum Beispiel zur Entwurfszeit **Server\-Explorer\/Datenbank\-Explorer**, um eine Verbindung zu einer Datenbank aufzubauen.  Wenn Sie später ein Formular entwerfen, können Sie die Datenbank durchsuchen, Spalten daraus auswählen und diese auf den [DataSet\-Designer](../data-tools/creating-and-editing-typed-datasets.md) ziehen.  Damit wird ein [TableAdapter](../data-tools/tableadapter-overview.md) im Dataset erstellt.  Außerdem wird ein neues Verbindungsobjekt erstellt, das Teil des neuen TableAdapters ist.  
  
 Informationen über Entwurfszeitverbindungen werden unabhängig von einem speziellen Projekt oder einer bestimmten Lösung auf Ihrem lokalen Computer gespeichert.  Deshalb wird, nachdem Sie einmal eine Entwurfszeitverbindung bei der Arbeit in einer Anwendung aufgebaut haben, diese immer dann in **Server\-Explorer\/Datenbank\-Explorer** angezeigt, wenn Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arbeiten, solange der Server verfügbar ist, auf den die Verbindung zeigt.  Weitere Informationen finden Sie unter [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/de-de/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../data-tools/includes/sqlobjectexplorer_md.md)]  
  
## Siehe auch  
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer Datenbank \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/de-de/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)