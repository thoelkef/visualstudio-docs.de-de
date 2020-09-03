---
title: Binden von WPF-Steuerelementen an Daten (Teil 1) | Microsoft-Dokumentation
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25b144409ae58f006602706a5b5cb498c0535ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540165"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Binden von WPF-Steuerelementen an Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]-Steuerelemente binden. Um diese Daten gebundenen Steuerelemente zu erstellen, können Sie Elemente aus dem **Datenquellen** Fenster auf den [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] in ziehen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In diesem Thema werden einige der häufigsten Aufgaben, Tools und Klassen beschrieben, mit denen Sie datengebundene [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]-Anwendungen erstellen können.

 Allgemeine Informationen zum Erstellen von Daten gebundenen Steuerelementen in finden Sie unterbinden von Steuer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Elementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Weitere Informationen zur [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] Datenbindung finden Sie unter [Übersicht über die Datenbindung](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Aufgaben beim Binden von WPF-Steuerelementen an Daten
 In der folgenden Tabelle werden die Aufgaben aufgeführt, die durch Ziehen von Elementen aus dem Fenster **Datenquellen** in den [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] ausgeführt werden können.

|Aufgabe|Weitere Informationen|
|----------|----------------------|
|Erstellen von neuen datengebundenen Steuerelementen<br /><br /> Binden Sie vorhandenen Steuerelemente an Daten.|[Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Binden von WPF-Steuerelementen an ein DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Erstellen von Steuerelementen, die verknüpfte Daten in Beziehungen zwischen übergeordneten und untergeordneten Elementen anzeigen: Wenn der Benutzer einen übergeordneten Datensatz in einem Steuerelement auswählt, werden in einem anderen Steuerelement verknüpfte untergeordnete Daten für den ausgewählten Datensatz angezeigt.|[Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)|
|Erstellen einer *Nachschlagetabelle*, in der Informationen aus einer Tabelle auf der Grundlage des Werts eines Fremdschlüsselfelds in einer anderen Tabelle angezeigt werden.|[Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Binden eines Steuerelements an ein Bild in einer Datenbank|[Vorgehensweise: Binden von Steuerelementen an Bilder aus einer Datenbank](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Gültige Ablageziele
 Sie können Elemente im **Datenquellenfenster** nur auf gültige Ablageziele im [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] ziehen. Es gibt zwei Hauptarten von gültigen Ablagezielen: Container und Steuerelemente. Ein Container ist ein Benutzeroberflächenelement, das in der Regel Steuerelemente enthält. Beispielsweise handelt es sich bei Rastern und Fenstern um Container.

## <a name="generated-xaml-and-code"></a>Generierte XAML und generierter Code
 Wenn Sie ein Element aus dem **Datenquellen** Fenster in das ziehen [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das ein neues Daten gebundenes Steuerelement definiert (oder ein vorhandenes Steuerelement an die Datenquelle bindet). Für einige Datenquellen generiert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auch Code in der Code-Behind-Datei, der die Datenquelle mit Daten füllt.

 In der folgenden Tabelle sind die [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] -und-Codes aufgeführt, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für jeden Daten Quellentyp im **Datenquellen** Fenster generiert.

|Datenquelle|Generieren von XAML, das ein Steuerelement an die Datenquelle bindet|Generieren von Code, der die Datenquelle mit Daten füllt|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Dataset|Ja|Ja|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Ja|Ja|
|Dienst|Ja|Nein|
|Object|Ja|Nein|

### <a name="datasets"></a>Datasets
 Wenn Sie eine Tabelle oder eine Spalte aus dem **Datenquellen** Fenster in den Designer ziehen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert, das folgende Aktionen durch [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] führt:

- Den Ressourcen des Containers, in den Sie das Element gezogen haben, werden das Dataset und eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Datasets zu navigieren und diese anzuzeigen.

- Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, erstellt das XAML das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Außerdem nimmt die folgenden Änderungen an der Code-Behind-Datei vor:

- Es wird ein <xref:System.Windows.FrameworkElement.Loaded>-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)]-Element erstellt, das das Steuerelement enthält. Der Ereignishandler füllt die Tabelle mit Daten, ruft die <xref:System.Windows.Data.CollectionViewSource> aus den Ressourcen des Containers ab, und legt dann das erste Datenelement als aktuelles Element fest. Wenn bereits ein- <xref:System.Windows.FrameworkElement.Loaded> Ereignishandler vorhanden ist, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fügt dem vorhandenen Ereignishandler diesen Code hinzu.

### <a name="entity-data-models"></a>Entity Data Models
 Wenn Sie eine Entität oder eine Entitäts Eigenschaft aus dem **Datenquellen** Fenster in den Designer ziehen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert, das folgende Aktionen durch [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] führt:

- Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten der Entität zu navigieren und diese anzuzeigen.

- Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, erstellt das Steuerelement, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

  Visual Studio nimmt außerdem die folgenden Änderungen an der Code-Behind-Datei vor:

- Es wird eine neue Methode hinzugefügt, die eine Abfrage für die Entität zurückgibt, die Sie in den Designer gezogen haben (oder für die Entität, die die Eigenschaft enthält, die Sie in den Designer gezogen haben). Die neue Methode hat den Namen get*EntityName*Query, wobei *EntityName* der Name der Entität ist.

- Es wird ein <xref:System.Windows.FrameworkElement.Loaded>-Ereignishandler für das [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)]-Element erstellt, das das Steuerelement enthält. Der Ereignishandler ruft die get*EntityName*Query-Methode auf, um die Entität mit Daten zu füllen, Ruft den <xref:System.Windows.Data.CollectionViewSource> aus den Ressourcen des Containers ab und legt dann das erste Datenelement als Aktuelles Element ab. Wenn bereits ein- <xref:System.Windows.FrameworkElement.Loaded> Ereignishandler vorhanden ist, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fügt dem vorhandenen Ereignishandler diesen Code hinzu.

### <a name="services"></a>Dienste
 Wenn Sie ein Dienst Objekt oder eine Eigenschaft aus dem **Datenquellen** Fenster in den Designer ziehen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das ein Daten gebundenes Steuerelement erstellt (oder ein vorhandenes Steuerelement an das Objekt oder die Eigenschaft bindet). [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert jedoch keinen Code, der das Proxydienstobjekt mit Daten füllt. Sie müssen diesen Code selbst schreiben. Ein Beispiel, das die Vorgehensweise veranschaulicht, finden Sie unter [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio generiert XAML, das folgende Aktionen ausführt:

- Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des von dem Dienst zurückgegebenen Objekts zu navigieren und diese anzuzeigen.

- Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, erstellt das Steuerelement, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

### <a name="objects"></a>erzwingen
 Wenn Sie ein Objekt oder eine Eigenschaft aus dem **Datenquellen** Fenster in den Designer ziehen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] das ein Daten gebundenes Steuerelement erstellt (oder ein vorhandenes Steuerelement an das Objekt oder die Eigenschaft bindet). [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert jedoch keinen Code, um das Objekt mit Daten zu füllen. Sie müssen diesen Code selbst schreiben.

> [!NOTE]
> Benutzerdefinierte Klassen müssen öffentlich sein und verfügen standardmäßig über einen Konstruktor ohne Parameter. Sie können keine Klassen mit einem "Punkt" in ihrer Syntax enthalten. Weitere Informationen finden Sie unter [XAML und benutzerdefinierte Klassen für WPF](https://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , das folgende Aktionen durchführt:

- Den Ressourcen des Containers, in den Sie das Element gezogen haben, wird eine neue <xref:System.Windows.Data.CollectionViewSource> hinzugefügt. Die <xref:System.Windows.Data.CollectionViewSource> ist ein Objekt, das verwendet werden kann, um in den Daten des Objekt zu navigieren und diese anzuzeigen.

- Es wird eine Datenbindung für ein Steuerelement erstellt. Wenn Sie das Element auf ein vorhandenes Steuerelement im Designer ziehen, bindet das XAML das Steuerelement an das Element. Wenn Sie das Element in einen Container ziehen, erstellt das XAML das Steuerelement, das für das gezogene Element ausgewählt wurde, und bindet das Steuerelement an das Element. Das Steuerelement wird in einem neuen <xref:System.Windows.Controls.Grid> erstellt.

## <a name="see-also"></a>Weitere Informationen
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
