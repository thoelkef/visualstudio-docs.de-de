---
title: Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms) | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651135"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Visual Studio können Sie eine Verbindung mit einer Access-Datenbank (eine MDF-Datei oder eine ACCDB-Datei) herstellen. Nachdem Sie die Verbindung definiert haben, werden die Daten im Fenster **Datenquellen** angezeigt. Von dort können Sie Tabellen oder Ansichten auf die Formulare ziehen.

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Um diese Prozeduren verwenden zu können, benötigen Sie ein Windows Forms-Anwendungsprojekt und entweder eine Access-Datenbank (. ACCDB-Datei) oder eine Access 2000 – 2003-Datenbank (MDB-Datei). Führen Sie die Prozedur aus, die dem Dateityp entspricht.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Erstellen des DataSets für eine ACCDB-Datei
 Mithilfe des folgenden Verfahrens können Sie eine Verbindung mit Datenbanken herstellen, die über Access 2013, Office 365, Access 2010 oder Access 2007 erstellt wurden.

#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet

1. Öffnen Sie die Windows Forms-Anwendung, mit der Sie Daten verknüpfen möchten.

2. Wählen Sie im Menü **Ansicht** die Option **Weitere Fenster**  > **Datenquellen**aus.

     ![Anzeigen anderer Windows-Datenquellen](../data-tools/media/viewdatasources.png "Viewdatasources")

3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

     ![Neue Datenquelle hinzufügen](../data-tools/media/dataaddnewdatasource.png "dataaddnewdatasource")

4. Wählen Sie auf der Seite **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

5. Wählen Sie auf der Seite **Datenbankmodell auswählen** die Option **DataSet** aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** die Option **Neue Verbindung** aus, um eine neue Datenverbindung zu konfigurieren.

7. Ändern Sie die **Datenquelle** in **.NET Framework Datenanbieter für OLE DB**.

     ![Ändern Sie Datenanbieter in OLE DB](../data-tools/media/datachangedatasourceoledb.png "datachangedatasourceoledb")

    > [!IMPORTANT]
    > Obwohl eine Datenquelle der **Microsoft Access-Datenbankdatei (OLE DB)** wie die richtige Wahl erscheinen mag, verwenden Sie diesen Daten Quellentyp nur für MDB-Datenbankdateien.

8. Wählen Sie in **OLE DB Anbieter** **Microsoft Office 12,0 Access Datenbank-Engine OLE DB Anbieters**aus.

     ![OLE DB Anbieter Microsoft Office 12,0-Zugriff](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. Geben Sie unter **Server-oder Dateiname**den Pfad und den Namen der ACCDB-Datei an, mit der Sie eine Verbindung herstellen möchten, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Wenn die Datenbankdatei einen Benutzernamen und ein Kennwort enthält, geben Sie Sie an, bevor Sie auf **OK**klicken.

10. Klicken Sie auf der Seite **Wählen Sie Ihre Datenverbindung** aus auf **weiter** .

11. Klicken Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** auf **weiter** .

12. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

13. Wählen Sie die gewünschten Tabellen oder Sichten in Ihrem DataSet aus, und klicken Sie dann auf **Fertig**stellen.

     Das DataSet wird Ihrem Projekt hinzugefügt, und die Tabellen und Ansichten werden im Fenster **Datenquellen** angezeigt.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Erstellen des Datasets für eine MDB-Datei
 Das Dataset wird erstellt, indem der **Assistent zum Konfigurieren von Datenquellen** ausgeführt wird.

#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet

1. Öffnen Sie die Windows Forms-Anwendung, mit der Sie Daten verknüpfen möchten.

2. Wählen Sie im Menü **Ansicht** die Option **Weitere Fenster**  > **Datenquellen**aus.

     ![Anzeigen anderer Windows-Datenquellen](../data-tools/media/viewdatasources.png "Viewdatasources")

3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

4. Wählen Sie auf der Seite **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

5. Wählen Sie auf der Seite **Datenbankmodell auswählen** die Option **DataSet** aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** die Option **Neue Verbindung** aus, um eine neue Datenverbindung zu konfigurieren.

7. Wenn es sich bei der Datenquelle nicht um eine **Microsoft Access-Datenbankdatei (OLE DB)** handelt, wählen Sie **ändern** aus, um das Dialogfeld **Datenquelle ändern** zu öffnen, **und wählen Sie** **Microsoft Access-Datenbankdatei**aus.

8. Geben Sie unter **Name der Datenbankdatei**den Pfad und den Namen der MDB-Datei an, mit der Sie eine Verbindung herstellen möchten, und klicken Sie dann auf **OK**.

     ![Datenbankdatei für Verbindungs Zugriff hinzufügen](../data-tools/media/dataaddconnectionaccessmdb.png "dataaddconnectionaccessmdb")

9. Klicken Sie auf der Seite **Wählen Sie Ihre Datenverbindung** aus auf **weiter** .

10. Klicken Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** auf **weiter** .

11. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

12. Wählen Sie die gewünschten Tabellen oder Sichten in Ihrem DataSet aus, und klicken Sie dann auf **Fertig**stellen.

     Das DataSet wird Ihrem Projekt hinzugefügt, und die Tabellen und Ansichten werden im Fenster **Datenquellen** angezeigt.

## <a name="security"></a>Sicherheit
 Das Speichern vertraulicher Informationen (z. B. ein Kennwort) kann sich auf die Sicherheit der Anwendung auswirken. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Nächste Schritte
 Das soeben erstellte Dataset ist jetzt im **Datenquellen** Fenster verfügbar. Sie können nun eine der folgenden Aufgaben ausführen:

- Wählen Sie im Fenster **Datenquellen** die Option Elemente aus, und ziehen Sie Sie auf das Formular (siehe [Binden von Windows Forms Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Öffnen Sie die Datenquelle im DataSet-Designer, um die Objekte, aus denen das DataSet besteht, hinzuzufügen oder zu bearbeiten.

- Fügen Sie der <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging>-Ereignis der Datentabellen im DataSet eine Validierungs Logik hinzu (siehe [Validieren von Daten in Datasets](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Siehe auch

 [Vorbereiten der Anwendung für den Empfang von Daten](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [Bindungs Steuerelementen an Daten in Visual Studio über](../data-tools/bind-controls-to-data-in-visual-studio.md) prüfen von exemplarischen Vorgehensweisen für [Daten](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [Daten](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)