---
title: "Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterst&#252;tzt. | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_ia64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterst&#252;tzt.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio unterstützt kein Debugging im gemischten Modus für verwalteten und systemeigenen Code in IA64\-Prozessen.  Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu systemeigenem Code oder von systemeigenem Code zu verwaltetem Code wechseln können.  
  
### Problemumgehung  
  
-   Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.  
  
     – oder –  
  
     Debuggen Sie den gemischten Code als 32\-Bit\-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### So ändern Sie die Plattform in 32\-Bit \(Visual Basic oder C\#\)  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend im Kontextmenü auf **Eigenschaften**.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.  
  
3.  Klicken Sie auf **Plattform**, und wählen Sie x86 aus der Liste der Plattformen aus.  
  
     Die Visual Basic\- und C\#\-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann.  Auf einem 64\-Bit\-Computer werden diese Binärdateien als 64\-Bit\-Prozesse ausgeführt.  Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32\-Bit\-Prozess wünschen.  
  
### So ändern Sie die Plattform in 32\-Bit \(C\/C\+\+\)  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend im Kontextmenü auf **Eigenschaften**.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie Win32 aus der Liste der Plattformen aus.  
  
## Siehe auch  
 [Debuggen von 64\-Bit\-Anwendungen](../debugger/debug-64-bit-applications.md)