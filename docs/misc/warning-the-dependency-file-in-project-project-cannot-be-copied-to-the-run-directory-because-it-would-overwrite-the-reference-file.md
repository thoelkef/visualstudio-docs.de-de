---
title: "Fehler: Die Abh&#228;ngigkeit &quot;Datei&quot; in Projekt &quot;Projekt&quot; kann nicht in das Ausf&#252;hrungsverzeichnis kopiert werden, da sie den Verweis &quot;Datei&quot; &#252;berschreiben w&#252;rde | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_warning"
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Fehler: Die Abh&#228;ngigkeit &quot;Datei&quot; in Projekt &quot;Projekt&quot; kann nicht in das Ausf&#252;hrungsverzeichnis kopiert werden, da sie den Verweis &quot;Datei&quot; &#252;berschreiben w&#252;rde
Es liegt ein Konflikt zwischen Abhängigkeiten vor: Mehrere unterschiedliche Assemblydateien mit demselben Dateinamen sollen in das Verzeichnis „bin“ für die auszuführende Anwendung kopiert werden. Das Ausführungsverzeichnis kann den Konflikt lösen, da es sich bei einer der Abhängigkeiten um einen Primärverweis handelt.  
  
 Durch Doppelklicken auf dieses Aufgabenlistenelement gelangen Sie zu dem den Konflikt auslösenden Primärverweisknoten.  
  
 Diese Warnung tritt auf, wenn Sie einen Abhängigkeitskonflikt haben, den Sie jedoch umgehen konnten, indem Sie eine der in Konflikt stehenden Abhängigkeiten als Verweis hinzufügen. Möglicherweise hatten Sie einen Version 1\-Verweis und dann einen zweiten Verweis hinzugefügt, der wiederum auf Version 2 des ersten Verweises verweist.  
  
 D. h. dieser Fehler tritt auf, weil die Projekte in der Projektmappe aufeinander verweisen, wobei die Verweise jedoch als Dateiverweise erstellt wurden \(mithilfe der Schaltfläche **Durchsuchen** im Dialogfeld [Verweis hinzufügen](http://msdn.microsoft.com/de-de/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)\), anstatt als Verweise zwischen Projekten \(mithilfe der Registerkarte **Projekt** im Dialogfeld **Verweis hinzufügen**\). Der Vorteil eines Verweises zwischen Projekten besteht darin, dass eine Abhängigkeit zwischen den Projekten im Buildsystem erstellt wird, sodass das abhängige Projekt erstellt wird, wenn es sich seit der letzten Erstellung des verweisenden Projekts geändert hat. Bei Dateiverweisen wird keine Buildabhängigkeit erstellt, d. h., das verweisende Projekt kann ohne Erstellen des abhängigen Projekts erstellt werden, sodass der Verweis veraltet sein kann. Ein Projekt kann auf eine zuvor erstellte Version des Projekts verweisen. Dies kann dazu führen, dass im BIN\-Verzeichnis mehrere Versionen einer einzigen DLL erforderlich sind, was jedoch nicht möglich ist. Dies führt dann letztendlich zu dieser Fehlermeldung.  
  
 Diese Meldung wird jedes Mal, wenn ein Konflikt im Bin\-Verzeichnis vorliegt und die Anwendung möglicherweise nicht ordnungsgemäß ausgeführt werden kann. Auch wenn Sie dieses Problem umgangen haben, wird diese Warnung weiterhin angezeigt, da das Projektsystem nicht bestimmen kann, ob die Version einer Abhängigkeit mit allen Komponenten ordnungsgemäß funktioniert.  
  
 **So beheben Sie diesen Fehler**  
  
-   Kopieren Sie eine \(oder keine\) Assemblydatei in das Bin\-Verzeichnis, indem Sie die Assemblydateien im globalen Assemblycache ablegen. Der globale Assemblycache löst Konflikte aufgrund von Dateinamen. Es werden keine lokalen Kopien der Assemblydatei angelegt, da die Common Language Runtime weiß, wie sie Assemblys im globalen Assemblycache finden kann. Weitere Informationen finden Sie unter [Arbeiten mit Assemblys und dem globalen Assemblychache](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md) und [Fehler: Die Abhängigkeit "Datei" in Projekt "Projekt" kann nicht in das Ausführungsverzeichnis kopiert werden, da sie mit Abhängigkeit "Datei" in Konflikt stehen würde](../misc/error-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-file.md).  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [Globaler Assemblycache](../Topic/Global%20Assembly%20Cache.md)   
 [Gewusst wie: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)