---
title: Richtlinienfehler bei der Codeanalyse
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 661f029b617c430f7205552080a94affc5bd543b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445889"
---
# <a name="code-analysis-policy-errors"></a>Richtlinienfehler bei der Codeanalyse

Die folgenden Fehler treten auf, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird:

**Die Code Analyse Einstellungen für mindestens ein Projekt sind mit der Code Analyse Richtlinie nicht kompatibel.**

Die Code Analyseanforderungen, die an die Projekt Quell Code Verwaltung einchecken, wurden für ein oder mehrere Code Projekte nicht erfüllt. Dieser Fehler kann durch eine oder mehrere der folgenden Bedingungen verursacht werden:

- Die Codeanalyse ist nicht für das Build für alle Projekte in der Projektmappe aktiviert.

- Der lokale Regelsatz für das Projekt in Visual Studio verfügt über eine weniger einschränkende **Aktions** Einstellung als der Projekt Regelsatz. eine Regel, die auf **Aktion** festgelegt ist, =**Fehler** auf dem Server auf " **Warnung** " **festgelegt ist** , oder **Keine** im Regelsatz, der in Visual Studio ausgeführt wird.

- Der in Visual Studio angegebene Regelsatz enthält nicht alle Regeln, die im Regelsatz angegeben sind, der in der Eincheck Richtlinie für die Code Analyse für das Projekt angegeben ist.

**Die Code Analyse Richtlinie ist fehlgeschlagen. In Project {0} sind Fehler aufgetreten, oder der Build ist nicht auf dem neuesten Stand.**

Der Build enthält entweder Fehler, oder die Fehler wurden korrigiert. Nach der Korrektur wurde jedoch keine Codeanalyse ausgeführt.

**Fehler beim Einchecken. Die Code Analyse Richtlinie erfordert, dass Sie Visual Studio mit einer geöffneten Projekt Mappe einchecken.**

Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.

**Nicht alle Dateien im ausstehenden Einchecken befinden sich in der aktuell geöffneten Projekt Mappe.**

Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Dieser Fehler tritt auf, wenn eine Projektmappe geöffnet ist, aber einige Dateien in der Ansicht "Anstehende Eincheckvorgänge" nicht zur gerade geöffneten Projektmappe gehören. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.

**Die Version von ' {0} ' ist nicht richtig. Der in der Richtlinie angegebene starke Name ist "{1}".**

Dieser Fehler bezieht sich auf .NET-Projekte. Eine für die Codeanalyserichtlinie erforderliche Regel-DLL ist auf dem lokalen Computer vorhanden, aber die Version/der öffentliche Schlüssel stimmt nicht überein. Um diesen Fehler zu beheben, muss der Richtlinien Ersteller die DLLs im Verzeichnis " *c:\Programme\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* " auf dem Computer aktualisieren.

**die in der Richtlinie angegebene ' {0} '-Assembly ist nicht vorhanden.**

Dieser Fehler bezieht sich auf .NET-Projekte. Für eine für die Codeanalyserichtlinie erforderliche Regel ist die entsprechende DLL nicht auf dem Clientcomputer installiert. Um diesen Fehler zu beheben, muss der Richtlinien Ersteller die dll im Verzeichnis *c:\Programme\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* auf dem Computer aktualisieren.

**Die Projekt {0} Regel Einstellungen stimmen nicht mit der Code Analyse Richtlinie überein.**

Dieser Fehler bezieht sich auf .NET-Projekte. Die Regeleinstellungen des verwalteten Codes sind nicht so streng wie von der Richtlinie gefordert. Um diesen Fehler zu beheben, muss die Clienteinstellung mindestens so streng wie die Richtlinienanforderung auf dem Server sein.

**Die Code Analyse ist für die aktive Konfiguration nicht aktiviert. Wechseln Sie vor dem Einchecken zu Konfigurations {0}, und erstellen Sie Project {1}.**

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist für die aktive Konfiguration keine Codeanalyse aktiviert, es ist jedoch mindestens eine Codeanalyse aktiviert.

**Sie müssen die Code Analyse für verwaltete Binärdateien in Project {0} Eigenschaften und Build vor dem Einchecken aktivieren.**

Dieser Fehler gilt für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-.NET-Anwendungen. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

**Sie müssen die Code Analyse in Project {0}-Eigenschaften und-Builds aktivieren, bevor Sie einchecken.**

Dieser Fehler wurde auf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte und Webprojekte angewendet. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

**Sie müssen die C/C++ Code-Analyse in Project {0} Eigenschaften und Build vor dem Einchecken aktivieren.**

Dieser Fehler bezieht sich auf nicht verwaltete Projekte. Gemäß der Codeanalyserichtlinie ist eine Codeanalyse für C/C++ erforderlich, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

## <a name="see-also"></a>Siehe auch

- [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
