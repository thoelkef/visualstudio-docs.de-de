---
title: "Gewusst wie: Unterdr&#252;cken von Warnungen &#252;ber das Men&#252;element | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Warnungen, unterdrücken"
  - "Codeanalyse, Unterdrücken von Warnungen"
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Unterdr&#252;cken von Warnungen &#252;ber das Men&#252;element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  In der Unterdrückung im Quellcode wird für Websiteprojekte nicht unterstützt.  
  
 Sie können das Codeanalysefenster verwenden, um Codeanalysewarnungen zu unterdrücken.  Eine Warnung zu unterdrücken ist nicht identisch, es deaktivieren.  Wenn Sie eine Warnung unterdrücken, gilt dies nur für eine bestimmte Instanz der Regelverletzung.  Andere Verletzungen, auf die mit der gleichen Warnung hingewiesen wird, werden weiterhin im Fenster Fehlerliste aufgeführt.  
  
 Nachdem Sie eine Codeanalyse ausführen, stellen Sie möglicherweise fest, dass eine oder mehrere der Codeanalysewarnungen, die im Codeanalysefenster angezeigt werden, nicht in der Anwendung auf.  Sie kommen möglicherweise zu dem Schluss, dass der Code im aktuellen Zustand richtig ist.  Oder vielleicht liegen Regelverletzungen vor, die aber eine so geringe Priorität haben, dass sie im aktuellen Entwicklungszyklus nicht korrigiert werden.  Unabhängig vom jeweiligen Grund anzugeben ist häufig nützlich, dass die Warnung nicht zutreffend ist, die Teammitglieder erkennen, dass der Code bereits überprüft wurde und dass es bestimmt wurde, die Warnung zu unterdrücken.  In der Unterdrückung im Quellcode ist hilfreich, da Sie setzen können Unterdrückung eng an, der die Warnung generiert wird.  
  
 Sie können auswählen, ob die Unterdrückung im Quellcode oder in der globalen Unterdrückungsdatei angezeigt wird.  Einige Unterdrückungen müssen in die globale Unterdrückungsdatei eingefügt werden.  In diesem Fall wird die Option **In Quelle** deaktiviert.  
  
### So unterdrücken Sie eine Warnung über das Menüelement  
  
1.  Klicken Sie im Menü **Analysieren** wählen Sie **Fenster** und wählen Sie dann **Codeanalyse** aus.  
  
2.  Im Fenster **Codeanalyse** wählen Sie die Warnung unterdrücken aus.  
  
3.  Wählen Sie Aktionen aus, wählen Sie **Meldung unterdrücken** und wählen Sie dann entweder **In Quelle** oder **In Projektunterdrückungsdatei**.  
  
     Die betreffende Warnung wird unterdrückt, und die Warnung wird im Codeanalysefenster durchgestrichen.  
  
> [!NOTE]
>  Unterdrückungen ohne Ziel werden in der globalen Unterdrückungsdatei angezeigt.