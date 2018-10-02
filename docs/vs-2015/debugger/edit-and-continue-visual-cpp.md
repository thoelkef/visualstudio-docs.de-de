---
title: Bearbeiten und Fortfahren (Visual C++) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b95de832050cd6283b85ec4fe6bd99b67c8c1d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522259"
---
# <a name="edit-and-continue-visual-c"></a>Bearbeiten und Fortfahren (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [bearbeiten und Fortfahren (Visual C++)](https://docs.microsoft.com/visualstudio/debugger/edit-and-continue-visual-cpp).  
  
Sie können „Bearbeiten und Fortfahren“ in Visual C++-Projekten verwenden. Finden Sie unter [unterstützt-Code-Änderungen (C++)](../debugger/supported-code-changes-cpp.md) für Informationen zu den Einschränkungen von bearbeiten und fortfahren.  
  
 Ab Visual Studio 2015 Update 1 ist jetzt können bearbeiten und Fortfahren in Windows Store C++ und DirectX-apps, da er jetzt unterstützt die **"/ Zi"** -Compilerschalter mit **/bigobj** wechseln. Sie können auch bearbeiten und Fortfahren mit Binärdateien kompiliert wird, mit der **Fastlink** wechseln.  
  
 Weitere Update 1-Verbesserungen sind ein neues Wartedialogfeld, das abgebrochen werden kann, sowie eine Benachrichtigung für den Fall, dass „Bearbeiten und Fortfahren“ für eine Datei nicht unterstützt wird. Weitere Informationen zu Update 1-Verbesserungen, finden Sie unter [Verbesserungen für C++-bearbeiten und Fortfahren in Visual Studio 2015 Update 1](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx).  
  
 Die [/zo (optimiertes Debuggen verbessern)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) Compileroption, die in Visual Studio 2013 Update 3 eingeführte PDB-Dateien (Symboldateien) zusätzliche Informationen hinzugefügt, für die Kompilierung von Binärdateien ohne die  [ /Od (deaktivieren (Debuggen)) ](http://msdn.microsoft.com/library/aafb762y.aspx) Option.  
  
 **/ Zo** bearbeiten und Fortfahren deaktiviert. Finden Sie unter [Vorgehensweise: Debuggen von optimiertem Code](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Aktivieren oder Deaktivieren von „Bearbeiten und Fortfahren“  
 Möglicherweise möchten Sie das automatische Aufrufen von „Bearbeiten und Fortfahren“ deaktivieren, wenn Sie Änderungen am Code vornehmen, die nicht während der aktuellen Debugsitzung angewendet werden sollen. Sie können das automatische Aufrufen von „Bearbeiten und Fortfahren“ später wieder aktivieren.  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2.  Wählen Sie im Dialogfeld **Optionen** den Eintrag **Debugging / Allgemein**aus.  
  
3.  Aktivieren bzw. deaktivieren Sie in der Gruppe **Bearbeiten und Fortfahren** das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** .  
  
 Eine Änderung dieser Einstellung betrifft alle Projekte, an denen Sie arbeiten. Sie müssen die Anwendung nicht neu erstellen, nachdem Sie die Einstellung geändert haben. Sie können die Einstellung sogar ändern, während Sie debuggen. Wenn Sie die Anwendung über die Befehlszeile oder mit einem Makefile erstellen, jedoch in der Visual Studio-Umgebung debuggen, können Sie die Option „Bearbeiten und Fortfahren“ trotzdem verwenden, sofern Sie die **/ZI** -Option festlegen.  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Gewusst wie: Explizites Übernehmen von Codeänderungen  
 In Visual C++ kann „Bearbeiten und Fortfahren“ Codeänderungen auf zweierlei Weise übernehmen. Codeänderungen können implizit übernommen werden, wenn Sie einen Ausführungsbefehl wählen, oder explizit, wenn Sie den Befehl **Codeänderungen übernehmen** verwenden.  
  
 Wenn Sie Codeänderungen explizit übernehmen, bleibt das Programm im Unterbrechungsmodus und wird nicht ausgeführt.  
  
-   Um Codeänderungen explizit zu übernehmen, wählen Sie im Menü **Debuggen** die Option **Codeänderungen übernehmen**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> Gewusst wie: Anhalten von Codeänderungen  
 Während Bearbeiten und Fortfahren Codeänderungen übernimmt, können Sie den Vorgang anhalten.  
  
 So halten Sie das Übernehmen von Codeänderungen an:  
  
-   Wählen Sie im Menü **Debuggen** die Option **Übernehmen von Codeänderungen beenden**.  
  
 Dieses Menüelement ist nur sichtbar, wenn Codeänderungen übernommen werden.  
  
 Bei Verwendung dieser Option wird keine der Codeänderungen übernommen.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Gewusst wie: Zurücksetzen des Ausführungspunkts  
 Einige Codeänderungen können dazu führen, dass der Ausführungspunkt an eine neue Position verschoben wird, wenn die Änderung von "Bearbeiten und Fortfahren" übernommen wird. Mit "Bearbeiten und Fortfahren" wird der Ausführungspunkt so genau wie möglich platziert. Das Ergebnis ist jedoch möglicherweise nicht korrekt.  
  
 In Visual C++ werden Sie durch ein Dialogfeld über eine Änderung des Ausführungspunkts informiert. Überprüfen Sie, ob die Position richtig ist, bevor Sie das Debuggen fortsetzen. Ist die Position nicht korrekt, verwenden Sie den Befehl **Nächste Anweisung festlegen** . Weitere Informationen finden Sie unter [Nächste auszuführende Anweisung festlegen](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> Gewusst wie: Arbeiten mit veraltetem Code  
 In einigen Fällen kann Bearbeiten und Fortfahren die Codeänderungen nicht sofort in die ausführbare Datei übernehmen, dies aber möglicherweise zu einem späteren Zeitpunkt nachholen, wenn Sie mit dem Debuggen fortfahren. Dies geschieht, wenn Sie eine Funktion bearbeiten, die die aktuelle Funktion aufruft, bzw. wenn Sie einer Funktion in der Aufrufliste neue Variablen von mehr als 64 Bytes hinzufügen.  
  
 In diesen Fällen fährt der Debugger so lange mit der Ausführung des ursprünglichen Codes fort, bis die Änderungen übernommen werden können. Der veraltete Code wird als temporäre Quelldatei in einem separaten Quellcodefenster angezeigt, mit einem Titel wie `enc25.tmp`. Der bearbeitete Quellcode wird weiterhin im ursprünglichen Quellcodefenster angezeigt. Wenn Sie versuchen, den veralteten Code zu bearbeiten, wird eine Warnmeldung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)



