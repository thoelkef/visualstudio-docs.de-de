---
title: 'Fehler: die Abhängigkeit &#39;Datei&#39; im Projekt &#39;Projekt&#39; kann nicht in das Ausführungsverzeichnis kopiert werden, da sie mit Abhängigkeit in Konflikt stehen würde &#39;Datei&#39; | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7726d615c3495845ffdf73d69ffc7d8fae155272
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688281"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Fehler: die Abhängigkeit &#39;Datei&#39; im Projekt &#39;Projekt&#39; kann nicht in das Ausführungsverzeichnis kopiert werden, da sie mit Abhängigkeit in Konflikt stehen würde &#39;Datei&#39;
Es liegt ein Konflikt zwischen Verweisen vor: Mehrere unterschiedliche Abhängigkeiten mit demselben Dateinamen wurden in das Verzeichnis „bin“ für die auszuführende Anwendung kopiert. Das Ausführungsverzeichnis kann den Konflikt nicht lösen, da es sich bei den Abhängigkeiten nicht um Primärverweise handelt.  
  
 Dieser Fehler führt dazu, dass der Build fehlschlägt.  
  
 Wenn Sie auf dieses Aufgabenlistenelement doppelklicken, gelangen Sie zum Verweisknoten des Projekts, in dem der Konflikt auftritt.  
  
 **Um diesen Fehler zu beheben**  
  
- Richten Sie eine der Assemblys als direkten Verweis auf das Projekt ein. Ein möglicher Nachteil dabei ist jedoch, dass die ausgewählte Assembly nicht unbedingt mit Assemblys arbeitet, die eine andere Version der Assembly benötigen, auf die verwiesen wird.  
  
     \- oder –  
  
- Stellen Sie sicher, dass beide Kopien der Assembly einen starken Namen haben und sich im globalen Assemblycache befinden. Dadurch müssen die Assemblys nicht mehr in das Verzeichnis „bin“ kopiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [Globaler Assemblycache](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Assemblys mit starkem Namen](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Assemblyversionen](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Vorgehensweise: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)