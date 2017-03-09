---
title: "Gewusst wie: Hinzuf&#252;gen von Validierungen zu einem N-Tier-DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "N-Tier-Anwendungen, Validieren"
  - "Validierung von N-Tier-Datenanwendungen"
  - "Validierung [Visual Basic], N-Tier-Datenanwendungen"
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 23
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Hinzuf&#252;gen von Validierungen zu einem N-Tier-DataSet
Validierungen werden einem DataSet, das in eine N\-Tier\-Projektmappe aufgeteilt ist, grundsätzlich auf die gleiche Art hinzugefügt wie einem DataSet in einer einzelnen Datei \(in einem einzelnen Projekt\).  Es wird empfohlen, die Datenvalidierung während des <xref:System.Data.DataTable.ColumnChanging>\-Ereignisses und\/oder des <xref:System.Data.DataTable.RowChanging>\-Ereignisses einer Datentabelle auszuführen.  
  
 Vom [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) wird die Funktionalität zum Erstellen von partiellen Klassen bereitgestellt, zu denen Sie Benutzercode für Spalten\- und Zeilenänderungsereignisse der Datentabellen im DataSet hinzufügen können.  Weitere Informationen über das Hinzufügen von Code zu einem Dataset in einer N\-Tier\-Projektmappe finden Sie unter [Gewusst wie: Hinzufügen von Code zu DataSets in N\-Tier\-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md) und [Gewusst wie: Hinzufügen von Code zu TableAdapters in N\-Tier\-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md).  Weitere Informationen zu partiellen Klassen finden Sie unter [How to: Split a Class into Partial Classes \(Class Designer\)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) und unter [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
> [!NOTE]
>  Bei einer Abtrennung der DataSets von TableAdapters \(durch Festlegen der **DataSet\-Projekt**\-Eigenschaft\) werden vorhandene partielle DataSet\-Klassen in dem Projekt nicht automatisch verschoben.  Vorhandene partielle DataSet\-Klassen müssen manuell in das DataSet\-Projekt verschoben werden.  
  
> [!NOTE]
>  Vom DataSet\-Designer werden in C\# nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis und das <xref:System.Data.DataTable.RowChanging>\-Ereignis erstellt.  Sie müssen manuell einen Ereignishandler erstellen und ihn mit dem zugrunde liegenden Ereignis verknüpfen.  Das folgende Verfahren erläutert die Schritte, um die erforderlichen Ereignishandler sowohl in Visual Basic als auch in C\# zu erstellen.  
  
## Validieren von Änderungen in einzelnen Spalten  
 Validieren Sie die Werte in einzelnen Spalten durch Behandeln des <xref:System.Data.DataTable.ColumnChanging>\-Ereignisses.  Das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis wird ausgelöst, wenn der Wert in einer Spalte geändert wird.  Erstellen Sie einen Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis, indem Sie auf die gewünschte Spalte im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) doppelklicken.  
  
 Beim ersten Doppelklicken auf eine Spalte wird vom Designer ein Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis erstellt.  Außerdem wird zusätzlich zum <xref:System.Data.DataTable.ColumnChanging>\-Ereignis eine `If…Then`\-Anweisung erstellt, von der Tests für die spezifische Spalte ausführt.  Der folgende Code wird beispielsweise erstellt, wenn Sie auf die RequiredDate\-Spalte der Tabelle Northwind Orders doppelklicken:  
  
```vb#  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  In C\#\-Projekten werden vom DataSet\-Designer nur partielle Klassen für das DataSet sowie einzelne Tabellen im DataSet erstellt.  Vom DataSet\-Designer werden in C\#, im Gegensatz zu Visual Basic, nicht automatisch Ereignishandler für das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis und das <xref:System.Data.DataTable.RowChanging>\-Ereignis erstellt.  In C\#\-Projekten müssen Sie manuell eine Methode erstellen, um das Ereignis zu behandeln und die Methode mit dem zugrunde liegenden Ereignis zu verknüpfen.  Das folgende Verfahren erläutert die Schritte, um die erforderlichen Ereignishandler sowohl in Visual Basic als auch in C\# zu erstellen.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So fügen Sie Validierungen bei Änderung einzelner Spaltenwerte hinzu  
  
1.  Öffnen Sie das Dataset im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) durch Doppelklicken auf die **XSD\-Datei** im Projektmappen\-Explorer.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Doppelklicken Sie auf die zu validierende Spalte.  Durch diese Aktion wird der <xref:System.Data.DataTable.ColumnChanging>\-Ereignishandler erstellt.  
  
    > [!NOTE]
    >  Der Dataset\-Designer erstellt den Ereignishandler für das C\#\-Ereignis nicht automatisch.  Der zum Behandeln des Ereignisses in C\# erforderliche Code wird unten aufgeführt.  `SampleColumnChangingEvent` wird erstellt, und dann wird es in das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis in der <xref:System.Data.DataTable.EndInit%2A>\-Methode eingebunden.  
  
3.  Fügen Sie Code hinzu, mit dem überprüft wird, ob die Daten in `e.ProposedValue` den Anforderungen der Anwendung entsprechen.  Wenn der vorgeschlagene Wert unzulässig ist, legen Sie für die Spalte fest, dass ein Fehler angezeigt wird.  
  
     Das folgende Codebeispiel überprüft, ob die Mengenspalte einen Wert größer 0 enthält.  Wenn die Menge kleiner oder gleich 0 ist, wird die Spalte auf einen Fehler festgelegt.  Die `Else`\-Klausel löscht den Fehler, wenn die Menge größer 0 ist.  Der Code im spaltenändernden Ereignishandler sollte etwa folgendermaßen aussehen:  
  
    ```vb#  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```  
  
    ```c#  
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
  
## Validieren von Änderungen an ganzen Zeilen  
 Überprüfen Sie Werte in ganzen Zeilen durch Behandeln des <xref:System.Data.DataTable.RowChanging>\-Ereignisses.  Das <xref:System.Data.DataTable.RowChanging>\-Ereignis wird ausgelöst, wenn ein Commit für die Werte in allen Spalten ausgeführt wird.  Wenn der Wert in einer Spalte von dem Wert in einer anderen Spalte abhängt, ist es erforderlich, dies im <xref:System.Data.DataTable.RowChanging>\-Ereignis zu überprüfen.  Betrachten Sie beispielsweise OrderDate und RequiredDate in der Tabelle Orders in Northwind.  Wenn die Bestellungen eingegeben werden, wird durch die Validierung sichergestellt, dass keine Bestellung mit einem RequiredDate eingegeben wird, das vor dem OrderDate liegt oder mit diesem übereinstimmt.  In diesem Beispiel müssen die Werte für die Spalten RequiredDate und OrderDate verglichen werden, es ist daher nicht sinnvoll, eine einzelne Spaltenänderung zu überprüfen.  
  
 Erstellen Sie einen Ereignishandler für das <xref:System.Data.DataTable.RowChanging>\-Ereignis, indem Sie im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) in der Titelleiste der Tabelle auf den Tabellennamen doppelklicken.  
  
#### So fügen Sie Validierungen bei Änderung ganzer Zeilen hinzu  
  
1.  Öffnen Sie das Dataset im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) durch Doppelklicken auf die **XSD\-Datei** im Projektmappen\-Explorer.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Doppelklicken Sie im Designer auf die Titelleiste der Datentabelle.  
  
     Eine partielle Klasse wird mit einem `RowChanging`\-Ereignishandler erstellt und im Code\-Editor geöffnet.  
  
    > [!NOTE]
    >  Vom DataSet\-Designer wird in C\#\-Projekten nicht automatisch ein Ereignishandler für das <xref:System.Data.DataTable.RowChanging>\-Ereignis erstellt.  Sie müssen eine Methode erstellen, mit der Sie das <xref:System.Data.DataTable.RowChanging>\-Ereignis behandeln und Code ausführen können, um das Ereignis mit der Initialisierungsmethode der Tabelle zu verknüpfen.  
  
3.  Fügen Sie Benutzercode innerhalb der Deklaration der partiellen Klasse hinzu.  
  
4.  Im folgenden Code wird für Visual Basic dargestellt, an welcher Stelle während des <xref:System.Data.DataTable.RowChanging>\-Ereignisses Benutzercode zur Validierung hinzugefügt werden kann:  
  
    ```vb#  
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
  
5.  Im folgenden Code wird für C\# dargestellt, wie der `RowChanging`\-Ereignishandler erstellt wird und an welcher Stelle während des <xref:System.Data.DataTable.RowChanging>\-Ereignisses Benutzercode zur Validierung hinzugefügt werden kann:  
  
    ```c#  
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
            // Perfom the validation logic.  
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
  
## Siehe auch  
 [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer N\-Tier\-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)