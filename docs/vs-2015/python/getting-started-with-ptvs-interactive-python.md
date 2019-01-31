---
title: 'Erste Schritte mit PTVS: Interaktives Python | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780985"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Erste Schritte mit PTVS: Interaktives Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktive Eingabeaufforderungen oder REPLs (Read-Eval-Print-Loop) sind ein wichtiges Tool für produktive Programmiersprachen.  Sie ermöglichen die Ausführung von Codeausschnitten zum Untersuchen und Erlernen von APIs, das Experimentieren mit der API und das interaktive Entwickeln von Arbeitscode für Projekte oder Programme.  
  
 Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) ansehen.  
  
 Im Fenster „Python Environments“ sehen Sie eine Liste aller Python-Umgebungen.  Sie können eine Umgebung auswählen, um ein interaktives Fenster oder eine REPL zu öffnen.  Wenn Sie "Python.exe" bereits in einer Eingabeaufforderung ausgeführt haben, wurde Ihnen auch schon eine Python-REPL angezeigt.  Die REPL stellt eine Eingabeaufforderung bereit, in die Sie Code eingeben, die EINGABETASTE drücken und sofort die Ergebnisse Ihrer Codeausführung anzeigen können.  Dies ist ein Ausführungskontext, der sämtliche Zustände Ihrer Ausführungen, Variablenzuweisungen usw. enthält.  Sie können in späteren Anweisungen an die REPL-Eingabeaufforderung auf Variablen mit Ergebnissen verweisen.  Sie können mehrere Codezeilen schreiben und alle auf einmal ausführen (z. B. eine Methodendeklaration oder mehrere Anweisungen).  
  
 Wenn Sie eine neue Bibliothek verwenden möchten, stellt die REPL eine hervorragende Möglichkeit dar, um die Bibliothek zu testen.  Sie können die Bibliothek importieren und dann die untergeordneten Pakete, Klassen und Funktionen untersuchen.  Python informiert Sie über alle diese Informationen mithilfe der `help()`-Funktion.  Darüber hinaus stellen die Python-Tools für Visual Studio (PTVS) Vorschläge und Dokumentation auf Grundlage der im Editor verwendeten Codemodellierung bereit, ohne dass dafür die Bibliothek ausgeführt werden muss.  Wenn Sie Code ausführen, verwenden die PTVS Informationen aus der Python-Laufzeit zur Verbesserung der PTVS-Vorschläge.  
  
 Das interaktive Fenster ist auch nützlich für die Entwicklung von iterativem oder evolutionärem Code und zum Testen von Code während der Entwicklung.  Wählen Sie eine Funktion in einem Editor-Fenster aus, drücken Sie die Schaltfläche mit dem Pfeil nach rechts, und wählen Sie dann die Option für das Senden an die interaktive Eingabeaufforderung aus.  Dieser Befehl kopiert die Auswahl als nächste Eingabe in das interaktive Fenster und führt sie aus.  Die Ergebnisse werden sofort angezeigt.  Wenn Sie Änderungen an der vorherigen Eingabe vornehmen müssen, können Sie auf den Pfeil nach oben klicken. Sie wechseln damit zurück zum Code und können ihn ändern. Drücken Sie dann STRG+EINGABETASTE, um den Code auszuführen.  Durch Drücken der EINGABETASTE am Ende der Eingabe wird diese ausgeführt. Wenn Sie aber die EINGABETASTE in der Mitte der Eingabe drücken, wird eine neue Zeile eingefügt.  
  
 Sie können für jede Python-Installation beliebig viele interaktive Fenster öffnen.  Mithilfe von Schaltflächen am oberen Fensterrand können Sie die Anzeige leeren, den Ausführungskontext zurücksetzen usw.  Der Verlauf bleibt unverändert.  
  
 Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) ansehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiki-Dokumentation](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [PTVS-Videos: Einstieg und ausführliche Erläuterungen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
