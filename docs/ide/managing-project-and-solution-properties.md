---
title: Verwalten von Projekt- und Projektmappeneigenschaften
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96581fbaff9c2ddc85fbb92d73096f2a369d4c7b
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746311"
---
# <a name="manage-project-and-solution-properties"></a>Verwalten von Projekt- und Projektmappeneigenschaften

Projekte haben Eigenschaften, die viele Aspekte der Kompilierung, des Debuggens, des Testens und des Bereitstellens steuern. Einige Eigenschaften gibt es für alle Projekttypen, und einige gelten nur für bestimmte Sprachen oder Plattformen. Sie erhalten Zugriff auf die Projekteigenschaften, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten klicken und **Eigenschaften** auswählen. Alternativ können Sie „Eigenschaften“ in das Suchfeld **Schnellstart** auf der Menüleiste eingeben.

![Projekt-Kontextmenü](../ide/media/vs2015_proj_prop_menu.gif)

.NET-Projekte haben womöglich außerdem einen Eigenschaftenknoten in der Projektstruktur selbst.

![Knoten "Eigenschaften" in der Struktur des Projektmappen-Explorers](../ide/media/vs2015_props_se.png)

## <a name="project-properties"></a>Projekteigenschaften

Projekteigenschaften werden in Gruppen organisiert, und jede Gruppe hat eine eigene Eigenschaftenseite. Diese kann je nach Sprache und Projekttyp unterschiedlich aussehen.

### <a name="c-visual-basic-and-f-projects"></a>C#-, Visual Basic- und F#-Projekte

In C#-, Visual Basic- und F#-Projekten sind Eigenschaften im **Projekt-Designer** verfügbar. Folgende Abbildung zeigt die Eigenschaftsseite **Build** für ein WPF-Projekt in C#:

![Visual Studio-Projekt-Designer](../ide/media/vs2015_proppage_build.png)

Informationen zu den einzelnen Eigenschaftsseiten im **Projekt-Designer** finden Sie unter [Project properties reference (Referenz zu Projekteigenschaften)](../ide/reference/project-properties-reference.md).

> [!TIP]
> Projektmappen besitzen ebenso wie Projektelemente einige Eigenschaften. Auf diese Eigenschaften wird nicht über den **Projekt-Designer**, sondern über das [Eigenschaftenfenster](../ide/reference/properties-window.md) zugegriffen.

### <a name="c-and-javascript-projects"></a>C++- und JavaScript-Projekte

C++- und JavaScript-Projekte haben eine andere Benutzeroberfläche zum Verwalten von Projekteigenschaften. Die folgende Abbildung zeigt eine Eigenschaftenseite für ein C++-Projekt (JavaScript-Seiten sind ähnlich):

![Visual C&#43;&#43;-Projekteigenschaften](../ide/media/vs2015_projprops_cpp.png)

Informationen zu C++-Projekteigenschaften finden Sie unter [Arbeiten mit Projekteigenschaften (C++)](/cpp/ide/working-with-project-properties). Weitere Informationen zu JavaScript-Eigenschaften finden Sie unter [Eigenschaftenseiten, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Projektmappeneigenschaften

Um auf Eigenschaften für die Projektmappe zuzugreifen, klicken Sie mit der rechten Maustaste auf den Projektmappenknoten im **Projektmappen-Explorer** und wählen **Eigenschaften** aus. In diesem Dialogfeld können Sie Projektkonfigurationen für **Debug-** oder **Releasebuilds** festlegen. Sie können auswählen, welche Projekte beim Drücken von **F5** als Startprojekt verwendet werden sollen, und Sie können Codeanalyseoptionen festlegen.

## <a name="see-also"></a>Siehe auch

- [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
