---
title: "Verwalten von Projekt- und Projektmappeneigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Verwalten von Projekt- und Projektmappeneigenschaften
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Projekte haben Eigenschaften, die viele Aspekte der Kompilierung, des Debuggens, des Testens und des Bereitstellens steuern.  Einige Eigenschaften gibt es für alle Projekttypen, und einige gelten nur für bestimmte Sprachen oder Plattformen.  Sie erhalten Zugriff auf die Projekteigenschaften, indem Sie im Projektmappen\-Explorer mit der rechten Maustaste auf den Projektknoten klicken und „Eigenschaften“ auswählen, oder indem Sie Eigenschaften in das **Schnellstart**\-Suchfeld in der Menüleiste eingeben.  
  
 ![Projekt&#45;Kontextmenü](../ide/media/vs2015_proj_prop_menu.png "vs2015\_proj\_prop\_menu")  
  
 .NET\-Projekte haben außerdem einen Eigenschaftenknoten im Projektbaum selbst.  
  
 ![Knoten "Eigenschaften" in der Struktur des Projektmappen&#45;Explorers](../ide/media/vs2015_props_se.png "VS2015\_Props\_SE")  
  
> [!TIP]
>  Projektmappen haben einige Eigenschaften, ebenso wie Projektelemente. Auf diese Eigenschaften wird im [Eigenschaftenfenster](../ide/reference/properties-window.md), nicht im **Projekt\-Designer**, zugegriffen.  
  
## Projekteigenschaften  
 Projekteigenschaften sind in Gruppen organisiert, und jede Gruppe hat ihre eigene Eigenschaftenseite. Dabei können die Seiten für unterschiedliche Sprachen und Projekttypen unterschiedlich sein.  
  
### C\#\- und Visual Basic\-Projekte  
 In C\#\- und Visual Basic\-Projekten sind Eigenschaften im **Projekt\-Designer** verfügbar.  Die folgende Abbildung zeigt die Eigenschaftsseite „Build“ für ein WPF\-Projekt in C\#:  
  
 ![Visual Studio&#45;Projekt&#45;Designer](../ide/media/vs2015_proppage_build.png "VS2015\_PropPage\_Build")  
  
 Informationen zu den einzelnen Eigenschaftsseiten im Projekt\-Designer finden Sie unter [Projekteigenschaftenverweise](../ide/reference/project-properties-reference.md).  
  
### C\+\+\- und JavaScript\-Projekte  
 C\+\+\- und JavaScript\-Projekte haben eine andere Benutzeroberfläche zum Verwalten von Projekteigenschaften.  Die folgende Abbildung zeigt eine Eigenschaftenseite für ein C\+\+\-Projekt \(JavaScript\-Seiten sind ähnlich\):  
  
 ![Visual C&#43;&#43;&#45;Projekteigenschaften](../ide/media/vs2015_projprops_cpp.png "VS2015\_ProjProps\_cpp")  
  
 Informationen zu C\+\+\-Projekteigenschaften finden Sie unter [Arbeiten mit Projekteigenschaften](/visual-cpp/ide/working-with-project-properties).  Weitere Informationen zu JavaScript\-Eigenschaften finden Sie unter [Eigenschaftenseiten, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## Projektmappeneigenschaften  
 Um auf Eigenschaften für die Projektmappe zuzugreifen, klicken Sie mit der rechten Maustaste auf den Projektmappenknoten im **Projektmappen\-Explorer** und wählen **Eigenschaften** aus.  In dem Dialogfeld können Sie Projektkonfigurationen für Debug\- oder Releasebuilds festlegen. Sie können auswählen, welche Projekte beim Drücken von F5 als Startprojekt verwendet werden sollen, und Sie können Codeanalyseoptionen festlegen.  
  
## Siehe auch  
 [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)