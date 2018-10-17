---
title: Richtlinienfehler bei der Codeanalyse Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bb8e429c7f8ee54ab2c7f0bad08129542d4ce87d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286376"
---
# <a name="code-analysis-policy-errors"></a>Richtlinienfehler bei der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden Fehler treten auf, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird:  
  
 **Die codeanalyseeinstellungen für ein oder mehrere Projekte sind nicht kompatibel mit der Codeanalyserichtlinie.**  
  
 Das Einchecken der Anforderungen an die Codeanalyse in die Quellcodeverwaltung des Teamprojekts wurde für ein oder mehrere Codeprojekte nicht erfüllt. Dieser Fehler kann durch eine oder mehrere der folgenden Bedingungen verursacht werden:  
  
1.  Die Codeanalyse ist nicht für das Build für alle Projekte in der Projektmappe aktiviert.  
  
2.  Für das Projekt in Visual Studio eine weniger restriktive hat der lokale Regelsatz **Aktion** festlegen, als der Teamprojekt-Regelsatz z. B. eine Regel, die festgelegt wird festlegen, um **Aktion**=**Fehler**  auf dem Server verfügt über seine **Aktion** festgelegt **Warnung** oder **keine** in der Regel legen Sie in Visual Studio ausgeführt wird).  
  
3.  Der Regelsatz, der in Visual Studio festgelegt ist, enthält nicht alle Regeln, die im Regelsatz angegeben sind, der in der Eincheckrichtlinie für die Codeanalyse für das Teamprojekt definiert ist.  
  
 **Fehler bei der Richtlinie der Codeanalyse. Fehler im Projekt vorliegen {0} oder der Build ist nicht auf dem neuesten Stand.**  
  
 Der Build enthält entweder Fehler, oder die Fehler wurden korrigiert. Nach der Korrektur wurde jedoch keine Codeanalyse ausgeführt.  
  
 **Fehler beim Check-in. Die Codeanalyserichtlinie erfordert, dass Sie über Visual Studio mit einer geöffneten Projektmappe einchecken.**  
  
 Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.  
  
 **Nicht alle Dateien im ausstehenden Einchecken befinden sich innerhalb der aktuell geöffneten Projektmappe.**  
  
 Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Dieser Fehler tritt auf, wenn eine Projektmappe geöffnet ist, aber einige Dateien in der Ansicht "Anstehende Eincheckvorgänge" nicht zur gerade geöffneten Projektmappe gehören. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.  
  
 **Die Version von "{0}' ist nicht korrekt. Der angegebene starke Name in der Richtlinie wird "{1}".**  
  
 Dieser Fehler bezieht sich auf .NET-Projekte. Eine für die Codeanalyserichtlinie erforderliche Regel-DLL ist auf dem lokalen Computer vorhanden, aber die Version/der öffentliche Schlüssel stimmt nicht überein. Um diesen Fehler zu beheben, muss der Richtlinienersteller die DLLs im aktualisieren *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  Verzeichnis auf ihrem Computer.  
  
 **"{0}" in der Richtlinie angegebene Assembly ist nicht vorhanden.**  
  
 Dieser Fehler bezieht sich auf .NET-Projekte. Für eine für die Codeanalyserichtlinie erforderliche Regel ist die entsprechende DLL nicht auf dem Clientcomputer installiert. Um diesen Fehler zu beheben, die muss Richtlinienersteller der Dll im *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  Verzeichnis auf ihrem Computer.  
  
 **Projekt {0} regeleinstellungen sind nicht in Übereinstimmung mit der Codeanalyserichtlinie.**  
  
 Dieser Fehler bezieht sich auf .NET-Projekte. Die Regeleinstellungen des verwalteten Codes sind nicht so streng wie von der Richtlinie gefordert. Um diesen Fehler zu beheben, muss die Clienteinstellung mindestens so streng wie die Richtlinienanforderung auf dem Server sein.  
  
 **Codeanalyse ist für die aktive Konfiguration nicht aktiviert. Wechseln Sie zur Konfiguration {0} und Buildprojekt {1} vor dem Einchecken.**  
  
 In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist für die aktive Konfiguration keine Codeanalyse aktiviert, es ist jedoch mindestens eine Codeanalyse aktiviert.  
  
 **Sie müssen die Codeanalyse für verwaltete Binärdateien im Projekt aktivieren {0} Eigenschaften und Build vor dem Einchecken.**  
  
 Dieser Fehler gilt für [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-.NET-Anwendungen. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
 **Sie müssen die Codeanalyse im Projekt aktivieren {0} Eigenschaften und Build vor dem Einchecken.**  
  
 Dieser Fehler galt für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekte und Webprojekte. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
 **Sie müssen die C/C++-Codeanalyse im Projekt aktivieren {0} Eigenschaften und Build vor dem Einchecken.**  
  
 Dieser Fehler bezieht sich auf nicht verwaltete Projekte. Gemäß der Codeanalyserichtlinie ist eine Codeanalyse für C/C++ erforderlich, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)



