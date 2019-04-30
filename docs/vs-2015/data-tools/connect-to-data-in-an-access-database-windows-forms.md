---
title: Verbinden mit Daten in einer Access-Datenbank (Windows Forms) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 4a6909bade36dce15bfae725fbaab60f24236451
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437000"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mit einer Access-Datenbank (entweder eine MDF-Datei oder eine ACCDB-Datei) mithilfe von Visual Studio verbinden. Nachdem Sie die Verbindung definiert haben, werden die Daten im Fenster **Datenquellen** angezeigt. Von dort können Sie Tabellen oder Ansichten auf die Formulare ziehen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese Prozeduren verwenden zu können, benötigen Sie ein Windows Forms-Anwendungsprojekt, und einer Access-Datenbank (ACCDB-Datei) oder eine Access 2000 – 2003-Datenbank (MDB-Datei). Führen Sie die Prozedur aus, die dem Dateityp entspricht.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Erstellen des DataSets für eine ACCDB-Datei  
 Sie können mit Datenbanken über Access 2013, Office 365, Access 2010 oder Access 2007 erstellt wurden, mithilfe des folgenden Verfahrens verbinden.  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1. Öffnen Sie die Windows Forms-Anwendung, mit der Sie Daten verknüpfen möchten.  
  
2. Auf der **Ansicht** , wählen Sie im Menü **Other Windows** > **Datenquellen**.  
  
     ![Anzeigen der Daten aus anderen Windows-Quellen](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
     ![Neue Datenquelle hinzufügen](../data-tools/media/dataaddnewdatasource.png "DataAddNewDataSource")  
  
4. Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.  
  
5. Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.  
  
6. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** die Option **Neue Verbindung** aus, um eine neue Datenverbindung zu konfigurieren.  
  
7. Ändern der **Datenquelle** zu **.NET Framework-Datenanbieter für OLE DB**.  
  
     ![Datenanbieter für OLE DB ändern](../data-tools/media/datachangedatasourceoledb.png "DataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    > Obwohl eine Datenquelle **Microsoft Access-Datenbankdatei (OLE DB)** mag die richtige Wahl, Sie verwenden diese Datenquellentyp nur für MDB-Datenbankdateien.  
  
8. In **OLE DB-Anbieter**Option **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.  
  
     ![OLE DB Provider Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. In **Server-oder Dateiname**, geben Sie den Pfad und Namen der ACCDB-Datei zu dem Sie eine Verbindung herstellen, und wählen Sie dann möchten **OK**.  
  
    > [!NOTE]
    > Wenn die Datenbankdatei einen Benutzernamen und ein Kennwort verfügt, geben Sie diese vor der Auswahl **OK**.  
  
10. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.  
  
11. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
12. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
13. Wählen Sie alle Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.  
  
     Das DataSet wird Ihrem Projekt hinzugefügt, und die Tabellen und Ansichten werden im Fenster **Datenquellen** angezeigt.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Erstellen des Datasets für eine MDB-Datei  
 Das Dataset wird erstellt, indem der **Assistent zum Konfigurieren von Datenquellen** ausgeführt wird.  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1. Öffnen Sie die Windows Forms-Anwendung, mit der Sie Daten verknüpfen möchten.  
  
2. Auf der **Ansicht** , wählen Sie im Menü **Other Windows** > **Datenquellen**.  
  
     ![Anzeigen der Daten aus anderen Windows-Quellen](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
4. Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.  
  
5. Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.  
  
6. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** die Option **Neue Verbindung** aus, um eine neue Datenverbindung zu konfigurieren.  
  
7. Die Datenquelle ist nicht **Microsoft Access-Datenbankdatei (OLE DB)** wählen **Änderung** zu öffnen der **Datenquelle wechseln** , und wählen Sie im Dialogfeld **Microsoft Zugriff auf die Datenbankdatei**, und wählen Sie dann **OK**.  
  
8. In der **Name der Datenbankdatei**, geben Sie den Pfad und Namen der MDB-Datei zu dem Sie eine Verbindung herstellen, und wählen Sie dann möchten **OK**.  
  
     ![Verbindungszugriff-Datenbankdatei hinzufügen](../data-tools/media/dataaddconnectionaccessmdb.png "DataAddConnectionAccessMDB")  
  
9. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.  
  
10. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
11. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
12. Wählen Sie alle Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.  
  
     Das DataSet wird Ihrem Projekt hinzugefügt, und die Tabellen und Ansichten werden im Fenster **Datenquellen** angezeigt.  
  
## <a name="security"></a>Sicherheit  
 Das Speichern vertraulicher Informationen (z. B. ein Kennwort) kann sich auf die Sicherheit der Anwendung auswirken. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Das Dataset, das Sie gerade erstellt haben, ist jetzt verfügbar ist, in der **Datenquellen** Fenster. Sie können nun eine der folgenden Aufgaben ausführen:  
  
- Wählen Sie Elemente in der **Datenquellen** Fenster und ziehen Sie sie auf das Formular (finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
- Öffnen Sie die Datenquelle im Dataset-Designer zum Hinzufügen oder bearbeiten die Objekte, die das Dataset bilden.  
  
- Eine Validierungslogik Hinzufügen der <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignis der Datentabellen im Dataset (finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Siehe auch

 [Vorbereiten der Anwendung auf den Empfang von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)