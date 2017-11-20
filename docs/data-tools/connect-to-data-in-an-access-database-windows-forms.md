---
title: Verbinden mit Daten in einer Access-Datenbank (Windows Forms) | Microsoft Docs
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 1f67a87f4a704d3f76ccddba62112983c058a9f3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Verbinden Sie mit Daten in einer Access-Datenbank (Windows Forms)
Sie können mit einer Access-Datenbank (entweder eine MDF-Datei oder eine ACCDB-Datei) mithilfe von Visual Studio verbinden. Nachdem Sie die Verbindung definiert, die Daten angezeigt, der **Datenquellen** Fenster. Von dort können Sie Tabellen oder Ansichten auf die Formulare ziehen.   
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Verwenden dieser Prozeduren benötigen Sie ein Windows Forms-Anwendungsprojekt und entweder eine Access-Datenbank (ACCDB-Datei) oder eine Access 2000-2003-Datenbank (MDB-Datei). Führen Sie die Prozedur aus, die dem Dateityp entspricht.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Erstellen des Datasets für eine ACCDB-Datei  
 Sie können mit Datenbanken in Access 2013, Office 365, Access 2010 oder Access 2007 erstellt werden, mithilfe des folgenden Verfahrens verbinden.  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1.  Öffnen Sie die Windows Forms-Anwendung, die Sie Daten anbinden möchten.  
  
2.  Auf der **Ansicht** klicken Sie im Menü **Weitere Fenster** > **Datenquellen**.  
  
     ![Weitere Windows-Datenquellen anzeigen](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  

     Die **Data Source Configuration Wizard** wird geöffnet.  
  
4.  Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.  
  
5.  Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.  
  
6.  Auf der **wählen Sie Ihre Datenverbindung** Seite **neue Verbindung** eine neue Datenverbindung zu konfigurieren.  

     Die **Verbindung hinzufügen** Dialogfeld wird geöffnet.  
  
7.  Wählen Sie die **Änderung** neben der **Datenquelle** Textfeld.

     Die **Datenquelle wechseln** Dialogfeld wird geöffnet.  
  
8.  Wählen Sie in der Liste der Datenquellen,  **\<andere\>**. In der **Datenanbieter** Dropdownliste, wählen **.NET Framework-Datenanbieter für OLE DB-**, wählen Sie dann **OK**.  

9. In der **Verbindung hinzufügen** wählen Sie im Dialogfeld **Microsoft Office 12.0 Access Database Engine OLE DB Provider** aus der **OLE DB-Anbieter** Dropdown-Menü.  
  
     ![OLE DB-Anbieter Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  

     > [!NOTE]
     >  Wenn Sie nicht sehen **Microsoft Office 12.0 Access Database Engine OLE DB Provider** in OLE DB-Anbieter, Dropdown-Menü, müssen Sie möglicherweise Installieren der [2007 Office System Driver: Data Connectivity Components](https://www.microsoft.com/download/confirmation.aspx?id=23734).
  
9. In der **Server- oder Dateiname** Textfeld, geben Sie den Pfad und Namen der ACCDB-Datei, die Sie herstellen möchten, und wählen Sie dann der Datei **OK**. (Wenn die Datenbankdatei einen Benutzernamen und ein Kennwort verfügt, geben Sie diese vor der Auswahl **OK**.)    
  
10. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.  

     Möglicherweise erhalten Sie, dass ein Dialogfeld, dass die Datendatei ist nicht in Ihrem aktuellen Projekt. Wählen Sie **Ja** oder **Nein**.
  
11. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
12. Erweitern Sie die **Tabellen** Knoten auf die **wählen Sie Ihre Datenbankobjekte** Seite.  
  
13. Wählen Sie die Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.  
  
     Das Dataset wird Ihrem Projekt hinzugefügt, und die Tabellen und Sichten angezeigt, der **Datenquellen** Fenster.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Erstellen des Datasets für eine MDB-Datei  
 Erstellen Sie das Dataset durch Ausführen der **Datenquellen Konfigurations-Assistenten**.  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1.  Öffnen Sie die Windows Forms-Anwendung, die Sie Daten anbinden möchten.  
  
2.  Auf der **Ansicht** klicken Sie im Menü **Weitere Fenster** > **Datenquellen**.  
  
     ![Weitere Windows-Datenquellen anzeigen](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  

     Die **Data Source Configuration Wizard** wird geöffnet.
  
4.  Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.  
  
5.  Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.  
  
6.  Auf der **wählen Sie Ihre Datenverbindung** Seite **neue Verbindung** eine neue Datenverbindung zu konfigurieren.  
  
7.  Die Datenquelle ist nicht **Microsoft Access-Datenbankdatei (OLE DB)**wählen **ändern** So öffnen die **Datenquelle wechseln** (Dialogfeld), und wählen **Microsoft Zugriff auf die Datenbankdatei**, und wählen Sie dann **OK**.  
  
8.  In der **Datenbankdateiname**, geben Sie den Pfad und Namen der MDB-Datei, die Sie verwenden möchten, Herstellen einer Verbindung mit, und wählen Sie dann **OK**.  
  
     ![Verbindungszugriff-Datenbankdatei hinzufügen](../data-tools/media/dataaddconnectionaccessmdb.png "DataAddConnectionAccessMDB")  
  
9. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.  
  
10. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
11. Erweitern Sie die **Tabellen** Knoten auf die **wählen Sie Ihre Datenbankobjekte** Seite.  
  
12. Wählen Sie die Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.  
  
     Das Dataset wird Ihrem Projekt hinzugefügt, und die Tabellen und Sichten angezeigt, der **Datenquellen** Fenster.  
  
## <a name="security"></a>Sicherheit  
 Das Speichern vertraulicher Informationen (z. B. ein Kennwort) kann sich auf die Sicherheit der Anwendung auswirken. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](/dotnet/framework/data/adonet/protecting-connection-information).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Die neu erstellte Dataset ist jetzt verfügbar in der **Datenquellen** Fenster. Sie können nun eine der folgenden Aufgaben ausführen:  
  
-   Wählen Sie Elemente in der **Datenquellen** Fenster, und ziehen Sie sie auf das Formular (finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
-   Öffnen Sie die Datenquelle in der **Dataset-Designer** hinzufügen oder bearbeiten die Objekte, die das Dataset bilden.  
  
-   Eine Validierungslogik Hinzufügen der <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignis der Datentabellen im Dataset (finden Sie unter [Validieren von Daten in Datasets](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Siehe auch
[Hinzufügen von Verbindungen](../data-tools/add-new-connections.md)
