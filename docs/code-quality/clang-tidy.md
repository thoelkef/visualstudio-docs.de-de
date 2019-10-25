---
title: Verwenden von clang-tidy in Visual Studio
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: e226ac6c83839474b9d8ac6be7fb57e376de4a4f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745989"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Verwenden von clang-tidy in Visual Studio

Die Code Analyse unterstützt [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) sowohl für MSBuild-als auch für cmake-Projekte, unabhängig davon, ob clang-oder MSVC-Toolsets verwendet werden. Clang-saubere Überprüfungen können als Teil der Hintergrund Code Analyse ausgeführt werden, als in-Editor-Warnungen (Wellenlinien) angezeigt und in der Fehlerliste angezeigt werden.

Um clang-tidy verwenden zu können, muss dieC++ Komponente "clang-Tools für Windows" über das Visual Studio-Installer installiert werden.

Clang-Tidy ist das Standardanalyse Tool, wenn Sie das llvm/clang-cl-Toolset verwenden, das sowohl in MSBuild als auch in cmake verfügbar ist. Wenn Sie ein MSVC-Toolset verwenden, können Sie es so konfigurieren, dass es parallel ausgeführt wird, oder die standardmäßige Code Analyse durchführen. Wenn Sie das clang-cl-Toolset verwenden, ist die Microsoft-Code Analyse nicht verfügbar.

Clang-Tidy wird nach erfolgreicher Kompilierung ausgeführt. Möglicherweise müssen Sie Quell Code Fehler auflösen, um clang-saubere Ergebnisse zu erhalten.


## <a name="msbuild"></a>MSBuild

Sie können clang-tidy so konfigurieren, dass Sie als Teil der Code Analyse ausgeführt wird, und auf der Seite **Code Analyse**  > **Allgemein** im Projekt Eigenschaftenfenster. Optionen zum Konfigurieren des Tools finden Sie im Untermenü clang-tidy.

Weitere Informationen finden Sie unter Gewusst [wie: Festlegen von Code Analyse Eigenschaften für CC++ /-Projekte](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

In cmake-Projekten können Sie clang-saubere Überprüfungen innerhalb `CMakeSettings.json` konfigurieren. Klicken Sie nach dem Öffnen in der oberen rechten Ecke des cmake-Projekt Einstellungs-Editors auf "JSON bearbeiten". Die folgenden Schlüssel werden erkannt:

- `enableMicrosoftCodeAnalysis`: aktiviert die Microsoft-Code Analyse.
- `enableClangTidyCodeAnalysis`: aktiviert die clang-saubere Analyse
- `clangTidyChecks`: clang-saubere Konfiguration, angegeben als eine durch Trennzeichen getrennte Liste, d. h., Sie prüft, ob Sie aktiviert oder deaktiviert werden soll.

Wenn keine der Optionen "enable" angegeben wird, wählt Visual Studio das Analysetool aus, das dem verwendeten Platt Form Toolset entspricht.

## <a name="warning-display"></a>Anzeige von Warnungen

Clang-saubere Ausführungen führen zu Warnungen, die in der Fehlerliste angezeigt werden, und als im Editor befindliche Wellenlinien unterhalb relevanter Code Abschnitte. Verwenden Sie die Spalte "Category" im Fehlerliste, um clang-saubere Warnungen zu sortieren und zu organisieren. Sie können in-Editor-Warnungen konfigurieren, indem Sie die Einstellung "Code Analyse Wellenlinien deaktivieren **" unter Extras**  > **Optionen**.

## <a name="clang-tidy-configuration"></a>Clang-saubere Konfiguration

Über die Option " **clang-saubere Prüfungen** " können Sie überprüfen, ob "clang-tidy" in Visual Studio ausgeführt wird. Diese Eingabe wird für das **--Checks-** Argument des Tools bereitgestellt. Jede weitere Konfiguration kann in benutzerdefinierte **. clang-** Dateien eingefügt werden. Weitere Informationen finden Sie [in der Dokumentation zu clang-tidy auf llvm.org](https://clang.llvm.org/extra/clang-tidy/) .

## <a name="see-also"></a>Siehe auch

- [Clang/llvm-Unterstützung für MSBuild-Projekte](https://aka.ms/cpp/clangmsbuild)
- [Clang/llvm-Unterstützung für cmake-Projekte](https://aka.ms/cpp/clangcmake)
