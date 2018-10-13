---
title: 'Vorgehensweise: Erstellen von TableAdapter-Abfragen | Microsoft-Dokumentation'
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c4b800bcb70e41e1d80bf9a0a37d72f08f78c7a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195545"
---
# <a name="how-to-create-tableadapter-queries"></a>Gewusst wie: Erstellen von TableAdapter-Abfragen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter-Abfragen sind SQL-Anweisungen oder gespeicherte Prozeduren, die Ihre Anwendung für eine Datenbank ausführen kann.  
  
 Fügen Sie so viele Abfragen einen TableAdapter die Anwendung erforderlich sind. TableAdapter-Abfragen werden als Methoden für einen TableAdapter angezeigt. Beim Erstellen einer Abfrage mit dem Namen `FillByCity` , die akzeptiert eines Parameters, der Wert für den Ort darstellt, wird die Abfrage der TableAdapter hinzugefügt. Es wird hinzugefügt, als eine typisierte Methode, die den richtigen Typ des Parameters als Argument akzeptiert – in diesem Fall eine Zeichenfolge, die den Wert für den Ort darstellt. Sie haben die TableAdapter-Abfrage wie jede Methode für jedes Objekt aufrufen. Der folgende Code beispielsweise führt die `FillByCity` Abfrage- und füllt die `Customers` Tabelle mit allen Kunden mit einem City-Wert, der `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 TableAdapter-Abfragen können eine Tabelle eingeben (`Fill` und `FillBy` Abfragen) oder neue Datentabellen, die mit den Daten, die von der Abfrage zurückgegebenen aufgefüllt zurückgeben (`GetData` und `GetDataBy` Abfragen).  
  
 Sie können Abfragen auf vorhandene TableAdapters hinzufügen, mit der [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md). (Mit der rechten Maustaste in einen beliebigen TableAdapter, und wählen Sie **Abfrage hinzufügen**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Erstellen Sie eine Abfrage im Dataset-Designer  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Zum Hinzufügen einer Abfrage zu einem TableAdapter im Dataset-Designer  
  
1.  Öffnen Sie ein Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Mit der rechten Maustaste in des gewünschten TableAdapter, und wählen **Abfrage hinzufügen**.  
  
     - oder -   
  
3.  Ziehen Sie eine **Abfrage** aus der **DataSet** Registerkarte die **Toolbox** auf eine Tabelle im Designer.  
  
     Die **Konfigurations-Assistenten für TableAdapter-Abfragen** wird geöffnet.  
  
4.  Schließen Sie den Assistenten; die Abfrage wird dem TableAdapter hinzugefügt.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Erstellen Sie eine Abfrage direkt auf einem Formular in der Windows-Anwendung  
 Wenn Sie eine Instanz eines TableAdapter auf dem Formular haben können Sie hinzufügen, eine Abfrage mit der [-Generator das Dialogfeld Suchkriterien](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), wird eine <xref:System.Windows.Forms.ToolStrip> -Steuerelement auf das Formular, das akzeptiert alle benötigten Eingabeparameter, die von der Abfrage erforderlich als auch ein Schaltfläche, um die Abfrage auszuführen.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Zum Hinzufügen einer Abfrage einen TableAdapter mithilfe des Dialogfelds Suchkriterien  
  
1.  Wählen Sie einen TableAdapter in der Komponentenleiste.  
  
2.  Klicken Sie auf dem TableAdapter-Smarttag, und wählen **Abfrage hinzufügen**.  
  
3.  Schließen Sie das Dialogfeld, und die Abfrage wird dem TableAdapter hinzugefügt. Weitere Informationen finden Sie unter [-Generator das Dialogfeld Suchkriterien](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Vorgehensweise: Bearbeiten von TableAdapter-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Erstellen und Bearbeiten von typisierten "Datasets"](../data-tools/creating-and-editing-typed-datasets.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Vorgehensweise: Datennavigation mithilfe des BindingNavigator-Steuerelements in Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)