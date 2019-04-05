---
title: 'Warnung: die Abhängigkeit &#39;Datei&#39; im Projekt &#39;Projekt&#39; kann nicht in das Ausführungsverzeichnis kopiert werden, da sie den Verweis überschreiben würde &#39;Datei. &#39; | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a97dfc6e7f93602b50102da51127fff6169ac3dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957397"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Warnung: die Abhängigkeit &#39;Datei&#39; im Projekt &#39;Projekt&#39; kann nicht in das Ausführungsverzeichnis kopiert werden, da sie den Verweis überschreiben würde &#39;Datei.&#39;
Es liegt ein Konflikt zwischen Abhängigkeiten vor: Mehrere unterschiedliche Assemblydateien mit demselben Dateinamen sollen in das Verzeichnis „bin“ für die auszuführende Anwendung kopiert werden. Das Ausführungsverzeichnis kann den Konflikt lösen, da es sich bei einer der Abhängigkeiten um einen Primärverweis handelt.  
  
 Durch Doppelklicken auf dieses Aufgabenlistenelement gelangen Sie zu dem den Konflikt auslösenden Primärverweisknoten.  
  
 Diese Warnung tritt auf, wenn Sie einen Abhängigkeitskonflikt haben, den Sie jedoch umgehen konnten, indem Sie eine der in Konflikt stehenden Abhängigkeiten als Verweis hinzufügen. Möglicherweise hatten Sie einen Version 1-Verweis und dann einen zweiten Verweis hinzugefügt, der wiederum auf Version 2 des ersten Verweises verweist.  
  
 D. h. dieser Fehler tritt auf, weil die Projekte in der Projektmappe aufeinander verweisen, wobei die Verweise jedoch als Dateiverweise erstellt wurden (mithilfe der Schaltfläche **Durchsuchen** im Dialogfeld [Verweis hinzufügen](http://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ), anstatt als Verweise zwischen Projekten (mithilfe der Registerkarte **Projekt** im Dialogfeld **Verweis hinzufügen** ). Der Vorteil eines Verweises zwischen Projekten besteht darin, dass eine Abhängigkeit zwischen den Projekten im Buildsystem erstellt wird, sodass das abhängige Projekt erstellt wird, wenn es sich seit der letzten Erstellung des verweisenden Projekts geändert hat. Bei Dateiverweisen wird keine Buildabhängigkeit erstellt, d. h., das verweisende Projekt kann ohne Erstellen des abhängigen Projekts erstellt werden, sodass der Verweis veraltet sein kann. Ein Projekt kann auf eine zuvor erstellte Version des Projekts verweisen. Dies kann dazu führen, dass im BIN-Verzeichnis mehrere Versionen einer einzigen DLL erforderlich sind, was jedoch nicht möglich ist. Dies führt dann letztendlich zu dieser Fehlermeldung.  
  
 Diese Meldung wird jedes Mal, wenn ein Konflikt im Bin-Verzeichnis vorliegt und die Anwendung möglicherweise nicht ordnungsgemäß ausgeführt werden kann. Auch wenn Sie dieses Problem umgangen haben, wird diese Warnung weiterhin angezeigt, da das Projektsystem nicht bestimmen kann, ob die Version einer Abhängigkeit mit allen Komponenten ordnungsgemäß funktioniert.  
  
 **Um diesen Fehler zu beheben**  
  
-   Kopieren Sie eine (oder keine) Assemblydatei in das Bin-Verzeichnis, indem Sie die Assemblydateien im globalen Assemblycache ablegen. Der globale Assemblycache löst Konflikte aufgrund von Dateinamen. Es werden keine lokalen Kopien der Assemblydatei angelegt, da die Common Language Runtime weiß, wie sie Assemblys im globalen Assemblycache finden kann. Weitere Informationen finden Sie unter [Working with Assemblies and the Global Assembly Cache](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) und [Error: the dependency 'file' in project 'project' cannot be copied to the run directory because it would conflict with dependency 'file'](/visualstudio/misc/error-dependency-file?view=vs-2015).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [Globaler Assemblycache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Vorgehensweise: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)