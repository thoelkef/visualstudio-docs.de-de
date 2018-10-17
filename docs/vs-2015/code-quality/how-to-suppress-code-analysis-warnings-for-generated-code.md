---
title: 'Vorgehensweise: Unterdrücken von Codeanalysewarnungen für generierten Code | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07858183af427e2b67e1e0f63d1f8889caf72fbe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293741"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Gewusst wie: Unterdrücken von Codeanalysewarnungen für generierten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Compiler für verwalteten Code generieren häufig Code, der ein Projekt aus, um die schnelle Codeentwicklung zu vereinfachen hinzugefügt wird. Darüber hinaus verwenden Entwickler häufig Drittanbieter-Tools ab, um schnell Anwendungen zu entwickeln. Diese Tools generieren auch Code, der dem Projekt hinzugefügt wird.  
  
 Sie möchten die Verletzungen angezeigt, die Codeanalyse in generiertem Code ermittelt. Möglicherweise möchten Sie nicht angezeigt, wenn Sie nicht anzeigen und verwalten den Code, der den Verstoß enthält.  
  
 Die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen auf der Eigenschaftenseite "Codeanalyse" eines Projekts können Sie auswählen, ob codeanalysewarnungen aus von einem Drittanbieter-Tool generierten Code angezeigt werden sollen.  
  
> [!NOTE]
>  Diese Option unterdrücken, wenn die Fehler und Warnungen in Formularen und Vorlagen werden keine Codeanalysefehler und-Warnungen zu generiertem Code. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>So unterdrücken Sie Warnungen für generierten Code in einem Projekt  
  
1.  Mit der rechten Maustaste in des Projekts im Projektmappen-Explorer, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Codeanalyse**.  
  
3.  Wählen Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.



