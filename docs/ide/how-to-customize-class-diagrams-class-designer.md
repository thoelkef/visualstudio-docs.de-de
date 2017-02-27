---
title: "How to: Customize Class Diagrams (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "class diagrams, customizing"
  - "shapes, removing type from class diagrams"
  - "type shapes, removing from class diagrams"
  - "class diagrams, removing type shapes"
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# How to: Customize Class Diagrams (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Art und Weise ändern, in der in Klassendiagrammen Informationen angezeigt werden.  Sie können das gesamte Diagramm oder die einzelnen Typen auf der Entwurfsoberfläche anpassen.  
  
 Beispielsweise können Sie den Zoomfaktor eines gesamten Klassendiagramms einstellen, die Gruppierung und Sortierung einzelner Typmember ändern, Beziehungen anzeigen oder ausblenden, und einzelne Typen oder mehrere Typen gemeinsam an eine beliebige Position auf dem Diagramm verschieben.  
  
> [!NOTE]
>  Durch das Anpassen der Art und Weise, wie Formen im Diagramm angezeigt werden, wird der zugrunde liegende Code für die im Diagramm angezeigten Typen nicht geändert.  
  
 Abschnitte, die Typmember enthalten, wie beispielsweise der Abschnitt "Eigenschaften" in einer Klasse, werden als Depots bezeichnet.  Sie können einzelne Depots und Typmember anzeigen oder ausblenden.  
  
 **In diesem Thema**  
  
-   [Vergrößern und Verkleinern der Ansicht des Klassendiagramms](../ide/how-to-customize-class-diagrams-class-designer.md#ZoomInOut)  
  
-   [Anpassen der Gruppierung und Sortierung von Typmembern](../ide/how-to-customize-class-diagrams-class-designer.md#CustomizeGroupingSorting)  
  
-   [Ausblenden von Depots für einen Typ](../ide/how-to-customize-class-diagrams-class-designer.md#HideCompartments)  
  
-   [Ausblenden einzelner Member für einen Typ](../ide/how-to-customize-class-diagrams-class-designer.md#HideMembers)  
  
-   [Anzeigen ausgeblendeter Depots und Member für einen Typ](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayHiddenCompartmentsAndMemberrs)  
  
-   [Ausblenden von Beziehungen](../ide/how-to-customize-class-diagrams-class-designer.md#HideAssociationAndInheritance)  
  
-   [Anzeigen ausgeblendeter Beziehungen](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayAssociationAndInheritance)  
  
-   [Entfernen einer Typform aus einem Klassendiagramm](../ide/how-to-customize-class-diagrams-class-designer.md#RemoveCodeAndShape)  
  
-   [Löschen einer Typform und des zugrunde liegenden Codes](../ide/how-to-customize-class-diagrams-class-designer.md#DeleteTypeShapeAndCode)  
  
##  <a name="ZoomInOut"></a> Vergrößern und Verkleinern der Ansicht des Klassendiagramms  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie auf der Klassen\-Designer Symbolleiste auf die Schaltfläche **Vergrößern** oder **Verkleinern**, um den Zoomfaktor der Designeroberfläche zu ändern.  
  
     oder  
  
     Geben Sie einen bestimmten Zoomwert an.  Sie können die Dropdownliste **Zoom** verwenden oder einen gültigen Zoomfaktor \(der gültige Bereich ist 10 % bis 400 %\) eingeben.  
  
    > [!NOTE]
    >  Das Ändern des Zoomfaktors wirkt sich nicht auf die Skalierung des ausgedruckten Klassendiagramms aus.  
  
##  <a name="CustomizeGroupingSorting"></a> Anpassen der Gruppierung und Sortierung von Typmembern  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf einen leeren Bereich auf der Entwurfsoberfläche, und zeigen Sie auf **Member gruppieren**.  
  
3.  Wählen Sie eine der verfügbaren Optionen aus:  
  
    1.  **Nach Art gruppieren** unterteilt einzelne Typmember in eine gruppierte Liste von Eigenschaften, Methoden, Ereignissen und Feldern.  Die einzelnen Gruppen hängen von der Entitätendefinition ab: Beispielsweise wird in einer Klasse keine Gruppe von Ereignissen angezeigt, wenn noch keine Ereignisse für diese Klasse definiert sind.  
  
    2.  **Nach Zugriff gruppieren** unterteilt einzelne Typmember auf der Grundlage der Zugriffsmodifizierer des Members in eine gruppierte Liste.  Beispiel: Public und Private.  
  
    3.  **Alphabetisch sortieren** zeigt die Elemente, aus denen eine Entität besteht, als einzelne alphabetisch sortierte Liste an.  Die Liste ist in aufsteigender Reihenfolge sortiert.  
  
##  <a name="HideCompartments"></a> Ausblenden von Depots für einen Typ  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Memberkategorie in dem Typ, die Sie anpassen möchten \(wählen Sie z. B. den Knoten **Methoden** in einer Klasse aus\).  
  
3.  Klicken Sie auf **Depot ausblenden**.  
  
     Das ausgewählte Depot wird im Typcontainer ausgeblendet.  
  
##  <a name="HideMembers"></a> Ausblenden einzelner Member für einen Typ  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie mit der rechten Maustaste in dem Typ auf den Member, den Sie ausblenden möchten.  
  
3.  Klicken Sie auf **Ausblenden**.  
  
     Der ausgewählte Member wird im Typcontainer ausgeblendet.  
  
##  <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Anzeigen ausgeblendeter Depots und Member für einen Typ  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Namen des Typs mit dem ausgeblendeten Depot.  
  
3.  Klicken Sie auf **Alle Member anzeigen**.  
  
     Alle ausgeblendeten Depots und Member werden im Typcontainer angezeigt.  
  
##  <a name="HideAssociationAndInheritance"></a> Ausblenden von Beziehungen  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Zuordnungs\- oder Vererbungszeile, die Sie ausblenden möchten.  
  
3.  Klicken Sie für Zuordnungszeilen auf **Ausblenden**, und klicken Sie für Vererbungszeilen auf **Vererbungszeile ausblenden**.  
  
4.  Klicken Sie auf **Alle Member anzeigen**.  
  
     Alle ausgeblendeten Depots und Member werden im Typcontainer angezeigt.  
  
##  <a name="DisplayAssociationAndInheritance"></a> Anzeigen ausgeblendeter Beziehungen  
  
1.  Öffnen Sie eine Klassendiagrammdatei im Klassen\-Designer, und wählen Sie sie aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Typ mit der ausgeblendeten Zuordnung oder Vererbung.  
  
 Klicken Sie für Zuordnungszeilen auf **Alle Member anzeigen**, und klicken Sie für Vererbungszeilen auf **Basisklasse anzeigen** oder **Abgeleitete Klassen anzeigen**.  
  
##  <a name="RemoveCodeAndShape"></a> Entfernen einer Typform aus einem Klassendiagramm  
 Sie können eine Typform aus dem Klassendiagramm entfernen, ohne dass dies Auswirkungen auf den zugrunde liegenden Code des Typs hat.  Das Entfernen von Typformen aus einem Klassendiagramm wirkt sich nur auf das jeweilige Diagramm aus. Der zugrunde liegende Code, der den Typ definiert, und andere Diagramme, die den Typ anzeigen, sind nicht betroffen.  
  
1.  Wählen Sie im Klassendiagramm die aus dem Diagramm zu entfernende Typform aus.  
  
2.  Klicken Sie im Menü **Bearbeiten** auf **Aus Diagramm entfernen**.  
  
     Die Typform und sämtliche mit der Form verbundene Assoziations\- oder Vererbungslinien werden aus dem Diagramm entfernt.  
  
##  <a name="DeleteTypeShapeAndCode"></a> Löschen einer Typform und des zugrunde liegenden Codes  
  
1.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf die Form.  
  
2.  Wählen Sie im Kontextmenü die Option **Code löschen**.  
  
     Die Form wird aus dem Diagramm entfernt, und der zugrunde liegende Code wird aus dem Projekt gelöscht.  
  
## Siehe auch  
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)   
 [How to: Change Between Member Notation and Association Notation \(Class Designer\)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../ide/how-to-view-existing-types-class-designer.md)   
 [Viewing Types and Relationships \(Class Designer\)](../ide/viewing-types-and-relationships-class-designer.md)