---
title: Hinzufügen von Validierungen zu einem n-Tier-DataSet | Microsoft-Dokumentation
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
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673054"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Hinzufügen von Validierungen zu einem N-Tier-Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Validierungen werden einem DataSet, das in eine N-Tier-Projektmappe aufgeteilt ist, grundsätzlich auf die gleiche Art hinzugefügt wie einem DataSet in einer einzelnen Datei (in einem einzelnen Projekt). Es wird empfohlen, die Datenvalidierung während des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses und/oder des <xref:System.Data.DataTable.RowChanging>-Ereignisses einer Datentabelle auszuführen.

Der DataSet-Designer stellt die Funktionalität zum Erstellen von partiellen Klassen bereit, denen Sie Spalten-und Zeilenumbruch Ereignissen der Datentabellen im DataSet Benutzercode hinzufügen können. Weitere Informationen zum Hinzufügen von Code zu einem Dataset in einer n-Tier-Projekt Mappe finden [Sie unter Hinzufügen von Code zu Datasets in n-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)und [Hinzufügen von Code zu TableAdapters in n-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Weitere Informationen zu partiellen Klassen finden Sie unter Gewusst [wie: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) oder [partielle Klassen und Methoden](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> Wenn Sie Datasets von TableAdapters trennen (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle DataSet-Klassen im Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Vom DataSet-Designer werden in C# nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis und das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. Sie müssen manuell einen Ereignishandler erstellen und den Ereignishandler an das zugrunde liegende Ereignis anschließen. In den folgenden Prozeduren wird beschrieben, wie die erforderlichen Ereignishandler sowohl in Visual Basic als auch in c# erstellt werden.

## <a name="validatechanges-to-individual-columns"></a>ValidateChanges in einzelne Spalten
 Validieren Sie die Werte in einzelnen Spalten durch Behandeln des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses. Das- <xref:System.Data.DataTable.ColumnChanging> Ereignis wird ausgelöst, wenn ein Wert in einer Spalte geändert wird. Erstellen Sie einen Ereignishandler für das- <xref:System.Data.DataTable.ColumnChanging> Ereignis, indem Sie auf die gewünschte Spalte im DataSet doppelklicken.

 Beim ersten Doppelklicken auf eine Spalte wird vom Designer ein Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis erstellt. `If…Then`Außerdem wird eine-Anweisung erstellt, die auf die jeweilige Spalte prüft. Der folgende Code wird beispielsweise generiert, wenn Sie auf die Spalte "Requirements ddate" in der Tabelle "Northwind Orders" doppelklicken:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> In C#-Projekten werden vom DataSet-Designer nur partielle Klassen für das DataSet sowie einzelne Tabellen im DataSet erstellt. Vom DataSet-Designer werden in C#, im Gegensatz zu Visual Basic, nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis und das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. In c#-Projekten müssen Sie manuell eine Methode erstellen, um das Ereignis zu behandeln und die Methode mit dem zugrunde liegenden Ereignis zu verbinden. Das folgende Verfahren erläutert die Schritte, um die erforderlichen Ereignishandler sowohl in Visual Basic als auch in C# zu erstellen.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>So fügen Sie Validierungen bei Änderung einzelner Spaltenwerte hinzu

1. Öffnen Sie das Dataset im Designer, indem Sie in **Projektmappen-Explorer**auf die **XSD** -Datei doppelklicken. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Datasets in der DataSet-Designer](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doppelklicken Sie auf die zu validierende Spalte. Durch diese Aktion wird der <xref:System.Data.DataTable.ColumnChanging>-Ereignishandler erstellt.

    > [!NOTE]
    > Der Dataset-Designer erstellt den Ereignishandler für das C#-Ereignis nicht automatisch. Der Code, der zum Behandeln des Ereignisses in c# erforderlich ist, ist im nächsten Abschnitt enthalten. `SampleColumnChangingEvent` wird erstellt und dann in der-Methode mit dem- <xref:System.Data.DataTable.ColumnChanging> Ereignis verknüpft <xref:System.Data.DataTable.EndInit%2A> .

3. Fügen Sie Code hinzu, mit dem überprüft wird, ob die Daten in `e.ProposedValue` den Anforderungen der Anwendung entsprechen. Wenn der vorgeschlagene Wert unzulässig ist, legen Sie für die Spalte fest, dass ein Fehler angezeigt wird.

     Im folgenden Codebeispiel wird überprüft, ob die Spalte **Menge** mehr als 0 (null) enthält. Wenn die **Menge** kleiner oder gleich 0 ist, wird die Spalte auf einen Fehler festgelegt. Die- `Else` Klausel löscht den Fehler, wenn die **Menge** größer als 0 ist. Der Code im spaltenändernden Ereignishandler sollte etwa folgendermaßen aussehen:

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
    // C#
    // Add this code to the DataTable
    // partial class.

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

## <a name="validatechanges-to-whole-rows"></a>ValidateChanges in ganze Zeilen
 Überprüfen Sie Werte in ganzen Zeilen durch Behandeln des <xref:System.Data.DataTable.RowChanging>-Ereignisses. Das <xref:System.Data.DataTable.RowChanging>-Ereignis wird ausgelöst, wenn ein Commit für die Werte in allen Spalten ausgeführt wird. Wenn der Wert in einer Spalte von dem Wert in einer anderen Spalte abhängt, ist es erforderlich, dies im <xref:System.Data.DataTable.RowChanging>-Ereignis zu überprüfen. Betrachten Sie beispielsweise OrderDate und RequiredDate in der Tabelle Orders in Northwind.

 Wenn die Bestellungen eingegeben werden, wird durch die Validierung sichergestellt, dass keine Bestellung mit einem RequiredDate eingegeben wird, das vor dem OrderDate liegt oder mit diesem übereinstimmt. In diesem Beispiel müssen die Werte für die Spalten RequiredDate und OrderDate verglichen werden, es ist daher nicht sinnvoll, eine einzelne Spaltenänderung zu überprüfen.

 Erstellen Sie einen Ereignishandler für das- <xref:System.Data.DataTable.RowChanging> Ereignis, indem Sie in der Titelleiste der Tabelle auf den Tabellennamen doppelklicken.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>So fügen Sie Validierungen bei Änderung ganzer Zeilen hinzu

1. Öffnen Sie das Dataset im Designer, indem Sie in **Projektmappen-Explorer**auf die **XSD** -Datei doppelklicken. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Datasets in der DataSet-Designer](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doppelklicken Sie im Designer auf die Titelleiste der Datentabelle.

     Eine partielle Klasse wird mit einem `RowChanging`-Ereignishandler erstellt und im Code-Editor geöffnet.

    > [!NOTE]
    > Vom DataSet-Designer wird in C#-Projekten nicht automatisch ein Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. Sie müssen eine Methode erstellen, um das Ereignis zu behandeln <xref:System.Data.DataTable.RowChanging> und Code auszuführen, um das Ereignis in der Initialisierungs Methode der Tabelle einzuschließen.

3. Fügen Sie Benutzercode innerhalb der Deklaration der partiellen Klasse hinzu.

4. Im folgenden Code wird für Visual Basic dargestellt, an welcher Stelle während des <xref:System.Data.DataTable.RowChanging>-Ereignisses Benutzercode zur Validierung hinzugefügt werden kann:

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

5. Im folgenden Code wird für C# dargestellt, wie der `RowChanging`-Ereignishandler erstellt wird und an welcher Stelle während des <xref:System.Data.DataTable.RowChanging>-Ereignisses Benutzercode zur Validierung hinzugefügt werden kann:

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

## <a name="see-also"></a>Weitere Informationen
 [Übersicht über n-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md) Exemplarische Vorgehensweise [: Erstellen einer n-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md) überprüfen von [Daten in Datasets](../data-tools/validate-data-in-datasets.md)
