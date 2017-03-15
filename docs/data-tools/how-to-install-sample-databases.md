---
title: "Gewusst wie: Installieren von Beispieldatenbanken | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Adventure Works-Beispieldatenbank"
  - "Daten [Visual Studio], Beispieldatenbanken"
  - "Northwind-Beispieldatenbank"
  - "Beispieldatenbanken, Adventure Works"
  - "Beispieldatenbanken, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Installieren von Beispieldatenbanken
Viele Datenbeispiele setzen die Möglichkeit voraus, eine Verbindung mit den Beispieldatenbanken "Northwind", "Pubs" und "AdventureWorks" herzustellen.  Sie können diese Datenbanken installieren und eine Verbindung mit ihnen herstellen, indem Sie die folgenden Verfahren verwenden.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Installieren von Datenbanken  
 Für viele Datenbeispiele ist die Verfügbarkeit von Beispieldatenbanken erforderlich, die von Websites heruntergeladen werden können.  Die Beispieldatenbanken umfassen die Datenbanken AdventureWorks, Northwind und Pubs.  
  
#### So installieren Sie die Beispieldatenbanken Northwind und Pubs für SQL Server  
  
1.  Gehen Sie auf die Website von [Beispieldatenbanken Northwind und Pubs](http://go.microsoft.com/fwlink?linkid=64296).  
  
2.  Laden Sie das Installationsprogramm herunter und führen Sie es aus.  
  
     Das Installationsprogramm fügt dem Stammordner auf Ihrem Computer einen Ordner **SQL Server 2000\-Beispieldatenbanken** hinzu.  \(Beispielsweise: **C:\\SQL Server 2000\-Beispieldatenbanken**\).  
  
3.  Suchen Sie das SQL\-Skript für die Datenbank, die verwendet werden soll, "Northwind" oder "Pubs".  
  
    > [!WARNING]
    >  Die .MDF\-Datenbankdatei kann nicht einfach in ein Format konvertiert werden, das Sie in den aktuellen Versionen von SQL Server verwenden können. Deshalb ist es am besten, das Skript zu verwenden, um die Datenbank zu erstellen.  
  
4.  Erstellen Sie im **Server\-Explorer** eine Verbindung mit einer SQL Server\-Instanz, in der Sie die Datenbank installieren möchten.  Wenn Sie über keinen spezifischen SQL Server verfügen, den Sie verwenden möchten, können Sie die Datenbank verwenden, die automatisch mit Visual Studio installiert wird.  Geben Sie hierzu `(localdb)\v11.0` als Servernamen an.  
  
     Führen Sie folgende Schritte aus, um die Verbindung zu erstellen:  
  
    ###### So erstellen Sie eine Verbindung mit einer SQL Server\-Instanz  
  
    1.  Öffnen Sie im **Server\-Explorer** das Kontextmenü für den Knoten **Datenverbindungen**, und wählen Sie dann **Verbindung hinzufügen** aus.  
  
         Das Dialogfeld **Verbindung hinzufügen** wird angezeigt.  
  
    2.  Geben Sie den Namen des SQL Servers ein, auf dem Sie die Datenbank "Northwind" oder "Pubs" erstellen möchten, oder geben Sie "\(localdb\)\\v11.0" ein.  
  
    3.  Wählen Sie unter **Einen Datenbanknamen auswählen oder eingeben** eine beliebige Datenbank in der Liste aus, beispielsweise "tempdb".  
  
    4.  Wählen Sie die Schaltfläche **Verbindung testen** aus, um sicherzustellen, dass alles funktioniert, und klicken Sie dann auf die Schaltfläche **OK**.  
  
         Ein neuer Verbindungsknoten wird im **Server\-Explorer** angezeigt.  
  
5.  Im Kontextmenü für den Verbindungsknoten für den Server wählen Sie anschließend die Schaltfläche **Neue Abfrage** aus.  
  
     Ein Editorfenster wird geöffnet und zeigt eine leere SQL\-Skriptdatei an.  
  
6.  Fügen Sie den Inhalt von "instnwnd.sql" oder von "instpubs.sql" in das Editorfenster ein.  
  
7.  Wählen Sie die Schaltfläche "Abfrage ausführen" aus \(das geöffnete Symbol grünes Dreieck oben rechts im Abfragefenster\).  
  
     Wenn die Abfrage erfolgreich ist, wird die Nachricht **Befehle erfolgreich abgeschlossen** angezeigt.  Dies bedeutet, dass die Northwind\- oder Pubs\-Datenbank erstellt wurde.  
  
     Sie müssen trotzdem eine Verbindung zur Datenbank hinzufügen.  Öffnen Sie im **Server\-Explorer** das Kontextmenü für den Knoten **Datenverbindungen** und wählen Sie dann **Verbindung hinzufügen** aus.  
  
8.  Wählen Sie derselben Datenbank\-Server aus, den Sie zuvor ausgewählt haben, aber dieses Mal unter "Auswählen" oder "Datenbankname eingeben". Dann wählen Sie die Northwind\- oder Pubs\-Datenbank und die Schaltfläche **OK** aus.  
  
     Es wird ein neuer Knoten unter Datenverbindungen für die Beispieldatenbank angezeigt.  
  
9. Schließen Sie das Editorfenster und bestätigen Sie, dass Sie die Datei nicht speichern möchten.  Es ist nicht erforderlich, das Erstellungsskript für die Datenbank zu speichern, nach dem Sie die Datenbank erstellt haben.  
  
#### So installieren Sie die AdventureWorks\-Beispieldatenbanken  
  
-   Laden Sie die AdventureWorks\-Beispieldatenbanken von der [CodePlex\-Website](http://go.microsoft.com/fwlink/?linkid=87843) herunter.  
  
#### So installieren Sie die Beispieldatenbank Northwind für Microsoft Access  
  
1.  Suchen Sie in Microsoft Access 2010 oder höher Northwind Online\-Vorlagen und wählen Sie **Beispieldatenbank Nordwind 2007 Desktop** aus.  
  
2.  Speichern Sie die Datenbankdatei in Microsoft Access als Northwind.accdb.  
  
 Die neue Erweiterung für Access\-Datenbanken ist ".accdb".  Siehe [Datenprogrammierung mit Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx).  Zum Herstellen einer Verbindung zur Northwind\-Datenbank mithilfe von Access finden Sie Informationen unter [Gewusst wie: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## .NET Framework-Sicherheit  
 Die Beispieldatenbanken dienen nur zu Illustrationszwecken und zeigen nicht unbedingt die besten Sicherheitsmaßnahmen.  
  
## Siehe auch  
 [Bestimmen der Version und Edition von SQL Server und seiner Komponenten](http://support.microsoft.com/kb/321185)   
 [Exemplarische Vorgehensweise: Erstellen einer lokalen Datenbankdatei in Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Gewusst wie: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)