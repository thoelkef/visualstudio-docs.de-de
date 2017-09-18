---
title: "Gewusst wie: Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen | Microsoft Docs"
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
  - "Suchtabellen"
  - "Suchtabellen, Erstellen"
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
Sie können Nachschlagetabellen erstellen, indem Sie den Hauptknoten einer übergeordneten Tabelle \(aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)\) auf ein Steuerelement in einem Formular ziehen, das bereits an die Spalte in der zugehörigen untergeordneten Tabelle gebunden ist.  
  
 Die Begriff *Nachschlagetabelle* bezeichnet Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden werden.  Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.  
  
 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält.  Jeder Datensatz in der Tabelle `Orders` enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag erteilt hat.  Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt.  In diesem Szenario können Sie nun im **Datenquellenfenster** die Tabelle `Orders` erweitern und den Hauptknoten auf **Details** festlegen. Dann legen Sie fest, dass die `CustomerID`\-Spalte ein <xref:System.Windows.Forms.ComboBox>\-Steuerelement \(oder ein anderes Steuerelement, das die Nachschlagebindung unterstützt\) verwenden soll, und ziehen den Knoten `Orders` auf das Formular.  Anschließend ziehen Sie den Knoten `Customers` auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall auf das <xref:System.Windows.Forms.ComboBox>\-Steuerelement, das an die `CustomerID`\-Spalte gebunden ist.  
  
### So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her  
  
1.  Öffnen Sie das **Datenquellenfenster**.  
  
    > [!NOTE]
    >  Für Nachschlagetabellen ist es erforderlich, dass im **Datenquellenfenster** zwei zusammengehörige Tabellen oder Objekte verfügbar sind.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms\-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
2.  Erweitern Sie im **Datenquellenfenster** die Knoten, bis die übergeordnete Tabelle und die zugehörige untergeordnete Tabelle jeweils mit allen Spalten angezeigt werden.  
  
    > [!NOTE]
    >  Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.  
  
3.  Ändern Sie den Ablagetyp auf **Details**, indem Sie am Knoten der untergeordneten Tabelle in der Steuerelementliste die Option **Details** auswählen.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Wechseln Sie zu dem Knoten, über den die beiden Tabellen verbunden sind \(in obigem Beispiel der Knoten `CustomerID`\), und ändern Sie den Ablagetyp in <xref:System.Windows.Forms.ComboBox>, indem Sie aus der Steuerelementliste **ComboBox** auswählen.  
  
5.  Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus dem **Datenquellenfenster** auf das Formular.  
  
     Auf dem Formular werden datengebundene Steuerelemente \(mit beschreibenden Bezeichnungen\) sowie ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) angezeigt.  Auf der Komponentenleiste werden ein [Dataset](../data-tools/dataset-tools-in-visual-studio.md), ein [TableAdapter](../data-tools/tableadapter-overview.md), eine <xref:System.Windows.Forms.BindingSource> und ein <xref:System.Windows.Forms.BindingNavigator> angezeigt.  
  
6.  Ziehen Sie den Hauptknoten der übergeordneten Tabelle aus dem **Datenquellenfenster** direkt auf das Nachschlagesteuerelement \(<xref:System.Windows.Forms.ComboBox>\).  
  
     Die Nachschlagebindungen werden jetzt festgelegt.  In der folgenden Tabelle sind die speziellen Eigenschaften aufgeführt, die für das Steuerelement festgelegt wurden.  
  
    |Eigenschaft|Erklärung der Einstellung|  
    |-----------------|-------------------------------|  
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> fest, die für die auf das Steuerelement gezogene Tabelle erstellt wurde \(also nicht auf die <xref:System.Windows.Forms.BindingSource>, die bei der Erstellung des Steuerelements erstellt wurde\).<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|  
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Namen der Spalte festlegen, die Sie anzeigen möchten.|  
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Primärschlüssel in der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|  
    |**SelectedValue**|Visual Studio legt diese Eigenschaft auf die ursprüngliche, aus dem **Datenquellenfenster** gezogene und abgelegte Spalte fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die Fremdschlüsselspalte in der zugehörigen Tabelle festlegen.|  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer Suchtabelle in einer Windows Forms\-Anwendung](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Gewusst wie: Erstellen einer Suchtabelle für ComboBox\-, ListBox\- oder CheckedListBox\-Steuerelemente in Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20for%20a%20Windows%20Forms%20ComboBox,%20ListBox,%20or%20CheckedListBox%20Control.md)   
 [Gewusst wie: Erstellen einer Suchtabelle mit der BindingSource\-Komponente in Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)