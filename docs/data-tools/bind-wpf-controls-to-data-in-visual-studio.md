---
title: Binden von WPF-Steuerelementen an Daten in Visual Studio - Teil 1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4c059013703a73a83a9a6f35b3c89f7b27c523d5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Binden von WPF-Steuerelementen an Daten in Visual Studio
Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]-Steuerelemente binden. Um diese datengebundenen Steuerelemente erstellen, können Sie Elemente aus ziehen die **Datenquellen** auf die [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In diesem Thema werden einige der häufigsten Aufgaben, Tools und Klassen beschrieben, mit denen Sie datengebundene [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]-Anwendungen erstellen können.  
  
 Allgemeine Informationen zum Erstellen von datengebundenen Steuerelementen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Weitere Informationen zu [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] -Datenbindung finden Sie unter [Übersicht zur Datenbindung](/dotnet/framework/wpf/data/data-binding-overview).  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Aufgaben beim Binden von WPF-Steuerelementen an Daten  
 Die folgende Tabelle enthält die Aufgaben, die durchgeführt werden können, durch Ziehen von Elementen aus der **Datenquellen** Fenster aus, um die [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Aufgabe|Weitere Informationen|  
|----------|----------------------|  
|Erstellen von neuen datengebundenen Steuerelementen<br /><br /> Binden Sie vorhandenen Steuerelemente an Daten.|[WPF-Steuerelemente an einen Datensatz binden](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|Erstellen von Steuerelementen, die verknüpfte Daten in Beziehungen zwischen übergeordneten und untergeordneten Elementen anzeigen: Wenn der Benutzer einen übergeordneten Datensatz in einem Steuerelement auswählt, werden in einem anderen Steuerelement verknüpfte untergeordnete Daten für den ausgewählten Datensatz angezeigt.|[Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)|  
|Erstellen einer *Nachschlagetabelle* , die Informationen aus einer Tabelle anhand des Werts eines Fremdschlüsselfelds in einer anderen Tabelle anzeigt.|[Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Binden eines Steuerelements an ein Bild in einer Datenbank|[Vorgehensweise: Binden von Steuerelementen an Bilder aus einer Datenbank](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>Gültige Ablageziele  
 Sie können Elemente auch ziehen, der **Datenquellen** nur auf gültige Ablageziele im die [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Es gibt zwei Hauptarten von gültigen Ablagezielen: Container und Steuerelemente. Ein Container ist ein Benutzeroberflächenelement, das in der Regel Steuerelemente enthält. Beispielsweise handelt es sich bei Rastern und Fenstern um Container.  
  
## <a name="generated-xaml-and-code"></a>Generierten XAML und generierter code  
 Beim Ziehen eines Elements aus der **Datenquellen** Fenster aus, um die [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die ein neues datengebundenes Steuerelement definiert (oder ein vorhandenes Steuerelement an die Datenquelle bindet). Für einige Datenquellen generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auch Code in der Code-Behind-Datei, der die Datenquelle mit Daten füllt.  
  
 Die folgende Tabelle enthält die [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und codieren, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für jeden Typ von Datenquelle generiert der **Datenquellen** Fenster.  
  
|Datenquelle|Generieren von XAML, das ein Steuerelement an die Datenquelle bindet|Generieren von Code, der die Datenquelle mit Daten füllt|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|DataSet|Ja|Ja|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Ja|Ja|  
|Dienst|Ja|Nein|  
|Object|Ja|Nein|  
  
### <a name="datasets"></a>Datasets  
 Beim Ziehen einer Tabelle oder Spalte aus der **Datenquellen** in den Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die bewirkt Folgendes:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, werden das Dataset und eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Datasets zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, erstellt das XAML das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nimmt außerdem die folgenden Änderungen an der Code-Behind-Datei vor:  
  
-   Es wird ein <xref:System.Windows.FrameworkElement.Loaded>-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)]-Element erstellt, das das Steuerelement enthält. Der Ereignishandler füllt die Tabelle mit Daten, ruft die <xref:System.Windows.Data.CollectionViewSource> aus den Ressourcen des Containers ab, und legt dann das erste Datenelement als aktuelles Element fest. Wenn eine <xref:System.Windows.FrameworkElement.Loaded> Ereignishandler bereits vorhanden ist, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dem vorhandenen Ereignishandler diesen Code hinzugefügt.  
  
### <a name="entity-data-models"></a>Entity Data models  
 Wenn Sie eine Entität oder eine Entitätseigenschaft aus ziehen die **Datenquellen** in den Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die bewirkt Folgendes:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten der Entität zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen die [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] erstellt das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
Visual Studio nimmt außerdem die folgenden Änderungen an der Code-Behind-Datei vor:  
  
-   Es wird eine neue Methode hinzugefügt, die eine Abfrage für die Entität zurückgibt, die Sie in den Designer gezogen haben (oder für die Entität, die die Eigenschaft enthält, die Sie in den Designer gezogen haben). Die neue Methode hat den Namen Get*EntityName*Abfrage, wobei *EntityName* ist der Name der Entität.  
  
-   Es wird ein <xref:System.Windows.FrameworkElement.Loaded>-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)]-Element erstellt, das das Steuerelement enthält. Der Ereignishandler ruft die Get*EntityName*Query-Methode zum Füllen der Entität mit Daten, ruft die <xref:System.Windows.Data.CollectionViewSource> aus des Containers Ressourcen und legt dann das erste Datenelement des aktuellen Elements. Wenn eine <xref:System.Windows.FrameworkElement.Loaded> Ereignishandler bereits vorhanden ist, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dem vorhandenen Ereignishandler diesen Code hinzugefügt.  
  
### <a name="services"></a>Dienste  
 Wenn Sie ziehen ein Dienstobjekt oder eine Eigenschaft aus der **Datenquellen** in den Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , das ein datengebundenes Steuerelement erstellt (oder ein vorhandenes Steuerelement an das Objekt bzw. die Eigenschaft bindet). [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert jedoch keinen Code, der das Proxydienstobjekt mit Daten füllt. Sie müssen diesen Code selbst schreiben. Ein Beispiel hierzu finden Sie unter [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio generiert XAML, das folgende Aktionen ausführt:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des von dem Dienst zurückgegebenen Objekts zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen die [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] erstellt das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
### <a name="objects"></a>erzwingen  
 Beim Ziehen eines Objekts oder einer Eigenschaft aus der **Datenquellen** in den Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , das ein datengebundenes Steuerelement erstellt (oder ein vorhandenes Steuerelement an das Objekt bzw. die Eigenschaft bindet). [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert jedoch keinen Code, um das Objekt mit Daten zu füllen. Sie müssen diesen Code selbst schreiben.  
  
> [!NOTE]
>  Benutzerdefinierte Klassen müssen öffentlich sein und standardmäßig verfügen über einen Konstruktor ohne Parameter. Sie can'tbe geschachtelte Klassen, die einen "Punkt" in der Syntax definiert. Weitere Informationen finden Sie unter [XAML und benutzerdefinierte Klassen für WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die bewirkt Folgendes:  
  
-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Objekt zu navigieren und diese anzuzeigen.  
  
-   Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, erstellt das XAML das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.  
  
## <a name="see-also"></a>Siehe auch
[Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
