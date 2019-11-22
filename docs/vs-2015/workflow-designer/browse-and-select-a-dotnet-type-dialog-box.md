---
title: Browse and Select a .NET Type Dialog Box | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297617"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Dialogfeld '.NET-Typ suchen und auswählen'
In the **Properties** window, dialog boxes, or designers such as the variable designer, when you select **Browse for Types…** from a list of data types, is the **Browse and Select a .NET Type** dialog box (referred to in an abbreviated form as the “type browser”). In diesem Dialogfeld können Sie einen Typ aus der Strukturansicht der referenzierten Assemblys und Projekte auswählen.

 Dieses Dialogfeld wird in einer Reihe von Benutzerszenarien wie dem Folgendem eingesetzt:

- Beim Festlegen des Typs einer Variable oder eines Arguments.

- Beim Auswählen eines Typs für eine generische Aktivität.

- Beim Hinzufügen einer catch-Anweisung für die <xref:System.Activities.Statements.TryCatch>-Aktivität.

> [!NOTE]
> Der Typbrowser kann verzweigte Visual Basic-Arraytypen, aber keine mehrdimensionalen Arraytypen anzeigen. See [Jagged Arrays](https://go.microsoft.com/fwlink/?LinkId=195226) and [Multidimensional Arrays](https://go.microsoft.com/fwlink/?LinkId=195227) for details.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Auswählen eines Werts oder eines Verweistyps im Typbrowser

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>So wählen Sie einen Wert- oder Verweistyp im Typbrowser aus

1. In the **Type Name** box, enter the name of the type that you want to use.

2. Führen Sie einen der folgenden Schritte aus:

    - Once the name of the type that you want to use appears in the tree in the **Type Name** box, double-click the type to select it.

    - Type enough characters in the **Type Name** box to uniquely identify the type that you want to use and then press enter to select the type

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>So wählen Sie einen generischen Typ im Typbrowser aus

1. In the **Type Name** box, type in the name of the type that you want to use.

2. Once the name of the type that you want to use appears in the tree in the **Type Name** box, click the type to select it to cause drop-down boxes appear.

     Select the type that you want to use to close the generic from the drop-down boxes, and then click **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Typen, die im Typbrowser angezeigt werden
 Welche Typen im Typbrowser angezeigt werden, hängt davon ab, wie der Typbrowser aufgerufen wurde. If the type browser was launched from a workflow project inside of **vs2010**, by default all of the types in the referenced assemblies and referenced projects are shown. If the type browser was launched from outside of a **vs2010** project system (such as in a rehosted workflow application or in a standalone workflow file), then by default the types from all of the assemblies loaded in the AppDomain are shown.

 Die Typen im Typbrowser können von den Aktivitätsdesignerentwicklern gefiltert werden. Für jede gegebene Aktivität wird möglicherweise nur eine Teilmenge der Typen angezeigt. Zum Beispiel werden in der <xref:System.Activities.Statements.TryCatch>-Aktivität nur die Typen, die von <xref:System.Exception> abgeleitet sind, im Typbrowser angezeigt.

## <a name="filtering-search-results-in-the-type-browser"></a>Filter von Suchergebnissen im Typbrowser
 The list of types in the **Type Name** box gets shorter as you type more characters to find a match. Nur Typen, deren vollqualifizierte Namen mit der eingegebenen Zeichenfolge beginnen, oder Typen, deren Kurzname mit der eingegebenen Zeichenfolge beginnen, erscheinen in der gefilterten Liste.

 Beispiel:

1. Typing **Operation** matches <xref:System.OperationCanceledException> but not <xref:System.InvalidOperationException>. Um <xref:System.InvalidOperationException> zu finden, geben Sie System.I oder Invalid ein.

2. Typing **Generic** matches <xref:System.GenericUriParser> but not types in the <xref:System.Collections.Generic> namespace. Um nach Typen im <xref:System.Collections.Generic>-Namespace zu suchen, geben Sie den vollqualifizierten Namen des Namespaces ein.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Auswählen eines Dienstvertrags mithilfe des Typbrowserdialogfelds
 Beim Auswählen eines Dienstvertragstyps zeigt der Typbrowser nur Typen an, die über das <xref:System.ServiceModel.ServiceContractAttribute>-Attribut verfügen.

## <a name="see-also"></a>Siehe auch
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)