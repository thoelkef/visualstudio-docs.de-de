---
title: Speichern von Daten in einer Datenbank (mehrere Tabellen) | Microsoft-Dokumentation
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 986df2d58c9a8955c9de9b45edaa5276b2e68bfb
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218403"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Speichern von Daten in einer Datenbank (mehrere Tabellen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Eines der häufigsten Szenarios in der Anwendungsentwicklung ist das Anzeigen von Daten auf einem Formular in einer Windows-Anwendung, das Bearbeiten der Daten und das Senden der aktualisierten Daten zurück an die Datenbank. In dieser exemplarischen Vorgehensweise wird ein Formular erstellt, in dem Daten aus zwei verknüpften Tabellen angezeigt werden. Darüber hinaus wird gezeigt, wie Datensätze bearbeitet und Änderungen wieder in der Datenbank gespeichert werden. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.  
  
 Sie können Daten in der Anwendung wieder in der Datenbank speichern, indem Sie die `Update`-Methode eines TableAdapter aufrufen. Beim Ziehen von Tabellen aus der **Datenquellen** auf das Formular, den Code, der zum Speichern von Daten erforderlich ist, wird automatisch hinzugefügt. Weiteren Tabellen, die zu einem Formular hinzugefügt werden, erfordern das manuelle Hinzufügen dieses Codes. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Code hinzugefügt wird, um Aktualisierungen aus mehreren Tabellen zu speichern.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Befehle im Menü angezeigten unterscheiden sich von den in der Hilfe beschriebenen, je nach Ihren aktiven Einstellungen oder die Edition, die Sie verwenden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen **Windows-Anwendung** Projekt.  
  
-   Erstellen und Konfigurieren einer Datenquelle in Ihrer Anwendung mit der [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Festlegen der Steuerelemente für die Elemente in der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
-   Ändern einige Datensätze in jeder Tabelle im Dataset.  
  
-   Ändern von Code zum Zurücksenden der aktualisierten Daten des Datasets an die Datenbank.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Erstellen Sie die Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**. Während dieses Schritts ist ein Name zugewiesen, auf das Projekt optional, aber wir geben einen Namen, da wir beabsichtigen, es später gespeichert.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Um das neue Windows-Anwendungsprojekt zu erstellen.  
  
1.  Auf der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Benennen Sie das Projekt mit `UpdateMultipleTablesWalkthrough`.  
  
3.  Wählen Sie **Windows-Anwendung**, und wählen Sie dann **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **UpdateMultipleTablesWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Erstellen der Datenquelle  
 Dieser Schritt wird eine Datenquelle erstellt, aus der Northwind-Datenbank mithilfe der **Assistenten zur Datenquellenkonfiguration**. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Auf der **Daten** , wählen Sie im Menü**Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster**neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.  
  
3.  Auf der **wählen Sie einen Datenquellentyp**auf **Datenbank**, und wählen Sie dann **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung**Bildschirm führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** zum Öffnen der **Verbindung hinzufügen/ändern** Dialogfeld.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern**Option **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen**Bildschirm, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die **Kunden** und **Bestellungen** Tabellen, und wählen Sie dann **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die Tabellen werden der **Datenquellen** Fenster.  
  
## <a name="set-the-controls-to-be-created"></a>Festlegen der Kontrollen, die erstellt werden  
 In dieser exemplarischen Vorgehensweise die Daten in die `Customers` Tabelle befindet sich in einem **Details** Layout, in denen die Daten in einzelnen Steuerelementen angezeigt. Die Daten aus der `Orders` Tabelle befindet sich in einem **Raster** Layout, das angezeigt wird eine <xref:System.Windows.Forms.DataGridView> Steuerelement.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest  
  
1.  In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten.  
  
2.  Auf der **Kunden** Knoten **Details** aus der Steuerungsliste so ändern Sie die Kontrolle über die **Kunden** Table in einzelne Steuerelemente. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Erstellen des datengebundenen Formulars  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
1.  Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf **Form1**.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
2.  Ziehen Sie den zugehörigen **Bestellungen** Knoten aus der **Datenquellen** auf **Form1**.  
  
    > [!NOTE]
    >  Die zugehörigen **Bestellungen** Knoten befindet sich unterhalb der **Fax** Spalte und ist ein untergeordneter Knoten von der **Kunden** Knoten.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [OrdersTableAdapter](../data-tools/tableadapter-overview.md) und <xref:System.Windows.Forms.BindingSource> werden in der Komponentenleiste angezeigt.  
  
## <a name="addcode-to-update-the-database"></a>Addcode zum Aktualisieren der Datenbank  
 Sie können die Datenbank aktualisieren, durch den Aufruf der `Update` Methoden der der **Kunden** und **Bestellungen** TableAdapters. Standardmäßig wird ein Ereignishandler für die **speichern** -Schaltfläche der<xref:System.Windows.Forms.BindingNavigator> Code des Formulars zum Senden von Updates in der Datenbank hinzugefügt. In dieser Prozedur wird den Code zum Senden von Updates in der richtigen Reihenfolge. Dadurch wird die Möglichkeit, referenzielle Integritätsfehler auslösen. Mit dem Code wird außerdem die Fehlerbehandlung implementiert, indem der Aktualisierungsaufruf mit einem Try-Catch-Block umschlossen wird. Sie können den Code entsprechend den Anforderungen der Anwendung anpassen.  
  
> [!NOTE]
>  Aus Gründen der Übersichtlichkeit wird in dieser exemplarischen Vorgehensweise eine Transaktion nicht verwendet. Wenn jedoch aktualisieren Sie zwei oder mehr verknüpfte Tabellen, enthalten Sie alle Aktualisierungslogik einer Transaktion. Eine Transaktion ist ein Prozess, der gewährleistet, dass alle zugehörige Änderungen an einer Datenbank erfolgreich sind, bevor ein Commit für Änderungen ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen und Parallelität](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>So fügen Sie der Anwendung Aktualisierungslogik hinzu  
  
1.  Wählen Sie die **speichern** Schaltfläche der <xref:System.Windows.Forms.BindingNavigator>. Daraufhin wird der Code-Editor in die `bindingNavigatorSaveItem_Click` -Ereignishandler.  
  
2.  Ändern Sie den Code im Ereignishandler, sodass die `Update`-Methoden der verknüpften TableAdapters aufgerufen werden. Mit folgendem Code werden zunächst drei temporäre Datentabellen zum Speichern der aktualisierten Informationen für jeden <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> und <xref:System.Data.DataRowState>) erstellt. Updates werden dann in der richtigen Reihenfolge ausgeführt. Der Code sollte wie folgt aussehen:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Wählen Sie **F5**.  
  
2.  Nehmen Sie in jeder Tabelle einige Änderungen an den Daten eines oder mehrerer Datensätze vor.  
  
3.  Wählen Sie die **speichern** Schaltfläche.  
  
4.  Überprüfen Sie die Werte in der Datenbank, um sicherzustellen, dass die Änderungen gespeichert wurden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Je nach den Anforderungen Ihrer Anwendung sind mehrere Schritte, die Sie möglicherweise nach dem Erstellen eines datengebundenen Formulars in der Windows-Anwendung ausführen möchten. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Fügen Sie dem Formular Suchfunktionalität hinzu. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer parametrisierten Abfrage auf einer Windows Forms-Anwendung](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Bearbeiten der Datenquelle zum Hinzufügen oder Entfernen von Datenbankobjekten. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten eines Datasets](http://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

