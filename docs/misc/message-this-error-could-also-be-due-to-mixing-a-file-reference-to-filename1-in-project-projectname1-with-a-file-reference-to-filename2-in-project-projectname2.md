---
title: "&lt;Meldung&gt; Dieser Fehler k&#246;nnte auch auf die Kombination eines Dateiverweises auf &lt;Dateiname1&gt; in Projekt &lt;Projektname1&gt; mit einem Dateiverweis auf &lt;Dateiname2&gt; in Projekt &lt;Projektname2&gt; zur&#252;ckzuf&#252;hren sein. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30970"
  - "vbc30970"
helpviewer_keywords: 
  - "BC30970"
ms.assetid: 81cc4f7b-cc16-46cc-9a49-74980300e158
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Meldung&gt; Dieser Fehler k&#246;nnte auch auf die Kombination eines Dateiverweises auf &lt;Dateiname1&gt; in Projekt &lt;Projektname1&gt; mit einem Dateiverweis auf &lt;Dateiname2&gt; in Projekt &lt;Projektname2&gt; zur&#252;ckzuf&#252;hren sein.
\<Meldung\> Dieser Fehler könnte auch auf die Kombination eines Dateiverweises auf \<Dateipfadname1\> in Projekt \<Projektname1\> mit einem Dateiverweis auf \<Dateipfadname2\> in Projekt \<Projektname2\> zurückzuführen sein.  Wenn die beiden Assemblys identisch sind, ersetzen Sie die beiden Verweise durch Verweise vom gleichen Speicherort.  
  
 Code in Ihrem Projekt greift auf einen Member eines anderen Projekts zu, aufgrund der Konfiguration Ihrer Projektmappe kann der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler den Verweis aber nicht auflösen.  
  
 Für den Zugriff auf einen Typ in einer anderen Assembly benötigt der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler einen Verweis auf diese Assembly. Dabei muss es sich um einen einzelnen, eindeutigen Verweis handeln, der keine Zirkelverweise in Projekten verursacht.  
  
 **Fehler\-ID:** BC30970  
  
### So beheben Sie diesen Fehler  
  
1.  Bestimmen Sie, welches Projekt die Assembly erzeugt, auf die Ihr Projekt am besten verweisen kann. Für diese Entscheidung können Sie Kriterien wie den einfachen Zugriff auf Dateien und die Häufigkeit von Updates verwenden.  
  
2.  Fügen Sie in den Projekteigenschaften einen Verweis auf die Datei mit der Assembly hinzu, die den von Ihnen verwendeten Typ definiert.  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NICHT IM BUILD: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)