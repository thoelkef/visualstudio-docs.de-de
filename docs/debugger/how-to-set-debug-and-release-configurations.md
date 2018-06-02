---
title: 'Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen | Microsoft Docs'
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ae43c5cab67d79450cea1dc024da98fe25c5375
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34690665"
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen in Visual Studio
Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Wie die Namen bereits vermuten lassen, erstellen Sie die Debugversion zum Debuggen und die Releaseversion für das endgültige Release, d. h. die Freigabe.  
  
Die Debugkonfiguration des Programms wird mit vollständigen symbolischen Debuginformationen und ohne Optimierung kompiliert. Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.  
  
Die Releasekonfiguration des Programms enthält keine symbolischen Debuginformationen und wird vollständig optimiert. Debuggen können in PDB-Dateien generiert werden [abhängig von den Compileroptionen](#BKMK_symbols_release) verwendet werden. PDB-Dateien erstellen kann sehr nützlich sein, wenn Sie später die Releaseversion debuggen müssen.  
  
Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
Sie können die Buildkonfiguration aus ändern die **erstellen** im Menü auf der Symbolleiste oder in den Eigenschaftenseiten des Projekts. Die Eigenschaftenseiten des Projekts sind sprachspezifisch. Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird. Weitere Informationen zum Ändern die Buildkonfiguration in Projekten, die in verschiedenen Sprachen finden Sie unter auch finden Sie im Abschnitt unten.  
  
## <a name="change-the-build-configuration"></a>Ändern Sie die Buildkonfiguration  
  
1.  Aus der **erstellen** klicken Sie im Menü **Configuration Manager**, und wählen Sie dann **Debuggen** oder **Version**.  
  
2.  Wählen Sie auf der Symbolleiste **Debuggen** oder **Release** aus der **Projektmappenkonfigurationen** Listenfeld.  
  
     ![Symbolleiste Buildkonfiguration](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Diese Symbolleiste ist in Express-Editionen nicht verfügbar. Können Sie die **erstellen Lösung F6** und **Debuggen F5 starten** Menüelemente, um die Konfiguration auszuwählen.

## <a name="BKMK_symbols_release"></a>Generieren von Symboldateien (.pdb) für einen build

Für die meisten Projekttypen die PDB-Dateien werden generiert, wird standardmäßig sowohl Debug- und Releasebuilds, aber die Standardeinstellungen unterscheiden sich je nach Ihrer bestimmten Projekttyp und die Version von Visual Studio. Sie können konfigurieren, ob der Compiler die PDB-Dateien generiert und welche Art von Debuginformationen einschließen.

> [!IMPORTANT] 
> Der Debugger lädt nur eine PDB-Datei für eine ausführbare Datei, die genau mit der PDB-Datei übereinstimmt, die zum Zeitpunkt der Erstellung der ausführbaren Datei ebenfalls erstellt wurde (das heißt, die PDB-Datei muss die originale PDB-Datei oder eine Kopie der originalen PDB-Datei sein). Weitere Informationen finden unter [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Jeder Projekttyp möglicherweise eine andere Art der Festlegen dieser Optionen.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generieren von Symboldateien für ein C#-, ASP.NET oder Visual Basic-Projekt

Ausführliche Informationen zu projekteinstellungen für die Debugkonfigurationen in c#, finden Sie unter [Projekteinstellungen für eine C#-Debugkonfiguration](../debugger/project-settings-for-csharp-debug-configurations.md). Visual Basic finden Sie unter [in diesem Thema](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie **Eigenschaften**.

2. Wählen Sie eine **Version** oder **Debuggen** erstellen, die von der **Konfiguration** Liste.

2. Wählen Sie **erstellen** Einstellungen, und klicken Sie dann auf die **erweitert** Schaltfläche.

    Wählen Sie in Visual Basic die **Kompilieren** Einstellungen und die **Erweiterte Kompilierungsoptionen** stattdessen die Schaltfläche.

3. Wählen Sie **vollständige**, **portable**, oder **Pdb_only** in der **Debuginformationen** Listenfeld (**Debuginfo generieren** in Visual Basic).

    Die portable ist das letzte plattformübergreifende Format für .NET Core. Weitere Informationen zu Optionen finden Sie unter [Dialogfeld "Erweiterte Buildeinstellungen" (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![PDBs für Builds in c# generieren](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Erstellen Sie das Projekt.

    Die Symbol-Dateien im gleichen Ordner wie die ausführbare Datei oder die Haupt-Ausgabedatei erstellt.

### <a name="generate-symbol-files-for-a-c-project"></a>Generieren von Symboldateien für ein C++-Projekt

1. Mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie **Eigenschaften**.

2. Wählen Sie eine **Version** oder **Debuggen** erstellen, die von der **Konfiguration** Liste.

2. Klicken Sie unter **Linker > Debugging**, wählen Sie gewünschten Optionen für **Debuginfo generieren**.

    Ausführliche Informationen zu projekteinstellungen für die Debugkonfigurationen in C++, finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Konfigurieren der Optionen für Programmdatenbankdateien generieren

    In den meisten C++-Projekten, der Standardwert ist `$(OutDir)$(TargetName).pdb`, die PDB-Dateien im Ordner "Ausgabe" generiert.

    ![Generieren von PDB-Dateien für Builds in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Erstellen Sie das Projekt.

    Die Symbol-Dateien im gleichen Ordner wie die ausführbare Datei oder die Haupt-Ausgabedatei erstellt.
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symbol(PDB)- und Quelldateien im Visua Studio-debugger](../debugger/debugger-settings-and-preparation.md)  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
