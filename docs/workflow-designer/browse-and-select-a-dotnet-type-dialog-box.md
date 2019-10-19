---
title: Dialog Feld ' .NET-Typ Workflow-Designer durchsuchen und auswählen
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: dfdbe972034920869908c1bac1cb349c98d96d3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650721"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Dialogfeld '.NET-Typ suchen und auswählen'

Wenn Sie im **Eigenschaften** Fenster, in den Dialogfeldern oder in Designern wie dem Variablen-Designer **nach Typen** aus einer Liste von Datentypen suchen auswählen, wird das Dialogfeld **.NET-Typ suchen und auswählen** (in Kürzungs Form als "Typ" bezeichnet). Browser "). In diesem Dialogfeld können Sie einen Typ aus der Strukturansicht der referenzierten Assemblys und Projekte auswählen.

Dieses Dialogfeld wird in einer Reihe von Benutzerszenarien wie dem Folgendem eingesetzt:

- Beim Festlegen des Typs einer Variable oder eines Arguments.

- Beim Auswählen eines Typs für eine generische Aktivität.

- Beim Hinzufügen einer catch-Anweisung für die <xref:System.Activities.Statements.TryCatch>-Aktivität.

> [!NOTE]
> Der Typbrowser kann verzweigte Visual Basic-Arraytypen, aber keine mehrdimensionalen Arraytypen anzeigen. Weitere Informationen finden Sie unter verzweigte [Arrays](http://go.microsoft.com/fwlink/?LinkId=195226) und mehr [dimensionale Arrays](http://go.microsoft.com/fwlink/?LinkId=195227) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Auswählen eines Werts oder eines Verweistyps im Typbrowser

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>So wählen Sie einen Wert- oder Verweistyp im Typbrowser aus

1. Geben Sie im Feld **Typname** den Namen des Typs ein, den Sie verwenden möchten.

2. Führen Sie einen der folgenden Schritte aus:

    - Sobald der Name des Typs, den Sie verwenden möchten, in der Struktur im Feld **Typname** angezeigt wird, doppelklicken Sie auf den Typ, um ihn auszuwählen.

    - Geben Sie im Feld **Typname** genügend Zeichen ein, um den Typ eindeutig zu identifizieren, den Sie verwenden möchten, und drücken Sie dann die EINGABETASTE, um den Typ auszuwählen.

### <a name="to-select-a-generic-type-from-the-type-browser"></a>So wählen Sie einen generischen Typ im Typbrowser aus

1. Geben Sie im Feld **Typname** den Namen des Typs ein, den Sie verwenden möchten.

2. Sobald der Name des Typs, den Sie verwenden möchten, in der Struktur im Feld **Typname** angezeigt wird, klicken Sie auf den Typ, um die Dropdown Felder auszuwählen.

     Wählen Sie den Typ aus, den Sie verwenden möchten, um das generische in den Dropdown Feldern zu schließen, und klicken Sie dann auf **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Typen, die im Typbrowser angezeigt werden

Welche Typen im Typbrowser angezeigt werden, hängt davon ab, wie der Typbrowser aufgerufen wurde. Wenn der Typbrowser von einem Workflow Projekt in **VS2010**gestartet wurde, werden standardmäßig alle Typen in den Assemblys, auf die verwiesen wird, und referenzierte Projekte angezeigt. Wenn der Typbrowser von außerhalb eines **VS2010** -Projekt Systems gestartet wurde (z. b. in einer neu gehosteten Workflow Anwendung oder in einer eigenständigen Workflow Datei), werden standardmäßig die Typen aus allen in der AppDomain geladenen Assemblys angezeigt.

Die Typen im Typbrowser können von den Aktivitätsdesignerentwicklern gefiltert werden. Für jede gegebene Aktivität wird möglicherweise nur eine Teilmenge der Typen angezeigt. Zum Beispiel werden in der <xref:System.Activities.Statements.TryCatch>-Aktivität nur die Typen, die von <xref:System.Exception> abgeleitet sind, im Typbrowser angezeigt.

## <a name="filtering-search-results-in-the-type-browser"></a>Filter von Suchergebnissen im Typbrowser

Die Liste der Typen im Feld **Typname** wird kürzer, da Sie mehr Zeichen eingeben, um eine Entsprechung zu finden. Nur Typen, deren fullyqualified-Name mit der eingegebenen Zeichenfolge beginnt, oder Typen, deren Kurzname mit der Zeichenfolge beginnt, die Sie eingegeben haben, werden in der gefilterten Liste angezeigt.

Beispiel:

1. Der Eingabe **Vorgang** entspricht <xref:System.OperationCanceledException>, aber nicht <xref:System.InvalidOperationException>. Um <xref:System.InvalidOperationException> zu finden, geben Sie System.I oder Invalid ein.

2. Das Eingeben von **generischen** Übereinstimmungen <xref:System.GenericUriParser>, aber nicht von Typen im <xref:System.Collections.Generic>-Namespace. Geben Sie den voll qualifizierten Namen des Namespace ein, um im <xref:System.Collections.Generic>-Namespace nach Typen zu suchen.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Auswählen eines Dienstvertrags mithilfe des Typbrowserdialogfelds

Beim Auswählen eines Dienstvertragstyps zeigt der Typbrowser nur Typen an, die über das <xref:System.ServiceModel.ServiceContractAttribute>-Attribut verfügen.

## <a name="see-also"></a>Siehe auch

- [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)