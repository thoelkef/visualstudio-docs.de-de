---
title: 'Fehler &#39;: die Abhängigkeits&#39; Datei in &#39;Project&#39; Project kann nicht in das Verzeichnis "Run" kopiert werden, da &#39;Sie&#39; mit der Abhängigkeits Datei in Konflikt steht. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656046"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>&#39;Fehler: die Abhängigkeits&#39; Datei in &#39;Project&#39; Project kann nicht in das Lauf Verzeichnis kopiert werden, da Sie mit &#39;der Abhängigkeits Datei in Konflikt steht.&#39;
Es liegt ein Konflikt zwischen Verweisen vor: Mehrere unterschiedliche Abhängigkeiten mit demselben Dateinamen wurden in das Verzeichnis „bin“ für die auszuführende Anwendung kopiert. Das Ausführungsverzeichnis kann den Konflikt nicht lösen, da es sich bei den Abhängigkeiten nicht um Primärverweise handelt.

 Dieser Fehler führt dazu, dass der Build fehlschlägt.

 Wenn Sie auf dieses Aufgabenlistenelement doppelklicken, gelangen Sie zum Verweisknoten des Projekts, in dem der Konflikt auftritt.

 **So beheben Sie diesen Fehler**

- Richten Sie eine der Assemblys als direkten Verweis auf das Projekt ein. Ein möglicher Nachteil dabei ist jedoch, dass die ausgewählte Assembly nicht unbedingt mit Assemblys arbeitet, die eine andere Version der Assembly benötigen, auf die verwiesen wird.

     \- oder –

- Stellen Sie sicher, dass beide Kopien der Assembly einen starken Namen haben und sich im globalen Assemblycache befinden. Dadurch müssen die Assemblys nicht mehr in das Verzeichnis „bin“ kopiert werden.

## <a name="see-also"></a>Siehe auch
 [Verwalten von Verweisen in einem](../ide/managing-references-in-a-project.md) [globalen projektassemblycache](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) Assemblys mit [starkem Namen](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [Assemblys assemblyversionierung](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [How to: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)