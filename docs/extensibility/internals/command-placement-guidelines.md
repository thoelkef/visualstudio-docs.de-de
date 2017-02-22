---
title: "Richtlinien zur Platzierung Befehl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, kleine Befehlssätze"
  - "kleine Befehlssätze"
  - "Befehlssätze"
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Richtlinien zur Platzierung Befehl
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bewährte Methoden für die Positionierung von Befehlen in der Visual Studio\-IDE \(IDE\) variieren abhängig von der Größe des Befehlssatzes. Befehle sind definiert, und entsprechend den Informationen in der VSCT\-Dateien positioniert.  
  
## Bewährte Methoden für alle Befehlssätze  
 Für jeden Satz von Befehlen die Richtlinien Sie folgenden aus:  
  
-   Bereiten Sie ein Diagramm mit der Befehlsstruktur im voraus. Identifizieren Sie die Befehle, Kombinationsfelder, Befehlsgruppen und Kontextmenüs, die in mehreren Speicherorten verwendet werden.  
  
-   Befehle in der gleichen Gruppe sollte verknüpft sein.  
  
-   Gruppen, die nur einen Befehl enthalten sind zulässig.  
  
-   Pakete sollten nicht viele Befehle für vorhandene Visual Studio\-Menüs hinzufügen. Stattdessen erstellen sie Menüs oder Untermenüs, um die neuen Befehle zu hosten.  
  
-   Wenn Sie einen Befehl auf einem vorhandenen Menü, Name des Befehls platzieren, zwecks deaktiviert und nicht mit vorhandenen verwechselt werden wird.  
  
## Bewährte Methoden für kleine Befehlssätze  
 Wenn Sie ein VSPackage, die nur wenige Befehle enthalten sind entwickeln, gelten Sie auch folgende Richtlinien:  
  
-   Verwenden Sie nach Möglichkeit die [Parent\-Element](../../extensibility/parent-element.md) eines Befehls, Kombinationsfeld, Gruppe oder Untermenü in die entsprechende Gruppe abzulegen.  
  
-   Weisen Sie diese Gruppen angezeigt, wenn das VSPackage Menüs zu.  
  
-   Das übergeordnete Element eines untergeordneten Menüs oder eines Befehls muss ein [Group\-Element](../../extensibility/group-element.md). Weisen Sie Befehle und Menüs des untergeordneten Gruppen zu, und weisen Sie die Gruppen dann den übergeordneten Menüs.  
  
-   Sie können einen Befehl in zusätzliche Gruppen einfügen, durch Hinzufügen einer [CommandPlacements\-Element](../../extensibility/commandplacements-element.md) im Abschnitt nach der Definition des Befehls, und klicken Sie dann auf Hinzufügen die `CommandPlacements Element` eine [CommandPlacement\-Element](../../extensibility/commandplacement-element.md) für jede zusätzliche Gruppe.  
  
## Best Practices für große Befehlssätze  
 Wenn Ihr VSPackage viele Befehle verfügen, die in mehreren Kontexten angezeigt werden, gelten Sie auch folgende Richtlinien:  
  
-   Stellen Sie die Menüs, Gruppen und Befehle, die selbst Überordnung. D. h. weisen eine `Parent Element` in der Definition des Elements.  
  
-   Verwendung `CommandPlacement Element` Einträge in der `CommandPlacements Element` Abschnitt, Menüs, Gruppen und Befehle in ihrer übergeordneten Menüs und Gruppen zu speichern.  
  
-   In der `CommandPlacements` im Abschnitt, der Einträge, die einem bestimmten Menü Auffüllen oder Gruppe werden nebeneinander an. Dies unterstützt die Lesbarkeit und macht die `Priority` Rangfolgen einfacher zu bestimmen.  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)