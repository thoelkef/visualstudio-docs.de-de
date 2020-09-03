---
title: Erstellen von Nachschlage Tabellen in Windows Forms Anwendungen | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72630939"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Begriff *Nachschlagetabelle* bezeichnet Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden werden. Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.

 Sie können Nachschlage Tabellen erstellen, indem Sie den Haupt Knoten einer übergeordneten Tabelle (aus dem [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) auf ein Steuerelement auf dem Formular ziehen, das bereits an die Spalte in der zugehörigen untergeordneten Tabelle gebunden ist.

 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der Tabelle `Orders` enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag erteilt hat. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt. In diesem Szenario erweitern Sie die `Orders` Tabelle im **Datenquellen** Fenster und legen den Haupt Knoten auf **Details**fest. Legen Sie dann `CustomerID` für die Spalte die Verwendung eines <xref:System.Windows.Forms.ComboBox> (oder eines beliebigen anderen Steuer Elements, das die Such Bindung unterstützt) fest, und ziehen `Orders` Sie den Knoten auf das Formular. Ziehen Sie schließlich den `Customers` Knoten auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall die <xref:System.Windows.Forms.ComboBox> an die `CustomerID` Spalte gebundene.

## <a name="to-databind-a-lookup-control"></a>So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her

1. Öffnen Sie das Fenster **Datenquellen**.

    > [!NOTE]
    > Für Nachschlagetabellen ist es erforderlich, dass zwei zusammengehörige Tabellen oder Objekte im **Datenquellenfenster** verfügbar sind.

2. Erweitern Sie im **Datenquellenfenster** die Knoten, bis die übergeordnete Tabelle und die zugehörige untergeordnete Tabelle jeweils mit allen Spalten angezeigt werden.

    > [!NOTE]
    > Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.

3. Ändern Sie den Ablagetyp auf **Details**, indem Sie am Knoten der untergeordneten Tabelle in der Steuerelementliste die Option **Details** auswählen. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Suchen Sie den Knoten, der die beiden Tabellen verknüpft (der `CustomerID` Knoten im vorherigen Beispiel). Ändern Sie den Ablagetyp in ein, indem Sie in <xref:System.Windows.Forms.ComboBox> der Steuerelement Liste die Option **ComboBox** auswählen.

5. Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus dem **Datenquellenfenster** auf das Formular.

     Auf dem Formular werden datengebundene Steuerelemente (mit beschreibenden Bezeichnungen) sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> , und wird <xref:System.Windows.Forms.BindingNavigator> in der Komponenten Leiste angezeigt.

6. Ziehen Sie jetzt den Haupt Knoten der übergeordneten Tabelle aus dem **Datenquellen** Fenster direkt auf das Nachschlage Steuerelement ( <xref:System.Windows.Forms.ComboBox> ).

     Die Nachschlagebindungen werden jetzt festgelegt. In der folgenden Tabelle sind die speziellen Eigenschaften aufgeführt, die für das Steuerelement festgelegt wurden.

    |Eigenschaft|Erklärung der Einstellung|
    |--------------|----------------------------|
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> fest, die für die auf das Steuerelement gezogene Tabelle erstellt wurde (also nicht auf die <xref:System.Windows.Forms.BindingSource>, die bei der Erstellung des Steuerelements erstellt wurde).<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Namen der Spalte festlegen, die Sie anzeigen möchten.|
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf den Primärschlüssel in der Tabelle festlegen, aus der Sie eine Spalte anzeigen möchten.|
    |**SelectedValue**|Visual Studio legt diese Eigenschaft auf die ursprüngliche, aus dem **Datenquellenfenster** gezogene und abgelegte Spalte fest.<br /><br /> Falls eine Anpassung erforderlich ist, können Sie diese Eigenschaft auf die Fremdschlüsselspalte in der zugehörigen Tabelle festlegen.|

## <a name="see-also"></a>Weitere Informationen
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
