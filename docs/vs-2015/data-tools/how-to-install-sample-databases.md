---
title: 'Vorgehensweise: Installieren von Beispieldatenbanken | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd51bd397e6db3728c10f52db68d45e226fb605b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251035"
---
# <a name="how-to-install-sample-databases"></a>Gewusst wie: Installieren von Beispieldatenbanken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Viele Datenbeispiele setzen die Möglichkeit voraus, eine Verbindung mit den Beispieldatenbanken "Northwind", "Pubs" und "AdventureWorks" herzustellen. Sie können diese Datenbanken installieren und eine Verbindung mit ihnen herstellen, indem Sie die folgenden Verfahren verwenden.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Installieren von Datenbanken  
 Für viele Datenbeispiele ist die Verfügbarkeit von Beispieldatenbanken erforderlich, die von Websites heruntergeladen werden können. Die Beispieldatenbanken umfassen die Datenbanken AdventureWorks, Northwind und Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>So installieren Sie die Beispieldatenbanken Northwind und Pubs für SQL Server  
  
1.  Wechseln Sie zu der [Beispieldatenbanken Northwind und Pubs](http://go.microsoft.com/fwlink?linkid=64296) Website.  
  
2.  Laden Sie das Installationsprogramm herunter und führen Sie es aus.  
  
     Das Installationsprogramm Fügt einen Ordner **SQL Server 2000 Sample Databases** in den Stammordner auf Ihrem Computer. (Z. B.: **C:\SQL Server 2000 Sample Databases**).  
  
3.  Suchen Sie das SQL-Skript für die Datenbank, die verwendet werden soll, "Northwind" oder "Pubs".  
  
    > [!WARNING]
    >  Die .MDF-Datenbankdatei kann nicht einfach in ein Format konvertiert werden, das Sie in den aktuellen Versionen von SQL Server verwenden können. Deshalb ist es am besten, das Skript zu verwenden, um die Datenbank zu erstellen.  
  
4.  In **Server-Explorer**, Herstellen einer Verbindung mit einer SQL Server-Instanz, in dem die Datenbank installiert werden sollen. Wenn Sie über keinen spezifischen SQL Server verfügen, den Sie verwenden möchten, können Sie die Datenbank verwenden, die automatisch mit Visual Studio installiert wird. Geben Sie zu diesem Zweck `(localdb)\v11.0` als Servernamen ein.  
  
     Führen Sie folgende Schritte aus, um die Verbindung zu erstellen:  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>So erstellen Sie eine Verbindung mit einer SQL Server-Instanz  
  
    1.  In **Server-Explorer**, öffnen Sie das Kontextmenü für die **Datenverbindungen** Knoten, und wählen Sie **Verbindung hinzufügen**.  
  
         Die **Verbindung hinzufügen** Dialogfeld wird angezeigt.  
  
    2.  Geben Sie den Namen des SQL Servers ein, auf dem Sie die Datenbank "Northwind" oder "Pubs" erstellen möchten, oder geben Sie "(localdb)\v11.0" ein.  
  
    3.  Klicken Sie unter **auswählen oder Eingeben eines Datenbanknamens**, wählen Sie eine beliebige Datenbank aus der Liste, z. B. Tempdb.  
  
    4.  Wählen Sie die **Testverbindung** Schaltfläche, um sicherzustellen, dass alles funktioniert, und wählen Sie dann die **OK** Schaltfläche.  
  
         Ein neuer Verbindungsknoten wird im **Server-Explorer**.  
  
5.  Klicken Sie auf das Kontextmenü für den Verbindungsknoten für Ihren Server und wählen Sie dann die **neue Abfrage** Schaltfläche.  
  
     Ein Editorfenster wird geöffnet und zeigt eine leere SQL-Skriptdatei an.  
  
6.  Fügen Sie den Inhalt von "instnwnd.sql" oder von "instpubs.sql" in das Editorfenster ein.  
  
7.  Wählen Sie die Schaltfläche "Abfrage ausführen" aus (das geöffnete Symbol grünes Dreieck oben rechts im Abfragefenster).  
  
     Wenn die Abfrage erfolgreich ist, die Nachricht **Befehl(e) wurde(n) erfolgreich abgeschlossen** angezeigt wird. Dies bedeutet, dass die Northwind- oder Pubs-Datenbank erstellt wurde.  
  
     Sie müssen trotzdem eine Verbindung zur Datenbank hinzufügen. In **Server-Explorer**, öffnen Sie das Kontextmenü für die **Datenverbindungen** Knoten, und wählen Sie **Verbindung hinzufügen**.  
  
8.  Wählen Sie demselben Datenbankserver, die Sie vor, aber dieses Mal unter "auswählen" ausgewählt haben, oder geben Sie einen Datenbanknamen ein, wählen Sie die Northwind- oder Pubs-Datenbank und die **OK** Schaltfläche.  
  
     Es wird ein neuer Knoten unter Datenverbindungen für die Beispieldatenbank angezeigt.  
  
9. Schließen Sie das Editorfenster und bestätigen Sie, dass Sie die Datei nicht speichern möchten. Es ist nicht erforderlich, das Erstellungsskript für die Datenbank zu speichern, nach dem Sie die Datenbank erstellt haben.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>So installieren Sie die AdventureWorks-Beispieldatenbanken  
  
-   Herunterladen der AdventureWorks-Beispieldatenbanken von der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>So installieren Sie die Beispieldatenbank Northwind für Microsoft Access  
  
1.  In Microsoft Access 2010 oder höher Northwind online-Vorlagen suchen, und wählen **Beispieldatenbank Desktop Northwind 2007**.  
  
2.  Speichern Sie die Datenbankdatei in Microsoft Access als Northwind.accdb.  
  
 Die neue Erweiterung für Access-Datenbanken ist ".accdb". Finden Sie unter [Datenprogrammierung mit Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Zur Verbindung mit der Northwind-Datenbank mithilfe von Access finden Sie unter [Vorgehensweise: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Die Beispieldatenbanken dienen nur zu Illustrationszwecken und zeigen nicht unbedingt die besten Sicherheitsmaßnahmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Ermitteln der Version und Edition von SQL Server und dessen Komponenten](http://support.microsoft.com/kb/321185)   
 [Erstellen Sie eine SQL­Datenbank mithilfe eines Designers](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Gewusst wie: Verbinden mit der Datenbank Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)