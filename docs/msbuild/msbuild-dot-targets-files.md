---
title: TARGETS-Dateien von MSBuild | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c382d6e967705b95e46c6c797915c49841688c6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-targets-files"></a>.Targets-Dateien von MSBuild
In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sind mehrere TARGETS-Dateien verfügbar, die Elemente, Eigenschaften, Ziele und Aufgaben für allgemeine Szenarios enthalten. Diese Dateien werden in die meisten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektdateien automatisch importiert, um Lesbarkeit und Verwaltung zu vereinfachen.  

 Projekte importieren in der Regel mindestens eine TARGETS-Datei, um den entsprechenden Buildprozess zu definieren. Ein von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstelltes [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt importiert Microsoft.CSharp.targets, die wiederum Microsoft.Common.targets importiert. Das [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt definiert die jeweiligen Elemente und Eigenschaften dieses Projekts selbst. Die standardmäßigen Buildregeln für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt werden jedoch in den importierten TARGETS-Dateien definiert.  

 Der `$(MSBuildToolsPath)`-Wert gibt den Pfad dieser allgemeinen TARGETS-Dateien an. Handelt es sich um die `ToolsVersion` 4.0, befinden sich die Dateien im folgenden Speicherort: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  

> [!NOTE]
>  Informationen zum Erstellen eigener Ziele finden Sie unter [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele). Informationen dazu, wie Sie mithilfe des `Import`-Elements eine Projektdatei in eine andere Projektdatei einfügen können, finden Sie unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md) (Import-Element (MSBuild)) und [How to: Use the Same Target in Multiple Project Files](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md) (Vorgehensweise: Verwenden eines Ziels in mehreren Projektdateien).  

## <a name="common-targets-files"></a>Allgemeine TARGETS-Dateien  

|TARGETS-Datei|description|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Definiert die Schritte im Standardbuildprozess für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]- und [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekte.<br /><br /> Wird von Microsoft.CSharp.targets-Dateien und Microsoft.VisualBasic.targets-Dateien importiert, die die folgende Anweisung verwenden:`<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Definiert die Schritte im Standardbuildprozess für Visual C#-Projekte.<br /><br /> Wird von Visual C#-Projektdateien (CSPROJ) importiert, die die folgende Anweisung verwenden: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Definiert die Schritte im Standardbuildprozess für Visual Basic-Projekte.<br /><br /> Wird von Visual Basic-Projektdateien (VBPROJ) importiert, die die folgende Anweisung verwenden: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
Bei Directory.Build.targets handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt. Diese Datei wird automatisch aus Microsoft.Common.targets importiert, wenn die Eigenschaft **ImportDirectoryBuildTargets** nicht auf **FALSE** festgelegt wird.

## <a name="see-also"></a>Siehe auch  
 [Import Element (MSBuild)](../msbuild/import-element-msbuild.md)  (Import-Element (MSBuild))  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
