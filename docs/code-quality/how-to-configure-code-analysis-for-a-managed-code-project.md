---
title: "Gewusst wie: Konfigurieren der Codeanalyse f&#252;r ein Projekt mit verwaltetem Code | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "Codeanalyse, Auswählen von Regelsätzen"
  - "Codeanalyse, Regelsätze"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Konfigurieren der Codeanalyse f&#252;r ein Projekt mit verwaltetem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] und [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] können Sie in einer Liste *Regelsätze* für die Codeanalyse auswählen, um diese auf ein Projekt mit verwaltetem Code anzuwenden.  Der Standardregelsatz sind die Microsoft\-Mindestregeln.  Sie können einen anderen Regelsatz auf ein Projekt oder alle Projekte in einer Projektmappe anwenden.  
  
> [!NOTE]
>  Informationen über das Konfigurieren eines Regelsatzes für ASP.NET\-Anwendungen finden Sie unter [Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET\-Anwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### So konfigurieren Sie einen Regelsatz für ein .NET Framework\-Projekt  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf das Projekt.  
  
2.  Klicken Sie im Menü **Analysieren** auf **Codeanalyse für *ProjectName* konfigurieren**.  
  
3.  Klicken Sie in den Listen **Konfiguration** und **Plattform** auf die Buildkonfiguration und die Zielplattform.  
  
4.  Um die Codeanalyse immer auszuführen, wenn das Projekt mit der ausgewählten Konfiguration erstellt wird, aktivieren Sie das Kontrollkästchen **Codeanalyse für Build aktivieren \(definiert eine CODE\_ANALYSIS\-Konstante\)**.  Sie können die Codeanalyse auch manuell ausführen, indem Sie das Menü **Analysieren** öffnen und auf **Codeanalyse für *ProjectName* ausführen** klicken.  
  
5.  Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird.  Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken**.  
  
    > [!NOTE]
    >  Allerdings werden durch diese Option keine Codeanalysefehler und \-warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten.  Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
6.  Führen Sie für die Liste **Diesen Regelsatz ausführen** einen der folgenden Schritte aus:  
  
    -   Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    -   Klicken Sie auf **\<Durchsuchen...\>**, um einen vorhandenen benutzerdefinierten Regelsatz anzugeben, der nicht in der Liste aufgeführt ist.  
  
    -   Definieren Sie einen benutzerdefinierten Regelsatz.  
  
         Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)