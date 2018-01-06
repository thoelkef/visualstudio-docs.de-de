---
title: "Hinzufügen von Validierungen zu einem n-Tier-Dataset | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a3f37b734bb9d109634fc272fca3140d40c040f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Hinzufügen von Validierungen zu einem n-Tier-dataset
Validierungen werden einem DataSet, das in eine N-Tier-Projektmappe aufgeteilt ist, grundsätzlich auf die gleiche Art hinzugefügt wie einem DataSet in einer einzelnen Datei (in einem einzelnen Projekt). Es wird empfohlen, die Datenvalidierung während des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses und/oder des <xref:System.Data.DataTable.RowChanging>-Ereignisses einer Datentabelle auszuführen.  
  
 Das Dataset bietet die Funktionalität zum Erstellen von partiellen Klassen, die Sie Benutzercode auf Ereignisse Spalte und Zeile ändern, der Datentabellen im Dataset hinzufügen können. Weitere Informationen zum Hinzufügen von Code zu einem Dataset in einer n-Tier-Projektmappe finden Sie unter [fügen Code zu Datasets in n-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md), und [fügen Code zu TableAdapters in n-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Weitere Informationen zu partiellen Klassen finden Sie unter [wie: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) oder [partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
> [!NOTE]
>  Bei einer Abtrennung der Datasets von TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle Dataset-Klassen müssen manuell in das Dataset-Projekt verschoben werden.  
  
> [!NOTE]
>  Das Dataset-Designer erstellt nicht automatisch Ereignishandler in c# für den <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> Ereignisse. Sie müssen manuell einen Ereignishandler erstellen und den Ereignishandler an das zugrunde liegenden Ereignis verknüpfen. Die folgenden Verfahren wird beschrieben, wie die erforderlichen Ereignishandler in Visual Basic und c# zu erstellen.  
  
## <a name="validate-changes-to-individual-columns"></a>Überprüfen Sie die Änderungen in einzelnen Spalten  
 Validieren Sie die Werte in einzelnen Spalten durch Behandeln des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses. Die <xref:System.Data.DataTable.ColumnChanging> Ereignis wird ausgelöst, wenn ein Wert in einer Spalte geändert wird. Erstellen Sie einen Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging> Ereignis durch Doppelklicken auf die gewünschte Spalte auf die **Dataset-Designer**.  
  
 Beim ersten Doppelklicken auf eine Spalte wird vom Designer ein Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis erstellt. Ein `If...Then` Anweisung wird auch erstellt, die für die spezifische Spalte testet. Beispielsweise wird der folgende Code generiert, wenn Sie auf die RequiredDate-Spalte der Tabelle Northwind Orders doppelklicken:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  In C#-Projekten werden vom DataSet-Designer nur partielle Klassen für das DataSet sowie einzelne Tabellen im DataSet erstellt. Vom DataSet-Designer werden in C#, im Gegensatz zu Visual Basic, nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis und das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. In C#-Projekten müssen Sie manuell erstellen, eine Methode zum Behandeln des Ereignisses, und die Methode, die die zugrunde liegenden Ereignis verknüpfen. Das folgende Verfahren erläutert die Schritte, um die erforderlichen Ereignishandler sowohl in Visual Basic als auch in C# zu erstellen.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>So fügen Sie Validierungen bei Änderung einzelner Spaltenwerte hinzu  
  
1.  Öffnen Sie das Dataset durch Doppelklicken auf die **XSD** Datei **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Doppelklicken Sie auf die zu validierende Spalte. Durch diese Aktion wird der <xref:System.Data.DataTable.ColumnChanging>-Ereignishandler erstellt.  
  
    > [!NOTE]
    >  Der Dataset-Designer erstellt den Ereignishandler für das C#-Ereignis nicht automatisch. Der Code, der für die Ereignisbehandlung in c# erforderlich ist, wird im nächsten Abschnitt enthalten. `SampleColumnChangingEvent`erstellt und verknüpft dann bis zu den <xref:System.Data.DataTable.ColumnChanging> Ereignis in der <xref:System.Data.DataTable.EndInit%2A> Methode.  
  
3.  Fügen Sie Code hinzu, mit dem überprüft wird, ob die Daten in `e.ProposedValue` den Anforderungen der Anwendung entsprechen. Wenn der vorgeschlagene Wert unzulässig ist, legen Sie für die Spalte fest, dass ein Fehler angezeigt wird.  
  
     Im folgenden Codebeispiel wird überprüft, ob die **Menge** Spalte enthält einen Wert größer als 0. Wenn **Menge** ist kleiner als oder gleich 0 ist, wird der Spaltensatz zu einem Fehler. Die `Else` -Klausel löscht den Fehler, wenn **Menge** ist größer als 0. Der Code im spaltenändernden Ereignishandler sollte etwa folgendermaßen aussehen:  
  
    ```vb  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```    
    ```csharp  
    // Add this code to the DataTable partial class.  
  
    public override void EndInit()  
    {  
        base.EndInit();  
        // Hook up the ColumnChanging event  
        // to call the SampleColumnChangingEvent method.  
        ColumnChanging += SampleColumnChangingEvent;  
    }  
  
    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)  
    {  
        if (e.Column.ColumnName == QuantityColumn.ColumnName)  
        {  
            if ((short)e.ProposedValue <= 0)  
            {  
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
            }  
            else  
            {  
                e.Row.SetColumnError("Quantity", "");  
            }  
        }  
    }  
    ```  
  
## <a name="validate-changes-to-whole-rows"></a>Überprüfen Sie die Änderungen an ganzen Zeilen  
 Überprüfen Sie Werte in ganzen Zeilen durch Behandeln des <xref:System.Data.DataTable.RowChanging>-Ereignisses. Das <xref:System.Data.DataTable.RowChanging>-Ereignis wird ausgelöst, wenn ein Commit für die Werte in allen Spalten ausgeführt wird. Wenn der Wert in einer Spalte von dem Wert in einer anderen Spalte abhängt, ist es erforderlich, dies im <xref:System.Data.DataTable.RowChanging>-Ereignis zu überprüfen. Betrachten Sie beispielsweise OrderDate und RequiredDate in der Tabelle Orders in Northwind.  
  
 Wenn die Bestellungen eingegeben werden, wird durch die Validierung sichergestellt, dass keine Bestellung mit einem RequiredDate eingegeben wird, das vor dem OrderDate liegt oder mit diesem übereinstimmt. In diesem Beispiel müssen die Werte für die Spalten RequiredDate und OrderDate verglichen werden, es ist daher nicht sinnvoll, eine einzelne Spaltenänderung zu überprüfen.  
  
 Erstellen Sie einen Ereignishandler für das <xref:System.Data.DataTable.RowChanging> Ereignis durch Doppelklicken auf den Tabellennamen in der Titelleiste der Tabelle auf die **Dataset-Designer**.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>So fügen Sie Validierungen bei Änderung ganzer Zeilen hinzu  
  
1.  Öffnen Sie das Dataset durch Doppelklicken auf die **XSD** Datei **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Doppelklicken Sie im Designer auf die Titelleiste der Datentabelle.  
  
     Eine partielle Klasse wird mit einem `RowChanging`-Ereignishandler erstellt und im Code-Editor geöffnet.  
  
    > [!NOTE]
    >  Vom DataSet-Designer wird in C#-Projekten nicht automatisch ein Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. Erstellen Sie eine Methode zum Behandeln der <xref:System.Data.DataTable.RowChanging> Ereignis und Code auszuführen, klicken Sie dann das Ereignis in der Initialisierungsmethode der Tabelle verknüpft.  
  
3.  Fügen Sie Benutzercode innerhalb der Deklaration der partiellen Klasse hinzu.  
  
4.  Der folgende Code zeigt, wo Sie Benutzercode zur Validierung beim Hinzufügen der <xref:System.Data.DataTable.RowChanging> Ereignis. Das C#-Beispiel enthält auch Code aus, um die Ereignishandlermethode zum Einbinden der `OrdersRowChanging` Ereignis.  
  
    ```vb  
    Partial Class OrdersDataTable  
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging  
            ' Add logic to validate columns here.  
            If e.Row.RequiredDate <= e.Row.OrderDate Then  
                ' Set the RowError if validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"  
            Else  
                ' Clear the RowError when validation passes.  
                e.Row.RowError = ""  
            End If  
        End Sub  
    End Class  
    ```  
    ```csharp  
    partial class OrdersDataTable  
    {  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the event to the  
            // RowChangingEvent method.  
            OrdersRowChanging += RowChangingEvent;  
        }  
  
        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)  
        {  
            // Perform the validation logic.  
            if (e.Row.RequiredDate <= e.Row.OrderDate)  
            {  
                // Set the row to an error when validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";  
            }  
            else  
            {  
                // Clear the RowError if validation passes.  
                e.Row.RowError = "";  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Daten von N-Tier-Anwendungen (Übersicht)](../data-tools/n-tier-data-applications-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)