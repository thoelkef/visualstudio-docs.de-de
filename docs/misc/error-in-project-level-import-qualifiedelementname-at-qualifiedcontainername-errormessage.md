---
title: "Fehler beim Import &quot;&lt;QualifizierterElementname&gt;&quot; auf Projektebene bei &quot;&lt;QualifizierterContainername&gt;&quot;: &lt;Fehlermeldung&gt; | Microsoft Docs"
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
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler beim Import &quot;&lt;QualifizierterElementname&gt;&quot; auf Projektebene bei &quot;&lt;QualifizierterContainername&gt;&quot;: &lt;Fehlermeldung&gt;
In einer Anweisung wird auf ein Programmierelement zugegriffen, das in einer anderen Assembly definiert ist, es gibt aber keinen Projektverweis auf diese Assembly.  
  
 Angenommen im Code wird versucht, auf eine Enumeration namens `desiredEnumeration` zuzugreifen, wobei die Qualifizierungszeichenfolge `otherNamespace.otherClass.desiredEnumeration` verwendet wird. Wenn der Compiler `otherNamespace.otherClass` nicht in den Verweisen des Projekts finden kann, generiert er diesen Fehler.  
  
 **Fehler\-ID:** BC30797  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass jedes Element in der Qualifizierungszeichenfolge des Programmierelements richtig geschrieben ist.  
  
2.  Vergewissern Sie sich, dass Ihr Projekt einen Verweis auf die Assembly hat, in der das gewünschte Programmierelement definiert ist.  
  
3.  Lesen Sie die Fehlermeldung, und ergreifen Sie entsprechende Maßnahmen.  
  
## Siehe auch  
 [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)