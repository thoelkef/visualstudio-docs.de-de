---
title: "Linting für R-Code mit den R Tools für Visual Studio | Microsoft-Dokumentation"
description: "Arbeiten mit der integrierten Lintingunterstützung für R von Visual Studio, einschließlich der Lintingoptionen."
ms.custom: 
ms.date: 01/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 34094aee7563c9f0715702ada5bdd7a0df99c4a7
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="linting-r-code-in-visual-studio"></a>Linting für R-Code in Visual Studio

Linting ist ein Prozess, der Code analysiert, um potenzielle Fehler, Formatierungsprobleme und andere Störfaktoren bei Codes (z.B. falschen Leerraum) aufzudecken. Linting hilft auch dabei, bestimmte Codierungskonventionen zu fördern, wie z.B. die Benennung von Bezeichnern, was in Teams und anderen Zusammenarbeitssituationen sehr hilfreich ist.

R Tools für Visual Studio (RTVS) bieten eine integrierte Linting-Funktion für R, deren Verhalten durch eine Vielzahl von Optionen gesteuert wird. Diese werden im vorliegenden Artikel beschrieben. Diese Optionen finden Sie unter **Extras > Optionen > Text-Editor > R > Lint**.

Linting ist standardmäßig deaktiviert. Um Linting zu aktivieren, legen Sie **Alle > Lint aktivieren** auf TRUE fest.

Falls aktiviert, wird Linting während der Eingabe im Editor angewendet. Probleme werden als grüne Wellenlinien angezeigt. In der folgenden Grafik hat RTVS beispielsweise sechs Linting-Probleme identifiziert, darunter die Verwendung von `=` anstelle von `<-` für eine Zuweisung, fehlende Abstände um Funktionsargumente, die Verwendung von Bezeichnern in Pascal-Schreibweise und Großbuchstaben sowie die Verwendung eines Semikolons. Beim Bewegen des Mauszeigers über einem Problem wird eine Beschreibung eingeblendet.

![Beispiele für Linting für R-Code](media/linting-01.png)

Sie ändern je nach den Anforderungen eines Projekts oder einer Datei häufig Linting-Optionen. Beispielcode eines Onlinekurses kann beispielsweise `=` anstelle von `<-` zusammen mit Bezeichnern in Pascal-Schreibweise verwenden. Ein solcher Code würde häufig Linting-Warnungen anzeigen, da die Linting-Standardoptionen diese Schreibweisen kennzeichnen. Beim Arbeiten mit diesem Code können Sie die Optionen dann einfach deaktivieren, statt sich mit der Korrektur der einzelnen Instanzen befassen zu müssen.

## <a name="assignment-group"></a>Zuweisungsgruppe

| Option | Standardwert | Linting-Effekt |
| --- | --- | --- |
| \<- erzwingen | `True` | Ermittelt, wenn `<-` nicht für die Zuweisung verwendet wird. |

## <a name="naming-group"></a>Gruppe „Benennung“

Diese Optionen kennzeichnen Bezeichner, die unterschiedliche Namenskonventionen nutzen:

| Option | Standardwert | Linting-Effekt |
| --- | --- | --- |
| camelCase markieren | `False` | Kennzeichnet Bezeichner mit gemischter Groß-/Kleinschreibung. |
| Lange Namen markieren | `False` | Kennzeichnet Bezeichner, deren Name die Einstellung „Maximale Namenslänge“ überschreitet. |
| Mehrere Punkte markieren | `True` | Kennzeichnet Bezeichner mit mehreren Punkten. |
| PascalCase markieren | `True` | Kennzeichnet Bezeichner in Pascal-Schreibweise. |
| snake_case markieren | `False` | Kennzeichnet Bezeichner mit Unterstrichen. |
| GROßBUCHSTABEN markieren | `True` | Kennzeichnet Bezeichner in GROßBUCHSTABEN. |
| Maximale Namenslänge | 32 | Die über die Einstellung „Lange Namen markieren“ zugewiesene Länge. |

## <a name="spacing-group"></a>Gruppe „Abstand“

Diese Optionen, die alle standardmäßig auf `True` festgelegt sind, steuern, wo die Linting-Funktion Abstandsprobleme erkennt: hinter Funktionsnamen, um Kommas herum, um Operatoren herum, Position der öffnenden und schließenden geschweiften Klammer, Leerzeichen vor ( und Leerzeichen innerhalb von ().

## <a name="statements-group"></a>Gruppe „Anweisungen“

| Option | Standardwert | Linting-Effekt |
| --- | --- | --- |
| Mehrere | `True` | Ermittelt, wenn sich mehrere Anweisungen in derselben Zeile befinden. |
| Semikolons | `True` | Ermittelt die Verwendung von Semikolons. |

## <a name="text-group"></a>Gruppe „Text“

| Option | Standardwert | Linting-Effekt |
| --- | --- | --- |
| Grenzwert für Zeilenlänge | `False` | Legt fest, ob die Linting-Funktion Zeilen markiert, die länger als die Option „Maximale Zeilenlänge“ sind. |
| Maximale Zeilenlänge | 80 | Legt die Zeilenlänge fest, die durch die Option „Grenzwert für Zeilenlänge“ zugewiesen wird. |

## <a name="whitespace-group"></a>Gruppe „Leerraum“

Diese Optionen, die alle standardmäßig auf `True` festgelegt sind, steuern, wo die Linting-Funktion Leerraumprobleme ermittelt: Verwendung von Tabulatoren, Verwendung von doppelten Anführungszeichen, nachstehende leere Zeilen und nachstehender Leerraum.