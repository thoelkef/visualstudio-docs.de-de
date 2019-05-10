---
title: Durchsuchen, und wählen Sie ein Dialogfeld | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7a4169d57cd5b004ded9fbc9b8a16bf7537754b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417564"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Dialogfeld '.NET-Typ suchen und auswählen'
In der **Eigenschaften** Fenster, Dialogfelder und Designern, z. B. den Variablen-Designer, bei der Auswahl **nach Typen suchen...** eine Liste der Datentypen, stammt die **durchsuchen, und wählen Sie einen .NET** (Dialogfeld) (in abgekürzter Form als "Typbrowser" bezeichnet). In diesem Dialogfeld können Sie einen Typ aus der Strukturansicht der referenzierten Assemblys und Projekte auswählen.  
  
 Dieses Dialogfeld wird in einer Reihe von Benutzerszenarien wie dem Folgendem eingesetzt:  
  
- Beim Festlegen des Typs einer Variable oder eines Arguments.  
  
- Beim Auswählen eines Typs für eine generische Aktivität.  
  
- Beim Hinzufügen einer catch-Anweisung für die <xref:System.Activities.Statements.TryCatch>-Aktivität.  
  
> [!NOTE]
> Der Typbrowser kann verzweigte Visual Basic-Arraytypen, aber keine mehrdimensionalen Arraytypen anzeigen. Finden Sie unter [verzweigte Arrays](http://go.microsoft.com/fwlink/?LinkId=195226) und [mehrdimensionale Arrays](http://go.microsoft.com/fwlink/?LinkId=195227) Details.  
  
## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Auswählen eines Werts oder eines Verweistyps im Typbrowser  
  
#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>So wählen Sie einen Wert- oder Verweistyp im Typbrowser aus  
  
1. In der **Typnamen** Geben Sie den Namen des Typs, die Sie verwenden möchten.  
  
2. Führen Sie einen der folgenden Schritte aus:  
  
    - Sobald der Name des Typs, die Sie verwenden möchten, die in der Struktur im angezeigt wird der **Typnamen** Feld, doppelklicken Sie auf den Typ, um es auszuwählen.  
  
    - Geben Sie genug Zeichen in der **Typnamen** Feld zur eindeutigen Identifizierung den Typ, die Sie verwenden möchten, und drücken Sie die EINGABETASTE, um den Typ auszuwählen  
  
#### <a name="to-select-a-generic-type-from-the-type-browser"></a>So wählen Sie einen generischen Typ im Typbrowser aus  
  
1. In der **Typnamen** Feld den Namen des Typs, die Sie verwenden möchten.  
  
2. Sobald der Name des Typs, die Sie verwenden möchten, die in der Struktur im angezeigt wird der **Typnamen** Box, klicken Sie auf der Typ auswählen, die dazu führen, dass der Dropdown-Felder angezeigt werden.  
  
     Wählen Sie den Typ, den Sie verwenden, um die generische über die Dropdownfelder zu schließen, und klicken Sie dann auf möchten **OK**.  
  
## <a name="types-displayed-in-the-type-browser"></a>Typen, die im Typbrowser angezeigt werden  
 Welche Typen im Typbrowser angezeigt werden, hängt davon ab, wie der Typbrowser aufgerufen wurde. Wenn der Typbrowser, aus einem Workflowprojekt innerhalb von aufgerufen wurde **vs2010**, werden standardmäßig alle Typen in referenzierten Assemblys und referenzierten Projekte werden angezeigt. Wenn der Typbrowser von außerhalb der gestartet wurde eine **vs2010** -Projektsystems (z. B. in einer neu gehosteten workflowanwendung oder einer eigenständigen Workflowdatei), und klicken Sie dann in der Standardeinstellung die Typen aller in der Anwendungsdomäne geladenen Assemblys angezeigt werden .  
  
 Die Typen im Typbrowser können von den Aktivitätsdesignerentwicklern gefiltert werden. Für jede gegebene Aktivität wird möglicherweise nur eine Teilmenge der Typen angezeigt. Zum Beispiel werden in der <xref:System.Activities.Statements.TryCatch>-Aktivität nur die Typen, die von <xref:System.Exception> abgeleitet sind, im Typbrowser angezeigt.  
  
## <a name="filtering-search-results-in-the-type-browser"></a>Filter von Suchergebnissen im Typbrowser  
 Die Liste der Typen in der **Typnamen** Feld wird kürzer, während der Eingabe von mehr Zeichen ein, um eine Übereinstimmung zu finden. Nur Typen, deren vollqualifizierte Namen mit der eingegebenen Zeichenfolge beginnen, oder Typen, deren Kurzname mit der eingegebenen Zeichenfolge beginnen, erscheinen in der gefilterten Liste.  
  
 Zum Beispiel:  
  
1. Eingabe **Vorgang** entspricht <xref:System.OperationCanceledException> , nicht jedoch <xref:System.InvalidOperationException>. Um <xref:System.InvalidOperationException> zu finden, geben Sie System.I oder Invalid ein.  
  
2. Eingabe **generische** entspricht <xref:System.GenericUriParser> aber nicht Typen die <xref:System.Collections.Generic> Namespace. Um nach Typen im <xref:System.Collections.Generic>-Namespace zu suchen, geben Sie den vollqualifizierten Namen des Namespaces ein.  
  
## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Auswählen eines Dienstvertrags mithilfe des Typbrowserdialogfelds  
 Beim Auswählen eines Dienstvertragstyps zeigt der Typbrowser nur Typen an, die über das <xref:System.ServiceModel.ServiceContractAttribute>-Attribut verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)