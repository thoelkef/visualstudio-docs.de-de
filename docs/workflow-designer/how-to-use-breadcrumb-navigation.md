---
title: "Vorgehensweise: Verwenden der Brotkr&#252;melnavigation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Vorgehensweise: Verwenden der Brotkr&#252;melnavigation
Es gibt drei Hauptmethoden, den Satz von Aktivitäten zu ändern, der in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] angezeigt wird:  
  
1.  Doppelklicken Sie, um in zu einer untergeordneten Aktivität zu wechseln.  
  
2.  Klicken Sie auf eine Schaltfläche auf der Breadcrumb\-Leiste, um zu einer Vorgängeraktivität zu navigieren.  
  
3.  Erweitern oder reduzieren Sie Aktivitäten.  
  
### Verwenden der Brotkrümelnavigation  
  
1.  Doppelklicken Sie auf eine Aktivität in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], um die Stammaktivität in die betreffende Aktivität zu ändern.Die Aktivität, auf die Sie geklickt haben, wird am Stamm vollständig erweitert, und ihre Vorgänger werden in der Breadcrumb\-Leiste angezeigt.Gelegentlich wird dies auch Durchführen von Drillout bzw. Drillinto bei einer Aktivität genannt.  
  
2.  Um zu einem Vorgänger der aktuellen Stammaktivität zu navigieren, klicken Sie auf die Aktivität in der Breadcrumb\-Leiste.  
  
### Erweitern oder Reduzieren einer Aktivität an Ort und Stelle  
  
1.  Wenn Sie auf die Chevrons neben einer Aktivität klicken, wird die betreffende Aktivität an Ort und Stelle erweitert bzw. reduziert.  
  
2.  Wenn der Erweiterungszustand durch Klicken auf die Schaltfläche geändert wird, dann wird der neue Erweiterungszustand in XAML gespeichert.  
  
    > [!WARNING]
    >  Nicht alle Aktivitäten können an Ort und Stelle erweitert werden.Es gibt zwei Fälle, in denen eine Aktivität nicht an Ort und Stelle erweitert werden kann: wenn das übergeordnete Element der Aktivität es nicht zulässt, dass seine untergeordneten Elementen an Ort und Stelle erweitert werden, \(Aktivitäten in einem Flussdiagramm können z. B. nicht an Ort und Stelle erweitert werden\), und wenn der Aktivitätsdesigner nicht an Ort und Stelle erweitert werden kann.Obwohl kein Aktivitätsdesigner, der in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] enthalten ist, das oben beschriebene Verhalten aufweist, können einige benutzerdefinierte Aktivitäten dieses Verhalten zeigen.  
  
### Erweitern oder Reduzieren aller Aktivitäten  
  
1.  Verwenden Sie die Schaltfläche **Alle erweitern** und  **Alle reduzieren** der Benutzeroberfläche, um alle Aktivitäten unter dem aktuellen Breadcrumbstamm zu erweitern oder zu reduzieren.Beachten Sie, dass es sich bei "Alle erweitern" und "Alle reduzieren" um globale Zustände handelt.Dies bedeutet, dass bei einer Änderung der Stammaktivität mithilfe der Breadcrumbnavigation der Zustand "Alle erweitern" oder "Alle reduzieren" erhalten bleibt, bis Sie auf **Wiederherstellen** klicken.  
  
2.  Nachdem Sie Zustand "Alle erweitern" oder "Alle reduzieren" herbeigeführt haben, können Sie auf die Schaltfläche **Wiederherstellen** klicken, die den Zustand wiederherstellt, der zuvor für die einzelnen Aktivitäten übernommen wurde.  
  
    > [!WARNING]
    >  Wenn eine Aktivität, z. B. <xref:System.Activities.Statements.Flowchart>, nicht an Ort und Stelle erweiterbar ist, dann wird die den Schaltflächen **Alle erweitern** und **Alle reduzieren** zugeordnete Funktionalität im **Flowchart**\-Designer deaktiviert.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zum **Flowchart**\-Designer finden Sie im Thema [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md).  
  
    > [!WARNING]
    >  Im **Switch**\-Aktivitätsdesigner und im **TryCatch**\-Aktivitätsdesigner hat "Alles erweitern" überdies einen Spezialeffekt.Wenn Sie auf **Alle erweitern** klicken, werden alle switch\-Fälle und alle try\/catch\/finally\-Blöcke angezeigt.Durch Klicken auf **Wiederherstellen** oder **Alle reduzieren** werden diese Designer wieder auf ihren Standardzustand zurückgesetzt, in dem Sie auf einen einzelnen Fall bzw. Block klicken können, um seinen Inhalt anzuzeigen.