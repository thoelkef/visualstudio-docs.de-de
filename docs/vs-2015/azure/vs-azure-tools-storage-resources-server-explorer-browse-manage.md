---
title: Durchsuchen und Verwalten von Speicherressourcen mit Server-Explorer | Microsoft-Dokumentation
description: Durchsuchen und Verwalten von Speicherressourcen mit Server-Explorer
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002071"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Durchsuchen und Verwalten von Speicherressourcen mit dem Server-Explorer

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Übersicht

Wenn Sie Azure-Tools für Microsoft Visual Studio installiert haben, können Sie BLOB-, Warteschlangen- und Tabellendaten von Ihren Speicherkonten für Azure anzeigen. Azure **Storage** Knoten im Server-Explorer zeigt Daten, die in Ihrem lokalen speicheremulatorkonto und Ihren anderen Azure-Speicherkonten sind.

Wählen Sie zum Anzeigen von Server-Explorer in Visual Studio-Menüleiste den Menüpunkt **Ansicht** > **Server-Explorer**. Die **Storage** Knoten zeigt alle Speicherkonten an, die vorhanden sind, klicken Sie unter jeder Azure-Abonnement oder ein Zertifikat, das Sie verbunden sind. Wenn Ihr Speicherkonto nicht angezeigt wird, können Sie es hinzufügen, mithilfe der Anweisungen [weiter unten in diesem Artikel](#add-storage-accounts-by-using-server-explorer).

Ab Azure SDK 2.7 können können Sie auch Cloud-Explorer zum Anzeigen und Verwalten Ihrer Azure-Ressourcen. Weitere Informationen finden Sie unter [Verwalten von Azure-Ressourcen mit dem Cloud-Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Anzeigen und Verwalten von Speicherressourcen in Visual Studio

Server-Explorer zeigt automatisch eine Liste der Blobs, Warteschlangen und Tabellen in Ihrem speicheremulatorkonto an. Das speicheremulatorkonto finden Sie im Server-Explorer unter dem **Storage** Knoten als die **Entwicklung** Knoten.

Um das speicheremulatorkonto Ressourcen anzuzeigen, erweitern Sie die **Entwicklung** Knoten. Wenn der Speicheremulator nicht gestartet wurde, erweitern Sie die **Entwicklung** Knoten automatisch gestartet wird. Dieser Vorgang kann einige Sekunden dauern. Sie können weiterhin in anderen Bereichen von Visual Studio arbeiten, während der Speicheremulator gestartet wird.

Um Ressourcen in einem Speicherkonto anzuzeigen, erweitern Sie in das Storage-Konto-Knoten im Server-Explorer, sodass Sie sehen **Blobs**, **Warteschlangen**, und **Tabellen** Knoten.

## <a name="work-with-blob-resources"></a>Arbeiten mit blobressourcen

Die **Blobs** Knoten zeigt eine Liste der Container für das ausgewählte Speicherkonto an. Blobcontainer enthalten blobdateien, und Sie können diese Blobs in Ordnern und Unterordnern organisieren. Weitere Informationen finden Sie unter [wie Blob-Speicher aus .NET mit](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Um einen Blob-Container zu erstellen.

1. Öffnen Sie das Kontextmenü für die **Blobs** Knoten, und wählen Sie dann **Blob-Container erstellen**.
1. In der **Blob-Container erstellen** Dialogfeld Geben Sie den Namen des neuen Containers.  
1. Wählen Sie auf der Tastatur, oder Sie können klicken oder tippen außerhalb des Namensfelds, um den Blob-Container zu speichern.

   > [!NOTE]
   > Der Name des blobcontainers muss mit einer Zahl (0-9) oder ein Kleinbuchstabe (a-Z) beginnen.

### <a name="to-delete-a-blob-container"></a>So löschen Sie einen Blob-container

Öffnen Sie das Kontextmenü für den Blob-Container, die Sie verwenden möchten, entfernen, und wählen Sie dann **löschen**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Um eine Liste der Elemente in einem blobcontainer anzuzeigen

Öffnen Sie das Kontextmenü für einen blobcontainernamen in der Liste aus, und wählen Sie dann **öffnen**.

Wenn Sie den Inhalt eines blobcontainers anzeigen, wird auf einer Registerkarte, die als blobcontaineransicht bezeichnet.

![Blobcontaineransicht](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Sie können die folgenden Vorgänge für Blobs mithilfe der Schaltflächen in der oberen rechten Ecke der blobcontaineransicht ausführen:

* Geben Sie einen Filterwert, und wenden Sie es.
* Aktualisieren Sie die Liste der Blobs im Container.
* Hochladen einer Datei an.
* Löschen eines BLOBs an. (Eine Datei aus einem blobcontainer nicht die zugrunde liegende Datei gelöscht. Es wird lediglich entfernt es aus dem blobcontainer.)
* Öffnen eines BLOBs an.
* Speichern eines BLOBs auf dem lokalen Computer.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Erstellen Sie einen Ordner oder Unterordner in einem blobcontainer

1. Wählen Sie den blobcontainer im Cloud-Explorer. Wählen Sie im Containerfenster die **Blob hochladen** Schaltfläche.

1. In der **neue Datei hochladen** wählen Sie im Dialogfeld die **Durchsuchen** Schaltfläche, um die Datei anzugeben, die Sie hochladen möchten, und geben Sie dann einen Ordnernamen in das **Ordner (optional)** Feld.

   ![Hochladen einer Datei in einen blobordner](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Sie können Unterordner in Container und Ordner anhand den gleichen Schritt hinzufügen. Wenn Sie einen Ordnernamen nicht angeben, wird die Datei auf der obersten Ebene des blobcontainers hochgeladen. Die Datei wird im angegebenen Ordner im Container angezeigt.

   ![Ordner in einen blobcontainer hinzugefügt haben](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Doppelklicken Sie auf den Ordner, oder wählen Sie die EINGABETASTE, um den Inhalt des Ordners anzuzeigen. Wenn Sie im Ordner des Containers befinden, Sie können wechseln Sie zurück in das Stammverzeichnis des Containers durch Auswählen der **übergeordnetes Verzeichnis öffnen** (Pfeilschaltfläche).

### <a name="to-delete-a-container-folder"></a>So löschen Sie einen Containerordner

Löschen Sie alle Dateien im Ordner "".

Da es sich bei Ordnern in blobcontainern um virtuelle Ordner handelt, wird Sie keinen leeren Ordner mit erstellen. Sie auch einen Ordner, um die jeweiligen Dateiinhalte löschen können nicht gelöscht werden, jedoch müssen stattdessen löschen, den gesamten Inhalt eines Ordners auf den Ordner selbst zu löschen.

### <a name="to-filter-blobs-in-a-container"></a>So filtern Sie Blobs in einem container

Sie können die Blobs filtern, die angezeigt werden, indem Sie ein gemeinsames Präfix angeben.

Wenn Sie das Präfix Geben Sie z. B. **Hello** im Text-Feld "Filter" und wählen Sie dann die **Execute** (**!**) Schaltfläche nur Blobs angezeigt, die mit "Hello" beginnen.

![Textfeld filtern](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Im Textfeld "Filter" wird die Groß- und Filtervorgänge mit Platzhalterzeichen werden nicht unterstützt. BLOBs können nur nach Präfix gefiltert werden. Das Präfix kann ein Trennzeichen einschließen, wenn Sie eines Trennzeichens mithilfe Organisieren der Blobs in einer virtuellen Hierarchie. Filtern Sie beispielsweise nach dem Präfix "HelloFabric /" alle Blobs, die mit dieser Zeichenfolge beginnen zurückgegeben.

### <a name="to-download-blob-data"></a>Zum Herunterladen von blobdaten

Verwenden Sie im Cloud-Explorer eine der folgenden Methoden aus:

* Öffnen Sie das Kontextmenü für ein oder mehrere Blobs, und wählen Sie dann **öffnen**.
* Wählen Sie den blobnamen, und wählen Sie dann die **öffnen** Schaltfläche.
* Doppelklicken Sie auf den Namen des BLOBs.

Der Status eines blobdownloads wird im der **Azure Activity Log** Fenster.

Das Blob wird in der Standard-Editor für diesen Dateityp geöffnet. Wenn das Betriebssystem den Dateityp erkennt, wird die Datei in einer lokal installierten Anwendung geöffnet. Andernfalls werden Sie aufgefordert, eine Anwendung aus, die für den Dateityp des BLOBs geeignet ist. Die lokale Datei, die erstellt wird, wenn Sie einen Blob herunterladen wird als schreibgeschützt markiert.

BLOB-Daten ist lokal zwischengespeichert und für den Blob Last-modified-Zeit im Azure-Blob-Speicher aktiviert. Wenn das Blob seit dem letzten Herunterladen wurde aktualisiert wurde, wird es erneut heruntergeladen. Andernfalls wird das Blob vom lokalen Datenträger geladen.

Standardmäßig wird ein Blob in ein temporäres Verzeichnis heruntergeladen. Um Blobs in ein bestimmtes Verzeichnis herunterzuladen, öffnen Sie das Kontextmenü für die ausgewählten blobnamen, und wählen Sie **speichern**. Wenn Sie einen Blob auf diese Weise speichern, die Blobdatei nicht geöffnet, und die lokale Datei mit Lese-/schreibattributen erstellt wird.

### <a name="to-upload-blobs"></a>Zum Hochladen von blobs

Wählen Sie zum Hochladen von Blobs die **Blob hochladen** Schaltfläche, wenn der Container für die Anzeige in der blobcontaineransicht geöffnet ist.

Sie können eine oder mehrere Dateien zum Hochladen auswählen und Sie können Hochladen von Dateien eines beliebigen Typs. Die **Azure Activity Log** Fenster wird der Fortschritt des Uploads. Weitere Informationen über das Arbeiten mit blobdaten finden Sie unter [Gewusst wie: Verwenden von Azure Blob Storage in .NET](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>So zeigen Sie an Blobs übertragene Protokolle

Wenn Sie der Azure-Diagnose mithilfe Daten von der Azure-Anwendung protokollieren und Protokolle in Ihrem Speicherkonto übertragen haben, werden Container angezeigt, die Azure für diese Protokolle erstellt. Das Anzeigen dieser Protokolle im Server-Explorer ist eine einfache Möglichkeit, Probleme mit Ihrer Anwendung zu identifizieren, insbesondere dann, wenn sie in Azure bereitgestellt wurde.

Weitere Informationen zu Azure-Diagnose finden Sie unter [Sammeln von Protokollierungsdaten mit der Azure-Diagnose](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Um die URL für ein Blob abzurufen.

Öffnen Sie den Blob Kontextmenü, und wählen Sie dann **URL kopieren**.

### <a name="to-edit-a-blob"></a>So bearbeiten Sie einen blob

Wählen Sie das Blob, und wählen Sie dann die **Blob öffnen** Schaltfläche.

Die Datei ist an einen temporären Speicherort heruntergeladen und auf dem lokalen Computer geöffnet. Laden Sie das Blob erneut, nachdem Sie Änderungen vornehmen.

## <a name="work-with-queue-resources"></a>Arbeiten mit Warteschlangenressourcen

Speicherdienstwarteschlangen werden in Azure Storage-Konto gehostet. Sie können diese verwenden, können Ihre Cloud-Dienstrollen, um miteinander und mit anderen Diensten über einen Nachrichtenübergabemechanismus zu kommunizieren. Sie können die Warteschlange programmgesteuert über einen Cloud-Dienst und über einen Webdienst für externe Clients zugreifen. Sie können auch die Warteschlange zugreifen, direkt unter Verwendung von Server-Explorer in Visual Studio.

Wenn Sie einen Cloud-Dienst, der Warteschlangen verwendet entwickeln, empfiehlt es sich, Sie mit Visual Studio zum Erstellen von Warteschlangen und interaktiv mit ihnen arbeiten beim Entwickeln und des Codes testen.

Im Server-Explorer können Sie die Warteschlangen in einem Speicherkonto anzeigen, erstellen und Löschen von Warteschlangen, öffnen Sie eine Warteschlange zum Anzeigen von Nachrichten und Nachrichten an eine Warteschlange hinzufügen. Wenn Sie eine Warteschlange zum Anzeigen öffnen, können Sie die einzelnen Nachrichten anzeigen, und Sie können die folgenden Aktionen für die Warteschlange ausführen, mithilfe der Schaltflächen in der oberen linken Ecke:

* Aktualisieren Sie die Ansicht der Warteschlange.
* Hinzufügen einer Nachricht an die Warteschlange.
* Die oberste Nachricht aus der Warteschlange entfernt.
* Löschen der gesamten Warteschlange an.

Die folgende Abbildung zeigt eine Warteschlange, die zwei Nachrichten enthält:

![Anzeigen einer Warteschlange](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Weitere Informationen über speicherdienstwarteschlangen finden Sie unter [erste Schritte mit Azure Queue Storage mit .NET](http://go.microsoft.com/fwlink/?LinkID=264702). Informationen über den Webdienst für speicherdienstwarteschlangen finden Sie unter [Konzepte des Warteschlangendiensts](http://go.microsoft.com/fwlink/?LinkId=264788). Informationen dazu, wie Sie Nachrichten an eine speicherdienstwarteschlange gesendet werden mithilfe von Visual Studio finden Sie unter [Senden von Nachrichten an eine Speicherdienstwarteschlange](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Speicherdienstwarteschlangen unterscheiden sich von Azure Service Bus-Warteschlangen. Weitere Informationen zu Service Bus-Warteschlangen, finden Sie unter [Service Bus-Warteschlangen, Themen und Abonnements](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Arbeiten mit tabellenressourcen

Azure-Tabellenspeicher speichert große Mengen von strukturierten Daten. Der Dienst ist ein NoSQL-Datenspeicher, der authentifizierte Aufrufe von innerhalb und außerhalb der Azure-Cloud akzeptiert. Azure-Tabellen eignen sich ideal zum Speichern strukturierter nicht relationaler Daten.

### <a name="to-create-a-table"></a>So erstellen Sie eine Tabelle

1. Wählen Sie im Cloud-Explorer die **Tabellen** Knoten des Storage-Konto, und wählen Sie dann **Create Table**.
1. In der **Create Table** Dialogfeld Geben Sie einen Namen für die Tabelle.

### <a name="to-view-table-data"></a>Anzeigen von Tabellendaten

1. Öffnen Sie im Cloud-Explorer die **Azure** Knoten, und öffnen Sie die **Storage** Knoten.
1. Öffnen Sie den Storage-Konto-Knoten, die Sie interessiert sind, und öffnen Sie dann die **Tabellen** Knoten aus, um eine Liste der Tabellen für das Speicherkonto anzuzeigen.
1. Öffnen Sie das Kontextmenü für eine Tabelle, und wählen Sie dann **Sichttabelle**.

    ![Eine Azure-Tabelle im Projektmappen-Explorer](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

In der Tabelle ist nach Entitäten (Anzeige in Zeilen) und Eigenschaften (Anzeige in Spalten) organisiert. Die folgende Abbildung zeigt beispielsweise Entitäten, die im Tabellen-Designer aufgeführt.

### <a name="to-edit-table-data"></a>So bearbeiten Sie Tabellendaten

Öffnen Sie im Tabellen-Designer das Kontextmenü für eine Entität (eine einzelne Zeile) oder eine Eigenschaft (eine einzelne Zelle), und wählen Sie dann **bearbeiten**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Entitäten in einer einzelnen Tabelle nicht erforderlich, um den gleichen Satz von Eigenschaften (Spalten) aufweisen. Beachten Sie zum Anzeigen und Bearbeiten von Tabellendaten folgenden Einschränkungen:

* Sie können nicht anzeigen oder Bearbeiten von Binärdaten (`type byte[]`), aber Sie können in einer Tabelle speichern.
* Kann nicht bearbeitet werden die **PartitionKey** oder **RowKey** Werte, da dieser Vorgang vom Tabellenspeicher in Azure unterstützt wird.
* Sie können nicht erstellt, eine Eigenschaft namens **Zeitstempel**. Azure Storage-Dienste verwenden eine Eigenschaft mit diesem Namen.
* Bei Eingabe ein **"DateTime"** Wert führen Sie ein Format, das entsprechend den Regions- und spracheinstellungen des Computers (z. B. MM/TT/JJJJ hh: mm: [AM | PM] für Englisch (USA)).

### <a name="to-add-entities"></a>So fügen Sie Entitäten hinzu

1. Wählen Sie im Tabellen-Designer die **Entität hinzufügen** Schaltfläche.

    ![Entity-Schaltfläche "hinzufügen"](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. In der **Entität hinzufügen** Dialogfeld Geben Sie die Werte der **PartitionKey** und **RowKey** Eigenschaften.

    ![Dialogfeld für die Entität hinzufügen](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Geben Sie die Werte sorgfältig aus. Sie können nicht ändern, nachdem Sie das Dialogfeld schließen, es sei denn, Sie die Entität gelöscht und erneut hinzufügen.

### <a name="to-filter-entities"></a>So filtern Sie Entitäten

Sie können den Satz von Entitäten anpassen, die in einer Tabelle angezeigt werden, wenn Sie den Abfrage-Generator verwenden.

1. Um den Abfrage-Generator zu öffnen, öffnen Sie eine Tabelle für die Anzeige.
1. Wählen Sie die **Abfragegenerator** auf der Symbolleiste die Schaltfläche.

    Die **Abfragegenerator** Dialogfeld wird angezeigt. Die folgende Abbildung zeigt eine Abfrage, die erstellt wird, im Abfrage-Generator.

    ![Abfrage-Generator](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Wenn Sie fertig sind Erstellen der Abfrage, um das Dialogfeld schließen. Die resultierende Textform der Abfrage wird in einem Textfeld als WCF Data Services-Filter angezeigt.
1. Wählen Sie das grüne Dreieckssymbol, um die Abfrage auszuführen.

Sie können auch die Entitätsdaten filtern, die im Tabellen-Designer wird angezeigt, wenn Sie geben Sie eine WCF Data Services-Filterzeichenfolge direkt in das Textfeld "Filter". Diese Art von Zeichenfolge ist vergleichbar mit einer SQL-WHERE-Klausel jedoch als eine HTTP-Anforderung an den Server gesendet wird. Weitere Informationen über das Erstellen von Filterzeichenfolgen finden Sie unter [Constructing von Filterzeichenfolgen für den Tabellen-Designer](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings).

Die folgende Abbildung zeigt ein Beispiel für eine gültige Filterzeichenfolge:

![Filterzeichenfolge](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Aktualisieren von Speicherdaten

Wenn Server-Explorer stellt eine Verbindung her oder Daten aus einem Speicherkonto Ruft, kann der Vorgang zu einer Minute dauern Fertig stellen. Wenn der Server-Explorer keine Verbindung herstellen können, ggf. ein Timeout des Vorgangs. Während Daten abgerufen werden, können Sie weiterhin in anderen Teilen von Visual Studio arbeiten. Um den Vorgang abzubrechen, wenn es zu lange dauert, wählen Sie die **aktualisieren beenden** auf der Symbolleiste des Server-Explorer.

### <a name="to-refresh-blob-container-data"></a>Aktualisieren von Blob-Containerdaten

* Wählen Sie die **Blobs** Knoten unterhalb **Storage**, und wählen Sie dann die **aktualisieren** auf der Symbolleiste des Server-Explorer.
* Um die Liste der Blobs zu aktualisieren, die angezeigt wird, wählen Sie die **Execute** Schaltfläche.

### <a name="to-refresh-table-data"></a>Aktualisieren Sie Tabellendaten

* Wählen Sie die **Tabellen** Knoten unterhalb **Storage**, und wählen Sie dann die **aktualisieren** auf der Symbolleiste des Server-Explorer.
* Um die Liste der Entitäten aktualisieren, die im Tabellen-Designer angezeigt wird, wählen die **Execute** Schaltfläche im Tabellen-Designer.

### <a name="to-refresh-queue-data"></a>Um Daten aus der Warteschlange zu aktualisieren.

Wählen Sie die **Warteschlangen** Knoten unterhalb **Storage**, und wählen Sie dann die **aktualisieren** auf der Symbolleiste des Server-Explorer.

### <a name="to-refresh-all-items-in-a-storage-account"></a>So aktualisieren Sie alle Elemente in einem Speicherkonto

Wählen Sie den Kontonamen, und wählen Sie dann die **aktualisieren** auf der Symbolleiste des Server-Explorer.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Hinzufügen von Speicherkonten mithilfe des Server-Explorer

Es gibt zwei Möglichkeiten, Speicherkonten mithilfe des Server-Explorer hinzuzufügen. Sie können ein Speicherkonto im Azure-Abonnement erstellen, oder Sie können ein vorhandenes Speicherkonto anfügen.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>So erstellen Sie ein Speicherkonto mithilfe von Server-Explorer

1. Öffnen Sie im Server-Explorer das Kontextmenü für die **Storage** Knoten, und wählen Sie dann **Create Storage Account**.

1. In der **Create Storage Account** Dialogfeld Feld, wählen Sie aus, oder geben Sie die folgende Informationen:

   * Das Azure-Abonnement zu dem Sie das Storage-Konto hinzufügen möchten.
   * Der Name, den Sie für das neue Speicherkonto verwenden möchten.
   * Die Region oder Affinitätsgruppe (z. B. USA, Westen oder Ostasien).
   * Den Typ der Replikation, die Sie z. B. für das Speicherkonto verwenden möchten lokal redundant.

   ![Erstellen Sie ein Azure Storage-Konto](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Wählen Sie **Erstellen** aus.

Das neue Speicherkonto wird angezeigt, der **Storage** Liste im Projektmappen-Explorer.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>So fügen Sie ein vorhandenes Speicherkonto mit Server-Explorer hinzu

1. Öffnen Sie im Server-Explorer das Kontextmenü für den Azure **Storage** Knoten, und wählen Sie dann **Externspeicher Anfügen**.

    ![Hinzufügen eines vorhandenen Speicherkontos](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. In der **Create Storage Account** Dialogfeld Feld, wählen Sie aus, oder geben Sie die folgende Informationen:

   * Der Name des vorhandenen Speicherkontos, das Sie anfügen möchten.
   * Der Schlüssel für das ausgewählte Speicherkonto an. Dieser Wert wird in der Regel für Sie bereitgestellt werden, wenn Sie ein Speicherkonto auswählen. Wenn Sie Visual Studio den speicherkontoschlüssel merken soll, wählen Sie die **kontoschlüssel merken** Kontrollkästchen.
   * Das Protokoll, für die Verbindung mit dem Speicherkonto, z. B. HTTP, HTTPS oder einen benutzerdefinierten Endpunkt verwenden. Weitere Informationen zu benutzerdefinierten Endpunkten finden Sie unter [Verbindungszeichenfolgen konfigurieren](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Der sekundäre Endpunkte anzeigen

Bei der Erstellung eines Speicherkontos unter Verwendung der **Read-Access Geo Redundant** Replication-Option, Sie können dessen sekundäre Endpunkte anzeigen, indem Sie öffnen das Kontextmenü für den Kontonamen, und wählen Sie dann **Eigenschaften**.

![Sekundäre speicherendpunkte](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>So entfernen Sie ein Speicherkonto im Server-Explorer

Klicken Sie im Server-Explorer öffnen das Kontextmenü für den Kontonamen, und wählen Sie dann **löschen**. 

Wenn Sie ein Speicherkonto löschen, wird auch alle gespeicherten Schlüsselinformationen für dieses Konto entfernt.

Wenn Sie ein Speicherkonto im Server-Explorer löschen, wirkt sich nicht es aus Ihrem Speicherkonto oder die darin enthaltenen Daten. Es werden lediglich der Verweis aus Server-Explorer entfernt. Um ein Speicherkonto dauerhaft zu löschen, verwenden die [Azure-Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwenden von Azure Storage-Dienste finden Sie unter [den Zugriff auf Azure-Speicherdienste](https://msdn.microsoft.com/library/azure/ee405490.aspx).
