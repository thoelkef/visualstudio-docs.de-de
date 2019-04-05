---
title: Binden von WPF-Steuerelementen an Daten | Microsoft-Dokumentation
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ea4cb1b8c1a31c31d06cf6cc59cef20036a6674
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960248"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Binden von WPF-Steuerelementen an Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können datengebundene erstellen [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] Steuerelemente mithilfe der **Datenquellen** Fenster. Fügen Sie zunächst eine Datenquelle, die **Datenquellen** Fenster. Ziehen Sie Elemente aus der **Datenquellen** Fenster aus, um die**WPF-Designer**.

##  <a name="adding"></a> Hinzufügen einer Datenquelle zum Datenquellenfenster
 Bevor Sie datengebundene Steuerelemente erstellen können, müssen Sie zunächst eine Datenquelle zum Hinzufügen der **Datenquellen** Fenster.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>So fügen Sie dem Datenquellenfenster eine Datenquelle hinzu

1.  Auf der **Ansicht** Startmenü **andere Windows**, und klicken Sie dann auf **Datenquellen**.

2.  Klicken Sie auf **Neue Datenquelle hinzufügen**, und führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus.

3.  Führen Sie eine der folgenden Aufgaben aus, um datengebundene Steuerelemente zu erstellen:

    -   [Erstellen eines Steuerelements, an ein einzelnes Datenfeld gebunden ist](#simple).

    -   [Erstellen eines Steuerelements, an mehrere Datenfelder gebunden ist](#complex).

    -   [Erstellen einen Satz von Steuerelementen, die an mehrere Datenfelder gebunden sind](#details).

    -   [Binden von Daten an vorhandene Steuerelemente im Designer](#existing).

##  <a name="simple"></a> Erstellen Sie ein Steuerelement, das an ein einzelnes Datenfeld gebunden ist
 Nach dem Hinzufügen einer Datenquelle, die **Datenquellen** Fenster können Sie ein neues datengebundene Steuerelement, die Daten, ein einzelnes Datenfeld, z. B. anzeigt Erstellen einer <xref:System.Windows.Controls.ComboBox> oder <xref:System.Windows.Controls.TextBox>.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>So erstellen Sie ein Steuerelement, das an ein einzelnes Datenfeld gebunden ist

1.  In der **Datenquellen** Fenster, erweitern Sie ein Element, das eine Tabelle oder ein Objekt darstellt. Suchen Sie das untergeordnete Element, das die Spalte oder die Eigenschaft darstellt, an die das Steuerelement gebunden werden soll. Ein Bildbeispiel finden Sie unter [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Optional können Sie das zu erstellende Steuerelement auswählen. Jedes Element in der **Datenquellen** verfügt über ein Standardsteuerelement, das erstellt wird, wenn Sie das Element in den Designer ziehen. Das Standardsteuerelement hängt vom zugrunde liegenden Datentyp des Elements ab.

     Um ein anderes Steuerelement auszuwählen, klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie ein Steuerelement aus. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3.  Ziehen Sie das Element, auf einen gültigen Container im Designer. Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt das neue datengebundene Steuerelement und einem entsprechend bezeichneten <xref:System.Windows.Controls.Label> im Container. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert auch [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code zum Binden des Steuerelements an die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="complex"></a> Erstellen Sie ein Steuerelement, das an mehrere Datenfelder gebunden ist
 Nachdem Sie eine Datenquelle hinzugefügt haben. die **Datenquellen** Fenster können Sie ein neues datengebundene Steuerelement, das mehrere Datenfelder, z. B. anzeigt Erstellen einer <xref:System.Windows.Controls.DataGrid> oder <xref:System.Windows.Controls.ListView>.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>So erstellen Sie ein Steuerelement, das an mehrere Datenfelder gebunden ist

1.  In der **Datenquellen** Fenster, wählen Sie ein Element, das Sie eine Tabelle oder ein Objekt darstellt. Ein Bildbeispiel finden Sie unter [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Optional können Sie das zu erstellende Steuerelement auswählen. In der Standardeinstellung jedem Element im der **Datenquellen** Fenster, das eine Datentabelle oder ein Objekt darstellt. festgelegt ist, erstellen eine <xref:System.Windows.Controls.DataGrid> (wenn das Projekt .NET Framework 4 abzielt) oder <xref:System.Windows.Controls.ListView> (für frühere Versionen von .NET Framework).

     Um ein anderes Steuerelement auszuwählen, klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie ein Steuerelement aus. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    >  Wenn eine bestimmte Spalte oder Eigenschaft nicht angezeigt werden soll, erweitern Sie das Element, um seine untergeordneten Elemente anzuzeigen. Klicken Sie auf den Dropdownpfeil neben der Spalte oder Eigenschaft, die Sie nicht möchten, um anzuzeigen, und klicken Sie dann auf **keine**.

3.  Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>. Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt das neue datengebundene Steuerelement im Container. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert auch [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code zum Binden des Steuerelements an die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="details"></a> Erstellen Sie einen Satz von Steuerelementen, die an mehrere Datenfelder gebunden sind
 Nachdem Sie eine Datenquelle hinzugefügt haben. die **Datenquellen** Fenster können Sie eine Datentabelle oder ein Objekt an eine Gruppe von Steuerelementen binden. Für jede Spalte oder jede Eigenschaft in der Tabelle oder dem Objekt wird ein anderes Steuerelement erstellt.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>So erstellen Sie einen Satz von Steuerelementen, die an mehrere Datenfelder gebunden sind

1.  In der **Datenquellen** Fenster, wählen Sie ein Element, das Sie eine Tabelle oder ein Objekt darstellt. Ein Bildbeispiel finden Sie unter [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Klicken Sie auf den Dropdown-Pfeil neben dem Element, und wählen Sie **Details**.

    > [!NOTE]
    >  Wenn eine bestimmte Spalte oder Eigenschaft nicht angezeigt werden soll, erweitern Sie das Element, um seine untergeordneten Elemente anzuzeigen. Klicken Sie auf den Dropdownpfeil neben der Spalte oder Eigenschaft, die Sie nicht möchten, um anzuzeigen, und klicken Sie dann auf **keine**.

3.  Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>. Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt die neuen datengebundenen Steuerelemente im Container. Jedes Steuerelement wird an eine andere Spalte oder Eigenschaft gebunden, und jedes Steuerelement wird von einem entsprechend benannten <xref:System.Windows.Controls.Label>-Steuerelement begleitet. Außerdem generiert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auch [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sowie Code zum Binden der Steuerelemente an die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="existing"></a> BindData an vorhandene Steuerelemente im designer
 Nachdem Sie eine Datenquelle hinzugefügt haben. die **Datenquellen** Fenster können Sie ein vorhandenes Steuerelement im Designer eine Datenbindung hinzufügen.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>So binden Sie Daten an ein vorhandenes Steuerelement im Designer

1.  In der **Datenquellen** Fenster, verwenden Sie eine der folgenden Verfahren:

    -   Um einem vorhandenen Steuerelement, das mehrere Datenfelder anzeigt, z. B. ein <xref:System.Windows.Controls.DataGrid> oder eine <xref:System.Windows.Controls.ListView>, eine Datenbindung hinzuzufügen, wählen Sie das Element aus, das die Tabelle oder das Objekt darstellt, die bzw. das Sie an das Steuerelement binden möchten.

    -   Um einem vorhandenen Steuerelement, das ein einzelnes Datenfeld anzeigt, z. B. eine <xref:System.Windows.Controls.ComboBox> oder eine <xref:System.Windows.Controls.TextBox>, eine Datenbindung hinzuzufügen, erweitern Sie das Element, das die Tabelle oder das Objekt mit den Daten darstellt, und wählen Sie dann das Element aus, das die an das Steuerelement zu bindenden Daten darstellt.

2.  Ziehen Sie das ausgewählte Element aus der **Datenquellen** Fenster auf ein vorhandenes Steuerelement im Designer. Das Steuerelement muss ein gültiges Ablageziel sein. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code zum Binden des Steuerelements auf die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    >  Wenn das Steuerelement bereits an Daten gebunden ist, wird die Datenbindung für das Steuerelement auf das Element zurückgesetzt, das zuletzt auf das Steuerelement gezogen wurde.

## <a name="see-also"></a>Siehe auch
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md) [Anzeigen verknüpfter Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md) [Binden von WPF-Steuerelemente zu einem Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md) [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
