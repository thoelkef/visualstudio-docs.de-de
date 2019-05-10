---
title: Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen | Microsoft-Dokumentation
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: adea3666c3f8b8d78c37b32a1a42f7f8b270369c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431167"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Begriff *Nachschlagetabelle* bezeichnet Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden werden. Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.  
  
 Sie können Nachschlagetabellen erstellen, indem Sie den Hauptknoten einer übergeordneten Tabelle ziehen (aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) auf ein Steuerelement auf dem Formular, das bereits in die Spalte in die zugehörige untergeordnete Tabelle gebunden ist.  
  
 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der Tabelle `Orders` enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag erteilt hat. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt. Erweitern Sie in diesem Szenario die `Orders` -Tabelle in der **Datenquellen** Fenster, und legen Sie den Hauptknoten auf **Details**. Legen Sie dann die `CustomerID` zu verwendende Spalte ein <xref:System.Windows.Forms.ComboBox> (oder ein anderes Steuerelement verwenden, die nachschlagebindung unterstützt), und ziehen Sie die `Orders` Knoten auf das Formular. Ziehen Sie abschließend die `Customers` Knoten auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall die <xref:System.Windows.Forms.ComboBox> gebunden werden, um die `CustomerID` Spalte.  
  
## <a name="to-databind-a-lookup-control"></a>So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her  
  
1. Öffnen Sie das Fenster **Datenquellen**.  
  
    > [!NOTE]
    > Für Nachschlagetabellen ist es erforderlich, dass zwei zusammengehörige Tabellen oder Objekte im **Datenquellenfenster** verfügbar sind.
  
2. Erweitern Sie im **Datenquellenfenster** die Knoten, bis die übergeordnete Tabelle und die zugehörige untergeordnete Tabelle jeweils mit allen Spalten angezeigt werden.  
  
    > [!NOTE]
    > Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.  
  
3. Ändern Sie den Ablagetyp auf **Details**, indem Sie am Knoten der untergeordneten Tabelle in der Steuerelementliste die Option **Details** auswählen. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4. Suchen Sie den Knoten, die zwei Tabellen verknüpft (die `CustomerID` Knoten im vorherigen Beispiel). Ändern Sie den Ablagetyp in einem <xref:System.Windows.Forms.ComboBox> dazu **"ComboBox"** aus der Steuerungsliste.  
  
5. Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus dem **Datenquellenfenster** auf das Formular.  
  
     Auf dem Formular werden datengebundene Steuerelemente (mit beschreibenden Bezeichnungen) sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
6. Ziehen Sie den Hauptknoten der übergeordneten Tabelle aus der **Datenquellen** direkt auf das Nachschlagesteuerelement (die <xref:System.Windows.Forms.ComboBox>).  
  
     Die Nachschlagebindungen werden jetzt festgelegt. In der folgenden Tabelle sind die speziellen Eigenschaften aufgeführt, die für das Steuerelement festgelegt wurden.  
  
    |Eigenschaft|Erklärung der Einstellung|  
    |--------------|----------------------------|  
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> fest, die für die auf das Steuerelement gezogene Tabelle erstellt wurde (also nicht auf die <xref:System.Windows.Forms.BindingSource>, die bei der Erstellung des Steuerelements erstellt wurde).<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|  
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Namen der Spalte festlegen, die Sie anzeigen möchten.|  
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Primärschlüssel in der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|  
    |**SelectedValue**|Visual Studio legt diese Eigenschaft auf die ursprüngliche, aus dem **Datenquellenfenster** gezogene und abgelegte Spalte fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die Fremdschlüsselspalte in der zugehörigen Tabelle festlegen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
