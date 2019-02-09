---
title: 'Vorgehensweise: Unterdrücken von Codeanalysewarnungen für generierten Code'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0bc46684d94470bb5e12cbdbecb5538ceb89606
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936074"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Vorgehensweise: Unterdrücken von Codeanalysewarnungen für generierten Code
Compiler für verwalteten Code generieren häufig Code, der ein Projekt aus, um die schnelle Codeentwicklung zu vereinfachen hinzugefügt wird. Darüber hinaus verwenden Entwickler häufig Drittanbieter-Tools ab, um schnell Anwendungen zu entwickeln. Diese Tools generieren auch Code, der dem Projekt hinzugefügt wird.

 Sie möchten die Verletzungen angezeigt, die Codeanalyse in generiertem Code ermittelt. Möglicherweise möchten Sie nicht angezeigt, wenn Sie nicht anzeigen und verwalten den Code, der den Verstoß enthält.

 Die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen auf der Eigenschaftenseite "Codeanalyse" eines Projekts können Sie auswählen, ob codeanalysewarnungen aus von einem Drittanbieter-Tool generierten Code angezeigt werden sollen.

> [!NOTE]
>  Diese Option unterdrücken, wenn die Fehler und Warnungen in Formularen und Vorlagen werden keine Codeanalysefehler und-Warnungen zu generiertem Code. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>So unterdrücken Sie Warnungen für generierten Code in einem Projekt

1.  Mit der rechten Maustaste in des Projekts im Projektmappen-Explorer, und klicken Sie dann auf **Eigenschaften**.

2.  Klicken Sie auf **Codeanalyse**.

3.  Wählen Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.