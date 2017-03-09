---
title: "Die Mehrfachdateiassembly-Komponente &quot;Name_der_Komponentendatei&quot; kann nicht in die Datei &quot;Name_der_Zieldatei&quot; kopiert werden. &lt;Ursache&gt;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscattercomponent"
ms.assetid: 22f851fc-431b-4cdf-9de1-3a29727fa1e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Mehrfachdateiassembly-Komponente &quot;Name_der_Komponentendatei&quot; kann nicht in die Datei &quot;Name_der_Zieldatei&quot; kopiert werden. &lt;Ursache&gt;.
Die angegebene Komponente wurde nicht in das bin\-Verzeichnis kopiert.  
  
 Einige Assemblys bestehen aus mehreren Dateien. Diese Diagnosemeldung wird immer dann angezeigt, wenn eine Datei, die Teil einer Mehrfachdatei\-Assembly ist, nicht in das Ausführungsverzeichnis kopiert werden kann.  
  
 Es kann mehrere Ursachen für diesen Fehler geben. Beispielsweise unzureichenden Speicherplatz oder das Erreichen des MAX\_PATH\-Grenzwerts für die Pfadlänge. Darüber hinaus kann auch ein Prozess, wie etwa Visual Studio, eine Sperre für die nicht kopierbare Komponente eingerichtet haben.  
  
 **So beheben Sie diesen Fehler**  
  
-   Überprüfen Sie, ob ausreichend Speicherplatz verfügbar ist.  
  
-   Versuchen Sie, das Projekt in einen Ordner mit einer kürzeren Pfadlänge als die Pfadlänge des aktuellen Projektordners zu verschieben.  
  
-   Ändern Sie das Ausgabeverzeichnis in einen Ordner mit einer kürzeren absoluten Pfadlänge. Dies betrifft nur auf Clientprojekte \(nicht Webprojekte\).  
  
-   Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu.  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)