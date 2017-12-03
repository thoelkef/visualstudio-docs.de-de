---
title: Verwalten von Projekt- und Projektmappeneigenschaften | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9242bf08b879e415af658696b2be75a55dc5075
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2017
---
# <a name="managing-project-and-solution-properties"></a>Verwalten von Projekt- und Projektmappeneigenschaften

Projekte haben Eigenschaften, die viele Aspekte der Kompilierung, des Debuggens, des Testens und des Bereitstellens steuern. Einige Eigenschaften gibt es für alle Projekttypen, und einige gelten nur für bestimmte Sprachen oder Plattformen. Sie erhalten Zugriff auf die Projekteigenschaften, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten klicken und **Eigenschaften** auswählen, oder indem Sie Eigenschaften in das **Schnellstart**-Suchfeld auf der Menüleiste eingeben.

![Projekt-Kontextmenü](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")

.NET-Projekte haben womöglich außerdem einen Eigenschaftenknoten in der Projektstruktur selbst.

![Knoten „Eigenschaften“ in der Struktur des Projektmappen-Explorers](../ide/media/vs2015_props_se.png "VS2015_Props_SE")

> [!TIP]
> Projektmappen haben einige Eigenschaften, ebenso wie Projektelemente. Auf diese Eigenschaften wird im [Eigenschaftenfenster](../ide/reference/properties-window.md), nicht im **Projekt-Designer**, zugegriffen.

## <a name="project-properties"></a>Projekteigenschaften

Projekteigenschaften sind in Gruppen organisiert, und jede Gruppe hat ihre eigene Eigenschaftenseite. Dabei können die Seiten für unterschiedliche Sprachen und Projekttypen unterschiedlich sein.

### <a name="c-visual-basic-and-f-projects"></a>C#-, Visual Basic- und F#-Projekte

In C#-, Visual Basic- und F#-Projekten sind Eigenschaften im **Projekt-Designer** verfügbar. Die folgende Abbildung zeigt die Eigenschaftsseite „Build“ für ein WPF-Projekt in C#:

![Visual Studio-Projekt-Designer](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")

Informationen zu den einzelnen Eigenschaftsseiten im Projekt-Designer finden Sie unter [Projekteigenschaftenreferenz](../ide/reference/project-properties-reference.md).

### <a name="c-and-javascript-projects"></a>C++- und JavaScript-Projekte

C++- und JavaScript-Projekte haben eine andere Benutzeroberfläche zum Verwalten von Projekteigenschaften. Die folgende Abbildung zeigt eine Eigenschaftenseite für ein C++-Projekt (JavaScript-Seiten sind ähnlich):

![Visual C&#43;&#43;-Projekteigenschaften](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")

Informationen zu C++-Projekteigenschaften finden Sie unter [Arbeiten mit Projekteigenschaften (C++)](/cpp/ide/working-with-project-properties). Weitere Informationen zu JavaScript-Eigenschaften finden Sie unter [Eigenschaftenseiten, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Projektmappeneigenschaften

Um auf Eigenschaften für die Projektmappe zuzugreifen, klicken Sie mit der rechten Maustaste auf den Projektmappenknoten im **Projektmappen-Explorer** und wählen **Eigenschaften** aus. In dem Dialogfeld können Sie Projektkonfigurationen für Debug- oder Releasebuilds festlegen. Sie können auswählen, welche Projekte beim Drücken von F5 als Startprojekt verwendet werden sollen, und Sie können Codeanalyseoptionen festlegen.

## <a name="see-also"></a>Siehe auch

[Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
