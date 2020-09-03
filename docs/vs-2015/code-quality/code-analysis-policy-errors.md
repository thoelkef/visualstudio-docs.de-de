---
title: Fehler bei der Code Analyse Richtlinie | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8cb50fffc1411e77f771b0f74fbb947144eb6017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672921"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden Fehler treten auf, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird:

 **Die Codeanalyseeinstellungen für mindestens ein Projekt sind mit der Codeanalyserichtlinie nicht kompatibel.**

 Das Einchecken der Anforderungen an die Codeanalyse in die Quellcodeverwaltung des Teamprojekts wurde für ein oder mehrere Codeprojekte nicht erfüllt. Dieser Fehler kann durch eine oder mehrere der folgenden Bedingungen verursacht werden:

1. Die Codeanalyse ist nicht für das Build für alle Projekte in der Projektmappe aktiviert.

2. Der lokale Regelsatz für das Projekt in Visual Studio verfügt über eine weniger einschränkende **Aktions** Einstellung als der Teamprojekt-Regelsatz. eine Regel, die auf " **Aktions** = **Fehler** " auf dem Server **festgelegt ist** , ist auf " **Warning** " oder " **None** " in dem Regelsatz festgelegt, der in Visual Studio ausgeführt wird.

3. Der Regelsatz, der in Visual Studio festgelegt ist, enthält nicht alle Regeln, die im Regelsatz angegeben sind, der in der Eincheckrichtlinie für die Codeanalyse für das Teamprojekt definiert ist.

   **Die Code Analyse Richtlinie ist fehlgeschlagen. Es sind Fehler in Project vorhanden {0} , oder der Build ist nicht auf dem neuesten Stand.**

   Der Build enthält entweder Fehler, oder die Fehler wurden korrigiert. Nach der Korrektur wurde jedoch keine Codeanalyse ausgeführt.

   **Fehler beim Einchecken. Die Code Analyse Richtlinie erfordert, dass Sie Visual Studio mit einer geöffneten Projekt Mappe einchecken.**

   Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.

   **Nicht alle Dateien im ausstehenden Einchecken befinden sich in der gerade geöffneten Projektmappe.**

   Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Dieser Fehler tritt auf, wenn eine Projektmappe geöffnet ist, aber einige Dateien in der Ansicht "Anstehende Eincheckvorgänge" nicht zur gerade geöffneten Projektmappe gehören. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.

   **Die Version von ' {0} ' ist nicht richtig. Der in der Richtlinie angegebene starke Name ist " {1} ".**

   Dieser Fehler bezieht sich auf .NET-Projekte. Eine für die Codeanalyserichtlinie erforderliche Regel-DLL ist auf dem lokalen Computer vorhanden, aber die Version/der öffentliche Schlüssel stimmt nicht überein. Um diesen Fehler zu beheben, muss der Richtlinien Ersteller die DLLs im Verzeichnis " *c:\Programme\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\ * " auf dem Computer aktualisieren.

   **die {0} in der Richtlinie angegebene Assembly ist nicht vorhanden.**

   Dieser Fehler bezieht sich auf .NET-Projekte. Für eine für die Codeanalyserichtlinie erforderliche Regel ist die entsprechende DLL nicht auf dem Clientcomputer installiert. Um diesen Fehler zu beheben, muss der Richtlinien Ersteller die dll im Verzeichnis " *c:\Programme\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\ * " auf dem Computer aktualisieren.

   **{0}Die Projekt Regel Einstellungen stimmen nicht mit der Code Analyse Richtlinie überein.**

   Dieser Fehler bezieht sich auf .NET-Projekte. Die Regeleinstellungen des verwalteten Codes sind nicht so streng wie von der Richtlinie gefordert. Um diesen Fehler zu beheben, muss die Clienteinstellung mindestens so streng wie die Richtlinienanforderung auf dem Server sein.

   **Die Code Analyse ist für die aktive Konfiguration nicht aktiviert. Wechseln Sie zu Konfiguration, {0} und erstellen Sie das Projekt, {1} bevor Sie einchecken.**

   In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist für die aktive Konfiguration keine Codeanalyse aktiviert, es ist jedoch mindestens eine Codeanalyse aktiviert.

   **Sie müssen die Code Analyse für verwaltete Binärdateien in den Projekt {0} Eigenschaften und den Build vor dem Einchecken aktivieren.**

   Dieser Fehler gilt für [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-.NET-Anwendungen. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

   **Sie müssen die Code Analyse in den Projekt {0} Eigenschaften aktivieren und den Build vor dem Einchecken aktivieren.**

   Dieser Fehler galt für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekte und Webprojekte. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

   **Sie müssen die C/C++-Code Analyse in den Projekt {0} Eigenschaften und den Build vor dem Einchecken aktivieren.**

   Dieser Fehler bezieht sich auf nicht verwaltete Projekte. Gemäß der Codeanalyserichtlinie ist eine Codeanalyse für C/C++ erforderlich, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

## <a name="see-also"></a>Weitere Informationen
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
