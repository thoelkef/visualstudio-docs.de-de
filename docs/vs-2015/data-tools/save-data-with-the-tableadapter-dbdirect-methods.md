---
title: Speichern von Daten mit den TableAdapter-DBDirect Methoden | Microsoft-Dokumentation
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6bb326f1cad6ea019c5d057ca24d198c28dca2a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220810"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Speichern von Daten mit den TableAdapter-DBDirect-Methoden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Diese exemplarische Vorgehensweise enthält detaillierte Anweisungen zum Ausführen von SQL-Anweisungen direkt in einer Datenbank mithilfe von DBDirect-Methoden eines TableAdapters. DBDirect-Methoden eines TableAdapters bieten eine hochgradige Kontrolle über Ihre Datenbank. Können sie bestimmte SQL-Anweisungen und gespeicherte Prozeduren ausgeführt, indem die einzelnen `Insert`, `Update`, und `Delete` Methoden, die von Ihrer Anwendung nach Bedarf (im Gegensatz zur überladenen `Update` Methode, die das UPDATE ausführt. INSERT- und DELETE-Anweisungen in einem einzigen Aufruf).  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie ein neues **Windows-Anwendung**.  
  
-   Erstellen und konfigurieren Sie ein Dataset mit dem [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Wählen Sie das Steuerelement im Formular erstellt werden, beim Ziehen von Elementen aus der **Datenquellen** Fenster. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen ein datengebundenen Formulars durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
-   Hinzufügen von Methoden, um direkt auf die Datenbank zugreifen, und führen Sie einfügungen, Updates und löschungen...  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1.  In Visual Studio auf die **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2.  Nennen Sie das Projekt **TableAdapterDbDirectMethodsWalkthrough**.  
  
3.  Wählen Sie **Windows-Anwendung**, und wählen Sie anschließend**OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **TableAdapterDbDirectMethodsWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank  
 Dieser Schritt verwendet den **Assistenten zur Datenquellenkonfiguration** zum Erstellen einer Datenquelle basierend auf den `Region` -Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Auf der **Daten** , wählen Sie im Menü**Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.  
  
3.  Auf der **wählen Sie einen Datenquellentyp**auf **Datenbank**, und wählen Sie dann**Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung**Bildschirm, führen Sie eine der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und wählen Sie dann**Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern**auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen**Bildschirm, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die `Region` Tabelle, und wählen Sie dann**Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die `Region` Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols auf das Formular zum Anzeigen der Daten  
 Erstellen Sie datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Windows-Formular  
  
-   Ziehen Sie den Hauptknoten **Region** Knoten aus der **Datenquellen** auf das Formular.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Hinzufügen von Schaltflächen, die die einzelnen TableAdapter DbDirect-Methoden aufruft  
  
1.  Ziehen Sie drei <xref:System.Windows.Forms.Button> -Steuerelemente aus der **Toolbox** auf **Form1** (unterhalb der **RegionDataGridView**).  
  
2.  Legen Sie den folgenden **Namen** und **Text** Eigenschaften für jede Schaltfläche.  
  
    |name|Text|  
    |----------|----------|  
    |`InsertButton`|**Einfügen**|  
    |`UpdateButton`|**Update (Aktualisieren)**|  
    |`DeleteButton`|**Löschen**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Hinzufügen von Code für das Einfügen neuer Datensätze in die Datenbank  
  
1.  Wählen Sie**InsertButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.  
  
2.  Ersetzen Sie den Ereignishandler `InsertButton_Click`durch den folgenden Code:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Hinzufügen von Code für die Aktualisierung von Datensätzen in der Datenbank  
  
1.  Doppelklicken Sie auf die **UpdateButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.  
  
2.  Ersetzen Sie den Ereignishandler `UpdateButton_Click`durch den folgenden Code:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Hinzufügen von Code, um Datensätze aus der Datenbank zu löschen.  
  
1.  Wählen Sie**DeleteButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.  
  
2.  Ersetzen Sie den Ereignishandler `DeleteButton_Click`durch den folgenden Code:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Wählen Sie**F5** zum Ausführen der Anwendung.  
  
-   Wählen Sie die **einfügen** Schaltfläche, und stellen Sie sicher, dass der neue Datensatz im Raster angezeigt wird.  
  
-   Wählen Sie die **Update** Schaltfläche, und stellen Sie sicher, dass der Datensatz im Raster aktualisiert wird.  
  
-   Wählen Sie die **löschen** Schaltfläche, und stellen Sie sicher, dass der Eintrag aus dem Raster entfernt wird.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Je nach den Anforderungen Ihrer Anwendung sind mehrere Schritte, die Sie möglicherweise nach dem Erstellen eines datengebundenen Formulars ausführen möchten. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Fügen Sie dem Formular Suchfunktionalität hinzu. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer parametrisierten Abfrage auf einer Windows Forms-Anwendung](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Hinzufügen Weitere Tabellen zum Dataset dazu **DataSet mit Assistent konfigurieren** innerhalb der **Datenquellen** Fenster. Sie können Steuerelemente hinzufügen, die zugehörige Daten anzeigen, indem Sie die entsprechenden Knoten auf das Formular ziehen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen von verknüpften Daten in einer Windows Forms-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

