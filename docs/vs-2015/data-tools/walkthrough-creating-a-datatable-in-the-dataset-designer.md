---
title: 'Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 832dba200fca438d000bae101381389ea20cfb17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512514"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird erläutert, wie zum Erstellen einer <xref:System.Data.DataTable> (ohne einen TableAdapter) mithilfe der **Dataset-Designer**. Informationen zum Erstellen von Datentabellen, die TableAdapters enthalten, finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen ein neues Windows-Anwendungsprojekt  
  
-   Hinzufügen eines neuen Datasets für die Anwendung  
  
-   Das Dataset hinzugefügt eine neue Datentabelle  
  
-   Hinzufügen von Spalten zur Datentabelle  
  
-   Festlegen des Primärschlüssels für die Tabelle  
  
## <a name="creating-a-new-windows-application"></a>Erstellen einer neuen Windows-Anwendung.  
  
#### <a name="to-create-a-new-windows-application-project"></a>So erstellen Sie ein neues Windows-Anwendungsprojekt  
  
1.  Von der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Wählen Sie eine Programmiersprache, in der **Projekttypen** Bereich.  
  
3.  Klicken Sie auf **Windows-Anwendung** in die **Vorlagen** Bereich.  
  
4.  Nennen Sie das Projekt `DataTableWalkthrough`, und klicken Sie dann auf **OK**.  
  
     Visual Studio fügt das Projekt in **Projektmappen-Explorer** und zeigt **Form1** im Designer.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>So fügen Sie dem Projekt ein neues Dataset-Element hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld Neues Element hinzufügen wird angezeigt.  
  
2.  In der **Vorlagen** Kontrollkästchen **DataSet**.  
  
3.  Klicken Sie auf **Hinzufügen**.  
  
     Visual Studio fügt eine Datei namens **DataSet1.xsd** auf das Projekt, und öffnen sie in der **Dataset-Designer**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Das Dataset hinzugefügt eine neue DataTable  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Eine neue Datentabelle mit dem Dataset hinzufügen  
  
1.  Ziehen Sie eine **DataTable** aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.  
  
     Eine Tabelle namens **DataTable1** zum Dataset hinzugefügt wird.  
  
    > [!NOTE]
    >  Um eine Datentabelle zu erstellen, die einen TableAdapter enthält, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Klicken Sie auf der Titelleiste des Fensters **DataTable1** und benennen Sie sie `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Hinzufügen von Spalten zur Datentabelle  
  
#### <a name="to-add-columns-to-the-data-table"></a>Um die Datentabelle Spalten hinzuzufügen  
  
1.  Mit der rechten Maustaste die **Musik** Tabelle. Zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Spalte**.  
  
2.  Den Namen der Spalte `SongID`.  
  
3.  In der **Eigenschaften** legen die <xref:System.Data.DataColumn.DataType%2A> Eigenschaft <xref:System.Int16?displayProperty=fullName>.  
  
4.  Wiederholen Sie diesen Vorgang aus, und fügen Sie die folgenden Spalten:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Festlegen des Primärschlüssels für die Tabelle  
 Alle Datentabellen sollte es sich um einen Primärschlüssel besitzen können. Ein primärer Schlüssel identifiziert eindeutig einen bestimmten Datensatz in einer Datentabelle.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Der Primärschlüssel der Datentabelle festgelegt.  
  
-   Mit der rechten Maustaste die **SongID** Spalte, und klicken Sie dann auf **Primärschlüssel festlegen**.  
  
     Ein Schlüsselsymbol wird neben der **SongID** Spalte.  
  
## <a name="saving-your-project"></a>Beim Speichern des Projekts  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Zum Speichern des Projekts DataTableWalkthrough  
  
-   Auf der **Datei** Menü klicken Sie auf **Alles speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nun, dass Sie in der Tabelle erstellt haben, empfiehlt es sich um eine der folgenden Aktionen auszuführen:  
  
|Beschreibung|Siehe|  
|--------|---------|  
|Erstellen Sie ein Formular, um die Eingabedaten|[Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Hinzufügen von Daten in die Tabelle|[Hinzufügen von Daten zu einer "DataTable"](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Anzeigen von Daten in einer Tabelle|[Anzeigen von Daten in einer "DataTable"](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Bearbeiten von Daten|[Bearbeitungen von DataTable](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Löschen einer Zeile aus einer Tabelle|[DataRow-Löschung](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Siehe auch  
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)