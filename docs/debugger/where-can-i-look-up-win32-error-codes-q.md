---
title: "Wo sind die Win32-Fehlercodes zu finden? | Microsoft Docs"
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
  - "vc.errors"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Fehlercodes, Win32"
  - "Win32, Fehlercodes"
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wo sind die Win32-Fehlercodes zu finden?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**WINERROR.H** im Verzeichnis **INCLUDE** der Standardsysteminstallation enthält die Definitionen der Fehlercodes für die Win32\-API\-Funktionen.  
  
 Sie können den Fehlercode nachsehen, indem Sie den Code im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.  Beispiel:  
  
```  
0x80000004,hr  
```  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)