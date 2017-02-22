---
title: "MSBuild Multitargeting Overview | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Multitargeting Overview
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit MSBuild können Sie eine Anwendung kompilieren, die auf verschiedenen Versionen von .NET Framework und auf verschiedenen Systemplattformen ausgeführt werden kann.  Beispielsweise können Sie die gleiche Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32\-Bit\-Plattform und für die Ausführung in .NET Framework 4.5 auf einer 64\-Bit\-Plattform kompilieren.  
  
> [!IMPORTANT]
>  Trotz des Namens "Festlegung von Zielversionen" hat ein Projekt immer nur jeweils ein Framework und eine Plattform als Ziel.  
  
 Dies sind einige Funktionen von MSBuild für die Festlegung von Zielversionen:  
  
-   Sie können Anwendungen entwickeln, die auf frühere Versionen von .NET Framework abzielen, z. B. Version 2.0, 3.5 oder 4.  
  
-   Sie können neben .NET Framework auch auf andere Frameworks abzielen, z. B. auf das Silverlight\-Framework.  
  
-   Sie können auf ein *Frameworkprofil* abzielen, das eine vordefinierte Teilmenge eines Zielframeworks ist.  
  
-   Sie können ebenfalls auf neu veröffentlichte Service Packs für die aktuelle .NET Framework\-Version abzielen.  
  
-   Durch die Festlegung von Zielversionen mit MSBuild wird garantiert, dass von einer Anwendung nur die im Zielframework und die auf der Zielplattform verfügbaren Funktionen verwendet werden.  
  
## Zielframework und \-plattform  
 Ein *Zielframework* ist die Version von .NET Framework, in der ein erstelltes Projekt ausgeführt werden soll, und eine *Zielplattform* ist die Systemplattform, auf der das erstellte Projekt ausgeführt werden soll.  Beispielsweise können Sie eine Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32\-Bit\-Plattform entwickeln, die mit der 802x86\-Prozessorfamilie kompatibel ist \(x86\).  Die Kombination von Zielframework und Zielplattform wird als *Zielkontext* bezeichnet.  Weitere Informationen finden Sie unter [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## Toolset \(ToolsVersion\)  
 Ein Toolset umfasst die Tools, Aufgaben und Ziele, die verwendet werden, um die Anwendung zu erstellen.  Ein Toolset umfasst Compiler wie csc.exe und vbc.exe, die Datei mit allgemeinen Zielen \(microsoft.common.targets\) und die Datei mit allgemeinen Aufgaben \(microsoft.common.tasks\).  Das 4.5\-Toolset kann verwendet werden, um auf die .NET Framework\-Versionen 2.0, 3.0, 3.5, 4 und 4.5 abzuzielen. Das 2.0\-Toolset kann dagegen nur für .NET Framework Version 2.0 verwendet werden.  Weitere Informationen finden Sie unter [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Verweisassemblys  
 Die Verweisassemblys, die im Toolset angegeben sind, helfen Ihnen beim Entwerfen und Erstellen einer Anwendung.  Diese Verweisassemblys ermöglichen nicht nur einen bestimmten Zielbuild, sondern beschränken die Komponenten und Funktionen in der Visual Studio\-IDE auch auf die mit dem Ziel kompatiblen Komponenten und Funktionen.  Weitere Informationen finden Sie unter [Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md)  
  
## Konfigurieren von Zielen und Aufgaben  
 Sie können MSBuild\-Ziele und \-Aufgaben so konfigurieren, dass sie prozessextern mit MSBuild ausgeführt werden, damit Sie auf Kontexte abzielen können, die sich stark von dem unterscheiden, in dem Sie die Ausführung eigentlich vorgesehen haben.  Beispielsweise können Sie auf eine 32\-Bit\-.NET Framework 2.0\-Anwendung abzielen, während der Entwicklungscomputer auf einer 64\-Bit\-Plattform mit .NET Framework 4.5 ausgeführt wird. Weitere Informationen finden Sie unter [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md).  
  
## Problembehandlung  
 Es können Fehler angezeigt werden, wenn Sie versuchen, auf eine Assembly zu verweisen, die nicht Teil des Zielkontexts ist.  Weitere Informationen zu diesen Fehlern und deren Behebung finden Sie unter [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).