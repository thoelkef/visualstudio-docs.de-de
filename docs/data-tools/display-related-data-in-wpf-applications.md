---
title: "Gewusst wie: Anzeigen verkn&#252;pfter Daten in WPF-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2016"
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
  - "Daten [WPF], Anzeigen"
  - "Datenbindung, WPF"
  - "Anzeigen von Daten, WPF"
  - "WPF [WPF], Daten"
  - "WPF-Datenbindung [Visual Studio]"
  - "WPF-Designer, Datenbindung"
  - "WPF, Datenbindung in Visual Studio"
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Anzeigen verkn&#252;pfter Daten in WPF-Anwendungen
In einigen Anwendungen möchten Sie eventuell mit Daten arbeiten, die aus mehreren Tabellen oder Entitäten stammen, die in einer Beziehung zwischen übergeordneten und untergeordneten Elementen miteinander verknüpft sind.  Angenommen, Sie möchten in einem Raster Kunden aus der Tabelle `Customers` anzeigen.  Wenn der Benutzer einen bestimmten Kunden auswählt, werden in einem anderen Raster die Bestellungen für diesen Kunden aus der verknüpften Tabelle `Orders` angezeigt.  
  
 Sie können datengebundene Steuerelemente erstellen, die verknüpfte Daten anzeigen, indem Sie Elemente aus dem **Datenquellenfenster** in den WPF\-Designer ziehen.  
  
### So erstellen Sie Steuerelemente, die verknüpfte Datensätze anzeigen  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das **Datenquellenfenster** zu öffnen.  
  
2.  Klicken Sie auf **Neue Datenquelle hinzufügen**, und führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus.  
  
3.  Öffnen Sie den WPF\-Designer, und stellen Sie sicher, dass der Designer einen Container enthält, der ein gültiges Ablageziel für die Elemente im **Datenquellenfenster** ist.  
  
     Weitere Informationen über gültige Ablageziele finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  Erweitern Sie im **Datenquellenfenster** den Knoten, der die übergeordnete Tabelle oder das übergeordnete Objekt in der Beziehung darstellt.  Die übergeordnete Tabelle oder das übergeordnete Objekt stellt die 1 in einer 1:n\-Beziehung dar.  
  
5.  Ziehen Sie den übergeordneten Knoten \(oder einzelne Elemente im übergeordneten Knoten\) aus dem **Datenquellenfenster** auf ein gültiges Ablageziel im Designer.  
  
     Visual Studio generiert XAML, mit dem für jedes Element, das Sie ziehen, neue datengebundene Steuerelemente erstellt werden.  Mit dem XAML wird außerdem den Ressourcen des Ablageziels eine neue <xref:System.Windows.Data.CollectionViewSource> für die übergeordnete Tabelle oder das übergeordnete Objekt hinzugefügt.  Für einige Datenquellen generiert Visual Studio zudem Code, um die Daten in die übergeordnete Tabelle oder das übergeordnete Objekt zu laden.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Suchen Sie im **Datenquellenfenster** die verknüpfte untergeordnete Tabelle oder das verknüpfte untergeordnete Objekt.  Verknüpfte untergeordnete Tabellen und Objekte werden als erweiterbare Knoten am unteren Ende der Datenliste des übergeordneten Knotens angezeigt.  
  
7.  Ziehen Sie den untergeordneten Knoten \(oder einzelne Elemente im untergeordneten Knoten\) aus dem **Datenquellenfenster** auf ein gültiges Ablageziel im Designer.  
  
     Visual Studio generiert XAML, mit dem für jedes Element, das Sie ziehen, neue datengebundene Steuerelemente erstellt werden.  Mit dem XAML wird außerdem den Ressourcen des Ablageziels eine neue <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder das untergeordnete Objekt hinzugefügt.  Diese neue <xref:System.Windows.Data.CollectionViewSource> wird an die Eigenschaft der übergeordneten Tabelle oder des übergeordneten Objekts gebunden, die bzw. das Sie gerade in den Designer gezogen haben.  Für einige Datenquellen generiert Visual Studio zudem Code, um die Daten in die untergeordnete Tabelle oder das untergeordnete Objekt zu laden.  
  
     Die folgende Abbildung veranschaulicht die mit der Tabelle **Customers** verknüpfte Tabelle **Orders** in einem Dataset im **Datenquellenfenster**.  
  
     ![Relation im Datenquellenfenster](../data-tools/media/datasources2.gif "DataSources2")  
  
## Siehe auch  
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Gewusst wie: Erstellen von Nachschlagetabellen in WPF\-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF\-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)