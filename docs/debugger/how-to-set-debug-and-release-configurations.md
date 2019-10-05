---
title: Festlegen von Debug-und Releasekonfigurationen | Microsoft-Dokumentation
ms.date: 10/05/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75acf0a3a821b4d2561ea14e583e71761b8b476e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925477"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Festlegen von Debug- und Releasekonfigurationen in Visual Studio

Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Sie erstellen die Debugversion für das Debuggen und die Releaseversion für die endgültige releaseverteilung.

In der Debugkonfiguration wird das Programm mit vollständigen symbolischen Debuginformationen und ohne Optimierung kompiliert. Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.

Die Releasekonfiguration des Programms enthält keine symbolischen Debuginformationen und wird vollständig optimiert. Bei verwaltetem Code C++ und Code können Debuginformationen in PDB-Dateien generiert werden, [abhängig von den verwendeten Compileroptionen](#BKMK_symbols_release) . Das Erstellen von PDB-Dateien kann nützlich sein, wenn Sie später Ihre Releaseversion Debuggen müssen.

Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

Sie können die Buildkonfiguration über die Symbolleiste im Menü **Build** oder über die Eigenschaftenseiten des Projekts ändern. Die Eigenschaftenseiten des Projekts sind sprachspezifisch. Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird. Weitere Informationen zum Ändern der Buildkonfiguration in Projekten in verschiedenen Sprachen finden Sie im Abschnitt " [Siehe auch](#see-also) " weiter unten.

## <a name="change-the-build-configuration"></a>Ändern der Buildkonfiguration

So ändern Sie die Buildkonfiguration:

* Wählen Sie im Menü **Erstellen** **Configuration Manager**aus, und wählen Sie dann **Debuggen** oder **Release**aus.

oder

* Wählen Sie auf der Symbolleiste im Listenfeld **Projektmappenkonfigurationen** die Option **Debuggen** oder **Release** aus.

  Buildkonfiguration für ![Symbolleisten](../debugger/media/toolbarbuildconfiguration.png "Toolbarbuildconfiguration")

## <a name="BKMK_symbols_release"></a>Generieren von Symbol Dateien (PDB-Dateien) für einenC#Build C++(,, F#Visual Basic,)

Sie können auswählen, ob Symbol Dateien (PDB-Dateien) und welche Debuginformationen eingeschlossen werden sollen. Bei den meisten Projekttypen generiert der Compiler standardmäßig Symbol Dateien für Debug-und Releasebuilds, während andere Standardeinstellungen je nach Projekttyp und Visual Studio-Version unterschiedlich sind.

> [!IMPORTANT]
> Der Debugger lädt nur eine PDB-Datei für eine ausführbare Datei, die genau mit der PDB-Datei übereinstimmt, die zum Zeitpunkt der Erstellung der ausführbaren Datei ebenfalls erstellt wurde (das heißt, die PDB-Datei muss die originale PDB-Datei oder eine Kopie der originalen PDB-Datei sein). Weitere Informationen finden Sie unter [warum erfordert Visual Studio, dass Debugger-Symbol Dateien genau mit den Binärdateien übereinstimmen, mit denen Sie erstellt wurden?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

Jeder Projekttyp kann eine andere Möglichkeit haben, diese Optionen festzulegen.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generieren von Symbol Dateien für C#ein-, ASP.net-oder Visual Basic Projekt

Ausführliche Informationen zu den Projekteinstellungen für Debugkonfigurationen C# in oder Visual Basic finden Sie unter [Projekteinstellungen C# für eine Debugkonfiguration](../debugger/project-settings-for-csharp-debug-configurations.md) oder [Projekteinstellungen für eine Visual Basic Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Wählen Sie das Symbol **Eigenschaften** aus (oder drücken Sie **Alt + Eingabe**Taste).

3. Wählen Sie im Seitenbereich die Option **Erstellen** (oder in Visual Basic **Kompilieren** ).

4. Wählen Sie in der Liste **Konfiguration** die Option **Debuggen** oder **Release**aus.

5. Wählen Sie die Schaltfläche **erweitert** (oder die Schaltfläche **Erweiterte Kompilierungsoptionen** in Visual Basic) aus.

6. Wählen Sie in der Liste **Debuginformationen** (oder in der Liste **Debuginformationen generieren** in Visual Basic) die Option **vollständig**, **nur PDB**oder **portabel**aus.

   Das Portable Format ist das aktuellste plattformübergreifende Format für .net Core. Weitere Informationen zu Optionen finden Sie unter [Dialogfeld "Erweiterte Buildeinstellungen" (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generieren von pdsb für Builds C# in](../debugger/media/dbg_project_properties_pdb_csharp.png "Generatepdbsforcsharp")

7. Erstellen Sie das Projekt.

   Der Compiler erstellt die Symbol Dateien im selben Ordner wie die ausführbare Datei oder die Hauptausgabe Datei.

### <a name="generate-symbol-files-for-a-c-project"></a>Generieren von Symbol Dateien für C++ ein Projekt

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Wählen Sie das Symbol **Eigenschaften** aus (oder drücken Sie **Alt + Eingabe**Taste).

3. Wählen Sie in der Liste **Konfiguration** die Option **Debuggen** oder **Release**aus.

4. Wählen Sie im Seitenbereich **Linker > Debugging**aus, und wählen Sie dann Optionen zum **Generieren von Debuginformationen**aus.

   Ausführliche Informationen zu den Projekteinstellungen für Debugkonfigurationen C++in finden Sie unter [Projekteinstellungen C++ für eine Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Optionen für die **Generierung von Programm Datenbankdateien**konfigurieren.

   In den C++ meisten Projekten ist `$(OutDir)$(TargetName).pdb`der Standardwert, der PDB-Dateien im Ausgabeordner generiert.

   ![Generieren von pdsb für Builds C++ in](../debugger/media/dbg_project_properties_pdb_cplusplus.png "Generatepdbsforcplusplus")

6. Erstellen Sie das Projekt.

   Der Compiler erstellt die Symbol Dateien im selben Ordner wie die ausführbare Datei oder die Hauptausgabe Datei.

## <a name="see-also"></a>Siehe auch

- [Angeben von Symbol Dateien (. pdb) und Quelldateien im Visual Studio-Debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)<br/>
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Projekteinstellungen für eine C#-Debugkonfiguration](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
