---
title: "Gewusst wie: Ausf&#252;hren eines Upgrades auf LocalDB oder Fortsetzen von SQL Server Express | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "LocalDB"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQLEXPRESS"
  - "Upgrade von SQLExpress auf SQLExpress"
  - "Upgrade auf LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Ausf&#252;hren eines Upgrades auf LocalDB oder Fortsetzen von SQL Server Express
In diesem Thema werden die Optionen für das Aktualisieren der Datenbankdatei \(.mdf\) nachdem Sie [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] installieren und enthält Anweisungen für die folgenden Aufgaben:  
  
-   Aktualisieren Sie eine Datenbankdatei, um LocalDB zu verwenden  
  
-   Aktualisieren Sie eine Datenbankdatei, um eine neuere Version von SQL Server Express zu verwenden  
  
-   Arbeiten mit einer Datenbankdatei in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] aber behalten Kompatibilität mit [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)] bei  
  
-   Bereitstellen von SQL Server Express das standardmäßige Datenbankmodul her  
  
 Sie können [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] verwenden, um ein Projekt zu öffnen, das eine Datenbankdatei \(.mdf\) enthält die erstellt wurde, indem Sie eine frühere Version von SQL Server Express verwendet.  jedoch um fortzufahren, um das Projekt in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] zu entwickeln, müssen Sie entweder haben, dass die Version von SQL Server Express installiert auf dem gleichen Computer als Visual Studio bearbeiten, oder Sie müssen die Datenbankdatei aktualisieren, um SQL Server Express LocalDB zu verwenden.  Wenn Sie die Datenbankdatei aktualisieren, sind Sie nicht in der Lage, auf sie mit früheren Versionen von SQL Server Express zuzugreifen.  
  
 Sie werden auch aufgefordert, eine Datenbankdatei zu aktualisieren, die erstellt wurde, indem Sie [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] verwendet, wenn die Version der Datei nicht mit der Instanz von SQL Server Express kompatibel ist, die gerade installiert ist.  Um das Problem zu beheben, fordert Visual Studio Sie auf die Datei zur späteren Version von SQL Server Express zu aktualisieren.  
  
> [!IMPORTANT]
>  Es wird empfohlen, die Datenbankdatei sichern, bevor Sie sie aktualisieren.  
  
 Bevor Sie eine Datenbank aktualisieren, sollten Sie die folgenden Kriterien berücksichtigen:  
  
-   Aktualisieren Sie nicht, wenn Sie am Projekt in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] arbeiten möchten.  
  
-   Aktualisieren Sie nicht, wenn die Anwendung in der Umgebung verwendet wird, die SQL Server Express LocalDB anstatt verwenden.  
  
-   Aktualisieren Sie nicht, wenn die Anwendung Remoteverbindungen verwendet LocalDB, da sie nicht akzeptiert.  
  
-   Aktualisieren Sie nicht, wenn die Anwendung für Internetinformationsdienste \(IIS\) beruht.  
  
-   Erwägen Sie, zu aktualisieren, wenn Sie Datenbankanwendungen in einer Sandkastenumgebung testen möchten, aber keine Datenbank verwalten möchten.  
  
### So fügen Sie eine Datenbankdatei aktualisieren, um LocalDB zu verwenden  
  
1.  In **Server\-Explorer** wählen Sie die Schaltfläche **Mit Datenbank verbinden** aus.  
  
2.  Im Dialogfeld **Verbindung hinzufügen** geben Sie die folgenden Informationen an:  
  
    -   **Datenquelle:** Microsoft SQL Server \(SqlClient\)  
  
    -   **Servername:** \(LocalDB\) \\ v11.0  
  
    -   **Datenbankdatei anhängen:** *Pfad*, wo *Pfad* der physische Pfad der primären MDF\-Datei ist.  
  
    -   **Logischer Name:** *Name*, wo *Name* der Name ist, den Sie der Datei verwenden möchten.  
  
3.  Klicken Sie auf die Schaltfläche **OK**.  
  
4.  Wenn Sie aufgefordert werden, wählen Sie die Schaltfläche **Ja**, um die Datei zu aktualisieren.  
  
 Die Datenbank wird aktualisiert, um LocalDB\-Datenbankmodul angefügt, und nicht mehr kompatibel mit [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)].  
  
 Sie können eine SQLExpress\-Verbindung auch ändern, um LocalDB zu verwenden, indem Sie das Kontextmenü für die Verbindung öffnen und dann **Verbindung ändern** auswählen.  In Dialogfeld **Verbindung ändern** ändern, Servername zu \(LocalDB\) \\ v11.0.  Im Dialogfeld **Erweiterte Eigenschaften** überprüfen Sie, ob **Benutzerinstanz** False festgelegt wird.  
  
### Um auf eine neuere Version von SQL Server Express aktualisieren  
  
1.  Im Kontextmenü für die Verbindung zur Datenbank, wählen Sie **Verbindung ändern** aus.  
  
2.  Im Dialogfeld **Verbindung ändern** wählen Sie die Schaltfläche **Erweitert** aus.  
  
3.  Im Dialogfeld **Erweiterte Eigenschaften** wählen Sie die Schaltfläche **OK** aus, ohne den Servernamen zu ändern.  
  
 Die Datenbankdatei wird aktualisiert, um die aktuelle Version von [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] übereinstimmt.  
  
### Um mit der Datenbank in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] arbeiten jedoch die Kompatibilität mit [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)] beibehalten  
  
1.  In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] öffnen Sie das Projekt, ohne es zu aktualisieren.  
  
    -   Um das Projekt auszuführen, wählen Sie die F5\-TASTE.  
  
    -   Um die Datenbank zu bearbeiten, öffnen Sie die MDF\-Datei in **Projektmappen\-Explorer**, und erweitern Sie den Knoten in **Server\-Explorer** mit der Datenbank arbeiten wie in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] ausgeführt haben.  
  
### Um die SQL Server Express das standardmäßige Datenbankmodul erstellen  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Tools**, **Optionen** aus.  
  
2.  Im Dialogfeld **Optionen** erweitern Sie die **Datentools** Optionen, und wählen Sie dann den Knoten **Datenverbindungen** aus.  
  
3.  Im **Name der SQL Server\-Instanz** Textfeld geben Sie den Namen der Instanz von SQL Server Express an, die Sie verwenden möchten.  Wenn die Instanz nicht vorhanden ist, geben Sie `. \ SQLEXPRESS` an.  
  
4.  Klicken Sie auf die Schaltfläche **OK**.  
  
 SQL Server Express ist das standardmäßige Datenbankmodul für Anwendungen.  
  
## Siehe auch  
 [Übersicht über lokale Daten](../data-tools/local-data-overview.md)   
 [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)