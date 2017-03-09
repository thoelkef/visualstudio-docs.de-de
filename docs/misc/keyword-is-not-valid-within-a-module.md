---
title: "&#39;&lt;schl&#252;sselwort&gt;&#39; ist innerhalb eines Moduls ung&#252;ltig. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32001"
  - "bc32001"
helpviewer_keywords: 
  - "BC32001"
ms.assetid: b00757ac-5652-460d-9d2c-11b264d7ec7f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;schl&#252;sselwort&gt;&#39; ist innerhalb eines Moduls ung&#252;ltig.
Eine auf Klasseninstanzen bezogenes Schlüsselwort, wie etwa `Me` oder `MyBase`, wird innerhalb eines Moduls verwendet. Module weisen weder Vererbung noch Instanzen auf.  
  
 **Fehler\-ID:** BC32001  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Code, in dem das Schlüsselwort verwendet wird, Klasseninstanzen betrifft, verschieben Sie ihn in eine Klassenimplementierung.  
  
-   Wenn der Code, der das Schlüsselwort verwendet, sich auf das Modul bezieht, entfernen Sie das ungültige Schlüsselwort.  
  
## Siehe auch  
 [Me](http://msdn.microsoft.com/de-de/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyBase – löschen](http://msdn.microsoft.com/de-de/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)