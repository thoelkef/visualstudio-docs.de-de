---
title: "Debuggen im gemischten Modus f&#252;r x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder h&#246;her, unterst&#252;tzt | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen im gemischten Modus f&#252;r x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder h&#246;her, unterst&#252;tzt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.NET Framework\-Versionen vor Version 4 bieten keine Unterstützung für das Debuggen im gemischten Modus von x64\-Prozessen.  Das bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu systemeigenem Code oder von systemeigenem Code zu verwaltetem Code wechseln können.  
  
### Problemumgehung  
  
-   Aktualisieren Sie das Projekt, um Microsoft .NET Framework 4 oder höher zu verwenden.  
  
     – oder –  
  
     Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.  
  
     – oder –  
  
     Debuggen Sie den gemischten Code als 32\-Bit\-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### So ändern Sie die Plattform in 32\-Bit \(Visual Basic oder C\#\)  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.  
  
3.  Klicken Sie auf **Plattform**, und wählen Sie x86 aus der Liste der Plattformen aus.  
  
     Die Visual Basic\- und C\#\-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann.  Auf einem 64\-Bit\-Computer werden diese Binärdateien als 64\-Bit\-Prozesse ausgeführt.  Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32\-Bit\-Prozess wünschen.  
  
### So ändern Sie die Plattform in 32\-Bit \(C\/C\+\+\)  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie Win32 aus der Liste der Plattformen aus.  
  
### So beheben Sie diesen Fehler  
  
-   Siehe [Setting Up SQL Debugging](http://msdn.microsoft.com/de-de/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Siehe auch  
 [Debuggen von 64\-Bit\-Anwendungen](../debugger/debug-64-bit-applications.md)