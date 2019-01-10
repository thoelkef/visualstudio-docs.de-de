---
title: Binden von WPF-Steuerelementen an Daten per Push – Teil 1
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
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 6b1f884018be97e49dfa9c300a2ad126fa185cf4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932784"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Binden von WPF-Steuerelementen an Daten in Visual Studio

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]-Steuerelemente binden. Um diese datengebundene Steuerelemente zu erstellen, können Sie Elemente aus ziehen die **Datenquellen** Fenster auf die [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] in Visual Studio. In diesem Thema werden einige der häufigsten Aufgaben, Tools und Klassen beschrieben, mit denen Sie datengebundene [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]-Anwendungen erstellen können.

Allgemeine Informationen über das Erstellen von datengebundenen Steuerelementen in Visual Studio finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Weitere Informationen zur [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]-Datenbindung finden Sie in der [Übersicht über die Datenbindung](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Aufgaben beim Binden von WPF-Steuerelementen an Daten

In der folgenden Tabelle werden die Aufgaben aufgeführt, die durch Ziehen von Elementen aus dem Fenster **Datenquellen** in den [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] ausgeführt werden können.

|Aufgabe|Weitere Informationen|
|----------| - |
|Erstellen von neuen datengebundenen Steuerelementen<br /><br /> Binden Sie vorhandenen Steuerelemente an Daten.|[WPF-Steuerelemente an einen Datensatz binden](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Erstellen von Steuerelementen, die verknüpfte Daten in Beziehungen zwischen übergeordneten und untergeordneten Elementen anzeigen: Wenn der Benutzer einen übergeordneten Datensatz in einem Steuerelement auswählt, werden in einem anderen Steuerelement verknüpfte untergeordnete Daten für den ausgewählten Datensatz angezeigt.|[Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)|
|Erstellen einer *Nachschlagetabelle*, in der Informationen aus einer Tabelle auf der Grundlage des Werts eines Fremdschlüsselfelds in einer anderen Tabelle angezeigt werden.|[Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Binden eines Steuerelements an ein Bild in einer Datenbank|[Vorgehensweise: Binden von Steuerelementen an Bilder aus einer Datenbank](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Gültige Ablageziele

Sie können Elemente im **Datenquellenfenster** nur auf gültige Ablageziele im [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] ziehen. Es gibt zwei Hauptarten von gültigen Ablagezielen: Container und Steuerelemente. Ein Container ist ein Benutzeroberflächenelement, das in der Regel Steuerelemente enthält. Beispielsweise handelt es sich bei Rastern und Fenstern um Container.

## <a name="generated-xaml-and-code"></a>Generierte XAML und generierter Code

Beim Ziehen eines Elements aus der **Datenquellen** Fenster aus, um die [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], generiert Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die ein neues datengebundenen Steuerelement definiert (oder ein vorhandenes Steuerelement an die Datenquelle bindet). Für einige Datenquellen generiert Visual Studio Code auch in der CodeBehind-Datei, die die Datenquelle mit Daten füllt.

Die folgende Tabelle enthält die [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und Code, der für jeden Typ von Datenquelle in Visual Studio generiert die **Datenquellen** Fenster.

| Datenquelle | Generieren von XAML, das ein Steuerelement an die Datenquelle bindet | Generieren von Code, der die Datenquelle mit Daten füllt |
| - | - | - |
| DataSet | Ja | Ja |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Ja | Ja |
| Dienst | Ja | Nein |
| Object | Ja | Nein |

### <a name="datasets"></a>Datasets

Beim Ziehen einer Tabelle oder Spalte aus der **Datenquellen** in den Designer, Visual Studio generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die bewirkt Folgendes:

-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, werden das Dataset und eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Datasets zu navigieren und diese anzuzeigen.

-   Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, die XAML erstellt, das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

Visual Studio nimmt außerdem die folgenden Änderungen an der Code-Behind-Datei vor:

- Es wird ein <xref:System.Windows.FrameworkElement.Loaded>-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)]-Element erstellt, das das Steuerelement enthält. Der Ereignishandler füllt die Tabelle mit Daten, ruft die <xref:System.Windows.Data.CollectionViewSource> aus den Ressourcen des Containers ab, und legt dann das erste Datenelement als aktuelles Element fest. Wenn eine <xref:System.Windows.FrameworkElement.Loaded> Ereignishandler bereits vorhanden ist, wird Visual Studio fügt dem vorhandenen Ereignishandler diesen Code hinzu.

### <a name="entity-data-models"></a>Entity Data Models

Sie ziehen, wenn eine Entität oder eine Entitätseigenschaft aus dem **Datenquellen** in den Designer, Visual Studio generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die bewirkt Folgendes:

- Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten der Entität zu navigieren und diese anzuzeigen.

- Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement an das Element. Wenn Sie das Element in einen Container, ziehen die [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wird das Steuerelement erstellt, die für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

Visual Studio nimmt außerdem die folgenden Änderungen an der Code-Behind-Datei vor:

- Es wird eine neue Methode hinzugefügt, die eine Abfrage für die Entität zurückgibt, die Sie in den Designer gezogen haben (oder für die Entität, die die Eigenschaft enthält, die Sie in den Designer gezogen haben). Die neue Methode hat den Namen `Get<EntityName>Query`, wobei `\<EntityName>` ist der Name der Entität.

- Es wird ein <xref:System.Windows.FrameworkElement.Loaded>-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)]-Element erstellt, das das Steuerelement enthält. Der Ereignishandler ruft die `Get<EntityName>Query` Methode zum Auffüllen der Entitäts mit Daten, ruft der <xref:System.Windows.Data.CollectionViewSource> aus des Containers Ressourcen und legt dann das erste Datenelement als aktuellen Elements. Wenn eine <xref:System.Windows.FrameworkElement.Loaded> Ereignishandler bereits vorhanden ist, wird Visual Studio fügt dem vorhandenen Ereignishandler diesen Code hinzu.

### <a name="services"></a>Dienste

Sie ziehen, wenn ein Dienstobjekt oder eine Eigenschaft aus der **Datenquellen** in den Designer, Visual Studio generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die ein vom datengebundenen Steuerelement erstellt (oder ein vorhandenes Steuerelement an das Objekt oder die Eigenschaft bindet). Visual Studio generiert jedoch keinen Code, der das Proxydienstobjekt mit Daten füllt. Sie müssen diesen Code selbst schreiben. Ein Beispiel zur Veranschaulichung der Vorgehensweise hierfür finden Sie unter [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio generiert XAML, das folgende Aktionen ausführt:

- Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des von dem Dienst zurückgegebenen Objekts zu navigieren und diese anzuzeigen.

- Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] das Steuerelement an das Element. Wenn Sie das Element in einen Container, ziehen die [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wird das Steuerelement erstellt, die für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

### <a name="objects"></a>erzwingen

Beim Ziehen eines Objekts oder einer Eigenschaft aus der **Datenquellen** in den Designer, Visual Studio generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die ein vom datengebundenen Steuerelement erstellt (oder ein vorhandenes Steuerelement an das Objekt oder die Eigenschaft bindet). Visual Studio erzeugt Code, um das Objekt mit Daten füllen jedoch nicht. Sie müssen diesen Code selbst schreiben.

> [!NOTE]
> Benutzerdefinierte Klassen müssen öffentlich sein und in der Standardeinstellung haben einen Konstruktor ohne Parameter. Diese can'tbe geschachtelte Klassen, die einen "Punkt" in der Syntax definiert. Weitere Informationen finden Sie unter [XAML und benutzerdefinierte Klassen für WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , die bewirkt Folgendes:

-   Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Objekt zu navigieren und diese anzuzeigen.

-   Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, die XAML erstellt, das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement auf das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)