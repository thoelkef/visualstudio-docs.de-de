---
title: "Binden von WPF-Steuerelementen an Daten in Visual Studio | Microsoft Docs"
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
  - "Daten [WPF], Anzeigen"
  - "Datenbindung, WPF"
  - "Anzeigen von Daten, WPF"
  - "WPF [WPF], Daten"
  - "WPF-Datenbindung [Visual Studio]"
  - "WPF-Designer, Datenbindung"
  - "WPF, Datenbindung in Visual Studio"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Binden von WPF-Steuerelementen an Daten in Visual Studio
Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]\-Steuerelemente binden.  Um die datengebundenen Steuerelemente zu erstellen, können Sie Elemente aus dem **Datenquellenfenster** in den [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ziehen.  In diesem Thema werden einige der häufigsten Aufgaben, Tools und Klassen beschrieben, mit denen Sie datengebundene [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]\-Anwendungen erstellen können.  
  
 Allgemeine Informationen zum Erstellen von datengebundenen Steuerelementen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Weitere Informationen zur [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]\-Datenbindung finden Sie unter [Übersicht über Datenbindung](../Topic/Data%20Binding%20Overview.md).  
  
## Aufgaben beim Binden von WPF\-Steuerelementen an Daten  
 In der folgenden Tabelle werden die Aufgaben aufgeführt, die durch Ziehen von Elementen aus dem **Datenquellenfenster** in den [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] ausgeführt werden können.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Erstellen von neuen datengebundenen Steuerelementen<br /><br /> Binden Sie vorhandenen Steuerelemente an Daten.|[Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|Erstellen von Steuerelementen, die verknüpfte Daten in Beziehungen zwischen übergeordneten und untergeordneten Elementen anzeigen: Wenn der Benutzer einen übergeordneten Datensatz in einem Steuerelement auswählt, werden in einem anderen Steuerelement verknüpfte untergeordnete Daten für den ausgewählten Datensatz angezeigt.|[Gewusst wie: Anzeigen verknüpfter Daten in WPF\-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)|  
|Erstellen einer *Nachschlagetabelle*, in der Informationen aus einer Tabelle auf der Grundlage des Werts eines Fremdschlüsselfelds in einer anderen Tabelle angezeigt werden|[Gewusst wie: Erstellen von Nachschlagetabellen in WPF\-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Binden eines Steuerelements an ein Bild in einer Datenbank|[Gewusst wie: Binden von Steuerelementen an Bilder aus einer Datenbank](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## Gültige Ablageziele  
 Sie können Elemente im **Datenquellenfenster** nur auf gültige Ablageziele im [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] ziehen.  Es gibt zwei Hauptarten von gültigen Ablagezielen: Container und Steuerelemente.  Ein Container ist ein Benutzeroberflächenelement, das in der Regel Steuerelemente enthält.  Beispielsweise handelt es sich bei Rastern und Fenstern um Container.  
  
## Generiertes XAML und generierter Code  
 Wenn Sie ein Element aus dem **Datenquellenfenster** in den [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] ziehen, generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], das ein neues datengebundenes Steuerelement definiert \(oder ein vorhandenes Steuerelement an die Datenquelle bindet\).  Für einige Datenquellen generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auch Code in der Code\-Behind\-Datei, der die Datenquelle mit Daten füllt.  
  
 In der folgenden Tabelle werden [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und Code aufgeführt, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für die einzelnen Typen von Datenquellen im **Datenquellenfenster** generiert werden.  
  
|Datenquelle|Generieren von XAML, das ein Steuerelement an die Datenquelle bindet|Generieren von Code, der die Datenquelle mit Daten füllt|  
|-----------------|--------------------------------------------------------------------------|--------------------------------------------------------------|  
|DataSet|Ja|Ja|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Ja|Ja|  
|Dienst|Ja|Nein|  
|Objekt|Ja|Nein|  
  
### Datasets  
 Wenn Sie eine Tabelle oder eine Spalte aus dem Datenquellenfenster in den Designer ziehen, generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], das folgende Aktionen ausführt:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, werden das Dataset und eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt.  Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Datasets zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt.  Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element.  Wenn Sie das Element in einen Container ziehen, erstellt das XAML das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element.  Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nimmt außerdem die folgenden Änderungen an der Code\-Behind\-Datei vor:  
  
-   Es wird ein <xref:System.Windows.FrameworkElement.Loaded>\-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)]\-Element erstellt, das das Steuerelement enthält.  Der Ereignishandler füllt die Tabelle mit Daten, ruft die <xref:System.Windows.Data.CollectionViewSource> aus den Ressourcen des Containers ab, und legt dann das erste Datenelement als aktuelles Element fest.  Wenn bereits ein <xref:System.Windows.FrameworkElement.Loaded>\-Ereignishandler vorhanden ist, fügt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dem vorhandenen Ereignishandler diesen Code hinzu.  
  
### Entity Data Models  
 Wenn Sie eine Entität oder eine Entitätseigenschaft aus dem **Datenquellenfenster** in den Designer ziehen, generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], das folgende Aktionen ausführt:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt.  Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten der Entität zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt.  Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement an das Element.  Wenn Sie das Element in einen Container ziehen, erstellt das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element.  Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
 Visual Studio nimmt außerdem die folgenden Änderungen an der Code\-Behind\-Datei vor:  
  
-   Es wird eine neue Methode hinzugefügt, die eine Abfrage für die Entität zurückgibt, die Sie in den Designer gezogen haben \(oder für die Entität, die die Eigenschaft enthält, die Sie in den Designer gezogen haben\).  Der Name der neuen Methode lautet Get*EntityName*Query, wobei *EntityName* der Name der Entität ist.  
  
-   Es wird ein <xref:System.Windows.FrameworkElement.Loaded>\-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)]\-Element erstellt, das das Steuerelement enthält.  Der Ereignishandler ruft die Get*EntityName*Query\-Methode zum Auffüllen der Entität mit Daten auf, ruft die <xref:System.Windows.Data.CollectionViewSource>\-Entität aus den Ressourcen des Containers ab und legt dann das erste Datenelement als aktuelles Element fest.  Wenn bereits ein <xref:System.Windows.FrameworkElement.Loaded>\-Ereignishandler vorhanden ist, fügt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dem vorhandenen Ereignishandler diesen Code hinzu.  
  
### Dienste  
 Wenn Sie ein Dienstobjekt oder eine Diensteigenschaft aus dem **Datenquellenfenster** in den Designer ziehen, generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], das ein datengebundenes Steuerelement erstellt \(oder ein vorhandenes Steuerelement an das Objekt bzw. die Eigenschaft bindet\).  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert jedoch keinen Code, der das Proxydienstobjekt mit Daten füllt.  Sie müssen diesen Code selbst schreiben.  Ein Beispiel, das veranschaulicht, wie Sie dies vornehmen können, finden Sie unter [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an einen WCF\-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio generiert XAML, das folgende Aktionen ausführt:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt.  Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des von dem Dienst zurückgegebenen Objekts zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt.  Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement an das Element.  Wenn Sie das Element in einen Container ziehen, erstellt das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element.  Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
### Objekte  
 Wenn Sie ein Objekt oder eine Eigenschaft aus dem **Datenquellenfenster** in den Designer ziehen, generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], das ein datengebundenes Steuerelement erstellt \(oder ein vorhandenes Steuerelement an das Objekt bzw. die Eigenschaft bindet\).  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert jedoch keinen Code, um das Objekt mit Daten zu füllen.  Sie müssen diesen Code selbst schreiben.  
  
> [!NOTE]
>  Benutzerdefinierte Klassen müssen öffentlich sein und über einen parameterlosen öffentlichen Standardkonstruktor verfügen.  Sie können nicht als geschachtelte Klassen mit einem 'Punkt' in der Syntax definiert werden.  Weitere Informationen finden Sie unter [XAML\- und benutzerdefinierte Klassen für WPF](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], das folgende Aktionen ausführt:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt.  Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Objekt zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt.  Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element.  Wenn Sie das Element in einen Container ziehen, erstellt das XAML das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element.  Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
## Siehe auch  
 [Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Gewusst wie: Erstellen von Nachschlagetabellen in WPF\-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Gewusst wie: Anzeigen verknüpfter Daten in WPF\-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)   
 [Binden von WPF\-Steuerelementen an ein Entitätsdatenmodell](http://msdn.microsoft.com/data/jj574514.aspx)   
 [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an einen WCF\-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF\-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)