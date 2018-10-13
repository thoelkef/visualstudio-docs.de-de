---
title: 'Exemplarische Vorgehensweise: Verbinden mit Daten in einer lokalen Datenbankdatei (Windows Forms) | Microsoft-Dokumentation'
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
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 71898c88a8d7a1d4a119a7e7a932e295ae12eb34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176162"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten aus einer lokalen Datenbankdatei in der Anwendung schnell und problemlos anzeigen, indem Sie ein DataSet erstellen und der Anwendung datengebundene Steuerelemente hinzufügen. In dieser exemplarischen Vorgehensweise zeigen Sie Daten aus der lokalen Datenbankdatei, die Sie erstellt haben, indem Sie die Schritte in [erstellen Sie eine SQL­Datenbank mithilfe eines Designers](../data-tools/create-a-sql-database-by-using-a-designer.md). Nachdem Sie ein Windows Forms-Projekt erstellt haben, stellen Sie eine Verbindung mit dieser Datenbank her, und legen fest, dass Sie Daten aus der Tabelle "Customers" in einem Datenraster auf dem Formular für die Anwendung angezeigt werden sollen.  
  
 Wenn Sie eine Datenbank in Visual Studio 2013 erstellen, wird die SQL Server Express LocalDB-Engine verwendet, um auf eine Datenbankdatei (MDF) in SQL Server 2012 zuzugreifen. In früheren Versionen von Visual Studio wird die SQL Server Express-Engine verwendet, um auf eine Datenbankdatei (MDF) zuzugreifen. Finden Sie unter [Übersicht über lokale Daten](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:  
  
-   [Erstellen und Konfigurieren eines Datasets](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Hinzufügen von datengebundenen Steuerelementen](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise abzuschließen, benötigen Sie Zugriff auf die SampleDatabase.mdf-Datenbank, die Sie erstellen [erstellen Sie eine SQL­Datenbank mithilfe eines Designers](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Erstellen und Konfigurieren eines Datasets  
  
#### <a name="to-create-and-configure-a-dataset"></a>So erstellen und konfigurieren Sie ein Dataset  
  
1.  Erstellen Sie ein Windows Forms-Projekt, und nennen Sie es **"connectlocaldata"**.  
  
     Finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Wenn die **Datenquellen** Fenster nicht angezeigt, wählen Sie die Tasten UMSCHALT + Alt + D, oder wählen Sie auf der Menüleiste **Ansicht**, **Other Windows**, **Datenquellen anzeigen**.  
  
3.  In der **Datenquellen** Fenster, wählen Sie die **neue Datenquelle hinzufügen** Link.  
  
     In der **Assistenten zur Datenquellenkonfiguration**, wählen Sie die **Weiter** Schaltfläche zweimal, um die Standardeinstellungen zu übernehmen.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite die **neue Verbindung** Schaltfläche.  
  
     Die **Datenquelle auswählen** Dialogfeld wird angezeigt.  
  
5.  In der **Datenquelle** wählen **Microsoft SQL Server-Datenbankdatei**, und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Die **Verbindung hinzufügen** Dialogfeld wird angezeigt.  
  
6.  In der **Name der Datenbankdatei** geben die Datei, die Sie erstellt [erstellen Sie eine SQL­Datenbank mithilfe eines Designers](../data-tools/create-a-sql-database-by-using-a-designer.md), oder wählen Sie die **Durchsuchen** Schaltfläche, und suchen Sie dann Diese Datei.  
  
     Die Datei wird standardmäßig Benutzern\\*Ihrkonto*\Documents\Visual Studio *Version*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  Unter **am Server anmelden**, die Standardwerte übernehmen, wählen Sie die **OK** Schaltfläche, und wählen Sie dann die **Weiter** Schaltfläche.  
  
    > [!NOTE]
    >  Beim Herstellen einer Verbindung mit einer lokalen Datenbankdatei können Sie entweder eine Kopie der Datenbank in Ihrem Projekt erstellen oder eine Verbindung mit der vorhandenen Datenbankdatei an ihrem aktuellen Speicherort herstellen. Finden Sie unter [Vorgehensweise: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  Wählen Sie im angezeigten Dialogfeld **Ja** auf die Datenbankdatei in Ihr Projekt kopieren.  
  
9. Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite die **Weiter** Schaltfläche.  
  
10. Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten die **Kunden** und **Bestellungen** Kontrollkästchen, und klicken Sie dann Wählen Sie die **Fertig stellen** Schaltfläche.  
  
     Die **SampleDatabaseDataSet** wird Ihrem Projekt hinzugefügt und die **Kunden** und **Bestellungen** Tabellen angezeigt werden, der **Datenquellen** Fenster.  
  
##  <a name="BKMK_AddCtrls"></a> Hinzufügen von datengebundenen Steuerelementen  
  
#### <a name="to-add-data-bound-controls"></a>So fügen Sie datengebundene Steuerelemente hinzu  
  
1.  Verschieben Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf **Form1**.  
  
     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip-Element (<xref:System.Windows.Forms.BindingNavigator>) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können. Ein [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
2.  Um die Anwendung auszuführen und die Daten anzuzeigen, die Sie in der vorherigen exemplarischen Vorgehensweise hinzugefügt haben, drücken Sie die Taste F5.  
  
3.  Wählen Sie das gelbe Symbol zum Hinzufügen (![Schaltfläche "hinzufügen" im Windows-Formular](../data-tools/media/addrecord.png "AddRecord")), fügen Sie einen Kundendatensatz hinzu, und klicken Sie dann speichern Sie die Änderungen, indem Sie das Datenträgersymbol auswählen (![Schaltfläche "Speichern" im Windows-Formular](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Löschen des Eintrags, den Sie gerade erstellt haben, indem Sie ihn auswählen und dann auf das rote Löschsymbol (![löschen-Schaltfläche in der Windows-Formular](../data-tools/media/deleterecord.png "DeleteRecord")).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie erstellen oder Ändern von Objekten im Dataset, wenn Sie die Datenquelle im öffnen können die [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md). Sie können dem Ereignis <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> der Datentabellen im DataSet auch eine Validierungslogik hinzufügen. Finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über lokale Daten](../data-tools/local-data-overview.md)   
 [Vorgehensweise: Verwalten von lokalen Datendateien im Projekt](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)