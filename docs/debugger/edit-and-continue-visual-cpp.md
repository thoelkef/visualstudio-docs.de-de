---
title: Bearbeiten und Fortfahren (Visual C++) | Microsoft-Dokumentation
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1122e59d804387172d14f5ac9b24b6fad42213f9
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526528"
---
# <a name="edit-and-continue-visual-c"></a>Bearbeiten und Fortfahren (Visual C++)
Sie können „Bearbeiten und Fortfahren“ in Visual C++-Projekten verwenden. Finden Sie unter [unterstützt-Code-Änderungen (C++)](../debugger/supported-code-changes-cpp.md) für Informationen zu den Einschränkungen von bearbeiten und fortfahren.

Weitere Informationen zu Visual Studio 2015 Update 3 Verbesserungen, finden Sie unter [C++-bearbeiten und Fortfahren in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 Die Compileroption [/Zo (erweitertes optimiertes Debugging)](/cpp/build/reference/zo-enhance-optimized-debugging), die in Visual Studio 2013 Update 3 eingeführt wurde, fügt zusätzliche Informationen in PDB-Dateien (Symboldateien) für Binärdateien hinzu, die ohne die Option [/Od ((Debug) deaktivieren)](https://msdn.microsoft.com/library/aafb762y.aspx) kompiliert wurden.

 **/ Zo** bearbeiten und Fortfahren deaktiviert. Weitere Informationen finden Sie unter [How to: Debug Optimized Code (Vorgehensweise: Debuggen von optimiertem Code)](../debugger/how-to-debug-optimized-code.md).

##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Aktivieren oder Deaktivieren von „Bearbeiten und Fortfahren“
 Möglicherweise möchten Sie das automatische Aufrufen von „Bearbeiten und Fortfahren“ deaktivieren, wenn Sie Änderungen am Code vornehmen, die nicht während der aktuellen Debugsitzung angewendet werden sollen. Sie können das automatische Aufrufen von „Bearbeiten und Fortfahren“ später wieder aktivieren.

> [!IMPORTANT]
> Erforderliche Buildeinstellungen und andere Informationen zur featurekompatibilität von finden Sie [C++-bearbeiten und Fortfahren in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Wenn Sie in einer Debugsitzung sind, beenden Sie das Debuggen (**UMSCHALT + F5**).

2. Wählen Sie im Menü **Extras** den Befehl **Optionen**.

3. Wählen Sie im Dialogfeld **Optionen** den Eintrag **Debugging > Allgemein**aus.

4. Wählen Sie zum Aktivieren **bearbeiten und Fortfahren aktivieren**. Deaktivieren Sie das Kontrollkästchen, um zu deaktivieren.

5. Aktivieren bzw. deaktivieren Sie in der Gruppe **Bearbeiten und Fortfahren** das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** .

   Eine Änderung dieser Einstellung betrifft alle Projekte, an denen Sie arbeiten. Sie müssen die Anwendung nicht neu erstellen, nachdem Sie die Einstellung geändert haben. Wenn Sie die Anwendung über die Befehlszeile oder mit einem Makefile erstellen, jedoch in der Visual Studio-Umgebung debuggen, können Sie die Option „Bearbeiten und Fortfahren“ trotzdem verwenden, sofern Sie die **/ZI**-Option festlegen.

##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Gewusst wie: Explizites Übernehmen von Codeänderungen
 In Visual C++ kann „Bearbeiten und Fortfahren“ Codeänderungen auf zweierlei Weise übernehmen. Codeänderungen können implizit übernommen werden, wenn Sie einen Ausführungsbefehl wählen, oder explizit, wenn Sie den Befehl **Codeänderungen übernehmen** verwenden.

 Wenn Sie Codeänderungen explizit übernehmen, bleibt das Programm im Unterbrechungsmodus und wird nicht ausgeführt.

-   Um Codeänderungen explizit zu übernehmen, wählen Sie im Menü **Debuggen** die Option **Codeänderungen übernehmen**.

##  <a name="BKMK_How_to_stop_code_changes"></a> Gewusst wie: Anhalten von Codeänderungen
 Während Bearbeiten und Fortfahren Codeänderungen übernimmt, können Sie den Vorgang anhalten.

 So halten Sie das Übernehmen von Codeänderungen an:

- Wählen Sie im Menü **Debuggen** die Option **Übernehmen von Codeänderungen beenden**.

  Dieses Menüelement ist nur sichtbar, wenn Codeänderungen übernommen werden.

  Bei Verwendung dieser Option wird keine der Codeänderungen übernommen.

##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Gewusst wie: Zurücksetzen des Ausführungspunkts
 Einige Codeänderungen können dazu führen, dass der Ausführungspunkt an eine neue Position verschoben wird, wenn die Änderung von "Bearbeiten und Fortfahren" übernommen wird. Mit "Bearbeiten und Fortfahren" wird der Ausführungspunkt so genau wie möglich platziert. Das Ergebnis ist jedoch möglicherweise nicht korrekt.

 In Visual C++ werden Sie durch ein Dialogfeld über eine Änderung des Ausführungspunkts informiert. Überprüfen Sie, ob die Position richtig ist, bevor Sie das Debuggen fortsetzen. Ist die Position nicht korrekt, verwenden Sie den Befehl **Nächste Anweisung festlegen** . Weitere Informationen finden Sie unter [Nächste auszuführende Anweisung festlegen](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

##  <a name="BKMK_How_to_work_with_stale_code"></a> Gewusst wie: Arbeiten mit veraltetem Code
 In einigen Fällen kann Bearbeiten und Fortfahren die Codeänderungen nicht sofort in die ausführbare Datei übernehmen, dies aber möglicherweise zu einem späteren Zeitpunkt nachholen, wenn Sie mit dem Debuggen fortfahren. Dies geschieht, wenn Sie eine Funktion bearbeiten, die die aktuelle Funktion aufruft, bzw. wenn Sie einer Funktion in der Aufrufliste neue Variablen von mehr als 64 Bytes hinzufügen.

 In diesen Fällen fährt der Debugger so lange mit der Ausführung des ursprünglichen Codes fort, bis die Änderungen übernommen werden können. Der veraltete Code wird als temporäre Quelldatei in einem separaten Quellcodefenster angezeigt, mit einem Titel wie `enc25.tmp`. Der bearbeitete Quellcode wird weiterhin im ursprünglichen Quellcodefenster angezeigt. Wenn Sie versuchen, den veralteten Code zu bearbeiten, wird eine Warnmeldung angezeigt.

## <a name="see-also"></a>Siehe auch
- [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)