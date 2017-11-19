---
title: Richtlinienfehler bei der Codeanalyse Code | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyfailures
helpviewer_keywords: policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 052bb1314560089feb714027737f35167c947418
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-policy-errors"></a>Richtlinienfehler bei der Codeanalyse
Die folgenden Fehler treten auf, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird:  
  
 **Die codeanalyseeinstellungen für ein oder mehrere Projekte sind nicht kompatibel mit der Codeanalyserichtlinie.**  
  
 Das Einchecken der Anforderungen an die Codeanalyse in die Quellcodeverwaltung des Teamprojekts wurde für ein oder mehrere Codeprojekte nicht erfüllt. Dieser Fehler kann durch eine oder mehrere der folgenden Bedingungen verursacht werden:  
  
1.  Die Codeanalyse ist nicht für das Build für alle Projekte in der Projektmappe aktiviert.  
  
2.  Der lokale Regelsatz, der für das Projekt in Visual Studio eine weniger restriktive hat **Aktion** festlegen als der Teamprojekt-Regelsatz z. B. eine Regel, die festgelegt wird festlegen, um **Aktion**=**Fehler**  auf dem Server verfügt über seine **Aktion** festgelegt **Warnung** oder **keine** in der Regel legen Sie in Visual Studio ausgeführt wird).  
  
3.  Der Regelsatz, der in Visual Studio festgelegt ist, enthält nicht alle Regeln, die im Regelsatz angegeben sind, der in der Eincheckrichtlinie für die Codeanalyse für das Teamprojekt definiert ist.  
  
 **Fehler bei der Codeanalyserichtlinie. Fehler im Projekt {0} vorliegen, oder der Build ist nicht auf dem neuesten Stand.**  
  
 Der Build enthält entweder Fehler, oder die Fehler wurden korrigiert. Nach der Korrektur wurde jedoch keine Codeanalyse ausgeführt.  
  
 **Fehler beim Einchecken. Die Codeanalyserichtlinie setzt voraus, dass über Visual Studio mit einer geöffneten Projektmappe haben eingecheckt.**  
  
 Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.  
  
 **Nicht alle Dateien im ausstehenden Eincheckvorgang befinden sich in der gerade geöffneten Projektmappe.**  
  
 Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Dieser Fehler tritt auf, wenn eine Projektmappe geöffnet ist, aber einige Dateien in der Ansicht "Anstehende Eincheckvorgänge" nicht zur gerade geöffneten Projektmappe gehören. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.  
  
 **Die Version von "{0}" ist nicht richtig. Der angegebene starke Name in der Richtlinie ist "\ {1\}".**  
  
 Dieser Fehler bezieht sich auf .NET-Projekte. Eine für die Codeanalyserichtlinie erforderliche Regel-DLL ist auf dem lokalen Computer vorhanden, aber die Version/der öffentliche Schlüssel stimmt nicht überein. Um diesen Fehler zu beheben, muss der Richtlinienersteller aktualisieren, die DLLs im *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  Verzeichnis auf ihrem Computer.  
  
 **{0}-Assembly in der Richtlinie angegeben ist nicht vorhanden.**  
  
 Dieser Fehler bezieht sich auf .NET-Projekte. Für eine für die Codeanalyserichtlinie erforderliche Regel ist die entsprechende DLL nicht auf dem Clientcomputer installiert. Um diesen Fehler zu beheben, muss der Richtlinienersteller die Dll in aktualisieren *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  Verzeichnis auf ihrem Computer.  
  
 **Projekteinstellungen von {0}-Regel sind nicht in Übereinstimmung mit der Codeanalyserichtlinie.**  
  
 Dieser Fehler bezieht sich auf .NET-Projekte. Die Regeleinstellungen des verwalteten Codes sind nicht so streng wie von der Richtlinie gefordert. Um diesen Fehler zu beheben, muss die Clienteinstellung mindestens so streng wie die Richtlinienanforderung auf dem Server sein.  
  
 **Codeanalyse ist für die aktive Konfiguration nicht aktiviert. Wechseln Sie zur Konfiguration {0}, und erstellen Sie vor dem Einchecken Projekt \ {1\}.**  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist für die aktive Konfiguration keine Codeanalyse aktiviert, es ist jedoch mindestens eine Codeanalyse aktiviert.  
  
 **Sie müssen aktiviert die Codeanalyse für verwaltete Binärdateien in den Projekteigenschaften für {0}, und erstellen vor dem Einchecken.**  
  
 Dieser Fehler gilt für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-.NET-Anwendungen. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
 **Sie müssen aktiviert die Codeanalyse in den Projekteigenschaften für {0}, und erstellen vor dem Einchecken.**  
  
 Dieser Fehler galt für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekte und Webprojekte. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
 **Sie müssen C-/C++-Codeanalyse in den Projekteigenschaften für {0} zu aktivieren und erstellen vor dem Einchecken.**  
  
 Dieser Fehler bezieht sich auf nicht verwaltete Projekte. Gemäß der Codeanalyserichtlinie ist eine Codeanalyse für C/C++ erforderlich, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)