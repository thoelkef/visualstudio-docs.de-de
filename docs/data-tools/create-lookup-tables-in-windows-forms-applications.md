---
title: Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 75035b12972299c0c9d4b9b515cb4cbd51308739
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
Der Begriff *Nachschlagetabelle* Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden sind. Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.  
  
 Erstellen von Nachschlagetabellen ziehen den Hauptknoten der übergeordneten Tabelle (aus der [Datenquellenfenster](add-new-data-sources.md)) auf ein Steuerelement auf dem Formular, das bereits an die Spalte in die zugehörige untergeordnete Tabelle gebunden ist.  
  
 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der `Orders` Tabelle enthält eine `CustomerID`, der angibt, welcher Kunde den Auftrag erteilt. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt. In diesem Szenario, erweitern Sie die `Orders` -Tabelle in der **Datenquellen** Fenster, und legen Sie den Hauptknoten auf **Details**. Legen Sie dann die `CustomerID` zu verwendende Spalte ein <xref:System.Windows.Forms.ComboBox> (oder andere Steuerelemente, die Suche Bindung unterstützt), und ziehen Sie die `Orders` Knoten auf das Formular. Schließlich, ziehen Sie die `Customers` Knoten auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall die <xref:System.Windows.Forms.ComboBox> gebunden werden, um die `CustomerID` Spalte.  
  
## <a name="to-databind-a-lookup-control"></a>So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her  
  
1.  Öffnen der **Datenquellen** Fenster.  
  
    > [!NOTE]
    >  Nachschlagetabellen ist es erforderlich, dass zwei zusammengehörige Tabellen oder Objekte verfügbar sind die **Datenquellen** Fenster. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).  
  
2.  Erweitern Sie die Knoten in der **Datenquellen** bis Sie der übergeordneten Tabelle und alle zugehörigen Spalten und die zugehörige untergeordnete Tabelle und alle darin enthaltenen Spalten angezeigt werden.  
  
    > [!NOTE]
    >  Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.  
  
3.  Ändern Sie den Ablagetyp der untergeordneten Tabelle **Details** dazu **Details** aus der Steuerungsliste auf Knoten der untergeordneten Tabelle. Weitere Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Suchen Sie den Knoten, die zwei Tabellen verknüpft (die `CustomerID` Knoten im vorherigen Beispiel). Ändern Sie den Ablagetyp in einem <xref:System.Windows.Forms.ComboBox> dazu **ComboBox** aus der Steuerungsliste.  
  
5.  Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus der **Datenquellen** auf das Formular.  
  
     Auf dem Formular werden datengebundene Steuerelemente (mit beschreibenden Bezeichnungen) sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
6.  Ziehen Sie den Hauptknoten der übergeordneten Tabelle aus der **Datenquellen** direkt auf das Nachschlagesteuerelement (die <xref:System.Windows.Forms.ComboBox>).  
  
     Die Nachschlagebindungen werden jetzt festgelegt. In der folgenden Tabelle sind die speziellen Eigenschaften aufgeführt, die für das Steuerelement festgelegt wurden.  
  
    |Eigenschaft|Erklärung der Einstellung|  
    |--------------|----------------------------|  
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> fest, die für die auf das Steuerelement gezogene Tabelle erstellt wurde (also nicht auf die <xref:System.Windows.Forms.BindingSource>, die bei der Erstellung des Steuerelements erstellt wurde).<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|  
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Namen der Spalte festlegen, die Sie anzeigen möchten.|  
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Primärschlüssel in der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|  
    |**"SelectedValue"**|Visual Studio wird diese Eigenschaft auf die ursprüngliche Spalte gelöscht wird, aus der **Datenquellen** Fenster.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die Fremdschlüsselspalte in der zugehörigen Tabelle festlegen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)