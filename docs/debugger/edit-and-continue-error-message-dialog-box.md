---
title: "Fehlermeldungs-Dialogfeld f&#252;r &quot;Bearbeiten und Fortfahren&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Fehlermeldungs-Dialogfeld für "Bearbeiten und Fortfahren""
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Fehlermeldungs-Dialogfeld f&#252;r &quot;Bearbeiten und Fortfahren&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn Sie in einer Programmiersprache debuggen, bei der die Funktion "Bearbeiten und Fortfahren" unterstützt wird, **Bearbeiten und Fortfahren** aber für die Art der von Ihnen vorgenommenen Codeänderungen nicht verfügbar ist.  Die Fehlermeldung in dem Feld enthält eine ausführlichere Erklärung.  Folgende Gründe zum Anzeigen dieses Dialogfelds sind möglich:  
  
-   Sie haben versucht, verwalteten Code zu bearbeiten, während nicht verwaltetes Debuggen aktiviert war.  "Bearbeiten und Fortfahren" funktioniert nicht bei Debuggen im gemischten Modus.  
  
-   Sie haben versucht, SQL Server\-Code zu bearbeiten.  
  
-   Sie haben versucht, Code während des Debuggens eines Dr zu bearbeiten.  Dr.Watson\-Dumps.  
  
-   Sie haben versucht, Code nach dem Auftreten eines Ausnahmefehlers zu bearbeiten, und die Option "**Aufrufliste für Ausnahmefehler entladen**" war dabei nicht aktiviert.  
  
-   Sie haben versucht, Code zu bearbeiten, während Sie für eine eingebettete Laufzeitanwendung ein Debuggen durchgeführt haben.  
  
-   Sie haben versucht, Code in einem Programm zu bearbeiten, das Sie angefügt haben, anstatt im Menü **Debuggen** zu beginnen.  
  
-   Sie haben versucht, optimierten Code zu bearbeiten.  
  
-   Sie haben versucht, verwalteten Code zu bearbeiten, obwohl das Ziel eine 64\-Bit\-Anwendung ist.  Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. \(*Project* **Eigenschaften**, Registerkarte **Kompilieren**, **Erweiterte Compilereinstellungen**.\)  
  
-   Sie haben versucht, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert und erneut geladen wurde.  
  
-   Sie haben versucht, Code in einer Assembly zu bearbeiten, die nicht geladen wurde.  
  
-   Sie haben damit begonnen, eine alte Version der Anwendung zu debuggen \(da die neue Version Buildfehler enthält\).  
  
-   Sie haben versucht, Code während dessen Ausführung zu bearbeiten.  
  
## UIElement-Liste  
 **OK**  
 Schließen Sie das Dialogfeld, und brechen Sie den unmittelbar vorausgegangenen Bearbeitungsversuch ab.  
  
## Siehe auch  
 [Unterstützte Codeänderungen und \-einschränkungen \(C\+\+\)](../debugger/supported-code-changes-cpp.md)