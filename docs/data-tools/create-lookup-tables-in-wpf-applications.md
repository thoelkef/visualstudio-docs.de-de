---
title: "Gewusst wie: Erstellen von Nachschlagetabellen in WPF-Anwendungen | Microsoft Docs"
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Erstellen von Nachschlagetabellen in WPF-Anwendungen
Sie können eine Nachschlagetabelle erstellen, indem Sie den Hauptknoten einer übergeordneten Tabelle oder eines übergeordneten Objekts im **Datenquellenfenster** auf ein Steuerelement ziehen, das bereits an eine Spalte oder Eigenschaft in einer verknüpften untergeordneten Tabelle gebunden ist.  Als *Nachschlagetabelle* \(manchmal als *Nachschlagebindung* bezeichnet\) wird ein Steuerelement bezeichnet, das Informationen aus einer Datentabelle auf Grundlage des Werts eines Fremdschlüsselfelds in einer anderen Tabelle anzeigt.  
  
 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält.  Jeder Datensatz in der Tabelle `Orders` enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag erteilt hat.  Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt.  Wenn Sie eine Liste mit Aufträgen aus der Tabelle `Orders` anzeigen, möchten Sie eventuell statt der `CustomerID` den tatsächlichen Namen des Kunden anzeigen.  Da der Kundenname in der Tabelle `Customers` enthalten ist, müssen Sie zum Anzeigen des Kundennamens eine Nachschlagetabelle erstellen.  In der Nachschlagetabelle wird der `CustomerID`\-Wert im `Orders`\-Datensatz verwendet, um in der Beziehung zu navigieren und den benutzerfreundlichen Kundennamen zurückzugeben.  
  
### So erstellen Sie eine Suchtabelle  
  
1.  Fügen Sie dem Projekt einen der folgenden Typen von Datenquellen mit zugehörigen Daten hinzu:  
  
    -   Dataset oder Entity Data Model.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   WCF\-Datendienst, WCF\-Dienst oder Webdienst.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Objekte.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
    > [!NOTE]
    >  Bevor Sie eine Nachschlagetabelle erstellen können, müssen zwei verknüpfte Tabellen oder Objekte als Datenquelle für das Projekt vorhanden sein.  
  
2.  Öffnen Sie den **WPF\-Designer**, und stellen Sie sicher, dass der Designer einen Container enthält, der ein gültiges Ablageziel für die Elemente im **Datenquellenfenster** ist.  
  
     Weitere Informationen über gültige Ablageziele finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das **Datenquellenfenster** zu öffnen.  
  
4.  Erweitern Sie die Knoten im **Datenquellenfenster**, bis die übergeordnete Tabelle oder das übergeordnete Objekt und die verknüpfte untergeordnete Tabelle bzw. das verknüpfte untergeordnete Objekt sichtbar sind.  
  
    > [!NOTE]
    >  Die verknüpfte untergeordnete Tabelle oder das verknüpfte untergeordnete Objekt ist der Knoten, der unter der übergeordneten Tabelle bzw. dem übergeordneten Objekt als erweiterbarer untergeordneter Knoten angezeigt wird.  
  
5.  Klicken Sie auf das Dropdownmenü für den untergeordneten Knoten, und wählen Sie **Details** aus.  
  
6.  Erweitern Sie den untergeordneten Knoten.  
  
7.  Klicken Sie unter dem untergeordneten Knoten auf das Dropdownmenü für das Element, das die untergeordneten und übergeordneten Daten verknüpft \(im obigen Beispiel ist dies der Knoten **CustomerID**\).  Wählen Sie einen der folgenden Typen von Steuerelementen aus, die Nachschlagebindung unterstützen:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Wenn das **ListBox**\-Steuerelement oder das **ListView**\-Steuerelement nicht in der Liste angezeigt wird, können Sie der Liste diese Steuerelemente hinzufügen.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Ein beliebiges benutzerdefiniertes Steuerelement, das von <xref:System.Windows.Controls.Primitives.Selector> abgeleitet wird.  
  
        > [!NOTE]
        >  Informationen zum Hinzufügen von benutzerdefinierten Steuerelementen zu der Liste von Steuerelementen, die Sie im **Datenquellenfenster** als Elemente auswählen können, finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Ziehen Sie den untergeordneten Knoten aus dem **Datenquellenfenster** auf einen Container im WPF\-Designer \(im obigen Beispiel ist der untergeordnete Knoten der Knoten **Orders**\).  
  
     Visual Studio generiert XAML, mit dem für jedes Element, das Sie ziehen, neue datengebundene Steuerelemente erstellt werden.  Mit dem XAML wird außerdem den Ressourcen des Ablageziels eine neue <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder das untergeordnete Objekt hinzugefügt.  Für einige Datenquellen generiert Visual Studio zudem Code, um Daten in die Tabelle oder das Objekt zu laden.  Weitere Informationen finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Ziehen Sie den übergeordneten Knoten aus dem **Datenquellenfenster** auf das Nachschlagebindungs\-Steuerelement, das Sie zuvor erstellt haben \(im obigen Beispiel ist der übergeordnete Knoten der Knoten **Customers**\).  
  
     Visual Studio legt einige Eigenschaften für das Steuerelement fest, um die Nachschlagebindung zu konfigurieren.  In der folgenden Tabelle sind die Eigenschaften aufgeführt, die von Visual Studio geändert werden.  Sie können diese Eigenschaften ggf. im XAML oder im **Eigenschaftenfenster** ändern.  
  
    |Property|Erklärung der Einstellung|  
    |--------------|-------------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Diese Eigenschaft gibt die Auflistung oder die Bindung an, die verwendet wird, um die im Steuerelement angezeigten Daten abzurufen.  Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Data.CollectionViewSource> für die übergeordneten Daten fest, die Sie auf das Steuerelement gezogen haben.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Diese Eigenschaft gibt den Pfad des Datenelements an, das im Steuerelement angezeigt wird.  Visual Studio legt diese Eigenschaft auf die erste Spalte oder Eigenschaft in den übergeordneten Daten nach dem Primärschlüssel fest, die vom Datentyp String ist.<br /><br /> Wenn Sie eine andere Spalte oder Eigenschaft in den übergeordneten Daten anzeigen möchten, ändern Sie den Pfad der Eigenschaft in den Pfad einer anderen Eigenschaft.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bindet diese Eigenschaft an die Spalte oder Eigenschaft der untergeordneten Daten, die Sie in den Designer gezogen haben.  Dies ist der Fremdschlüssel für die übergeordneten Daten.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio legt diese Eigenschaft auf den Pfad der Spalte oder Eigenschaft der untergeordneten Daten fest, die der Fremdschlüssel für die übergeordneten Daten ist.|  
  
## Siehe auch  
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Gewusst wie: Anzeigen verknüpfter Daten in WPF\-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)   
 [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF\-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)