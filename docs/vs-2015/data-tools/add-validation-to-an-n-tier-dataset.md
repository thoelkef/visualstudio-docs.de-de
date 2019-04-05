---
title: Hinzufügen von Validierungen zu einem n-Tier-Dataset | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94a8f4f8fe0d1f93ce3467291a20377234db29f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960561"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Hinzufügen von Validierungen zu einem N-Tier-Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Validierungen werden einem DataSet, das in eine N-Tier-Projektmappe aufgeteilt ist, grundsätzlich auf die gleiche Art hinzugefügt wie einem DataSet in einer einzelnen Datei (in einem einzelnen Projekt). Es wird empfohlen, die Datenvalidierung während des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses und/oder des <xref:System.Data.DataTable.RowChanging>-Ereignisses einer Datentabelle auszuführen.  
  
Der DataSet-Designer stellt die Funktionalität zum Erstellen von partiellen Klassen, die Sie hinzufügen können, Benutzercode für Spalten- und Zeilen-wechselnde Ereignisse der Datentabellen im Dataset. Weitere Informationen zum Hinzufügen von Code zu einem Dataset in einer n-Tier-Projektmappe finden Sie unter [fügen Code zu Datasets in n-schichtige Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md), und [Hinzufügen von Code zu TableAdapters in n-schichtigen Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Weitere Informationen zu partiellen Klassen finden Sie unter [Vorgehensweise: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) oder [partielle Klassen und Methoden](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
>  Bei einer Abtrennung der Datasets von TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.  
  
> [!NOTE]
>  Vom DataSet-Designer werden in C# nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis und das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. Sie müssen manuell einen Ereignishandler erstellen und den Ereignishandler mit dem zugrunde liegenden Ereignis verknüpfen. Die folgenden Verfahren wird beschrieben, wie die erforderlichen Ereignishandler in Visual Basic und c# zu erstellen.  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges für einzelne Spalten  
 Validieren Sie die Werte in einzelnen Spalten durch Behandeln des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses. Die <xref:System.Data.DataTable.ColumnChanging> Ereignis wird ausgelöst, wenn ein Wert in einer Spalte geändert wird. Erstellen Sie einen Ereignishandler für die <xref:System.Data.DataTable.ColumnChanging> Ereignis durch Doppelklicken auf die gewünschte Spalte im DataSet.  
  
 Beim ersten Doppelklicken auf eine Spalte wird vom Designer ein Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis erstellt. Ein `If…Then` Anweisung wird auch erstellt, die für die spezifische Spalte überprüft. Beispielsweise wird der folgende Code generiert, wenn Sie auf die RequiredDate-Spalte der Tabelle Northwind Orders doppelklicken:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  In C#-Projekten werden vom DataSet-Designer nur partielle Klassen für das DataSet sowie einzelne Tabellen im DataSet erstellt. Vom DataSet-Designer werden in C#, im Gegensatz zu Visual Basic, nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>-Ereignis und das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. In c#-Projekten müssen Sie manuell eine Methode zum Behandeln des Ereignisses und die Methode, die dem zugrunde liegenden Ereignis verknüpfen zu erstellen. Das folgende Verfahren erläutert die Schritte, um die erforderlichen Ereignishandler sowohl in Visual Basic als auch in C# zu erstellen.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>So fügen Sie Validierungen bei Änderung einzelner Spaltenwerte hinzu  
  
1.  Öffnen Sie das Dataset im Designer durch Doppelklicken auf die **XSD** Datei **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doppelklicken Sie auf die zu validierende Spalte. Durch diese Aktion wird der <xref:System.Data.DataTable.ColumnChanging>-Ereignishandler erstellt.  
  
    > [!NOTE]
    >  Der Dataset-Designer erstellt den Ereignishandler für das C#-Ereignis nicht automatisch. Der Code, der zum Behandeln des Ereignisses in c# erforderlich ist, wird im nächsten Abschnitt enthalten. `SampleColumnChangingEvent` wird erstellt, und klicken Sie dann bis zu verknüpft die <xref:System.Data.DataTable.ColumnChanging> Ereignis in der <xref:System.Data.DataTable.EndInit%2A> Methode.  
  
3.  Fügen Sie Code hinzu, mit dem überprüft wird, ob die Daten in `e.ProposedValue` den Anforderungen der Anwendung entsprechen. Wenn der vorgeschlagene Wert unzulässig ist, legen Sie für die Spalte fest, dass ein Fehler angezeigt wird.  
  
     Im folgenden Codebeispiel wird überprüft, ob die **Menge** Spalte enthält mehr als 0. Wenn **Menge** ist kleiner als oder gleich 0 ist, wird die Spalte zu einem Fehler festgelegt. Die `Else` -Klausel löscht den Fehler, wenn **Menge** ist größer als 0. Der Code im spaltenändernden Ereignishandler sollte etwa folgendermaßen aussehen:  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges an ganzen Zeilen  
 Überprüfen Sie Werte in ganzen Zeilen durch Behandeln des <xref:System.Data.DataTable.RowChanging>-Ereignisses. Das <xref:System.Data.DataTable.RowChanging>-Ereignis wird ausgelöst, wenn ein Commit für die Werte in allen Spalten ausgeführt wird. Wenn der Wert in einer Spalte von dem Wert in einer anderen Spalte abhängt, ist es erforderlich, dies im <xref:System.Data.DataTable.RowChanging>-Ereignis zu überprüfen. Betrachten Sie beispielsweise OrderDate und RequiredDate in der Tabelle Orders in Northwind.  
  
 Wenn die Bestellungen eingegeben werden, wird durch die Validierung sichergestellt, dass keine Bestellung mit einem RequiredDate eingegeben wird, das vor dem OrderDate liegt oder mit diesem übereinstimmt. In diesem Beispiel müssen die Werte für die Spalten RequiredDate und OrderDate verglichen werden, es ist daher nicht sinnvoll, eine einzelne Spaltenänderung zu überprüfen.  
  
 Erstellen Sie einen Ereignishandler für die <xref:System.Data.DataTable.RowChanging> Ereignis durch Doppelklicken auf den Tabellennamen in der Titelleiste der Tabelle.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>So fügen Sie Validierungen bei Änderung ganzer Zeilen hinzu  
  
1.  Öffnen Sie das Dataset im Designer durch Doppelklicken auf die **XSD** Datei **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doppelklicken Sie im Designer auf die Titelleiste der Datentabelle.  
  
     Eine partielle Klasse wird mit einem `RowChanging`-Ereignishandler erstellt und im Code-Editor geöffnet.  
  
    > [!NOTE]
    >  Vom DataSet-Designer wird in C#-Projekten nicht automatisch ein Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis erstellt. Sie müssen eine Methode zum Behandeln von erstellen die <xref:System.Data.DataTable.RowChanging> Ereignis- und Ausführen von Code, um das Ereignis in der Initialisierungsmethode der Tabelle zu verknüpfen.  
  
3.  Fügen Sie Benutzercode innerhalb der Deklaration der partiellen Klasse hinzu.  
  
4.  Im folgenden Code wird für Visual Basic dargestellt, an welcher Stelle während des <xref:System.Data.DataTable.RowChanging>-Ereignisses Benutzercode zur Validierung hinzugefügt werden kann:  
  
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
  
5.  Im folgenden Code wird für C# dargestellt, wie der `RowChanging`-Ereignishandler erstellt wird und an welcher Stelle während des <xref:System.Data.DataTable.RowChanging>-Ereignisses Benutzercode zur Validierung hinzugefügt werden kann:  
  
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
 [Übersicht über N-Tier-Data-Anwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)
