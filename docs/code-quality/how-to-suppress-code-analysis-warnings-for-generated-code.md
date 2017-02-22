---
title: "Gewusst wie: Unterdr&#252;cken von Codeanalysewarnungen f&#252;r generierten Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Unterdr&#252;cken von Codeanalysewarnungen f&#252;r generierten Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Compiler für verwalteten Code generieren oft Code, der einem Projekt hinzugefügt wird, um eine schnelle Codeentwicklung zu ermöglichen.  Außerdem verwenden Entwickler oft Drittanbietertools, um die Anwendungsentwicklung zu beschleunigen.  Diese Tools generieren auch Code, der dem Projekt hinzugefügt wird.  
  
 Möglicherweise möchten Sie die Regelverletzungen anzeigen, die die Codeanalyse in generiertem Code ermittelt.  Allerdings sollen diese Verletzungen vielleicht nicht angezeigt werden, wenn der Code, der die Regelverletzung enthält, nicht angezeigt und verwaltet werden kann.  
  
 Mit dem Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** auf der Eigenschaftenseite für die Codeanalyse eines Projekts können Sie auswählen, ob Codeanalysewarnungen aus Code, der durch ein Drittanbietertool generiert wurde,  angezeigt werden.  
  
> [!NOTE]
>  Allerdings werden durch diese Option keine Codeanalysefehler und \-warnungen aus generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten.  Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
### So unterdrücken Sie Warnungen für generierten Code in einem Projekt  
  
1.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Codeanalyse**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken**.