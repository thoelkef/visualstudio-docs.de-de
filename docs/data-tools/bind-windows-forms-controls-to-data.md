---
title: "Gewusst wie: Binden von Windows Forms-Steuerelementen an Daten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Daten [Windows Forms], Anzeigen"
  - "Datenquellen, Anzeigen"
  - "Anzeigen von Daten, Windows Forms-Steuerelemente"
  - "Windows Forms, Anzeigen von Daten"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Binden von Windows Forms-Steuerelementen an Daten
Binden Sie Daten an Windows Forms\-Steuerelemente, indem Sie Objekte aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) ziehen.  Bevor Sie Elemente aus dem **Datenquellenfenster** ziehen, können Sie den Steuerelementtyp der Tabelle für einzelne Steuerelemente auf **Details** oder **DataGridView** für ein <xref:System.Windows.Forms.DataGridView>\-Element festlegen.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
 Wenn die Steuerelemente, die von der Anwendung erforderlich sind, nicht aus dem Fenster **Datenquellen** verfügbar sind, können Sie Steuerelemente hinzufügen.  Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Anzeigen einer gesamten Datentabelle in einzelnen Steuerelementen  
 Sie können eine gesamte Tabelle mit Daten in einzelnen Steuerelementen anzeigen, indem Sie die Tabelle \(oder einen Knoten, der eine Auflistung repräsentiert, wenn Sie ein Objekt als Datenquelle verwenden\) aus dem **Datenquellenfenster** auf ein Formular einer Windows\-Anwendung ziehen.  
  
#### So zeigen Sie eine gesamte Datentabelle  
  
1.  Öffnen Sie das **Datenquellenfenster**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Wenn das **Datenquellenfenster** leer ist, fügen Sie ihm eine Datenquelle hinzu.  Weitere Informationen finden Sie unter [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md).  
  
2.  Öffnen Sie das Formular im **Windows Forms\-Designer**.  
  
3.  Wählen Sie eine Tabelle im **Datenquellenfenster** aus, klicken Sie auf den Dropdownpfeil, und wählen Sie **Details** aus.  
  
4.  Ziehen Sie die Tabelle aus dem **Datenquellenfenster** auf ein Formular.  
  
     Auf dem Formular werden für jede Spalte oder Eigenschaft ein eigenes datengebundenes Steuerelement sowie ein diesem Steuerelement zugeordnetes und entsprechend benanntes Label\-Steuerelement erstellt.  
  
## Anzeigen von ausgewählten Datenspalten in einzelnen Steuerelementen  
 Sie zeigen einzelne Datenspalten in einzelnen Steuerelementen an, indem Sie die einzelnen Spalten \(oder Eigenschaften, wenn Sie ein Objekt als Datenquelle verwenden\) aus dem **Datenquellenfenster** auf ein Formular einer Windows\-Anwendung ziehen.  
  
#### So zeigen Sie ausgewählte Datenspalten an  
  
1.  Öffnen Sie das **Datenquellenfenster**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Wenn das **Datenquellenfenster** leer ist, fügen Sie ihm eine Datenquelle hinzu.  Weitere Informationen finden Sie unter [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md).  
  
2.  Erweitern Sie die Tabelle, um die einzelnen Spalten anzuzeigen.  
  
    > [!TIP]
    >  Um das Steuerelement festzulegen, das für die einzelnen Spalten erstellt wird, markieren Sie die Spalte im **Datenquellenfenster**, klicken Sie auf den Dropdownpfeil und wählen Sie ein Steuerelement in der Liste verfügbarer Steuerelemente aus.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Öffnen Sie das Formular im **Windows Forms\-Designer**.  
  
4.  Ziehen Sie die gewünschten Spalten aus dem **Datenquellenfenster** auf ein Formular.  
  
     Auf dem Formular werden für jede Spalte oder Eigenschaft, die Sie auf dieses ziehen, ein eigenes datengebundenes Steuerelement sowie ein diesem Steuerelement zugeordnetes und entsprechend benanntes Label\-Steuerelement erstellt.  
  
 Sie können auch Elemente aus dem **Datenquellenfenster** auf vorhandene Steuerelemente, also bereits in einem Formular enthaltene Steuerelemente, ziehen, um das Steuerelement an Daten zu binden.  Bei Steuerelementen, die bereits an Daten gebunden sind, werden die Datenbindungen auf das Element zurückgesetzt, das zuletzt auf das jeweilige Steuerelement gezogen wurde.  
  
> [!NOTE]
>  Als gültige Ziele zum Ablegen müssen Steuerelemente den zugrunde liegenden Datentyp des Elements anzeigen können, das aus dem **Datenquellenfenster** gezogen wird.  Es stellt z. B. keinen gültigen Vorgang dar, ein Element des Datentyps <xref:System.DateTime> auf eine <xref:System.Windows.Forms.CheckBox> zu ziehen, da die <xref:System.Windows.Forms.CheckBox> kein Datum anzeigen kann.  
  
#### So binden Sie ein vorhandenes Steuerelement an Daten  
  
1.  Öffnen Sie das **Datenquellenfenster**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md).  
  
2.  Öffnen Sie das Formular im [Windows Forms Designer](http://msdn.microsoft.com/de-de/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
3.  Erweitern Sie im **Datenquellenfenster** eine Tabelle oder ein Objekt, und zeigen Sie die einzelnen Spalten oder Eigenschaften an.  
  
4.  Ziehen Sie das gewünschte Element aus dem **Datenquellenfenster** auf ein vorhandenes Steuerelement.  
  
     Das Steuerelement ist jetzt an dieses ausgewählte Element gebunden.  
  
## Anzeigen von Daten in einem DataGridView\-Steuerelement  
  
#### So zeigen Sie Daten in einem neuen DataGridView\-Steuerelement für Windows Forms an  
  
1.  Öffnen Sie das **Datenquellenfenster**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Wenn das **Datenquellenfenster** leer ist, fügen Sie ihm eine Datenquelle hinzu.  Weitere Informationen finden Sie unter [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md).  
  
2.  Öffnen Sie das Formular im **Windows Forms\-Designer**.  
  
3.  Wählen Sie eine Tabelle im **Datenquellenfenster** aus, klicken Sie auf den Dropdownpfeil, und wählen Sie **DataGridView** aus.  
  
4.  Ziehen Sie die Tabelle aus dem **Datenquellenfenster** auf ein Formular.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement und ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  Auf der Komponentenleiste werden ein [Dataset](../data-tools/dataset-tools-in-visual-studio.md), ein [TableAdapter](../data-tools/tableadapter-overview.md), eine <xref:System.Windows.Forms.BindingSource> und ein <xref:System.Windows.Forms.BindingNavigator> angezeigt.  
  
#### So zeigen Sie Daten in einem vorhandenen DataGridView\-Steuerelement für Windows Forms an  
  
1.  Öffnen Sie das **Datenquellenfenster**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Wenn das **Datenquellenfenster** leer ist, fügen Sie ihm eine Datenquelle hinzu.  Weitere Informationen finden Sie unter [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md).  
  
2.  Öffnen Sie das Formular im **Windows Forms\-Designer**.  
  
3.  Wählen Sie eine Tabelle im **Datenquellenfenster** aus, klicken Sie auf den Dropdownpfeil, und wählen Sie **DataGridView** aus.  
  
4.  Ziehen Sie die Tabelle aus dem **Datenquellenfenster** auf die <xref:System.Windows.Forms.DataGridView> im Formular.  
  
     Das <xref:System.Windows.Forms.DataGridView>\-Steuerelement ist jetzt an die darauf gezogene Tabelle gebunden.  Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), ein [TableAdapter](../data-tools/tableadapter-overview.md) und eine <xref:System.Windows.Forms.BindingSource> werden auf der Komponentenleiste angezeigt.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über die BindingSource\-Komponente](../Topic/BindingSource%20Component%20Overview.md)   
 [Übersicht über das BindingNavigator\-Steuerelement](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Tools zum Arbeiten mit Datenquellen in Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)