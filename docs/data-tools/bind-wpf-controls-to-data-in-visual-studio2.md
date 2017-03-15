---
title: "Gewusst wie: Binden von WPF-Steuerelementen an Daten in Visual Studio | Microsoft Docs"
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Binden von WPF-Steuerelementen an Daten in Visual Studio
Sie können mit dem **Datenquellenfenster** datengebundene [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]\-Steuerelemente erstellen.  Fügen Sie zunächst dem **Datenquellenfenster** eine Datenquelle hinzu.  Ziehen Sie dann Elemente aus dem **Datenquellenfenster** in den **WPF\-Designer**.  
  
##  <a name="adding"></a> Hinzufügen einer Datenquelle zum Datenquellenfenster  
 Bevor Sie datengebundene Steuerelemente erstellen können, müssen Sie dem **Datenquellenfenster** eine Datenquelle hinzufügen.  
  
#### So fügen Sie dem Datenquellenfenster eine Datenquelle hinzu  
  
1.  Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **Datenquellen**.  
  
2.  Klicken Sie auf **Neue Datenquelle hinzufügen**, und führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus.  
  
3.  Führen Sie eine der folgenden Aufgaben aus, um datengebundene Steuerelemente zu erstellen:  
  
    -   [Erstellen eines Steuerelements, das an ein einzelnes Datenfeld gebunden ist](#simple)  
  
    -   [Erstellen eines Steuerelements, das an mehrere Datenfelder gebunden ist](#complex)  
  
    -   [Erstellen eines Satzes von Steuerelementen, die an mehrere Datenfelder gebunden sind](#details)  
  
    -   [Binden von Daten an vorhandene Steuerelemente im Designer](#existing)  
  
##  <a name="simple"></a> Erstellen eines Steuerelements, das an ein einzelnes Datenfeld gebunden ist  
 Nachdem Sie dem **Datenquellenfenster** eine Datenquelle hinzugefügt haben, können Sie ein neues datengebundenes Steuerelement erstellen, das ein einzelnes Datenfeld anzeigt, z. B. eine <xref:System.Windows.Controls.ComboBox> oder eine <xref:System.Windows.Controls.TextBox>.  
  
#### So erstellen Sie ein Steuerelement, das an ein einzelnes Datenfeld gebunden ist  
  
1.  Erweitern Sie im **Datenquellenfenster** ein Element, das eine Tabelle oder ein Objekt darstellt.  Suchen Sie das untergeordnete Element, das die Spalte oder die Eigenschaft darstellt, an die das Steuerelement gebunden werden soll.  Ein Bildbeispiel finden Sie unter [Datenquellenfenster](../Topic/Data%20Sources%20Window.md).  
  
2.  Optional können Sie das zu erstellende Steuerelement auswählen.  Jedes Element im **Datenquellenfenster** verfügt über ein Standardsteuerelement, das erstellt wird, wenn Sie das Element in den Designer ziehen.  Das Standardsteuerelement hängt vom zugrunde liegenden Datentyp des Elements ab.  
  
     Um ein anderes Steuerelement auszuwählen, klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie ein Steuerelement aus.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>.  Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt das neue datengebundene Steuerelement und eine <xref:System.Windows.Controls.Label> mit geeignetem Titel im Container.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert auch [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und Code zum Binden des Steuerelements an die Daten.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="complex"></a> Erstellen eines Steuerelements, das an mehrere Datenfelder gebunden ist  
 Nachdem Sie dem **Datenquellenfenster** eine Datenquelle hinzugefügt haben, können Sie ein neues datengebundenes Steuerelement erstellen, das mehrere Datenfelder anzeigt, z. B. ein <xref:System.Windows.Controls.DataGrid> oder eine <xref:System.Windows.Controls.ListView>.  
  
#### So erstellen Sie ein Steuerelement, das an mehrere Datenfelder gebunden ist  
  
1.  Wählen Sie im **Datenquellenfenster** ein Element aus, das eine Tabelle oder ein Objekt darstellt.  Ein Bildbeispiel finden Sie unter [Datenquellenfenster](../Topic/Data%20Sources%20Window.md).  
  
2.  Optional können Sie das zu erstellende Steuerelement auswählen.  Standardmäßig wird mit jedem Element im **Datenquellenfenster**, das eine Datentabelle oder ein Datenobjekt darstellt, ein <xref:System.Windows.Controls.DataGrid> \(wenn das Projekt für .NET Framework 4 vorgesehen ist\) oder eine <xref:System.Windows.Controls.ListView> \(für frühere Versionen von .NET Framework\) erstellt.  
  
     Um ein anderes Steuerelement auszuwählen, klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie ein Steuerelement aus.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Wenn eine bestimmte Spalte oder Eigenschaft nicht angezeigt werden soll, erweitern Sie das Element, um seine untergeordneten Elemente anzuzeigen.  Klicken Sie auf den Dropdownpfeil neben der Spalte oder Eigenschaft, die nicht angezeigt werden soll, und dann auf **Keine**.  
  
3.  Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>.  Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt das neue datengebundene Steuerelement im Container. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt außerdem [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und Code für das Binden des Steuerelements an die Daten.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="details"></a> Erstellen eines Satzes von Steuerelementen, die an mehrere Datenfelder gebunden sind  
 Nachdem Sie dem **Datenquellenfenster** eine Datenquelle hinzugefügt haben, können Sie eine Datentabelle oder ein Datenobjekt an einen Satz von Steuerelementen binden.  Für jede Spalte oder jede Eigenschaft in der Tabelle oder dem Objekt wird ein anderes Steuerelement erstellt.  
  
#### So erstellen Sie einen Satz von Steuerelementen, die an mehrere Datenfelder gebunden sind  
  
1.  Wählen Sie im **Datenquellenfenster** ein Element aus, das eine Tabelle oder ein Objekt darstellt.  Ein Bildbeispiel finden Sie unter [Datenquellenfenster](../Topic/Data%20Sources%20Window.md).  
  
2.  Klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie **Details** aus.  
  
    > [!NOTE]
    >  Wenn eine bestimmte Spalte oder Eigenschaft nicht angezeigt werden soll, erweitern Sie das Element, um seine untergeordneten Elemente anzuzeigen.  Klicken Sie auf den Dropdownpfeil neben der Spalte oder Eigenschaft, die nicht angezeigt werden soll, und dann auf **Keine**.  
  
3.  Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>.  Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt die neuen datengebundenen Steuerelemente im Container.  Jedes Steuerelement wird an eine andere Spalte oder Eigenschaft gebunden, und jedes Steuerelement wird von einem entsprechend benannten <xref:System.Windows.Controls.Label>\-Steuerelement begleitet. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt außerdem [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und Code für das Binden der Steuerelemente an die Daten.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="existing"></a> Binden von Daten an vorhandene Steuerelemente im Designer  
 Nachdem Sie dem **Datenquellenfenster** eine Datenquelle hinzugefügt haben, können Sie einem vorhandenen Steuerelement im Designer eine Datenbindung hinzufügen.  
  
#### So binden Sie Daten an ein vorhandenes Steuerelement im Designer  
  
1.  Verwenden Sie im **Datenquellenfenster** eines der folgenden Verfahren:  
  
    -   Um einem vorhandenen Steuerelement, das mehrere Datenfelder anzeigt, z. B. ein <xref:System.Windows.Controls.DataGrid> oder eine <xref:System.Windows.Controls.ListView>, eine Datenbindung hinzuzufügen, wählen Sie das Element aus, das die Tabelle oder das Objekt darstellt, die bzw. das Sie an das Steuerelement binden möchten.  
  
    -   Um einem vorhandenen Steuerelement, das ein einzelnes Datenfeld anzeigt, z. B. eine <xref:System.Windows.Controls.ComboBox> oder eine <xref:System.Windows.Controls.TextBox>, eine Datenbindung hinzuzufügen, erweitern Sie das Element, das die Tabelle oder das Objekt mit den Daten darstellt, und wählen Sie dann das Element aus, das die an das Steuerelement zu bindenden Daten darstellt.  
  
2.  Ziehen Sie das ausgewählte Element aus dem **Datenquellenfenster** auf ein vorhandenes Steuerelement im Designer.  Das Steuerelement muss ein gültiges Ablageziel sein.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] und Code zum Binden des Steuerelements an die Daten.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
    > [!NOTE]
    >  Wenn das Steuerelement bereits an Daten gebunden ist, wird die Datenbindung für das Steuerelement auf das Element zurückgesetzt, das zuletzt auf das Steuerelement gezogen wurde.  
  
## Siehe auch  
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Gewusst wie: Erstellen von Nachschlagetabellen in WPF\-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Gewusst wie: Anzeigen verknüpfter Daten in WPF\-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)   
 [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an einen WCF\-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF\-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)