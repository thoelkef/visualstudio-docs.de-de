---
title: Festlegen von Debug- und Releasekonfigurationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: reference
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
ms.openlocfilehash: 9a65a3331c210bdfb4143ff890180fdc7d663229
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257224"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Festlegen von Debug- und Releasekonfigurationen in Visual Studio

Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Sie erstellen die Debugversion zum Debuggen und die Releaseversion für die endgültige Version.

In der Debugkonfiguration kompiliert Ihr Programm mit vollständigen symbolischen Debuginformationen und ohne Optimierung. Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.

Die Releasekonfiguration des Programms hat keine symbolischen Debuginformationen und wird vollständig optimiert. Debuggen kann Informationen in PDB-Dateien generiert werden [abhängig von den Compileroptionen](#BKMK_symbols_release) , die verwendet werden. Erstellen die PDB-Dateien ist nützlich, wenn Sie später die Releaseversion debuggen müssen.

Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

Sie können die Buildkonfiguration Ändern der **erstellen** im Menü auf der Symbolleiste oder in den Eigenschaftenseiten des Projekts. Die Eigenschaftenseiten des Projekts sind sprachspezifisch. Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird. Weitere Informationen dazu, wie Sie die Buildkonfiguration in Projekten, die in verschiedenen Sprachen zu ändern, finden Sie die [Siehe auch](#see-also) Abschnitt weiter unten.

## <a name="change-the-build-configuration"></a>Ändern Sie die Buildkonfiguration

So ändern Sie die Buildkonfiguration, entweder:

* Von der **erstellen** , wählen Sie im Menü **Configuration Manager**, und wählen Sie dann **Debuggen** oder **Version**.

oder

* Wählen Sie auf der Symbolleiste entweder **Debuggen** oder **Version** aus der **Projektmappenkonfigurationen** Liste.

  ![Symbolleisten-Buildkonfiguration](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Symboldateien (.pdb) für einen Build zu generieren (C#, C++, Visual Basic F#)

Sie können auch Symboldateien (.pdb) und was generiert Debuginformationen einschließen. Für die meisten Projekttypen generiert der Compiler Symboldateien standardmäßig zum Debuggen, und Version erstellt wurde, während andere Standardeinstellungen nach Projekttyp und Visual Studio-Version unterscheiden.

> [!IMPORTANT]
> Der Debugger lädt nur eine PDB-Datei für eine ausführbare Datei, die genau mit der PDB-Datei übereinstimmt, die zum Zeitpunkt der Erstellung der ausführbaren Datei ebenfalls erstellt wurde (das heißt, die PDB-Datei muss die originale PDB-Datei oder eine Kopie der originalen PDB-Datei sein). Weitere Informationen finden Sie unter [Why Visual Studio require Debugger Symbol-Dateien zu genau den Binärdateien bereitgestellt, die mit der sie erstellt wurden?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Jeder Projekttyp möglicherweise eine andere Art der Festlegen dieser Optionen.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generieren von Symboldateien für ein C#-, ASP.NET und Visual Basic-Projekt

Ausführliche Informationen zu projekteinstellungen für die Debugkonfigurationen in c# oder Visual Basic, finden Sie unter [projekteinstellungen für C#-Debugkonfiguration](../debugger/project-settings-for-csharp-debug-configurations.md) oder [projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Wählen Sie die **Eigenschaften** Symbol (oder drücken Sie **Alt + Eingabe**).

3. Wählen Sie im Seitenbereich **erstellen** (oder **Kompilieren** in Visual Basic).

4. In der **Konfiguration** wählen **Debuggen** oder **Version**.

5. Wählen Sie die **erweitert** Schaltfläche (oder die **Advanced Compile Options** -Schaltfläche in Visual Basic).

6. In der **Debuginformationen** Liste (oder die **Debuginfo generieren** Liste in Visual Basic), wählen Sie **vollständige**, **Pdb-only**, oder **Portable**.

   Die portable ist das neueste Cross-Platform-Format für .NET Core. Weitere Informationen zu Optionen finden Sie unter [Dialogfeld "Erweiterte Buildeinstellungen" (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generieren von PDB-Dateien für Builds in c#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Erstellen Sie das Projekt.

   Der Compiler erstellt die Symbol-Dateien im selben Ordner wie die ausführbare Datei oder Hauptausgabedatei.

### <a name="generate-symbol-files-for-a-c-project"></a>Generieren von Symboldateien für ein C++-Projekt

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Wählen Sie die **Eigenschaften** Symbol (oder drücken Sie **Alt + Eingabe**).

3. In der **Konfiguration** wählen **Debuggen** oder **Version**.

4. Wählen Sie im Seitenbereich **Linker > Debugging**, wählen Sie dann auf Optionen für die **Debuginfo generieren**.

   Ausführliche Informationen zu projekteinstellungen für die Debugkonfigurationen in C++, finden Sie unter [projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Konfigurieren der Optionen für **Programmdatenbankdateien generieren**.

   In den meisten C++-Projekten, der Standardwert ist `$(OutDir)$(TargetName).pdb`, die PDB-Dateien im Ordner "Output" generiert.

   ![Generieren von PDB-Dateien für Builds in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Erstellen Sie das Projekt.

   Der Compiler erstellt die Symbol-Dateien im selben Ordner wie die ausführbare Datei oder Hauptausgabedatei.

## <a name="see-also"></a>Siehe auch
 
[Angeben von Symbol(PDB)- und Quelldateien im Visual Studio-debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)<br/>
[Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[Projekteinstellungen für eine C#-Debugkonfiguration](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
