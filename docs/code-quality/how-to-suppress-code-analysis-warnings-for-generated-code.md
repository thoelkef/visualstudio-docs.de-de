---
title: "Vorgehensweise: Unterdrücken von Codeanalysewarnungen für generierten Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd917c8c9a3b66dc1fe34e089e14481c2b7df5a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Gewusst wie: Unterdrücken von Codeanalysewarnungen für generierten Code
Compiler für verwalteten Code generieren häufig Code, der einem Projekt um eine schnelle Codeentwicklung zu ermöglichen hinzugefügt wird. Darüber hinaus verwenden Entwickler häufig Drittanbietertools, um schnelle Entwicklung von Anwendungen helfen. Diese Tools generieren auch Code, der dem Projekt hinzugefügt wird.  
  
 Möglicherweise möchten die Verletzungen von Schwellenwertregeln angezeigt, die Codeanalyse in generiertem Code ermittelt. Möglicherweise möchten Sie nicht angezeigt, wenn nicht möglich, anzeigen und verwalten den Code, der den Verstoß enthält.  
  
 Die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen auf der Codeanalyse-Eigenschaftenseite eines Projekts können Sie auswählen, ob Warnungen der Codeanalyse von einem Drittanbieter-Tool generierten Code angezeigt werden soll.  
  
> [!NOTE]
>  Diese Option unterdrücken, wenn die Fehler und Warnungen in Formularen und Vorlagen angezeigt werden keine Codeanalysefehler und-Warnungen zu generiertem Code. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Unterdrücken von Warnungen für generierten Code in einem Projekt  
  
1.  Mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Codeanalyse**.  
  
3.  Wählen Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.