---
title: "Gewusst wie: Konfigurieren der Codeanalyse f&#252;r eine ASP.NET-Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Konfigurieren der Codeanalyse f&#252;r eine ASP.NET-Anwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] und [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] können Sie *Regelsätze* für die Codeanalyse aus einer Liste auswählen, um diese auf die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung anzuwenden.  Der Standardregelsatz sind die Microsoft\-Mindestregeln.  Sie können eine andere Regel auswählen, die auf die Website angewendet werden soll.  
  
### So konfigurieren Sie einen Regelsatz für ein ASP.NET\-Seitenframeworkprojekt  
  
1.  Wählen Sie die Website im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Analyse** auf **Codeanalyse für Website konfigurieren**.  
  
3.  Wenn Sie die Projektmappe ausgewählt haben und diese mehrere Projekte enthält, wählen Sie in den Listen **Konfiguration** und **Plattform** die Buildkonfiguration sowie das Zielbetriebssystem aus.  
  
4.  Klicken Sie für jedes Projekt in der Lösung auf die Spalte **Regelsatz** und anschließend auf den Namen des auszuführenden Regelsatzes.  
  
5.  Standardmäßig wird die Codeanalyse für alle Projekte in der Lösung ausgeführt.  Um Codeanalyse für ein bestimmtes Projekt zu deaktivieren oder zu aktivieren, führen Sie folgende Schritte aus:  
  
    1.  Klicken Sie mit der rechten Maustaste auf den Projektnamen, und klicken Sie anschließend auf Eigenschaften.  
  
    2.  Aktivieren oder deaktivieren Sie das Kontrollkästchen **Codeanalyse aktivieren**.  Sie können die Codeanalyse auch manuell ausführen, indem Sie im Menü **Analyse** die Option **Codeanalyse auf Website ausführen** auswählen.  
  
6.  Führen Sie in der Dropdownliste **Diesen Regelsatz ausführen** die folgenden Schritte aus:  
  
    -   Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    -   Wählen **\<Durchsuchen\>**, um einen vorhandenen benutzerdefinierten Regelsatz anzugeben, der nicht in der Liste ist.  
  
    -   Definieren Sie einen benutzerdefinierten Regelsatz.  Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).