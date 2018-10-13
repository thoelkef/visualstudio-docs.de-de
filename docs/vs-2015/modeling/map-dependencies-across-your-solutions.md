---
title: Projektmappenübergreifendes Zuordnen von Abhängigkeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: ae5e9491b8a02293a48a3ccc3e5e21a87fa5e878
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200771"
---
# <a name="map-dependencies-across-your-solutions"></a>Projektmappenübergreifendes Zuordnen von Abhängigkeiten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Abhängigkeiten innerhalb Ihres Codes verstehen möchten, stellen Sie diese visuell dar, indem Sie Code Maps erstellen. Dadurch können Sie sehen, wie der Code ohne Lesen von Codezeilen und Dateien zusammenpasst.  
  
 ![Anzeigen von Abhängigkeiten in Ihren Lösungen](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **Hier finden Sie einige Videos**:  
  
-   [Verstehen der Codeabhängigkeiten durch Visualisierung](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
-   [Visualisieren der Auswirkungen einer Änderung](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
-   [Nachvollziehen komplexen Codes mit Code Maps](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
##  <a name="GetStarted"></a> Erste Schritte mit Code Maps  
 **Zur Verwendung von Code Maps benötigen Sie abhängig von Ihrer Visual Studio-Version**:  
  
-   Visual Studio Enterprise: Erstellen Sie Code Maps im Code-Editor, im Projektmappen-Explorer, in der Klassenansicht oder im Objektbrowser.  
  
-   Visual Studio Professional: Öffnen Sie Code Maps, nehmen Sie eingeschränkte Bearbeitungen vor, und navigieren Sie im Code.  
  
> [!WARNING]
>  Vergewissern Sie sich, dass alle Elemente in der Code Map (beispielsweise ausgeblendete Elemente, erweiterte Gruppen und gruppenübergreifende Links) sichtbar sind, bevor Sie in Visual Studio Enterprise erstellte Code Maps für Benutzer von Visual Studio Professional freigeben.  
  
 **Codeabhängigkeiten können in folgenden Sprachen durch Code Maps dargestellt werden**:  
  
-   Visual C# .NET oder Visual Basic .NET in einer Projektmappe oder in Assemblys (.dll oder .exe)  
  
-   Den systemeigenen oder verwalteten C oder C++-Code in Visual C++-Projekten, Headerdateien (.h oder `#include`) oder Binärdateien  
  
-   Aus .NET-Modulen für Microsoft Dynamics AX erstellte X++-Projekte und X++-Assemblydateien  
  
 **Hinweis:** Für andere als C#- oder Visual Basic .NET-Projekte sind weniger Optionen zum Starten einer Code Map oder zum Hinzufügen von Elementen zu einer vorhanden Code Map verfügbar. Beispielweise können Sie nicht mit der rechten Maustaste auf ein Objekt im Text-Editor eines C++-Projekts klicken, es einer Code Map hinzuzufügen. Sie können jedoch einzelne Codeelemente oder Dateien per Drag & Drop aus dem Projektmappen-Explorer, der Klassenansicht und dem Objektbrowser verschieben.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>So zeigen Sie die allgemeinen Abhängigkeiten in einer Projektmappe an  
  
1.  Öffnen Sie das Menü **Architektur** .  
  
2.  Wenn Sie die Projektmappe bisher nur geöffnet und noch nicht erstellt haben, oder wenn sich der Code seit der letzten Erstellung geändert hat, wählen Sie **Code Map für Projektmappe generieren**aus.  
  
3.  Wenn sich der Code seit der letzten Erstellung nicht geändert hat, wählen Sie **Code Map für Projektmappe ohne Erstellung generieren** aus, um das Erstellen der Code Map zu beschleunigen.  
  
4.  Unter[Erkennen allgemeiner Abhängigkeiten](#SeeOverviewSource) wird erläutert, wie Sie Code Maps verwenden können, um die allgemeinen Abhängigkeiten in einer Projektmappe anzuzeigen.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>So zeigen Sie spezifische Abhängigkeiten in einer Projektmappe an  
  
1.  Laden Sie die Projektmappe, und öffnen Sie den **Projektmappen-Explorer**.  
  
2.  Wählen Sie alle Projekte, Assemblyverweise, Ordner, Dateien, Typen oder Member aus, die Sie darstellen möchten.  
  
3.  Auf der **Projektmappen-Explorer** Symbolleiste wählen **auf Code Map anzeigen**![Schaltfläche neu erstellen Diagramms aus ausgewählten Knoten](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Alternativ öffnen Sie das Kontextmenü, und wählen Sie **Auf Code Map anzeigen**aus. Sie können auch Elemente aus der Klassenansicht oder dem Objektbrowser in eine neue oder vorhandene Code Map ziehen.  
  
4.  Unter[Erkennen allgemeiner Abhängigkeiten](#SeeSpecificSource) wird erläutert, wie Sie Code Maps verwenden können, um spezifische Abhängigkeiten innerhalb einer Projektmappe anzuzeigen.  
  
###  <a name="CreateEmptyMap"></a> So fügen Sie einer Projektmappe eine neue leere Code Map hinzu  
  
1.  Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für den Projektmappenknoten auf oberster Ebene. Wählen Sie **Hinzufügen** und dann **Neues Element**aus.  
  
2.  Wählen Sie unter **Installiert**die Option **Allgemein**aus.  
  
3.  Wählen Sie im rechten Bereich **Dokument mit gerichtetem Diagramm** und dann **Hinzufügen**aus.  
  
     Sie verfügen nun über eine leere Code Map, die im Ordner **Projektmappenelemente** der Projektmappe angezeigt wird.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>So erstellen Sie eine neue leere Code Map, ohne sie der Projektmappe hinzuzufügen  
  
1.  Öffnen Sie das Menü **Architektur** , und wählen Sie die Option **Neue Code Map**aus.  
  
     \- oder –  
  
2.  Öffnen Sie das Menü **Datei** , und wählen Sie **Neu** und dann **Datei**aus.  
  
3.  Wählen Sie unter **Installiert**die Option **Allgemein**aus.  
  
4.  Wählen Sie im rechten Bereich **Dokument mit gerichtetem Diagramm** und dann **Öffnen**aus.  
  
     Sie verfügen nun über eine leere Code Map, die nicht in den Ordnern der Projektmappe angezeigt wird.  
  
##  <a name="SeeOverviewSource"></a> Erkennen allgemeiner Abhängigkeiten  
  
###  <a name="OverviewSource"></a> Erkennen von Abhängigkeiten innerhalb der Lösung  
  
1.  Wählen Sie im Menü **Architektur** die Option **Code Map für Projektmappe generieren**aus.  
  
     ![Generieren einer Code Map-Befehls](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
     Es wird eine Code Map erstellt, die die Assemblys der obersten Ebene und die Aggregatlinks zwischen diesen zeigt. Desto größer die Aggregatsverbindung, desto mehr Abhängigkeiten stellt sie dar.  
  
2.  Mit der Schaltfläche **Legende** auf der Symbolleiste der Code Map können Sie die Liste der Projekttypsymbole (z. B. Test, Web und Phone-Projekt), der Codeelemente (z. B. Klassen, Methoden und Eigenschaften) sowie der Beziehungstypen (z. B. Erbt von, Implementiert und Aufrufe) anzeigen oder ausblenden.  
  
     ![Top&#45;Ebene Abhängigkeitsdiagramm der Assemblys](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
     Diese Beispielprojektmappe enthält Projektmappenordner (**Tests** und **Komponenten**), Testprojekte, Webprojekte und Assemblys. Standardmäßig werden alle Einschlussbeziehungen als *Gruppen*dargestellt, die Sie erweitern und reduzieren können. Die Gruppe **Extern** enthält alle Elemente außerhalb der Projektmappe, einschließlich Plattformabhängigkeiten. Für externe Assemblys werden nur die Elemente angezeigt, die verwendet werden. Standardmäßig werden Systembasistypen auf der Code Map ausgeblendet, um die Übersichtlichkeit zu verbessern.  
  
3.  Um einen Drilldown in der Code Map durchzuführen, erweitern Sie die Gruppen, die Projekte und Assemblys darstellen. Sie können alle Gruppen erweitern, indem Sie durch Drücken von **STRG + A** alle Knoten auswählen und dann **Gruppe**, **Erweitern** im Kontextmenü auswählen.  
  
     ![Erweitern aller Gruppen in einer Code Map](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4.  Allerdings ist dieses Verfahren für große Projektmappen nicht unbedingt hilfreich. Tatsächlich können Sie bei komplexen Projektmappen aufgrund von Speicherbeschränkungen möglicherweise nicht alle Gruppen erweitern. Erweitern Sie in diesem Fall einen einzelnen Knoten, um seinen Inhalt anzuzeigen. Bewegen Sie den Mauszeiger auf einen Knoten, und klicken Sie dann auf das Chevron (Abwärtspfeil), wenn es angezeigt wird.  
  
     ![Erweitern eines Knotens in einer Code Map](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     Alternativ können Sie die Tastatur verwenden, indem Sie das Element auswählen und dann die Plus-Taste (**+**) drücken. Gehen Sie bei Namespaces, Typen und Mitglieder genauso vor, um tiefere Ebenen des Codes untersuchen.  
  
    > [!TIP]
    >  Weitere Informationen zum Arbeiten mit Code maps unter Verwendung den Maus, Tastatur und Toucheingabe finden Sie unter [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md).  
  
5.  Um die Code Map zu vereinfachen und sich auf einzelne Teile zu konzentrieren, wählen Sie **Filter** auf der Symbolleiste der Code Map aus, und wählen Sie dann nur die Knoten- und Linktypen aus, die für Sie von Interesse sind. Beispielsweise können Sie alle Projektmappenordner und Assemblycontainer ausblenden.  
  
     ![Vereinfachen der Zuordnung durch Filtern der Container](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
     Sie können die Code Map auch vereinfachen, indem Sie einzelne Gruppen und Elemente ausblenden oder aus der Code Map entfernen, ohne dass sich dies auf den zugrunde liegenden Projektmappencode auswirkt.  
  
6.  Um die Beziehungen zwischen Elementen anzuzeigen, wählen Sie die Elemente in der Code Map aus. Die Farben der Links zeigen die Beziehungstypen an, wie im Bereich **Legende** dargestellt.  
  
     ![Anzeigen von Abhängigkeiten in Ihren Lösungen](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
     In diesem Beispiel sind die violetten Links Aufrufe, die gepunkteten Links sind Verweise, und die hellblauen Links sind Feldzugriffe. Grüne Links können Vererbung darstellen, oder es kann sich um *Aggregatlinks* handeln, die mehrere Beziehungstypen (oder *Kategorien*) angeben.  
  
    > [!TIP]
    >  Wenn ein grüner Link angezeigt wird, muss dies nicht bedeuten, dass nur eine Vererbungsbeziehung besteht. Möglicherweise gibt es auch Methodenaufrufe, aber diese sind durch die Vererbungsbeziehung ausgeblendet. Um bestimmte Linktypen anzuzeigen, können Sie mit den Kontrollkästchen im Bereich **Filter** die Typen ausblenden, die für Sie nicht von Interesse sind.  
  
7.  Weitere Informationen zu einem Element oder einem Link erhalten Sie, indem Sie den Mauszeiger darauf bewegen und warten, bis eine QuickInfo angezeigt wird. Diese enthält Details zu einem Codeelement oder den Kategorien, die ein Link darstellt.  
  
     ![Anzeigen der Kategorien einer Beziehung](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8.  Wählen Sie zum Untersuchen von Elementen und Abhängigkeiten, die durch einen Aggregatlink dargestellt werden, zunächst den Link aus, und öffnen Sie dann das zugehörige Kontextmenü. Wählen Sie **Zugehörige Links anzeigen** (oder **Zugehörige Links auf neuer Code Map anzeigen**) aus. Hierdurch werden die Gruppen an beiden Enden des Links erweitert und nur die Elemente und Abhängigkeiten angezeigt, die zu dem Link gehören.  
  
9. Um sich auf bestimmte Teile der Code Map zu konzentrieren, können Sie weitere Elemente entfernen, an denen Sie nicht interessiert sind. Wenn Sie z. B. einen Drillinto für die Klassen- und Memberansicht ausführen möchten, filtern Sie einfach alle Namespaceknoten im Bereich **Filter** .  
  
     ![Drilldown auf Klassen-und Memberebene](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Eine andere Methode zum Fokussieren einer Code Map einer komplexen Projektmappe besteht darin, eine neue Code Map zu generieren, die ausgewählte Elemente aus einer vorhandenen Code Map enthält. Halten Sie **STRG** gedrückt, während Sie die Elemente auswählen, die Sie in den Fokus holen möchten, öffnen Sie das Kontextmenü, und wählen Sie **Neues Diagramm aus der Auswahl**aus.  
  
     ![Anzeigen der ausgewählten Elemente in einer neuen Code Map](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. Der enthaltende Kontext wird in die neue Code Map übernommen. Blenden Sie Projektmappenordner und andere Container, die nicht angezeigt werden sollen, mithilfe des Bereichs **Filter** aus.  
  
     ![Filtern der Container zum Vereinfachen der Ansicht](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Erweitern Sie die Gruppen, und wählen Sie Elemente in der Code Map aus, um die Beziehungen anzuzeigen.  
  
     ![Elemente auswählen, um die Anzeige der Beziehungen](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
 Siehe auch:  
  
-   [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   Ermitteln Sie potenzielle Probleme im Code durch [Ausführen einer Analyse](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
###  <a name="OverviewCompiled"></a> Finden Sie Abhängigkeiten zwischen Assemblys und Binärdateien  
  
1.  [Erstellen Sie eine leere Code Map](#GetStarted), oder öffnen Sie eine vorhandene Code Map (DGML-Datei).  
  
2.  Ziehen Sie die Assemblys oder Binärdateien, die Sie in der Code Map darstellen möchten, von einem Ort außerhalb von Visual Studio in die Code Map. Ziehen Sie z. B. Assemblys oder Binärdateien aus Windows-Explorer oder Datei-Explorer.  
  
> [!NOTE]
>  Das Ziehen von Assemblys oder Binärdateien aus Windows-Explorer oder Datei-Explorer ist nur möglich, wenn der betreffende Explorer und Visual Studio auf der gleichen Berechtigungsstufe der Benutzerkontensteuerung (User Account Control, UAC) ausgeführt werden. Beispiel: Wenn Sie Visual Studio bei aktivierter UAC als Administrator ausführen, wird der Ziehvorgang von Windows-Explorer oder Datei-Explorer blockiert. Zur Umgehung dieses Problems stellen Sie sicher, dass beide Programme mit der gleichen Berechtigungsstufe ausgeführt werden, oder deaktivieren Sie UAC.  
  
##  <a name="SeeSpecificSource"></a> Erkennen allgemeiner Abhängigkeiten  
 Angenommen, Sie müssen eine Codeüberprüfung in einigen Dateien mit ausstehenden Änderungen durchführen. Um die Abhängigkeiten in diesen Änderungen anzuzeigen, können Sie eine Code Map aus diesen Dateien erstellen.  
  
 ![Anzeigen bestimmter Abhängigkeiten in einer Code Map](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Anzeigen bestimmter Abhängigkeiten in Ihrer Projektmappe  
  
1.  Öffnen Sie den **Projektmappen-Explorer**. Wählen Sie die Projekte, Assemblyverweise, Ordner, Dateien, Typen und Mitglieder, die Sie interessieren. Zum Suchen von Elementen mit Abhängigkeiten von Typen oder Mitglied öffnen Sie das Kontextmenü für den Typ oder Mitglieder im **Projektmappen-Explorer**. Wählen Sie den Abhängigkeitstyp aus, und wählen Sie dann die Ergebnisse aus.  
  
2.  Stellen Sie die Elemente und ihre Member in einer Code Map dar. Auf der **Projektmappen-Explorer** Symbolleiste auf **auf Code Map anzeigen**![Schaltfläche neu erstellen Diagramms aus ausgewählten Knoten](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Wählen Sie die Elemente, die Sie zuordnen möchten](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  Die Code Map zeigt die ausgewählten Elemente in ihren enthaltenden Assemblys.  
  
     ![Ausgewählte Elemente als Gruppen in der Zuordnung](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     Sie können auch Elemente aus dem Projektmappen-Explorer, der Klassenansicht oder dem Objektbrowser in eine neue oder vorhandene Code Map ziehen. Anweisungen zum Erstellen einer leeren Code Map finden Sie unter [Erstellen einer leeren Code Map](#GetStarted). Um die übergeordnete Hierarchie für die Elemente einzuschließen, halten Sie die **STRG** -TASTE gedrückt, während Sie Elemente ziehen, oder verwenden Sie die Schaltfläche **Übergeordnete Elemente einschließen** auf der Symbolleiste der Code Map, um die Standardaktion anzugeben.  
  
    > [!NOTE]
    >  Wenn Sie Elemente aus einem Projekt hinzufügen, das von mehreren Apps wie Windows Phone oder Windows Store gemeinsam genutzt wird, werden diese Elemente mit dem derzeit aktiven App-Projekt in der Zuordnung angezeigt. Wenn Sie den Kontext für ein anderes App-Projekt ändern und mehrere Elemente aus dem freigegebenen Projekt hinzufügen, werden diese Elemente nun mit dem neuen aktiven App-Projekt angezeigt. Vorgänge, die Sie mit einem Element in der Zuordnung ausführen, gelten nur für solche Elemente, die denselben Kontext gemeinsam verwenden.  
  
4.  Um Elemente zu untersuchen, erweitern Sie diese. Bewegen Sie den Mauszeiger auf ein Element, und klicken Sie dann auf das Chevron (Abwärtspfeil), wenn es angezeigt wird.  
  
     ![Erweitern eines Knotens in einer Code Map](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     Um alle Elemente zu erweitern, wählen Sie diese mit **STRG + A**aus, öffnen Sie dann das Kontextmenü für die Code Map, und wählen Sie **Gruppe**, **Erweitern**aus. Diese Option ist jedoch nicht verfügbar, wenn das Erweitern aller Gruppen zu einer nicht verwendbaren Code Map oder zu Speicherproblemen führt.  
  
5.  Erweitern Sie weitere Elemente, die für Sie von Interesse sind, ggf. bis hinunter zur Klassen- und Memberebene.  
  
     ![Erweitern von Gruppen auf Klassen-und Memberebene](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Zum Anzeigen von Mitgliedern, die im Code, aber nicht angezeigt, auf der Karte, klicken Sie auf die **untergeordnete Elemente erneut abrufen** Symbol ![Symbol "untergeordnete" untergeordnete](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") oben Links von einer Gruppe.  
  
6.  Um weitere Elemente im Zusammenhang mit den auf der Code Map dargestellten anzuzeigen, wählen Sie ein Element aus, wählen Sie **Verwandte anzeigen** auf der Symbolleiste der Code Map aus, und wählen Sie dann den Typ verwandter Elemente aus, die der Code Map hinzugefügt werden sollen. Alternativ wählen Sie ein oder mehrere Elemente aus, öffnen Sie das Kontextmenü, und wählen Sie dann die Option **Anzeigen** für den Typ verwandter Elemente aus, die der Code Map hinzugefügt werden sollen. Zum Beispiel:  
  
     Für eine **Assembly**wählen Sie Folgendes aus:  
  
    |||  
    |-|-|  
    |**Assemblys anzeigen, auf die verwiesen wird**|Fügt Assemblys hinzu, auf die diese Assembly verweist. Externe Assemblys werden in der Gruppe **Extern** angezeigt.|  
    |**Assemblys anzeigen, die auf diese Funktion verweisen**|Fügt Assemblys in der Projektmappe hinzu, die auf diese Assembly verweisen.|  
  
     Für einen **Namespace**wählen Sie **Enthaltende Assembly anzeigen**aus, falls sie nicht sichtbar ist.  
  
     Für eine **Klasse** oder **Schnittstelle**wählen Sie Folgendes aus:  
  
    |||  
    |-|-|  
    |**Basistypen anzeigen**|Fügt einer Klasse die Basisklasse und die implementierten Schnittstellen hinzu.<br /><br /> Fügt einer Schnittstelle die Basisschnittstellen hinzu.|  
    |**Abgeleitete Typen anzeigen**|Fügt bei einer Klasse die abgeleiteten Klassen hinzu.<br /><br /> Fügt bei einer Schnittstelle die abgeleiteten Schnittstellen und die implementierenden Klassen oder Strukturen hinzu.|  
    |**Typen anzeigen, auf die verwiesen wird**|Fügt alle Klassen und deren Mitglieder hinzu, die diese Klasse verwendet.|  
    |**Typen anzeigen, die auf diese Funktion verweisen**|Fügt alle Klassen und deren Mitglieder hinzu, die diese Klasse verwenden.|  
    |**Enthaltenden Namespace anzeigen**|Fügt den übergeordneten Namespace hinzu.|  
    |**Enthaltende/n Namespace und Assembly anzeigen**|Fügt die übergeordnete Containerhierarchie hinzu.|  
    |**Alle Basistypen anzeigen**|Fügt die Basisklasse oder die Schnittstellenhierarchie rekursiv hinzu.|  
    |**Alle abgeleiteten Typen anzeigen**|Fügt bei einer Klasse alle abgeleiteten Klassen rekursiv hinzu.<br /><br /> Fügt bei einer Schnittstelle alle abgeleiteten Schnittstellen und die implementierenden Klassen oder Strukturen rekursiv hinzu.|  
  
     Für eine **Methode**wählen Sie Folgendes aus:  
  
    |||  
    |-|-|  
    |**Methode anzeigen, die aufruft**|Fügt die Methoden hinzu, die diese Methode aufruft.|  
    |**Felder anzeigen, auf die verwiesen wird**|Fügt die Felder hinzu, auf die diese Methode verweist.|  
    |**Enthaltenden Typ anzeigen**|Fügt den übergeordneten Typ hinzu.|  
    |**Enthaltende/n Typ, Namespace und Assembly anzeigen**|Fügt die übergeordnete Containerhierarchie hinzu.|  
    |**Überschriebene Methoden anzeigen**|Fügt bei einer Methode, die andere Methoden überschreibt oder die Methode einer Schnittstelle implementiert, alle abstrakten oder virtuellen Methoden in Basisklassen, die überschrieben werden, und ggf. die Methode der Schnittstelle, die implementiert wird, hinzu.|  
  
     Für ein **Feld** oder eine **Eigenschaft**wählen Sie Folgendes aus:  
  
    |||  
    |-|-|  
    |**Enthaltenden Typ anzeigen**|Fügt den übergeordneten Typ hinzu.|  
    |**Enthaltende/n Typ, Namespace und Assembly anzeigen**|Fügt die übergeordnete Containerhierarchie hinzu.|  
  
     ![Durch dieses Member aufgerufenen Methoden anzeigen, die](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  Die Beziehungen werden auf der Code Map angezeigt. In diesem Beispiel sind dies die von der `Find` -Methode aufgerufenen Methoden und ihre Position innerhalb oder außerhalb der Projektmappe.  
  
     ![Anzeigen bestimmter Abhängigkeiten in einer Code Map](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  Um die Code Map zu vereinfachen und sich auf einzelne Teile zu konzentrieren, wählen Sie **Filter** auf der Symbolleiste der Code Map aus, und wählen Sie dann nur die Knoten- und Linktypen aus, die für Sie von Interesse sind. Deaktivieren Sie z. B. die Anzeige von Projektmappenordnern, Assemblys und Namespaces.  
  
     ![Verwenden des Filterbereichs zum Vereinfachen der Anzeige](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> Anzeigen von Abhängigkeiten zwischen C- und C++-Quelldateien und Headerdateien  
 Wenn Sie ausführlichere Code Maps für C++-Projekte erstellen möchten, aktivieren Sie für diese Projekte die Compileroption zum Durchsuchen von Informationen (**/FR**). Siehe [/FR, /Fr (Create .Sbr File)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). Andernfalls werden Sie anhand einer Meldung aufgefordert, diese Option festzulegen. Bei Auswahl von **OK**wird die Option nur für die aktuelle Code Map festgelegt. Sie können angeben, dass die Meldung für alle späteren Code Maps ausgeblendet werden soll. Wenn Sie diese Meldung ausblenden, können Sie diese auch wieder einblenden. Legen Sie den folgenden Registrierungsschlüssel auf `0` fest oder löschen Sie den Schlüssel:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider: AutoEnableSbr**  
  
 Wenn Sie eine Projektmappe öffnen, die Visual C++-Projekte enthält, könnte die Aktualisierung der IntelliSense-Datenbank etwas Zeit beanspruchen. Während dieser Zeit können möglicherweise keine Code Maps für Headerdateien (.h oder `#include`) erstellt werden, bis die Aktualisierung der IntelliSense-Datenbank abgeschlossen ist. Sie können den Status der Aktualisierung in der Statusleiste von Visual Studio überwachen. Informationen zum Lösen von Problemen oder zu Meldungen, die angezeigt werden, weil bestimmte IntelliSense-Einstellungen deaktiviert sind, finden Sie unter [Problembehandlung bei Code Maps für C- und C++-Code](#Troubleshooting).  
  
-   Um Abhängigkeiten zwischen allen Quell- und Headerdateien in Ihrer Projektmappe anzuzeigen, klicken Sie im Menü **Architektur** auf **Diagramm für Includedateien generieren**.  
  
     ![Abhängigkeitsdiagramm für nativen Code](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   Um Abhängigkeiten zwischen den aktuell geöffneten Datei und zugehörige Quelldateien und Headerdateien anzuzeigen, öffnen Sie die Quelldatei oder die Header-Datei. Öffnen Sie das Kontextmenü "Datei" an einer beliebigen Stelle in der Datei. Wählen Sie **Diagramm für Includedateien generieren**aus.  
  
     ![Erste&#45;Ebene Abhängigkeitsdiagramm für .h-Datei](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> Problembehandlung bei Code Maps für C- und C++-Code  
 Diese Elemente werden für C- und C++-Code nicht unterstützt:  
  
-   Basistypen werden in Code Maps, die die übergeordnete Hierarchie enthalten, nicht angezeigt.  
  
-   Die meisten Elemente im Menü **Anzeigen** sind für C- und C++-Code nicht verfügbar.  
  
 Diese Probleme können auftreten, wenn Sie Code Maps für C- und C++-Code erstellen:  
  
|**Problem**|**Mögliche Ursache**|**Auflösung**|  
|---------------|------------------------|--------------------|  
|Fehler beim Generieren der Code Map.|Kein Projekt in der Projektmappe wurde erfolgreich erstellt.|Korrigieren Sie die aufgetretenen Buildfehler, und generieren Sie dann die Code Map erneut.|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] reagiert nicht mehr, wenn Sie versuchen, eine Code Map über das Menü **Architektur** zu generieren.|Die Programmdatenbankdatei (.pdb) ist möglicherweise beschädigt.<br /><br /> In einer PDB-Datei werden Debuginformationen gespeichert, z. B. Typ, Methode und Quelldateiinformationen.|Erstellen Sie die Projektmappe neu, und versuchen Sie es dann erneut.|  
|Bestimmte Einstellungen für die IntelliSense-Suchdatenbank sind deaktiviert.|Bestimmte IntelliSense-Einstellungen sind im Dialogfeld [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**von** möglicherweise deaktiviert.|Aktivieren Sie die Einstellungen, um sie verfügbar zu machen.<br /><br /> Finden Sie unter [Optionen, Text-Editor, C/C++, erweitert](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Die Meldung **Unbekannte Methode** wird in einem Methodenknoten angezeigt.<br /><br /> Dieses Problem tritt auf, da der Name der Methode nicht aufgelöst werden kann.|Die Binärdatei weist möglicherweise keine Basisverschiebungstabelle auf.|Aktivieren Sie die Option **/FIXED:NO** im Linker.<br /><br /> Siehe [/FIXED (Fixed Base Address)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|  
||Die Programmdatenbankdatei (.pdb) wird möglicherweise nicht erstellt.<br /><br /> In einer PDB-Datei werden Debuginformationen gespeichert, z. B. Typ, Methode und Quelldateiinformationen.|Aktivieren Sie die Option **/DEBUG** im Linker.<br /><br /> Siehe [/DEBUG (Generate Debug Info)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|  
||Die PDB-Datei kann an den erwarteten Speicherorten nicht geöffnet oder gefunden werden.|Stellen Sie sicher, dass die PDB-Datei an den erwarteten Speicherorten vorhanden ist.|  
||Debuginformationen wurden aus der PDB-Datei entfernt.|Wenn die Option **/PDBSTRIPPED** im Linker verwendet wurde, schließen Sie stattdessen die vollständige PDB-Datei ein.<br /><br /> Siehe [/PDBSTRIPPED (Strip Private Symbols)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
||Der Aufrufer ist keine Funktion und ist entweder ein Thunk in der Binärdatei oder ein Zeiger im Datenabschnitt.|Wenn der Aufrufer ein Thunk ist, versuchen Sie, den Thunk mithilfe von `_declspec(dllimport)` zu vermeiden.<br /><br /> Thema<br /><br /> -   [Allgemeine Regeln und Einschränkungen](http://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [Importieren von Funktionsaufrufen mithilfe von "__declspec(dllimport)" "](http://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [Dllexport, dllimport](http://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|  
  
##  <a name="RenderMoreQuickly"></a> Schnelleres Rendern von Code Maps  
 Wenn Sie eine Code Map zum ersten Mal generieren, werden von Visual Studio alle gefundenen Abhängigkeiten indiziert. Dieser Vorgang kann einige Zeit dauern, insbesondere bei großen Projektmappen, aber dies verbessert die Leistung zu einem späteren Zeitpunkt. Wenn Ihr Code geändert wird, wird von Visual Studio nur der aktualisierte Code neu indiziert. Um den Zeitaufwand für das Rendern der Code Map zu minimieren, beachten Sie Folgendes:  
  
-   [Stellen Sie nur die Abhängigkeiten in der Code Map dar, die Sie interessieren.](#SeeSpecificSource)  
  
-   Bevor Sie die Code Map für eine gesamte Projektmappe generieren, reduzieren Sie den Umfang der Projektmappe.  
  
-   Deaktivieren Sie die automatische Erstellung der Projektmappe mithilfe der Schaltfläche **Build überspringen** auf der Symbolleiste der Code Map.  
  
-   Deaktivieren Sie das automatische Hinzufügen von übergeordneten Elementen mithilfe der Schaltfläche **Übergeordnete Elemente einschließen** auf der Symbolleiste der Code Map.  
  
-   Bearbeiten Sie die Code Map direkt, um Knoten und Links zu entfernen, die Sie nicht benötigen. Das Ändern der Code Map wirkt sich nicht auf den zugrunde liegenden Code aus. Siehe [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
 ![Schaltflächen übergeordnete Elemente einschließen "und" Skip Build "](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
 Obwohl Visual Studio mit 1 GB Arbeitsspeicher ausgeführt werden kann, wird empfohlen, den Computer mit mindestens 2 GB Arbeitsspeicher auszustatten, um lange Verzögerungen während der Erstellung des Codeindex und der Generierung der Code Map durch Visual Studio zu vermeiden.  
  
 Es kann mehr Zeit in Anspruch nehmen, im Projektmappen-Explorer Code Maps zu erstellen oder einer Code Map Elemente hinzuzufügen, wenn für die Eigenschaft **In Ausgabeverzeichnis kopieren** eines Projektelements **Immer kopieren**festgelegt wurde. Dies kann zu Problemen mit inkrementellen Builds und Visual Studio führen, das Projekt jedes Mal neu zu erstellen. Ändern Sie diese Eigenschaft in **Kopieren, wenn neuer** oder `PreserveNewest`, um die Leistung zu erhöhen. Siehe [Incremental Builds](../msbuild/incremental-builds.md).  
  
 Die fertige Code Map zeigt die Abhängigkeiten nur für Code, der erfolgreich erstellt wurde. Wenn für bestimmte Komponenten Buildfehler auftreten, werden diese Fehler auf der Code Map angezeigt. Vergewissern Sie sich, dass eine Komponente tatsächlich erstellt wird und über Abhängigkeiten verfügt, bevor Sie auf Grundlage der Code Map architekturbezogene Entscheidungen treffen.  
  
##  <a name="SavingExporting"></a> Freigeben von Code Maps  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Freigeben der Code Map für andere Visual Studio-Benutzer  
 Verwenden Sie das Menü **Datei** , um die Code Map zu speichern.  
  
 - oder -   
  
 Wählen Sie zum Speichern der Zuordnung als Teil eines bestimmten Projekts auf der Symbolleiste der Map **Freigabe**, **verschieben** \< *CodeMapName*>**DGML in**, und wählen Sie dann auf das Projekt, in dem Sie die Code Map speichern möchten.  
  
 ![Verschieben einer Zuordnung in ein anderes Projekt](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Die Code Map wird von Visual Studio als DGML-Datei gespeichert, die Sie für andere Benutzer von Visual Studio Enterprise und Visual Studio Professional freigeben können.  
  
> [!NOTE]
>  Vergewissern Sie sich, dass alle Gruppen erweitert sind, alle ausgeblendeten Knoten und gruppenübergreifenden Links angezeigt werden, und rufen Sie alle gelöschten Knoten ab, die andere in der Code Map sehen sollen, bevor Sie eine Code Map für Benutzer von Visual Studio Professional freigeben. Andernfalls können andere Benutzer diese Elemente nicht sehen.  
>   
>  Wenn Sie eine Code Map speichern, die sich in einem Modellierungsprojekt befindet oder von einem Modellierungsprojekt an einen anderen Speicherort kopiert wurde, tritt möglicherweise der folgende Fehler auf:  
>   
>  " *Dateiname* kann nicht außerhalb des Projektverzeichnisses gespeichert werden. Verknüpfte Elemente werden nicht unterstützt."  
>   
>  Der Fehler wird zwar von Visual Studio angezeigt, die Version wird aber dennoch gespeichert. Erstellen Sie die Code Map außerhalb des Modellierungsprojekts, um diesen Fehler zu vermeiden. Sie können es anschließend am gewünschten Speicherort speichern. Es wird nicht funktionieren, die Datei einfach an eine andere Position in der Projektmappe zu kopieren und dort zu speichern.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Exportieren der Code Map als Bild, sodass Sie sie in andere Anwendungen kopieren können, beispielsweise Microsoft Word oder PowerPoint  
  
1.  Wählen Sie auf der Symbolleiste der Code Map **Freigeben**, **Als Bild per E-Mail senden** oder **Bild kopieren**aus.  
  
2.  Fügen Sie das Bild in eine andere Anwendung ein.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Exportieren der Code Map als XPS-Datei, sodass Sie sie in XML- oder XAML-Viewern wie Internet Explorer anzeigen können  
  
1.  Wählen Sie auf der Symbolleiste der Code Map **Freigeben**, **Als portables XPS per E-Mail senden** oder **Als portables XPS speichern**aus.  
  
2.  Durchsuchen Sie nach dem Ort, an dem die Datei gespeichert werden soll.  
  
3.  Benennen Sie die Code Map. Stellen Sie sicher, dass die **Dateityp** das Feld **XPS-Dateien (\*.xps)**. Wählen Sie **Speichern**.  
  
## <a name="what-else-can-i-do"></a>Welche weiteren Möglichkeiten gibt es?  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)



