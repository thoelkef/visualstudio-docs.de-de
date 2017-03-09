---
title: "Gewusst wie: Problembehandlung bei nicht erfolgreichen Visual Studio-Projektupgrades | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "Aktualisieren von Anwendungen, Visual Studio"
  - "Aktualisieren von Projekten [Visual Studio]"
  - "Projekte [Visual Studio], aktualisieren"
  - "Visual Studio-Konvertierungs-Assistent"
  - "Konvertierungs-Assistent"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Gewusst wie: Problembehandlung bei nicht erfolgreichen Visual Studio-Projektupgrades
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Manchmal kann ein Projekt von Visual Studio nicht vollständig von einer früheren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Version konvertiert werden.  Wenn durch die Tipps in den folgenden Abschnitten Ihr spezifisches Problem nicht behoben wird, finden Sie möglicherweise Informationen im TechNet [Wiki: Entwicklungsportal](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## Das Projekt wird nicht ausgeführt, da Dateien nicht gefunden werden können  
 Eine Projektdatei enthält fest codierte Dateipfade, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Ausführung des Projekts verwendet werden, wenn Sie F5 drücken.  Diese Pfade enthalten möglicherweise den Speicherort von devenv.exe und anderer erforderlicher Dateien.  In einer aktualisierten Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurden die Pfade dieser Dateien möglicherweise geändert.  
  
#### So lösen Sie falsche Dateipfade auf  
  
1.  Öffnen Sie die Projektdatei in einem Texteditor.  
  
2.  Suchen Sie nach Dateipfaden, die falsch sein könnten, insbesondere solchen, die eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Versionsnummer enthalten.  
  
3.  Ändern Sie falsche Dateipfade so, dass diese auf die neuen Ziele zeigen.  
  
## Das Projekt wird nicht erstellt, da Verweise nicht gültig sind  
 Wenn Sie ein Upgrade von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durchführen, wird möglicherweise auch die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version aktualisiert.  Wenn das Projekt Verweise enthält, die in der neueren [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version nicht mehr unterstützt werden, können diese nicht ordnungsgemäß aufgelöst werden.  Dies ist bei Verweisen mit Versionsnummern besonders wahrscheinlich, z. B. `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Wenn der Code zahlreiche ungültige Verweise aufweist, besteht die einfachste Lösung möglicherweise darin, die Funktion zur Festlegung von Zielversionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu verwenden, um das Ziel auf eine frühere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] festzulegen.  
  
#### So lösen Sie falsche Verweise auf  
  
1.  Öffnen Sie die Projektdatei in einem Texteditor.  
  
2.  Öffnen Sie die Projekteigenschaften.  
  
3.  Wählen Sie den richtigen **Zielframework**\-Wert aus.  Sie können auch den Wert des `<TargetFrameworkVersion>`\-Elements direkt in der Projektdatei ändern.  
  
 Wenn das Projekt in der aktualisierten [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version ausgeführt werden soll, müssen Sie die Verweise auf das Projekt und auch sämtliche `Imports`\-Anweisungen oder `Using`\-Anweisungen aktualisieren, die die Verweise aufrufen.  Wenn das Projekt in der IDE geladen wird, können Sie die Verweise mithilfe vom **Projektmappen\-Explorer** oder des Dialogfelds **Verweis\-Manager** aktualisieren.  
  
## Siehe auch  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)