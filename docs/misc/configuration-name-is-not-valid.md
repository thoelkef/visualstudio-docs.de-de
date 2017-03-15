---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
Im Allgemeinen tritt dieser Fehler auf, wenn der eingegebene Name für die Buildkonfiguration unzulässige Zeichen enthält, z. B. \<, \>, &#124; und \*.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Konfigurationsname keines der folgenden Zeichen enthält: \<, \>, \*, &#124;, :, \\, \/, &, %, ", ., \#, ? und außerdem keine voran\- oder nachstehenden Leerzeichen aufweist.  Darüber hinaus darf als Konfigurationsname kein von Windows oder DOS reservierter Namen \("nul", "aux", "con", "com\#", "lpt\#" usw.\) verwendet werden.  
  
2.  Geben Sie den Namen erneut ein.  
  
## Siehe auch  
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)