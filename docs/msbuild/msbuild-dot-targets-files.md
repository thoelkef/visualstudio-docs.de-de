---
title: TARGETS-Dateien von MSBuild | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/24/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3282495219e92da38fc90c9a98fa115791190d80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834564"
---
# <a name="msbuild-targets-files"></a>TARGETS-Dateien von MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] umfasst mehrere *TARGETS*-Dateien, die Elemente, Eigenschaften, Ziele und Aufgaben für allgemeine Szenarios enthalten. Diese Dateien werden in die meisten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektdateien automatisch importiert, um Lesbarkeit und Verwaltung zu vereinfachen.  

 Projekte importieren in der Regel mindestens eine *TARGETS*-Datei, um den entsprechenden Buildprozess zu definieren. Ein von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstelltes [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt importiert *Microsoft.CSharp.targets*, die wiederum *Microsoft.Common.targets* importiert. Das [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt definiert die jeweiligen Elemente und Eigenschaften dieses Projekts selbst. Die standardmäßigen Buildregeln für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt werden jedoch in den importierten *TARGETS*-Dateien definiert.  

 Der `$(MSBuildToolsPath)`-Wert gibt den Pfad dieser allgemeinen *TARGETS*-Dateien an. Für `ToolsVersion` 4.0 befinden die Dateien sich an folgendem Speicherort: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*  

> [!NOTE]
>  Informationen zum Erstellen eigener Ziele finden Sie unter [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele). Informationen dazu, wie Sie mithilfe des `Import`-Elements eine Projektdatei in eine andere Projektdatei einfügen können, finden Sie unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md) und [Vorgehensweise: Verwenden eines Ziels in mehreren Projektdateien](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Allgemeine TARGETS-Dateien  

| *TARGETS*-Datei | Beschreibung  |
|---------------------------------| - |
| *Microsoft.Common.targets* | Definiert die Schritte im Standardbuildprozess für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]- und [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekte.<br /><br /> Wird von *Microsoft.CSharp.targets*-Dateien und *Microsoft.VisualBasic.targets*-Dateien importiert, die die folgende Anweisung enthalten: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definiert die Schritte im Standardbuildprozess für Visual C#-Projekte.<br /><br /> Wird von Visual C#-Projektdateien (*CSPROJ*) importiert, die die folgende Anweisung enthalten: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definiert die Schritte im Standardbuildprozess für Visual Basic-Projekte.<br /><br /> Wird von Visual Basic-Projektdateien (*VBPROJ*) importiert, die die folgende Anweisung enthalten: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets
Bei *Directory.Build.targets* handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt. Diese Datei wird automatisch aus *Microsoft.Common.targets* importiert, wenn die Eigenschaft **ImportDirectoryBuildTargets** nicht auf **FALSE** festgelegt wird.

## <a name="see-also"></a>Siehe auch  
 [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
