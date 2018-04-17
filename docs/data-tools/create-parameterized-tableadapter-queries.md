---
title: Parametrisierte TableAdapter-Abfragen erstellen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 361bb7f9acea5d07283b63cb1b3b1b97bb495a8e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-parameterized-tableadapter-queries"></a>Erstellen von parametrisierten TableAdapter-Abfragen
Eine parametrisierte Abfrage gibt Daten zurück, die den Bedingungen einer WHERE-Klausel in der Abfrage entsprechen. Sie können beispielsweise eine Kundenliste parametrisieren, sodass nur Kunden in einem bestimmten Ort angezeigt werden. Fügen Sie dazu `WHERE City = @City` am Ende der SQL-Anweisung hinzu, was eine Liste von Kunden ausgibt.  
  
 Erstellen Sie parametrisierte TableAdapter-Abfragen in der **Dataset-Designer**. Sie können diese auch erstellen, in einer Windows-Anwendung mit der **parametrisierte Datenquelle** Befehl die **Daten** Menü. Die **parametrisierte Datenquelle** Befehl erstellt die Steuerelemente im Formular, in dem Sie die Eingabe von Parameterwerten und führen Sie die Abfrage können.  
  
> [!NOTE]
>  Wenn Sie eine parametrisierte Abfrage zu erstellen, verwenden Sie die Parameter-Notation, die für die Datenbank spezifisch ist, die Sie gegen codieren. Access- und OleDb-Datenquellen verwenden, z. B. das Fragezeichen "?" zur Angabe von Parametern, sodass die WHERE-Klausel wie folgt aussehen würde: `WHERE City = ?`.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle, die Sie sehen möglicherweise unterscheiden sich von denen je nach Ihren aktiven Einstellungen oder der Edition, die Sie verwenden in der Hilfe beschriebenen. Um die Einstellungen zu ändern, wechseln Sie zu der **Tools** Menü **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-parameterized-tableadapter-query"></a>Erstellen einer parametrisierten TableAdapter-Abfrage  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>So erstellen Sie parametrisierte Abfrage im DataSet-Designer  
  
-   Erstellen Sie einen neuen TableAdapter und fügen Sie eine WHERE-Klausel mit den gewünschten Parametern zur SQL-Anweisung hinzu. Weitere Informationen finden Sie unter [erstellen und Konfigurieren von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     - oder -   
  
-   Fügen Sie eine Abfrage zu einem vorhandenen TableAdapter hinzu und dann eine WHERE-Klausel mit den gewünschten Parametern für die SQL-Anweisung.
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>So erstellen Sie eine parametrisierte Abfrage beim Entwerfen eines datengebundenen Formulars  
  
1.  Wählen Sie ein Steuerelement auf dem Formular, das bereits an ein Dataset gebunden ist. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Auf der **Daten** klicken Sie im Menü **Abfrage hinzufügen**.  
  
3.  Führen Sie die **Suchkriterien-Generator** (Dialogfeld), die SQL-Anweisung eine WHERE-Klausel mit den gewünschten Parametern hinzugefügt.  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>So fügen Sie eine Abfrage einem vorhandenen datengebundenen Formular hinzu  
  
1.  Öffnen Sie das Formular in der **Windows Forms-Designer**.  
  
2.  Auf der **Daten** klicken Sie im Menü **Abfrage hinzufügen** oder **Smart Tags für Daten**.  
  
    > [!NOTE]
    >  Wenn **Abfrage hinzufügen** ist nicht verfügbar, auf die **Daten** Menü, wählen Sie ein Steuerelement auf dem Formular, zeigt Sie Datenquellen die Parametrisierung hinzufügen möchten. Wenn das Formular beispielsweise Daten in einem <xref:System.Windows.Forms.DataGridView>-Steuerelement anzeigt, wählen Sie dieses aus. Wenn das Formular Daten in einzelnen Steuerelementen anzeigt, wählen Sie irgendein datengebundenes Steuerelement.  
  
3.  In der **Select Datenquellentabelle** Bereich, markieren Sie die Tabelle die gewünschten hinzufügen Parametrisierung.  
  
4.  Geben Sie einen Namen in der **Neuer Abfragename** Feld, wenn Sie eine neue Abfrage erstellen.  
  
     - oder -   
  
     Wählen Sie eine Abfrage in der **vorhandener Abfragename** Feld.  
  
5.  In der **Abfragetext** Geben Sie eine Abfrage, die Parameter annimmt.  
  
6.  Klicken Sie auf **OK**.  
  
     Ein Steuerelement für die Eingabe des Parameters und eine **laden** Schaltfläche werden hinzugefügt, in das Formular in einer <xref:System.Windows.Forms.ToolStrip> Steuerelement.  
  
#### <a name="querying-for-null-values"></a>Abfragen von null-Werte  
TableAdapter-Parameter können null-Werte zugewiesen werden, wenn Sie Datensätze Abfragen, die keinen aktuellen Wert haben möchten. Betrachten Sie beispielsweise die folgende Abfrage, die verfügt über eine `ShippedDate` Parameter in seiner `WHERE` Klausel:  
  
 ```sql
SELECT CustomerID, OrderDate, ShippedDate  
FROM Orders  
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```  
  
 Wenn dies eine Abfrage für einen TableAdapter wäre, konnte Sie für alle Aufträge Abfragen, die nicht durch den folgenden Code gesendet wurden:  
  
 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]  

 So aktivieren Sie eine Abfrage, um null-Werte annehmen:

1.  In der **Dataset-Designer**, wählen Sie die TableAdapter-Abfrage, die der null-Parameterwerte akzeptieren muss.  
  
2.  In der **Eigenschaften** wählen **Parameter**, klicken Sie dann auf die Auslassungspunkte (**...** ) die Schaltfläche, um die **Editor für die Parameters-Auflistung**.  
  
3.  Wählen Sie den Parameter, die null-Werte zulässt, und legen Sie die **AllowDbNull** Eigenschaft `true`.  
  
## <a name="see-also"></a>Siehe auch  
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)