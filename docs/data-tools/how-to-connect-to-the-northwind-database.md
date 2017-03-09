---
title: "Gewusst wie: Verbinden mit der Datenbank Northwind | Microsoft Docs"
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
  - "Verbindungen [Visual Studio], Northwind-Datenbank"
  - "Northwind-Beispieldatenbank"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Verbinden mit der Datenbank Northwind
Während Sie das Erstellen von Datenbankanwendungen mithilfe von Visual Studio lernen, müssen Sie eine Verbindung mit der Datenbank Northwind herstellen, um vielen der Beispielen in der Dokumentation für dieses Produkt zu folgen.  Je nachdem, welchem Beispiel Sie folgen, müssen Sie eine Verbindung entweder mit einer Datenbank in SQL Server oder in einer Datenbankdatei, beispielsweise in einer für Microsoft Access oder SQL Server, herstellen.  
  
## Erstellen von Datenverbindungen mit der Northwind\-Datenbank  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So erstellen Sie eine Datenverbindung mit der Northwind\-Datenbank \(SQL Server\)  
  
1.  Wählen Sie im Menü **AnsichtServer\-Explorer**\/**Datenbank\-Explorer** aus.  
  
2.  Öffnen Sie im **Server\-Explorer**\/**Datenbank\-Explorer** das Kontextmenü für **Datenverbindungen** und wählen Sie **Verbindung hinzufügen** aus.  
  
     Nachdem Sie **Verbindung hinzufügen** ausgewählt haben, wird entweder das Dialogfeld **Datenquelle auswählen** oder das Dialogfeld **Verbindung hinzufügen** angezeigt.  
  
3.  Wenn das Dialogfeld **Datenquelle auswählen** angezeigt wird, wählen Sie **Microsoft SQL Server** und anschließend **OK** aus.  
  
     Wenn das Dialogfeld **Verbindung hinzufügen** angezeigt wird und die **Datenquelle** nicht **Microsoft SQL Server \(SqlClient\)** lautet, wählen Sie die Schaltfläche **Ändern** aus, um das Dialogfeld **Datenquelle wechseln** zu öffnen. Wählen Sie dort **Microsoft SQL Server** und anschließend die Schaltfläche **OK** aus.  
  
4.  Geben Sie in der Liste **Servername** den Namen des Servers an, auf dem sich die Datenbank Northwind befindet.  
  
5.  Wählen Sie \(je nach den Anforderungen Ihrer Version von SQL Server und der Datenbank Northwind\) entweder **Windows\-Authentifizierung verwenden** oder **SQL Server\-Authentifizierung verwenden** aus und geben Sie einen Benutzernamen und ein Kennwort zur Anmeldung an dem Computer ein, auf dem SQL Server ausgeführt wird.  
  
6.  Wählen Sie in der Liste **Datenbanknamen eingeben oder auswählen** die Datenbank Northwind aus.  
  
7.  Wählen Sie **Testverbindung** aus, um die Verbindung mit der Datenbank Northwind zu überprüfen.  
  
8.  Klicken Sie auf **OK**.  
  
     Dem **Server\-Explorer**\/**Datenbank\-Explorer** wird eine Datenverbindung zur Northwind\-Datenbank hinzugefügt.  
  
 Außer dem Herstellen einer Verbindung mit einer Remoteinstanz einer SQL Server\-Datenbank können Sie auch eine Verbindung direkt zu den eigentlichen Dateien herstellen, in denen sich die Datenbank befindet.  Auf diese Weise können Sie die Datenbankdateien direkt einem Projekt hinzufügen, wo sie dann als Teil der Anwendung bereitgestellt werden können.  Derzeit werden die folgenden lokalen Datenbankdateien unterstützt: SQL Server Compact\-Datenbankdateien \(.sdf\), [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]\- und SQL Server Express\-Datenbankdateien \(.mdf\) sowie Microsoft Access\-Datenbankdateien \(.mdb oder .accdb\).  
  
#### So erstellen Sie eine Datenverbindung zur Datenbank Northwind – MDF\-Datenbankdatei \(SQL Server\)  
  
1.  Wählen Sie im Menü **AnsichtServer\-Explorer**\/**Datenbank\-Explorer** aus.  
  
2.  Öffnen Sie im **Server\-Explorer**\/**Datenbank\-Explorer** das Kontextmenü für **Datenverbindungen** und wählen Sie **Verbindung hinzufügen** aus.  
  
     Nachdem Sie **Verbindung hinzufügen** ausgewählt haben, wird entweder das Dialogfeld **Verbindung hinzufügen** oder das Dialogfeld **Datenquelle auswählen** angezeigt.  
  
3.  Wenn das Dialogfeld **Datenquelle auswählen** angezeigt wird, wählen Sie **Microsoft SQL Server\-Datenbankdatei** und anschließend **OK** aus.  
  
4.  Wenn das Dialogfeld **Verbindung hinzufügen** angezeigt wird, müssen Sie überprüfen, dass die **Datenquelle** auf **Microsoft SQL Server\-Datenbankdatei \(SqlClient\)** eingestellt ist.  Wenn diese nicht auf **Microsoft SQL Server\-Datenbankdatei \(SqlClient\)** festgelegt ist, wählen Sie **Ändern** aus, um das Dialogfeld **Datenquelle wechseln** zu öffnen. Wählen Sie dort **Microsoft SQL Server\-Datenbankdatei** und anschließend die Schaltfläche **OK** aus.  
  
5.  Wählen Sie **Durchsuchen** aus, um die MDF\-Datei zu suchen, die die Datenbank Northwind enthält.  
  
6.  Wählen Sie \(je nach den Anforderungen Ihrer Version der Datenbank Northwind\) entweder **Windows\-Authentifizierung verwenden** oder **SQL Server\-Authentifizierung** aus und geben Sie einen Benutzernamen und ein Kennwort zur Anmeldung an dem Computer ein, auf dem SQL Server ausgeführt wird.  
  
7.  Klicken Sie auf die Schaltfläche **OK**.  
  
     Dem **Server\-Explorer**\/**Datenbank\-Explorer** wird eine Datenverbindung zur Northwind\-Datenbank hinzugefügt.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] umfasst Änderungen, die für die Northwind\-Datenbankdatei \(.mdf\) gelten.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie eine Datenverbindung mit der Northwind\-Datenbank \- Access\-Datenbankdatei \(.mdb oder .accdb\)  
  
1.  Wählen Sie im Menü **AnsichtServer\-Explorer**\/**Datenbank\-Explorer** aus.  
  
2.  Öffnen Sie im **Server\-Explorer**\/**Datenbank\-Explorer** das Kontextmenü für **Datenverbindungen** und wählen Sie **Verbindung hinzufügen** aus.  
  
     Nachdem Sie **Verbindung hinzufügen** ausgewählt haben, wird entweder das Dialogfeld **Verbindung hinzufügen** oder das Dialogfeld **Datenquelle auswählen** angezeigt.  
  
3.  Wenn das Dialogfeld **Datenquelle auswählen** angezeigt wird, wählen Sie **Microsoft Access\-Datenbankdatei** und anschließend **OK** aus.  
  
4.  Wenn das Dialogfeld **Verbindung hinzufügen** angezeigt wird, müssen Sie überprüfen, dass die **Datenquelle** auf **Microsoft Access\-Datenbankdatei** eingestellt ist.  Wenn diese nicht auf **Microsoft Access\-Datenbankdatei** festgelegt ist, wählen Sie **Ändern** aus, um das Dialogfeld **Datenquelle wechseln** zu öffnen. Wählen Sie dort **Microsoft Access\-Datenbankdatei** und anschließend die Schaltfläche **OK** aus.  
  
5.  Wählen Sie **Durchsuchen** aus, um die MDB\- oder ACCDB\-Datei zu suchen, die die Datenbank Northwind enthält.  
  
6.  Geben Sie einen Benutzernamen und ein Kennwort ein, wenn dies bei Ihrer Version der Datenbank Northwind erforderlich ist.  
  
7.  Klicken Sie auf **OK**.  
  
     Dem **Server\-Explorer**\/**Datenbank\-Explorer** wird eine Datenverbindung zur Northwind\-Datenbank hinzugefügt.  
  
## Siehe auch  
 [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md)   
 [Datenprogrammierung mit Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)