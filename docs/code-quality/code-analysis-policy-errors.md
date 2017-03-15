---
title: "Richtlinienfehler bei der Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.policyfailures"
helpviewer_keywords: 
  - "Richtlinienfehler, Codeanalyse"
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Richtlinienfehler bei der Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden Fehler treten auf, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird:  
  
 **Die Codeanalyseeinstellungen für mindestens ein Projekt sind mit der Codeanalyserichtlinie nicht kompatibel.**  
  
 Das Einchecken der Anforderungen an die Codeanalyse in die Quellcodeverwaltung des Teamprojekts wurde für ein oder mehrere Codeprojekte nicht erfüllt.  Dieser Fehler kann durch eine oder mehrere der folgenden Bedingungen verursacht werden:  
  
1.  Die Codeanalyse ist nicht für das Build für alle Projekte in der Projektmappe aktiviert.  
  
2.  Der lokale Regelsatz, der für das Projekt in Visual Studio festgelegt ist, verfügt über eine weniger restriktive Einstellung für **Aktion** als der Teamprojekt\-Regelsatz. Beispiel: Für eine Regel, für die **Aktion**\=**Fehler** auf dem Server festgelegt ist, ist deren **Aktion** auf **Warnung** oder **Keine** im Regelsatz eingestellt, der in Visual Studio ausgeführt wird\).  
  
3.  Der Regelsatz, der in Visual Studio festgelegt ist, enthält nicht alle Regeln, die im Regelsatz angegeben sind, der in der Eincheckrichtlinie für die Codeanalyse für das Teamprojekt definiert ist.  
  
 **Fehler bei der Codeanalyserichtlinie.  Projekt {0} enthält Fehler, oder der Build ist nicht aktuell.**  
  
 Der Build enthält entweder Fehler, oder die Fehler wurden korrigiert. Nach der Korrektur wurde jedoch keine Codeanalyse ausgeführt.  
  
 **Fehler beim Einchecken.  Die Codeanalyserichtlinie erfordert, dass Dateien über Visual Studio mit einer geöffneten Projektmappe eingecheckt werden.**  
  
 Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen.  Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.  
  
 **Nicht alle Dateien im ausstehenden Eincheckvorgang befinden sich in der gerade geöffneten Projektmappe.**  
  
 Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen.  Dieser Fehler tritt auf, wenn eine Projektmappe geöffnet ist, aber einige Dateien in der Ansicht "Anstehende Eincheckvorgänge" nicht zur gerade geöffneten Projektmappe gehören.  Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.  
  
 **Die Version von '{0}' ist nicht richtig.  Der in der Richtlinie angegebene starke Name lautet '{1}.'**  
  
 Dieser Fehler bezieht sich auf .NET\-Projekte.  Eine für die Codeanalyserichtlinie erforderliche Regel\-DLL ist auf dem lokalen Computer vorhanden, aber die Version\/der öffentliche Schlüssel stimmt nicht überein.  Um diesen Fehler zu korrigieren, muss der Richtlinienersteller die DLLs im Verzeichnis *C:\\Program Files\\Microsoft Visual Studio 8\\Team Tools\\Static Analysis Tools\\FxCop\\Rules\\* auf seinem Computer aktualisieren.  
  
 **Die in der Richtlinie angegebene Assembly '{0}' ist nicht vorhanden.**  
  
 Dieser Fehler bezieht sich auf .NET\-Projekte.  Für eine für die Codeanalyserichtlinie erforderliche Regel ist die entsprechende DLL nicht auf dem Clientcomputer installiert.  Um diesen Fehler zu korrigieren, muss der Richtlinienersteller die DLL im Verzeichnis *C:\\Program Files\\Microsoft Visual Studio 8\\Team Tools\\Static Analysis Tools\\FxCop\\Rules\\* auf seinem Computer aktualisieren.  
  
 **Die Regeleinstellungen für Projekt {0} entsprechen nicht der Codeanalyserichtlinie.**  
  
 Dieser Fehler bezieht sich auf .NET\-Projekte.  Die Regeleinstellungen des verwalteten Codes sind nicht so streng wie von der Richtlinie gefordert.  Um diesen Fehler zu beheben, muss die Clienteinstellung mindestens so streng wie die Richtlinienanforderung auf dem Server sein.  
  
 **Die Codeanalyse ist für die aktive Konfiguration nicht aktiviert.  Wechseln Sie vor dem Einchecken zu Konfiguration {0} und Buildprojekt {1}.**  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist für die aktive Konfiguration keine Codeanalyse aktiviert, es ist jedoch mindestens eine Codeanalyse aktiviert.  
  
 **Sie müssen die Codeanalyse für verwaltete Binärdateien in den Projekteigenschaften für {0} und im Build vor dem Einchecken aktivieren.**  
  
 Dieser Fehler gilt für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-.NET\-Anwendungen.  Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
 **Sie müssen die Codeanalyse in den Projekteigenschaften für {0} und im Build vor dem Einchecken aktivieren.**  
  
 Dieser Fehler galt für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekte und Webprojekte.  Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
 **Sie müssen die C\/C\+\+\-Codeanalyse in den Projekteigenschaften für {0} und im Build vor dem Einchecken aktivieren.**  
  
 Dieser Fehler bezieht sich auf nicht verwaltete Projekte.  Gemäß der Codeanalyserichtlinie ist eine Codeanalyse für C\/C\+\+ erforderlich, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.  
  
## Siehe auch  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)