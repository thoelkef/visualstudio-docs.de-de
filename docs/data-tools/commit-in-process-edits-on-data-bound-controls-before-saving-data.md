---
title: "Gewusst wie: Ausf&#252;hren eines Commits f&#252;r aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten | Microsoft Docs"
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
  - "BindingSource-Klasse, Übertragen von bearbeiteten Datensätzen"
  - "Übertragen von bearbeiteten Datensätzen"
  - "DataBinding-Klasse, Übertragen von bearbeiteten Datensätzen"
  - "Datengebundene Steuerelemente, Aktuell ausgeführte Bearbeitungen"
  - "EndEdit-Methode"
  - "Hierarchische Aktualisierung, Übertragen von bearbeiteten Datensätzen"
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Ausf&#252;hren eines Commits f&#252;r aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten
Wenn Werte in datengebundenen Steuerelementen bearbeitet werden, müssen die Benutzer vom aktuellen Datensatz weg navigieren, um den aktualisierten Wert in die zugrunde liegende Datenquelle zu übernehmen, an die das Steuerelement gebunden ist.  Wenn Sie Elemente aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auf ein Formular ziehen, generiert das erste abgelegte Element Code im <xref:System.Windows.Forms.BindingNavigator>\-Klickereignis für die Schaltfläche zum Speichern.  Dieser Code ruft die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Methode der <xref:System.Windows.Forms.BindingSource> auf.  Daher wird der Aufruf der <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Methode nur für die erste <xref:System.Windows.Forms.BindingSource> generiert, die dem Formular hinzugefügt wird.  
  
 Durch den <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Aufruf wird für sämtliche anstehenden Änderungen in allen gegenwärtig bearbeiteten datengebundenen Steuerelementen ein Commit ausgeführt.  Wenn das datengebundene Steuerelement daher immer noch über den Fokus verfügt und Sie auf die Schaltfläche **Speichern** klicken, wird vor dem eigentlichen Speichern für sämtliche anstehenden Bearbeitungen im Steuerelement ein Commit ausgeführt \(`TableAdapterManager.UpdateAll`\-Methode\).  
  
 Sie können die Anwendung so konfigurieren, dass für Änderungen während des Speichervorgangs automatisch ein Commit ausgeführt wird, auch wenn ein Benutzer versucht, Daten ohne Ausführen eines Commits für die Änderungen zu speichern.  
  
> [!NOTE]
>  Der Designer fügt den `BindingSource.EndEdit`\-Code nur für das erste Element hinzu, das auf einem Formular abgelegt wird.  Daher müssen Sie eine Codezeile hinzufügen, um die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Methode für jede <xref:System.Windows.Forms.BindingSource> auf dem Formular aufzurufen.  Sie können manuell eine Codezeile hinzufügen, um die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Methode für jede <xref:System.Windows.Forms.BindingSource> aufzurufen.  Es ist auch möglich, dem Formular die `EndEditOnAllBindingSources`\-Methode hinzuzufügen und sie vor dem Speichern aufzurufen.  
  
 Der folgende Code verwendet eine [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md), um alle <xref:System.Windows.Forms.BindingSource>\-Komponenten zu durchlaufen und die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Methode für jede <xref:System.Windows.Forms.BindingSource> auf einem Formular aufzurufen.  
  
### So rufen Sie EndEdit für alle BindingSource\-Komponenten auf einem Formular auf  
  
1.  Fügen Sie den folgenden Code dem Formular hinzu, das die <xref:System.Windows.Forms.BindingSource>\-Komponenten enthält.  
  
     [!code-cs[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  Fügen Sie die folgende Codezeile unmittelbar vor Aufrufen zum Speichern der Formulardaten hinzu \(`TableAdapterManager.UpdateAll()`\-Methode\):  
  
     [!code-cs[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## Siehe auch  
 [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md)   
 [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Übersicht über die BindingSource\-Komponente](../Topic/BindingSource%20Component%20Overview.md)