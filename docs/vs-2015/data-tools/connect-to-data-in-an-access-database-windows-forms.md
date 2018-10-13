---
title: Verbinden mit Daten in einer Access-Datenbank (Windows Forms) | Microsoft-Dokumentation
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
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4741dedb907bb88513147a98b916831abd965576
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207349"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Verbinden Sie mit Daten in einer Access-Datenbank (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können mit einer Access-Datenbank (entweder eine MDF-Datei oder eine ACCDB-Datei) mithilfe von Visual Studio verbinden. Nachdem Sie die Verbindung definiert, die Daten erscheinen in der **Datenquellen** Fenster. Von dort können Sie Tabellen oder Ansichten auf die Formulare ziehen. Wenn Sie möchten verstehen, wie das Projektsystem in Visual Studio diese lokalen Datenbankdateien verwaltet, finden Sie unter [Vorgehensweise: Verwalten von lokalen Datendateien in Ihr Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese Prozeduren verwenden zu können, benötigen Sie ein Windows Forms-Anwendungsprojekt, und einer Access-Datenbank (ACCDB-Datei) oder eine Access 2000 – 2003-Datenbank (MDB-Datei). Führen Sie die Prozedur aus, die dem Dateityp entspricht.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Erstellen des Datasets für eine ACCDB-Datei  
 Sie können mit Datenbanken über Access 2013, Office 365, Access 2010 oder Access 2007 erstellt wurden, mithilfe des folgenden Verfahrens verbinden.  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1.  Öffnen Sie die Windows Forms-Anwendung, die Sie Daten eine Verbindung herstellen möchten.  
  
2.  Auf der **Ansicht** , wählen Sie im Menü **Other Windows** > **Datenquellen**.  
  
     ![Anzeigen der Daten aus anderen Windows-Quellen](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
     ![Neue Datenquelle hinzufügen](../data-tools/media/dataaddnewdatasource.png "DataAddNewDataSource")  
  
4.  Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.  
  
5.  Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.  
  
6.  Auf der **wählen Sie Ihre Datenverbindung** Seite **neue Verbindung** eine neue Datenverbindung zu konfigurieren.  
  
7.  Ändern der **Datenquelle** zu **.NET Framework-Datenanbieter für OLE DB**.  
  
     ![Datenanbieter für OLE DB ändern](../data-tools/media/datachangedatasourceoledb.png "DataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  Obwohl eine Datenquelle **Microsoft Access-Datenbankdatei (OLE DB)** mag die richtige Wahl, Sie verwenden diese Datenquellentyp nur für MDB-Datenbankdateien.  
  
8.  In **OLE DB-Anbieter**Option **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.  
  
     ![OLE DB-Anbieter Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. In **Server-oder Dateiname**, geben Sie den Pfad und Namen der ACCDB-Datei zu dem Sie eine Verbindung herstellen, und wählen Sie dann möchten **OK**.  
  
    > [!NOTE]
    >  Wenn die Datenbankdatei einen Benutzernamen und ein Kennwort verfügt, geben Sie diese vor der Auswahl **OK**.  
  
10. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.  
  
11. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
12. Erweitern Sie die **Tabellen** Knoten auf den **Datenbankobjekte auswählen** Seite.  
  
13. Wählen Sie alle Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.  
  
     Das Dataset wird Ihrem Projekt hinzugefügt, und die Tabellen und Sichten angezeigt, der **Datenquellen** Fenster.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Erstellen des Datasets für eine MDB-Datei  
 Erstellen Sie das Dataset durch Ausführen der **Assistenten zur Datenquellenkonfiguration**.  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1.  Öffnen Sie die Windows Forms-Anwendung, die Sie Daten eine Verbindung herstellen möchten.  
  
2.  Auf der **Ansicht** , wählen Sie im Menü **Other Windows** > **Datenquellen**.  
  
     ![Anzeigen der Daten aus anderen Windows-Quellen](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
4.  Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.  
  
5.  Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.  
  
6.  Auf der **wählen Sie Ihre Datenverbindung** Seite **neue Verbindung** eine neue Datenverbindung zu konfigurieren.  
  
7.  Die Datenquelle ist nicht **Microsoft Access-Datenbankdatei (OLE DB)** wählen **Änderung** zu öffnen der **Datenquelle wechseln** , und wählen Sie im Dialogfeld **Microsoft Zugriff auf die Datenbankdatei**, und wählen Sie dann **OK**.  
  
8.  In der **Name der Datenbankdatei**, geben Sie den Pfad und Namen der MDB-Datei zu dem Sie eine Verbindung herstellen, und wählen Sie dann möchten **OK**.  
  
     ![Verbindungszugriff-Datenbankdatei hinzufügen](../data-tools/media/dataaddconnectionaccessmdb.png "DataAddConnectionAccessMDB")  
  
9. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.  
  
10. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
11. Erweitern Sie die **Tabellen** Knoten auf den **Datenbankobjekte auswählen** Seite.  
  
12. Wählen Sie alle Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.  
  
     Das Dataset wird Ihrem Projekt hinzugefügt, und die Tabellen und Sichten angezeigt, der **Datenquellen** Fenster.  
  
## <a name="security"></a>Sicherheit  
 Das Speichern vertraulicher Informationen (z. B. ein Kennwort) kann sich auf die Sicherheit der Anwendung auswirken. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Das Dataset, das Sie gerade erstellt haben, ist jetzt verfügbar ist, in der **Datenquellen** Fenster. Sie können nun die folgenden Aufgaben ausführen:  
  
-   Wählen Sie Elemente in der **Datenquellen** Fenster und ziehen Sie sie auf das Formular (finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
-   Öffnen Sie die Datenquelle in die [Dataset-Designer](../data-tools/creating-and-editing-typed-datasets.md) hinzufügen oder bearbeiten die Objekte, die das Dataset bilden.  
  
-   Eine Validierungslogik Hinzufügen der <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignis der Datentabellen im Dataset (finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)

