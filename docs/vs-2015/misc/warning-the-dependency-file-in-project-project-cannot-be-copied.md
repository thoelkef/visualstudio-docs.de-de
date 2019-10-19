---
title: '&#39;Warnung: die Abhängigkeits&#39; Datei in &#39;Project&#39; Project kann nicht in das Lauf Verzeichnis kopiert werden, da Sie die &#39;Verweis Datei überschreiben würde. &#39; | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a619168bd07fde5d27e5c3d87dc46f505cf5268d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672816"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>&#39;Warnung: die Abhängigkeits&#39; Datei in &#39;Project&#39; Project kann nicht in das Lauf Verzeichnis kopiert werden, da Sie die &#39;Verweis Datei überschreiben würde.&#39;
Es liegt ein Konflikt zwischen Abhängigkeiten vor: Mehrere unterschiedliche Assemblydateien mit demselben Dateinamen sollen in das Verzeichnis „bin“ für die auszuführende Anwendung kopiert werden. Das Ausführungsverzeichnis kann den Konflikt lösen, da es sich bei einer der Abhängigkeiten um einen Primärverweis handelt.

 Durch Doppelklicken auf dieses Aufgabenlistenelement gelangen Sie zu dem den Konflikt auslösenden Primärverweisknoten.

 Diese Warnung tritt auf, wenn Sie einen Abhängigkeitskonflikt haben, den Sie jedoch umgehen konnten, indem Sie eine der in Konflikt stehenden Abhängigkeiten als Verweis hinzufügen. Möglicherweise hatten Sie einen Version 1-Verweis und dann einen zweiten Verweis hinzugefügt, der wiederum auf Version 2 des ersten Verweises verweist.

 D. h. dieser Fehler tritt auf, weil die Projekte in der Projektmappe aufeinander verweisen, wobei die Verweise jedoch als Dateiverweise erstellt wurden (mithilfe der Schaltfläche **Durchsuchen** im Dialogfeld [Verweis hinzufügen](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ), anstatt als Verweise zwischen Projekten (mithilfe der Registerkarte **Projekt** im Dialogfeld **Verweis hinzufügen** ). Der Vorteil eines Verweises zwischen Projekten besteht darin, dass eine Abhängigkeit zwischen den Projekten im Buildsystem erstellt wird, sodass das abhängige Projekt erstellt wird, wenn es sich seit der letzten Erstellung des verweisenden Projekts geändert hat. Bei Dateiverweisen wird keine Buildabhängigkeit erstellt, d. h., das verweisende Projekt kann ohne Erstellen des abhängigen Projekts erstellt werden, sodass der Verweis veraltet sein kann. Ein Projekt kann auf eine zuvor erstellte Version des Projekts verweisen. Dies kann dazu führen, dass im BIN-Verzeichnis mehrere Versionen einer einzigen DLL erforderlich sind, was jedoch nicht möglich ist. Dies führt dann letztendlich zu dieser Fehlermeldung.

 Diese Meldung wird jedes Mal, wenn ein Konflikt im Bin-Verzeichnis vorliegt und die Anwendung möglicherweise nicht ordnungsgemäß ausgeführt werden kann. Auch wenn Sie dieses Problem umgangen haben, wird diese Warnung weiterhin angezeigt, da das Projektsystem nicht bestimmen kann, ob die Version einer Abhängigkeit mit allen Komponenten ordnungsgemäß funktioniert.

 **So beheben Sie diesen Fehler**

- Kopieren Sie eine (oder keine) Assemblydatei in das Bin-Verzeichnis, indem Sie die Assemblydateien im globalen Assemblycache ablegen. Der globale Assemblycache löst Konflikte aufgrund von Dateinamen. Es werden keine lokalen Kopien der Assemblydatei angelegt, da die Common Language Runtime weiß, wie sie Assemblys im globalen Assemblycache finden kann. Weitere Informationen finden Sie unter [Working with Assemblies and the Global Assembly Cache](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) und [Error: the dependency 'file' in project 'project' cannot be copied to the run directory because it would conflict with dependency 'file'](/visualstudio/misc/error-dependency-file?view=vs-2015).

## <a name="see-also"></a>Siehe auch
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md) [globalen Assemblycache](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) Gewusst [wie: Erstellen und Entfernen von Projekt Abhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)