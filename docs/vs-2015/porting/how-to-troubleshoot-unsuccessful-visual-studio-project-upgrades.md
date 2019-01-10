---
title: 'Vorgehensweise: Problembehandlung bei nicht erfolgreichen Projektupgrades | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 2e21feda11ef4d3405fa1488740fefe7c7238dc5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942017"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Vorgehensweise: Problembehandlung bei nicht erfolgreichen Visual Studio-Projektupgrades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manchmal kann ein Projekt von Visual Studio nicht vollständig von einer früheren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Version konvertiert werden. Wenn die Tipps in den folgenden Abschnitten Ihr spezifische Problem nicht beheben, ist Sie möglicherweise finden Sie weitere Informationen zu den TechNet [Wiki: Entwicklungs-Portal](http://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Das Projekt wird nicht ausgeführt, da Dateien nicht gefunden werden können
 Eine Projektdatei enthält fest codierte Dateipfade, die von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zur Ausführung des Projekts verwendet werden, wenn Sie F5 drücken. Diese Pfade enthalten möglicherweise den Speicherort von devenv.exe und anderer erforderlicher Dateien. In einer aktualisierten Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wurden die Pfade dieser Dateien möglicherweise geändert.

#### <a name="to-resolve-incorrect-file-paths"></a>So lösen Sie falsche Dateipfade auf

1.  Öffnen Sie die Projektdatei in einem Texteditor.

2.  Suchen Sie nach Dateipfaden, die falsch sein könnten, insbesondere solchen, die eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Versionsnummer enthalten.

3.  Ändern Sie falsche Dateipfade so, dass diese auf die neuen Ziele zeigen.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Das Projekt wird nicht erstellt, da Verweise nicht gültig sind
 Wenn Sie ein Upgrade von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durchführen, wird möglicherweise auch die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version aktualisiert. Wenn das Projekt Verweise enthält, die in der neueren [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version nicht mehr unterstützt werden, können diese nicht ordnungsgemäß aufgelöst werden. Dies ist bei Verweisen mit Versionsnummern besonders wahrscheinlich, z. B. `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Wenn der Code zahlreiche ungültige Verweise aufweist, besteht die einfachste Lösung möglicherweise darin, die Funktion zur Festlegung von Zielversionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu verwenden, um das Ziel auf eine frühere Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] festzulegen.

#### <a name="to-resolve-incorrect-references"></a>So lösen Sie falsche Verweise auf

1. Öffnen Sie die Projektdatei in einem Texteditor.

2. Öffnen Sie die Projekteigenschaften.

3. Wählen Sie den richtigen **Zielframework**-Wert aus. Sie können auch den Wert des `<TargetFrameworkVersion>`-Elements direkt in der Projektdatei ändern.

   Wenn das Projekt in der aktualisierten [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version ausgeführt werden soll, müssen Sie die Verweise auf das Projekt und auch sämtliche `Imports`-Anweisungen oder `Using`-Anweisungen aktualisieren, die die Verweise aufrufen. Wenn das Projekt in der IDE geladen wird, können Sie die Verweise mithilfe des **Projektmappen-Explorers** oder des Dialogfelds **Verweis-Manager** aktualisieren.

## <a name="see-also"></a>Siehe auch
 [/ Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [konvertieren in ASP.NET 4](http://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
