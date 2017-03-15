---
title: Durchsuchen und Neuanordnen von Code Maps | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
ms.assetid: 08f65f77-6ca7-4b25-b060-3f6c9f5847a4
caps.latest.revision: 91
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 08aabdfe0e268f93ef7723076375b7f65b15ccf3
ms.openlocfilehash: cbcac8a4fdb03fc1da610fde10bf59f8dd75e3af
ms.lasthandoff: 02/22/2017

---
# <a name="browse-and-rearrange-code-maps"></a>Durchsuchen und Neuanordnen von Code Maps
Ordnen Sie Elemente in Codeübersichten neu an, damit sie leichter zu lesen sind und ihre Leistung gesteigert wird.  
  
 Sie können Codeübersichten ohne Auswirkungen auf den zugrunde liegenden Code in einer Projektmappe anpassen. Dies ist hilfreich, wenn Sie sich auf wichtige Elemente konzentrieren oder Ideen zum Code kommunizieren möchten. Um beispielsweise interessante Bereiche hervorzuheben, können Sie Codeelemente in der Übersicht auswählen und filtern, den Stil von Codeelemente und Links ändern, Codeelemente ausblenden oder löschen und Codeelemente mithilfe von Eigenschaften, Kategorien oder Gruppen organisieren.  
  
 **Anforderungen**  
  
-   Zum Erstellen von Code Maps benötigen Sie Visual Studio Enterprise.  
  
-   In Visual Studio Professional können Sie Codeübersichten anzeigen und diese im begrenzten Maße bearbeiten.  
  
##  <a name="a-namemanagelargegraphsa-get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a>Bei den ersten Sie Schritten mit Code maps  
 Erstellen Sie eine Code Map (finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md) Weitere Einzelheiten). Wenn Sie nicht warten, bis die Karte um vollständig generieren möchten die **Abbrechen** Link jederzeit aufrufen, um den Generierungsprozess zu beenden. Allerdings werden in diesem Fall nicht die Details aller Abhängigkeiten und Links angezeigt.  
  
 Nachdem Sie die Übersicht generiert haben, beginnen Sie mit diesen Tipps zum Überprüfen des Codes:  
  
-   Achten Sie auf die natürlichen Abhängigkeitscluster im Code. Wählen Sie auf der Symbolleiste der Map **Layout**, **schnelle Cluster**![schnelle Cluster-Schaltfläche auf der Diagrammsymbolleiste](../modeling/media/quickclustersicon.gif "QuickClustersIcon"). Finden Sie unter [Ändern des übersichtlayouts](#Selecting).  
  
     ![Abhängigkeitsdiagramm - schnelle Clusterlayout](../modeling/media/dependencygraph_quickclusters.png "DependencyGraph_QuickClusters")  
  
-   Organisieren Sie die Übersicht in kleinere Bereiche, indem Sie verwandte Knoten gruppieren. Reduzieren Sie diese Gruppen, um nur die Abhängigkeiten zwischen den Gruppen zu sehen, die automatisch angezeigt werden. Finden Sie unter [Gruppenknoten](#OrganizeGroups).  
  
-   Verwenden Sie Filter, um die Übersicht zu vereinfachen und den Schwerpunkt auf die Typen von Knoten oder Links zu legen, an denen Sie interessiert sind. Finden Sie unter [Filtern von Knoten und Links](#FilterNodes).  
  
-   Maximieren Sie die Leistung von großen Übersichten. Finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md) Weitere Informationen. Schalten Sie z. B. **Skip Build** auf der Übersichtssymbolleiste, damit, die Visual Studio nicht die Projektmappe neu erstellen, bei der Aktualisierung von Elementen in der Zuordnung.  
  
##  <a name="a-nameselectinga-change-the-map-layout"></a><a name="Selecting"></a>Ändern des übersichtlayouts  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Ordnen Sie den Abhängigkeitsverlauf für die gesamte Übersicht in einer bestimmten Richtung an. Dies kann Ihnen helfen, Architekturebenen im Code zu finden.|Wählen Sie auf der Symbolleiste der Map **Layout**, und klicken Sie dann:<br /><br /> -   **Von oben nach unten** ![von oben nach unten-Schaltfläche "Diagramm"](../modeling/media/topbottomgraphbutton.gif "TopBottomGraphButton")<br />-   **Von unten nach oben** ![von unten nach oben Schaltfläche](../modeling/media/bottomtopgraphbutton.gif "BottomTopGraphButton")<br />-   **Von links nach rechts** ![von links nach rechts-Layout-Schaltfläche](../modeling/media/leftrightgraphbutton.gif "LeftRightGraphButton")<br />-   **Von rechts nach links** ![von rechts nach links-Schaltfläche](../modeling/media/rightleftgraphbutton.gif "RightLeftGraphButton")|  
|Zeigen Sie natürliche Abhängigkeitscluster im Code an, wobei die Knoten mit den meisten Abhängigkeiten in der Mitte der Cluster und die Knoten mit den wenigsten Abhängigkeiten an der Außenseite der Cluster angezeigt werden.|Wählen Sie auf der Symbolleiste der Map **Layout**, und klicken Sie dann **schnelle Cluster**![schnelle Cluster-Schaltfläche auf der Diagrammsymbolleiste](../modeling/media/quickclustersicon.gif "QuickClustersIcon").|  
|Wählen Sie mindestens einen Knoten in der Übersicht aus.|Klicken Sie auf einen Knoten, um ihn auszuwählen. Halten Sie zum Aktivieren oder deaktivieren mehr als einen Knoten, **STRG** beim Klicken.<br /><br /> Tastatur: Drücken Sie **Registerkarte** oder verschieben Sie den gepunkteten fokusrahmen auf einen Knoten, und drücken Sie die Pfeiltasten verwenden **Speicherplatz** um es auszuwählen. Drücken Sie **STRG** + **Speicherplatz** auswählen oder Aufheben der Auswahl Knoten.|  
|Verschieben Sie bestimmte Knoten in der Übersicht.|Ziehen Sie die Knoten, um sie zu verschieben. So verschieben Sie andere Knoten und Links aus dem Weg, wie Sie Knoten ziehen, halten Sie die **UMSCHALT** Schlüssel.<br /><br /> Tastatur: halten **STRG** , und drücken Sie die Pfeiltasten.|  
|Ändern Sie das Layout in einer Gruppe unabhängig von den anderen Knoten und Gruppen in der Übersicht.|Wählen Sie einen Knoten aus, und öffnen Sie das Kontextmenü. Wählen Sie **Layout** , und wählen Sie ein Layout-Format.<br /><br /> - oder -<br /><br /> Wählen Sie einen Knoten, und erweitern Sie, um die untergeordneten Knoten angezeigt. Klicken Sie auf den knotentitel, um die Popupsymbolleiste für Gruppen anzeigen, und öffnen Sie die **den Layoutstil der Gruppe**![Abhängigkeitsdiagramm - gruppensymbolleiste - Layout](../modeling/media/dependencygraph_grouptoolbar.gif "DependencyGraph_GroupToolbar") Liste. Wählen Sie eine der drei Layouts, **schnelle Cluster**, oder **Listenansicht** (die ordnet die Inhalte der Gruppe in eine Liste).<br /><br /> Finden Sie unter [Gruppenknoten](#OrganizeGroups) für weitere Details.|  
|Machen Sie eine Aktion in der Übersicht rückgängig.|Drücken Sie **STRG** + **Z** oder den Visual Studio **Rückgängig** Befehl.|  
  
##  <a name="a-nameexplorea-browse-the-map"></a><a name="Explore"></a>Durchsuchen der Übersicht  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Überprüfen Sie die Übersicht.|Ziehen Sie die Übersicht mithilfe der Maus in eine beliebige Richtung.<br /><br /> - oder -<br /><br /> Halten Sie **UMSCHALT** und drehen Sie das Mausrad, um einen horizontalen Bildlauf durchzuführen. Halten Sie **UMSCHALT** + **STRG** und drehen Sie das Mausrad, um einen horizontalen Bildlauf durchzuführen.|  
|Vergrößern oder verkleinern Sie die Übersicht.|Drehen Sie das Mausrad.<br /><br /> - oder -<br /><br /> Verwenden der **Zoom** Dropdown-Liste auf der Symbolleiste der Codeübersicht.<br /><br /> - oder -<br /><br /> Verwenden Sie die Tastenkombinationen. Drücken Sie zum Vergrößern **STRG + UMSCHALT +.** (Punkt). Drücken Sie zum Verkleinern **STRG + UMSCHALT +,** (Komma).|  
|Vergrößern Sie mit der Maus einen bestimmten Bereich.|Halten Sie die rechte Maustaste gedrückt, während Sie in diesem Bereich ein Rechteck um den für Sie interessanten Bereich aufziehen.|  
|Ändern Sie die Größe der Übersicht, und passen Sie sie auf die Fenstergröße an.|Wählen Sie **Zoom anpassen** aus der **Zoom** Liste auf der Symbolleiste der Codeübersicht.<br /><br /> - oder -<br /><br /> Klicken Sie auf die **Zoom anpassen** Symbol ![Zoom-Symbol auf der Symbolleiste der Map](../modeling/media/almcodemapzoomicon.png "ALMCodeMapZoomIcon") auf der Symbolleiste der Codeübersicht. Tastatur: Drücken Sie **STRG + 0** (null).|  
|Suchen Sie anhand des Namens einen Knoten in der Übersicht. **Tipp:** dies funktioniert nur für Elemente auf der Karte. Zum Suchen von Elementen in der Projektmappe jedoch nicht auf der Karte, befinden sich im **Projektmappen-Explorer**, und ziehen sie dann auf die Karte. (Ziehen Sie die Auswahl, oder klicken Sie auf der Symbolleiste Projektmappen-Explorer auf **in Code Map anzeigen**).|1.  Wählen Sie die **suchen** Symbol ![Suchsymbol auf zuordnungssymbolleiste](../modeling/media/almcodemapfindicon.png "ALMCodeMapFindIcon") auf der Symbolleiste der Codeübersicht (Tastatur: Drücken Sie die **STRG + F**) das Suchen in der rechten oberen Ecke der Karte angezeigt.<br />2.  Geben Sie den Elementnamen und drücken Sie die **zurückgeben** oder auf das Symbol "Bildschirmlupe". Das erste Element, das die Suche entspricht der Zuordnung angezeigt.<br />3.  Öffnen Sie die Dropdownliste, und wählen Sie eine Suchoption aus, um Ihre Suche anzupassen. Die Optionen sind **Weitersuchen**, **Vorheriges suchen**, und **Alles markieren**. Klicken Sie auf die entsprechende Schaltfläche neben dem Textfeld „Suchen“.<br />     ![Suche Optionen Dropdown-Liste](../modeling/media/almcodemapssearchdropdown.png "ALMCodeMapsSearchDropDown")<br />     Sie können auch mithilfe der Tastatur: Drücken Sie **F3** auf den nächsten übereinstimmenden Knoten auszuwählen oder **UMSCHALT + F3** den vorherigen übereinstimmenden Knoten auswählen.<br />4.  Wählen Sie eine der Optionen aus, die angeben, wie Suchbegriffe behandelt werden, indem Sie auf die Symbole unten dem Textfeld „Suchen“ klicken.<br />     ![Übereinstimmungsoptionen für Suche](../modeling/media/almcodemapssearchmatchicons.png "ALMCodeMapsSearchMatchIcons")<br />     Die Optionen sind (von links nach rechts) für die Übereinstimmung unter Berücksichtigung der Groß-/Kleinschreibung, für die Übereinstimmung mit ganzem Wort, für die Verwendung der normalen .NET-Ausdruckssyntax und für das automatische Erweitern von Gruppen, um Übereinstimmungen für eingeschlossene Elemente anzuzeigen. **Wichtig:** können das Suchfeld zum Suchen von Übereinstimmungen in reduzierten Gruppen nur dann, wenn diese Gruppen zuvor erweitert wurden. Wählen Sie diese Option unter dem Suchfeld aus, um diese Übereinstimmungen zu suchen und ihre übergeordneten Gruppen automatisch zu erweitern.|  
|Wählen Sie alle nicht markierten Knoten aus.|Öffnen Sie das Kontextmenü für die ausgewählten Knoten. Wählen Sie **auswählen**, **Auswahl umkehren**.|  
|Wählen Sie weitere Knoten aus, die Links zu den ausgewählten Knoten aufweisen.|Öffnen Sie das Kontextmenü für die ausgewählten Knoten. Wählen Sie **wählen** und eine der folgenden:<br /><br /> -Um zusätzliche Knoten auswählen, die direkt mit dem ausgewählten Knoten zu verknüpfen, wählen Sie **eingehende Abhängigkeiten**.<br />-Um zusätzlichen Knoten, die Verknüpfung direkt vom ausgewählten Knoten auszuwählen **ausgehende Abhängigkeiten**.<br />-Um zusätzliche Knoten auswählen, die direkt vom ausgewählten Knoten zu verknüpfen, wählen Sie **beide**.<br />-Um alle Knoten zu und von den ausgewählten Knoten mit Links auszuwählen, wählen Sie **Unterdiagramm verbunden**.<br />-, Um alle untergeordneten Elemente des ausgewählten Knotens auszuwählen **Kinder**.|  
  
##  <a name="a-namefilternodesa-filter-nodes-and-links"></a><a name="FilterNodes"></a>Filtern von Knoten und links  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Blenden Sie den Filterbereich ein oder aus.|Wählen Sie die **Filter** Schaltfläche auf der Symbolleiste der Codeübersicht. Der Filterbereich wird im Fenster des Projektmappen-Explorers standardmäßig als Seite mit Registerkarten angezeigt.|  
|Filtern Sie die Typen von Knoten, die in der Übersicht angezeigt werden.|Aktivieren oder deaktivieren Sie die Kontrollkästchen in der **Codeelemente** Liste im Bereich Filter.|  
|Filtern Sie die Typen von Links, die in der Übersicht angezeigt werden.|Aktivieren oder deaktivieren Sie die Kontrollkästchen in der **Beziehungen** Liste im Bereich Filter.|  
|Blenden Sie Testprojektknoten in der Übersicht ein oder aus.|Aktivieren oder deaktivieren Sie die **Testobjekte** Kontrollkästchen in der **Sonstiges** Liste im Bereich Filter.|  
  
 Die im Bereich „Legende“ der Übersicht angezeigten Symbole spiegeln die von Ihnen in der Liste vorgenommenen Einstellungen wider. Zum ein- oder Ausblenden des Bereichs der Legende, klicken Sie auf die **Legende** Schaltfläche auf der Symbolleiste der Codeübersicht.  
  
##  <a name="a-nameinspecta-examine-nodes-and-links"></a><a name="Inspect"></a>Untersuchen von Knoten und links  
 In Codeübersichten werden die folgenden Arten von Links angezeigt:  
  
-   Ein einzelner Link stellt eine einzelne Beziehung zwischen zwei Knoten dar.  
  
-   Ein gruppenübergreifender Link stellt eine Beziehung zwischen zwei Knoten in unterschiedlichen Gruppen dar.  
  
-   Ein Aggregatlink stellt alle gleichgerichteten Beziehungen zwischen zwei Gruppen dar.  
  
> [!TIP]
>  Gruppenübergreifende Links werden in der Übersicht standardmäßig nur für ausgewählte Knoten angezeigt. Um dieses Verhalten zum ein- oder Ausblenden von aggregatlinks zwischen Gruppen zu ändern, klicken Sie auf **Layout** Code zuordnen Symbolleiste, und wählen Sie **erweitert**, dann **alle gruppenübergreifenden Links anzeigen** oder **alle gruppenübergreifenden Links ausblenden**. Finden Sie unter [ausblenden oder Einblenden von Knoten und Links](#HidingShowing) für weitere Details.  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Zeigen Sie weitere Informationen zu einem Knoten oder Link an.|Bewegen Sie den Mauszeiger auf den Knoten oder Link, bis eine QuickInfo angezeigt wird.<br /><br /> Die QuickInfo eines Aggregatlinks enthält eine Liste der einzelnen Abhängigkeiten, die der Link darstellt.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für den Knoten oder den Link. Wählen Sie **bearbeiten**, **Eigenschaften**.|  
|Zeigen Sie den Inhalt einer Gruppe an oder blenden Sie ihn aus.|-Um eine Gruppe zu erweitern, öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **Gruppe**, **erweitern**.<br />     - oder -<br />     Bewegen Sie den Mauszeiger auf den Knoten, bis die Chevronschaltfläche (Pfeil nach unten) angezeigt wird. Klicken Sie auf diese Schaltfläche, um die Gruppe zu erweitern. Tastatur: zum Erweitern oder reduzieren die ausgewählte Gruppe, drücken Sie die **PLUS** Schlüssel (**+**) oder die **MINUS** Schlüssel (**-**).<br />-Um eine Gruppe zu reduzieren, öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **Gruppe**, **reduzieren**.<br />     - oder -<br />     Bewegen Sie den Mauszeiger auf eine Gruppe, bis die Chevronschaltfläche (Pfeil nach oben) angezeigt wird. Klicken Sie auf diese Schaltfläche, um die Gruppe zu reduzieren.<br />-Wenn Sie alle Gruppen erweitern möchten, drücken Sie die **STRG** + **ein** an alle Knoten auszuwählen. Öffnen Sie das Kontextmenü für die Karte, und wählen Sie **Gruppe**, **erweitern**. **Hinweis:** dieser Befehl ist nicht verfügbar, wenn das Erweitern aller Gruppen einer nicht verwendbaren Übersicht oder zu Speicherproblemen führt. Es wird empfohlen, die Übersicht nur bis zu der Detailstufe zu erweitern, die Sie interessiert.<br />-Öffnen Sie das Kontextmenü für einen Knoten oder für die Karte um alle Gruppen zu reduzieren. Wählen Sie **Gruppe**, **alle reduzieren**.|  
|Zeigen Sie die Codedefinition für einen Namespace, einen Typ oder einen Member an.|Öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **Gehe zu Definition**.<br /><br /> - oder - <br /><br /> Doppelklicken Sie auf den Knoten. Doppelklicken Sie bei erweiterten Gruppen auf den Header für die Gruppe.<br /><br /> - oder - <br /><br /> Wählen Sie den Knoten, und drücken Sie **F12**.<br /><br /> Zum Beispiel:<br /><br /> – Für einen Namespace, eine Klasse enthält wird die Codedatei für die Klasse Anzeigen der Definition dieser Klasse geöffnet. In anderen Fällen die **Ergebnisse der Symbolsuche** Fenster wird eine Liste der Codedateien. **Hinweis:** , wenn Sie diese Aufgabe für einen Visual Basic .NET-Namespace ausführen, wird die Codedatei hinter dem Namespace wird nicht geöffnet. Dieses Problem tritt auch auf, wenn Sie diese Aufgabe in einer Gruppe von ausgewählten Knoten ausführen, die einen Visual Basic .NET-Namespace enthalten. Sie können dieses Problem umgehen, indem Sie manuell zu der Codedatei hinter dem Namespace navigieren oder den Knoten für den Namespace nicht in die Auswahl einbeziehen.<br />– Für eine Klasse oder eine partielle Klasse wird die Codedatei für diese Klasse der Klassendefinition geöffnet.<br />-Bei einer Methode wird die Codedatei für die übergeordnete Klasse Definition der Methode geöffnet.|  
|Überprüfen Sie die Abhängigkeiten und Elemente, die Teil eines Aggregatlinks sind.|Wählen Sie die für Sie interessanten Links aus, und öffnen Sie das Kontextmenü für Ihre Auswahl. Wählen Sie **zugehörige Links anzeigen** oder **zugehörige Links auf neuer Code Map anzeigen**.<br /><br /> Visual Studio erweitert die Gruppen an beiden Enden des Links und zeigt nur die Elemente und Abhängigkeiten an, die zu dem Link gehören. **Hinweis:** bei der Überprüfung der Abhängigkeiten zwischen Elementen in partiellen Gruppen können Sie sehen, dass dieses Verhalten: <ul><li>Links zu Elementen, die bei der Überprüfung nicht einbezogen werden, werden in der Übersicht nicht mehr angezeigt, obwohl diese Links weiterhin vorhanden sind.</li><li>Angenommen, Sie überprüfen einen Link zu einem Element in einer partiellen Gruppe und überprüfen später einen anderen Link zum selben Element. Während der zweiten Überprüfung werden in der partiellen Gruppe des Ziels nur Elemente der ersten Prüfung angezeigt. Links und Zielelemente, die bei der ersten Überprüfung nicht, jedoch bei der zweiten Überprüfung einbezogen wurden, werden angezeigt.</li></ul> Um fehlende Elemente aus einer Gruppe anzuzeigen, wählen Sie **untergeordnete Elemente**![untergeordnete Kinder Symbol](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") (gibt an, dass nicht alle Mitglieder einer Gruppe auf der Karte angezeigt werden). Sie können auch versuchen, Ihre Aktionen rückgängig zu machen (Tastatur: Drücken Sie die **STRG + Z**) und die Abhängigkeiten in einer neuen Zuordnung überprüfen.|  
|Überprüfen Sie die Abhängigkeiten zwischen mehreren Knoten in unterschiedlichen Gruppen.|Erweitern Sie die Gruppen, sodass alle untergeordneten Elemente angezeigt werden. Wählen Sie alle für Sie interessanten Knoten aus – einschließlich der untergeordneten Elemente. In der Übersicht werden die gruppenübergreifenden Links zwischen den ausgewählten Knoten angezeigt.<br /><br /> Um alle Knoten in einer Gruppe auszuwählen, halten Sie **UMSCHALT** und die linke Maustaste gedrückt, während Sie ein um die gewünschte Gruppe Rechteck. Um alle Knoten auf einer Karte auszuwählen, drücken Sie die **STRG**+**ein**. **Tipp:** um gruppenübergreifende Links jederzeit anzuzeigen, wählen Sie **Layout** auf der Symbolleiste der Map **erweitert**, **alle gruppenübergreifenden Links anzeigen**.|  
|Zeigen Sie die Elemente an, auf die von einem Knoten oder Link verwiesen wird.|Öffnen Sie das Kontextmenü für den Knoten, und wählen Sie **alle Verweise suchen**. **Hinweis:** Dies gilt nur, wenn die `Reference` Attributsatz für den Knoten oder Link in der Zuordnung DGML-Datei. Verweisen auf Elemente aus Knoten oder Links finden Sie unter [Anpassen von Code maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|  
  
##  <a name="a-namehidingshowinga-hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a>Aus- oder Einblenden von Knoten und links  
 Wenn Knoten ausgeblendet werden, werden sie von Layoutalgorithmen nicht berücksichtigt. Gruppenübergreifende Links werden standardmäßig ausgeblendet. Gruppenübergreifende Links sind einzelne Links, durch die Knoten über Gruppen hinweg verbunden sind. Beim Reduzieren von Gruppen werden alle gruppenübergreifenden Links in der Übersicht zu einzelnen Links zwischen Gruppen aggregiert. Wenn Sie eine Gruppe erweitern und Knoten in der Gruppe auswählen, werden gruppenübergreifende Links angezeigt, die die Abhängigkeiten in dieser Gruppe darstellen.  
  
> [!CAUTION]
>  Vergewissern Sie sich, dass alle Knoten bzw. gruppenübergreifenden Links, die andere Benutzer sehen sollen, eingeblendet sind, bevor Sie eine Übersicht für Benutzer von Visual Studio Professional freigeben, die in Visual Studio Enterprise erstellt wurde. Andernfalls können diese Benutzer diese Elemente nicht einblenden.  
  
### <a name="to-hide-or-show-nodes"></a>So blenden Sie Knoten ein oder aus  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Blenden Sie die ausgewählten Knoten aus.|1.  Wählen Sie die auszublendenden Knoten aus.<br />2.  Öffnen Sie das Kontextmenü für die ausgewählten Knoten oder für die Übersicht. Wählen Sie **auswählen**, **Ausblenden aktiviert**.|  
|Blenden Sie nicht ausgewählte Knoten aus.|1.  Wählen Sie die Knoten aus, die sichtbar bleiben sollen.<br />2.  Öffnen Sie das Kontextmenü für die ausgewählten Knoten oder für die Übersicht. Wählen Sie **auswählen**, **ausblenden deaktiviert**.|  
|Zeigen Sie ausgeblendete Knoten an.|-Wenn Sie alle ausgeblendete Knoten in einer Gruppe anzeigen möchten, müssen Sie zunächst sicherstellen Sie, dass die Gruppe erweitert werden. Öffnen Sie das Kontextmenü, und wählen Sie **auswählen**, **untergeordnete Elemente einblenden**.<br />     - oder -<br />     Klicken Sie auf die **untergeordnete Elemente einblenden**![Symbol für untergeordnete Elemente einblenden](../modeling/media/dependencygraph_filtericon_hiddennodes.gif "DependencyGraph_FilterIcon_HiddenNodes") -Symbol in der oberen linken Ecke der Gruppe (Dies ist sichtbar nur bei der ausgeblendeten untergeordneten Knoten vorhanden sind).<br />-Wenn Sie alle ausgeblendeten Knoten anzuzeigen, öffnen Sie das Kontextmenü für das Schema oder einen Knoten, und wählen Sie **auswählen**, **alle einblenden**.|  
  
### <a name="to-hide-or-show-links"></a>So blenden Sie Links ein oder aus  
  
|**Aktion**|**Wählen Sie auf der Symbolleiste der Map Layout, erweitert, und wählen Sie dann**|  
|------------|----------------------------------------------------------------------|  
|Dauerhaftes Anzeigen gruppenübergreifender Links.|**Alle gruppenübergreifenden Links anzeigen**. Bei Auswahl dieser Option werden Aggregatlinks zwischen Gruppen ausgeblendet.|  
|Dauerhaftes ausblenden gruppenübergreifender Links.|**Alle gruppenübergreifenden Links ausblenden**|  
|Anzeigen ausschließlich gruppenübergreifender Links für ausgewählte Knoten.|**Gruppenübergreifende Links für ausgewählte Knoten anzeigen**|  
|Alle Links ausblenden.|**Alle Links ausblenden**. Wählen Sie eine der oben aufgeführten Optionen aus, um Links erneut anzuzeigen.|  
  
##  <a name="a-nameorganizegroupsa-group-nodes"></a><a name="OrganizeGroups"></a>Gruppieren von Knoten  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Zeigen Sie Containerknoten als Gruppen- oder Blattknoten an.|Zum Anzeigen von Containerknoten als Blattknoten: Wählen Sie die Knoten, öffnen Sie das Kontextmenü für die Auswahl, und wählen **Gruppe**, **in Blatt konvertieren**.<br /><br /> Zum Anzeigen von Containerknoten als Gruppenknoten: Wählen Sie die Knoten, öffnen Sie das Kontextmenü für die Auswahl, und wählen **Gruppe**, **in Gruppe konvertieren**.|  
|Ändern Sie das Layout in einer Gruppe.|Wählen Sie die Gruppe, öffnen Sie das Kontextmenü, wählen Sie **Layout**, und wählen Sie den gewünschten Layoutstil.<br /><br /> - oder -<br /><br /> 1.  Wählen Sie die Gruppe aus, und stellen Sie sicher, dass diese erweitert ist.<br />2.  Klicken Sie erneut auf den Gruppenkopf, damit die Gruppensymbolleiste angezeigt wird.<br />     ![Abhängigkeitsdiagramm - gruppensymbolleiste](../modeling/media/dependencygraph_group.png "DependencyGraph_Group")<br />3.  Öffnen Sie die **den Layoutstil der Gruppe** Liste ![Abhängigkeitsdiagramm - gruppensymbolleiste - Layout](../modeling/media/dependencygraph_grouptoolbar.gif "DependencyGraph_GroupToolbar") , und wählen Sie den gewünschten Layoutstil.<br /><br /> **Listenansicht** Mitglieder der Gruppe in einer Liste neu angeordnet. **Diagrammstandard** Gruppenlayout auf das Standardlayout für die Zuordnung. Weitere Optionen finden Sie unter [Ändern des übersichtlayouts](#Selecting).|  
|Fügen Sie einen Knoten zu einer Gruppe hinzu.|Ziehen Sie den Knoten auf die Gruppe.<br /><br /> Während Sie den Knoten ziehen, wird von Visual Studio durch einen Indikator angezeigt, dass Sie den Knoten verschieben.<br /><br /> Sie können Knoten auch aus einer Gruppe herausziehen.|  
|Fügen Sie einen Knoten zu einem Knoten hinzu, der zu keiner Gruppe gehört.|Ziehen Sie den Knoten auf den Zielknoten. Sie können beliebige Zielknoten in eine Gruppe konvertieren, indem Sie ihm Knoten hinzufügen.|  
|Gruppieren Sie ausgewählte Knoten.|1.  Wählen Sie die zu gruppierenden Knoten aus. Über dem zuletzt ausgewählten Knoten wird eine Popupsymbolleiste angezeigt.<br />     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")<br />2.  Wählen Sie auf der Symbolleiste das vierte Symbol **ausgewählte Knoten gruppieren** (wenn der Knoten erweitert ist es weist fünf statt vier Symbole angezeigt). Geben Sie den Namen für die neue Gruppe, und drücken Sie **zurückgeben**.<br />     - oder -<br />     Wählen Sie die zu gruppierenden Knoten aus, und öffnen Sie das Kontextmenü für Ihre Auswahl. Wählen Sie **Gruppe**, **übergeordnete Gruppe hinzufügen**, geben Sie den Namen für die neue Gruppe ein, und drücken Sie die **zurückgeben**.<br /><br /> Sie können eine Gruppe umbenennen. Öffnen Sie das Kontextmenü für die Gruppe, und wählen Sie **bearbeiten**, **Eigenschaften** Eigenschaftenfenster von Visual Studio zu öffnen. In der **Bezeichnung** -Eigenschaft, die Gruppe nach Bedarf umbenennen.|  
|Entfernen Sie Gruppen.|Wählen Sie die Gruppe oder die Gruppen aus, die Sie entfernen möchten. Öffnen Sie das Kontextmenü für die Auswahl, und wählen Sie **Gruppe**, **Gruppe entfernen**.|  
|Entfernen Sie Knoten aus der übergeordneten Gruppe.|Wählen Sie die Knoten aus, die Sie verschieben möchten. Öffnen Sie das Kontextmenü für die Auswahl, und wählen Sie **Gruppe**, **aus übergeordnetem Element entfernen**. Dadurch werden Knoten bis zur zweiten übergeordneten Ebene oder außerhalb der Gruppe entfernt, wenn keine zweite übergeordnete Ebene vorhanden ist.<br /><br /> - oder -<br /><br /> Wählen Sie die Knoten aus, und ziehen Sie sie aus der Gruppe.|  
  
##  <a name="a-nameaddremovenodeslinksa-add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a>Hinzufügen, entfernen oder Umbenennen von Knoten, Links und Kommentare  
 Sie können in einer Übersicht mehr oder weniger Elemente anzeigen, um Detailinformationen einzublenden oder die Übersicht zu vereinfachen. Sie können Elemente auch entfernen und ihnen Kommentare hinzufügen.  
  
> [!CAUTION]
>  Vergewissern Sie sich vor dem Freigeben einer mit Visual Studio Enterprise erstellten Übersicht für Benutzer von Visual Studio Professional, dass alle Codeelemente in der Übersicht angezeigt werden, die für andere angezeigt werden sollen. Andernfalls können diese Benutzer gelöschte Codeelemente nicht abrufen.  
  
### <a name="add-a-node-for-a-code-element"></a>Hinzufügen eines Knotens für ein Codeelement  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Fügen Sie einen neuen generischen Knoten an der aktuellen Position des Mauszeigers hinzu.|1.  Den Mauszeiger an die Stelle auf der Karte, wo sollen die neuen Code-Element, und drücken Sie **einfügen**.<br />     - oder -<br />     Öffnen Sie das Kontextmenü für die Karte, und wählen Sie **bearbeiten**, **hinzufügen**, **generischen Knoten**.<br />2.  Geben Sie den Namen für den neuen Knoten und drücken Sie **zurückgeben**.|  
|Fügen Sie eine bestimmte Art von Codeelementknoten an der aktuellen Position des Mauszeigers ein.|1.  Bewegen Sie den Mauszeiger in der Übersicht an die Stelle, an der Sie das neue Codeelement positionieren möchten, und öffnen Sie das Kontextmenü für die Übersicht.<br />2.  Wählen Sie **bearbeiten**, **hinzufügen**, und wählen Sie den Typ des Knotens werden soll.<br />3.  Geben Sie den Namen für den neuen Knoten und drücken Sie **zurückgeben**.|  
|Fügen Sie einen generischen oder eine bestimmte Art von Codeelementknoten zu einer Gruppe hinzu.|1.  Wählen Sie den Gruppenknoten aus, und öffnen Sie das Kontextmenü.<br />2.  Wählen Sie **bearbeiten**, **hinzufügen**, und wählen Sie den Typ des Knotens werden soll.<br />3.  Geben Sie den Namen für den neuen Knoten und drücken Sie **zurückgeben**.|  
|Fügen Sie einen neuen Knoten desselben Typs hinzu, der mit einem vorhandenen Knoten verknüpft ist.|1.  Wählen Sie das Codeelement aus. Darüber wird eine Popupsymbolleiste angezeigt.<br />     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")<br />2.  Wählen Sie auf der Symbolleiste das zweite Symbol **einen Knoten mit derselben Kategorie wie dieser Knoten erstellen und einen neuen Link hinzufügen**.<br />3.  Wählen Sie eine Position in der Übersicht aus, um das neue Codeelement abzulegen, und klicken Sie mit der linken Maustaste.<br />4.  Geben Sie den Namen für den neuen Knoten und drücken Sie **zurückgeben**.|  
|Fügen Sie einen neuen generischen Knoten hinzu, der mit einem vorhandenen Codeleement verknüpft ist, das über den Fokus verfügt.|1.  Mit der Tastatur: Drücken Sie **Registerkarte** , bis das Codeelement so verknüpfen Sie den Fokus (gepunkteter Rahmen) aufweist.<br />2.  Press **Alt**+**Insert**.<br />3.  Geben Sie den Namen für den neuen Knoten und drücken Sie **zurückgeben**.|  
|Fügen Sie einen neuen generischen Knoten hinzu, der mit einem vorhandenen Codeleement verknüpft ist, das über den Fokus verfügt.|1.  Mit der Tastatur: Drücken Sie **Registerkarte** , bis das Codeelement so verknüpfen Sie mit den Fokus (gepunkteter Rahmen) aufweist.<br />2.  Press **Alt**+**Shift**+**Insert**.<br />3.  Geben Sie den Namen für den neuen Knoten und drücken Sie **zurückgeben**.|  
  
|**Codeelemente für hinzufügen**|**Auszuführende Schritte**|  
|----------------------------------|-----------------------------|  
|Codeelemente in der Projektmappe.|1.  Suchen Sie das Codeelement in **Projektmappen-Explorer**. Verwenden der **Projektmappen-Explorer** Suchfeld ein, oder Durchsuchen Sie die Projektmappe. **Tipp:** Suche nach Codeelementen, die Abhängigkeiten für einen Typ oder Member aufweisen, öffnen Sie das Kontextmenü für den Typ oder den Member in **Projektmappen-Explorer**. Wählen Sie die Beziehung aus, die Sie interessiert. **Projektmappen-Explorer** zeigt nur die Codeelemente mit den angegebenen Abhängigkeiten.<br />2.  Ziehen Sie die für Sie interessanten Codeelemente auf die Oberfläche der Übersicht. Sie können Codeelemente auch aus der Klassenansicht oder dem Objektkatalog ziehen.<br />     - oder -<br />     In **Projektmappen-Explorer**, wählen Sie die Codeelemente, die Sie zuordnen möchten. Klicken Sie dann auf die **Projektmappen-Explorer** -Symbolleiste klicken Sie auf **in Code Map anzeigen**.<br /><br /> Standardmäßig wird die übergeordnete Containerhierarchie für die neuen Codeelemente in der Übersicht angezeigt. Verwenden der **übergeordnete Elemente einschließen** Schaltfläche auf der Symbolleiste der Codeübersicht auf dieses Verhalten zu ändern. Wenn diese Option deaktiviert ist, wird nur das Codeelement zur Übersicht hinzugefügt. Umkehren dieses Verhalten für nur eine Drag und drop-Aktion, drücken und halten die **STRG** gedrückt, während Sie die Codeelemente der Karte ziehen.<br /><br /> Von Visual Studio werden Codeelemente für die Codeelemente der obersten Ebene in der Auswahl hinzugefügt. Bewegen Sie den Mauszeiger über dem Anfang des Codeelements, sodass das Chevron (Pfeil nach unten) angezeigt wird, um zu prüfen, ob ein Codeelement andere Codeelemente enthält. Wählen Sie das Chevron aus, um das Codeelement zu erweitern. Um alle Codeelemente zu erweitern, drücken Sie die **STRG**+**ein** um alle Elemente auszuwählen, öffnen Sie das Kontextmenü für die Karte, und wählen Sie **Gruppe**, **erweitern**. Dieser Befehl ist nicht verfügbar, wenn das Erweitern aller Gruppen zu einer nicht verwendbaren Übersicht oder zu Speicherproblemen führt.|  
|Auf Codeelemente in der Übersicht bezogene Codeelemente.|Klicken Sie auf die **verwandte anzeigen** in der Symbolleiste der Codeübersicht auf die Schaltfläche, und wählen Sie den Typ verwandter Elemente, die Sie interessiert sind.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für das Codeelement. Wählen Sie eines der **anzeigen...** Elemente im Menü von der Art der Beziehung, die Sie interessieren. Beispielsweise können Sie Elemente, auf die das aktuelle Element verweist, Elemente, die auf das aktuelle Element verweisen, Basis- und abgeleitete Typen für Klassen, Methodenaufrufer und die enthaltenden Klassen, Namespaces sowie Assemblys anzeigen.<br /><br /> Weitere Informationen finden Sie unter [in diesem Thema](../modeling/map-dependencies-across-your-solutions.md).|  
|Kompilierte .NET-Assemblys (DLL oder EXE) oder Binärdateien.|Ziehen Sie die Assemblys oder Binärdateien, die sich außerhalb von Visual Studio befinden, in eine Übersicht.<br /><br /> Das Ziehen aus Windows-Explorer oder Datei-Explorer ist nur möglich, wenn der betreffende Explorer und Visual Studio auf der gleichen Berechtigungsstufe der Benutzerkontensteuerung (User Account Control, UAC) ausgeführt werden. Wenn z. B. die Benutzerkontensteuerung aktiviert ist und Sie Visual Studio als Administrator ausführen, wird der Ziehvorgang von Windows-Explorer oder Datei-Explorer blockiert.|  
  
###  <a name="AddNodes"></a>   
##### <a name="add-a-link-between-existing-code-elements"></a>Hinzufügen von Links zwischen vorhandenen Codeelementen  
  
1.  Wählen Sie das Quellcodeelement aus. Über dem Codeelement wird eine Symbolleiste angezeigt.  
  
     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")  
  
2.  Wählen Sie auf der Symbolleiste das erste Symbol, **erstellen neuen Link von diesem Knoten zu dem Knoten, auf den nächsten**.  
  
3.  Wählen Sie das Zielcodeelement aus. Zwischen den beiden Codeelementen wird ein Link angezeigt.  
  
 \- oder –  
  
1.  Wählen Sie das Quellcodeelement in der Übersicht aus.  
  
2.  Wenn Sie eine Maus installiert haben, bewegen Sie den Mauszeiger außerhalb der Begrenzungen der Übersicht.  
  
3.  Öffnen Sie die Code-Element-Kontextmenü, und wählen Sie **bearbeiten**, **hinzufügen**, **generischer Link**.  
  
4.  Wechseln Sie mithilfe der TABULATORTASTE zum Zielknotenelement für den Link.  
  
5.  Drücken Sie die **EINGABETASTE**.  
  
###  <a name="AddComments"></a>   
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Hinzufügen eines Kommentars zu einem vorhandenen Knoten in der Übersicht  
  
1.  Wählen Sie das Codeelement aus. Darüber wird eine Symbolleiste angezeigt.  
  
     ![Abhängigkeitsdiagramm-Symbolleiste](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")  
  
2.  Wählen Sie auf der Symbolleiste das dritte Symbol, **erstellen einen neuen Kommentarknoten mit einem neuen Link zum ausgewählten Knoten**.  
  
     \- oder –  
  
     Öffnen Sie das Kontextmenü für das Code-Element, und wählen Sie **bearbeiten**, **neuer Kommentar**.  
  
3.  Geben Sie Ihre Kommentare ein. Um auf eine neue Zeile eingeben, drücken Sie die **UMSCHALT** + **zurückgeben**.  
  
##### <a name="add-a-comment-to-the-map-itself"></a>Hinzufügen eines Kommentars zur Übersicht  
  
1.  Öffnen Sie das Kontextmenü für die Karte, und wählen Sie **bearbeiten**, **neuer Kommentar**.  
  
2.  Geben Sie Ihre Kommentare ein. Um auf eine neue Zeile eingeben, drücken Sie die **UMSCHALT** + **zurückgeben**.  
  
###  <a name="RenameNodes"></a>   
##### <a name="rename-a-code-element-or-link"></a>Umbenennen eines Codeelements oder Links  
  
1.  Wählen Sie das Codeelement oder den Link aus, das bzw. der umbenannt werden soll.  
  
2.  Drücken Sie **F2**, oder öffnen Sie das Kontextmenü, und wählen Sie **bearbeiten**, **umbenennen**.  
  
3.  Wenn das Eingabefeld in der Übersicht angezeigt wird, benennen Sie das Codeelement oder den Link um.  
  
     \- oder –  
  
4.  Öffnen Sie das Kontextmenü, und wählen Sie **bearbeiten**, **Eigenschaften**.  
  
5.  Bearbeiten der **Bezeichnung** Eigenschaft im Eigenschaftenfenster von Visual Studio.  
  
##### <a name="remove-a-code-element-or-link-from-the-map"></a>Entfernen eines Codeelements oder Links aus der Übersicht  
  
1.  Wählen Sie das Codeelement oder Link und drücken Sie die **löschen** Schlüssel.  
  
     \- oder –  
  
     Öffnen Sie das Kontextmenü für das Codeelement oder den Link, und wählen Sie **bearbeiten**, **entfernen**.  
  
2.  Wenn das Element oder einen Link zu einer Gruppe ist die **untergeordnete Elemente** Schaltfläche ![Symbol für untergeordnete Kinder](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") in der Gruppe angezeigt. Klicken Sie auf diese Option, um fehlende Elemente und Links abzurufen.  
  
-   Sie können Codeelemente und Links ohne Auswirkungen auf den zugrunde liegenden Code aus einer Übersicht entfernen. Wenn Sie diese löschen, werden die zugehörigen Definitionen aus der DGML-Datei (.dgml) entfernt.  
  
-   Die über die DGML-Datei durch Hinzufügen nicht definierter Codeelemente oder durch Verwenden früherer Versionen von Visual Studio erstellten Übersichten unterstützen diese Funktion nicht.  
  
##### <a name="flag-a-code-element-for-follow-up"></a>Kennzeichnen eines Codeelements zur Nachverfolgung  
  
1.  Wählen Sie das Codeelement oder den Link aus, das bzw. den Sie zur Nachverfolgung kennzeichnen möchten.  
  
2.  Öffnen Sie das Kontextmenü, und wählen Sie **bearbeiten**, **zur nachverfolgung kennzeichnen**.  
  
-   Das Codeelement erhält standardmäßig einen roten Hintergrund. Berücksichtigen Sie [einen Kommentar hinzufügen und](#AddComments) mit entsprechenden Nachverfolgungsinformationen.  
  
-   Die Hintergrundfarbe des Elements ändern oder deaktivieren Sie durch Auswählen der Nachverfolgungskennzeichnung **bearbeiten**, **andere Kennzeichenfarben**.  
  
##  <a name="a-namechangestylecodeorlinka-change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a>Ändern des Formats eines Codeelements oder links  
 Sie können die Symbole für Codeelemente und die Farben von Codeelementen und Links mithilfe vordefinierter Symbole und Farben ändern. Sie können z. B. eine Farbe auswählen, um Codeelemente und Links hervorzuheben, die eine bestimmte Kategorie oder Eigenschaft aufweisen. Dadurch können Sie bestimmte Bereiche der Übersicht kennzeichnen und sich auf diese Bereiche konzentrieren. Sie können benutzerdefinierte Symbole und Farben durch Bearbeiten der DGML-Datei für die Zuordnung angeben. finden Sie unter [Anpassen von Code maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>So wenden Sie eine vordefinierte Farbe oder ein vordefiniertes Symbol auf Codelemente oder Links mit einer bestimmten Kategorie oder Eigenschaft an  
  
1.  Wählen Sie auf der Symbolleiste der Map **Legende**.  
  
2.  In der **Legende** Feld, ob der Code Kategorie oder Eigenschaft bereits in der Liste angezeigt wird.  
  
3.  Wählen Sie die Kategorie oder Eigenschaft nicht in der Liste enthalten, ** + ** in der **Legende** und dann **Knoteneigenschaft**, **Knotenkategorie**, **Linkeigenschaft**, oder **Linkkategorie**. Wählen Sie dann die Eigenschaft oder Kategorie aus. Die Kategorie oder Eigenschaft wird jetzt der **Legende** Feld.  
  
    > [!NOTE]
    >  Zum Erstellen und Zuweisen einer Kategorie oder Eigenschaft auf ein Codeelement, können Sie die DGML-Datei der Map bearbeiten. finden Sie unter [Anpassen von Code maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
4.  In der **Legende** Feld, klicken Sie auf das Symbol neben der Kategorie oder Eigenschaft, die Sie hinzugefügt haben, oder Sie ändern möchten.  
  
5.  Orientieren Sie sich beim Auswählen des zu ändernden Stils an der folgenden Tabelle:  
  
    |**So ändern Sie die**|**Auswählen**|  
    |-----------------------|----------------|  
    |Hintergrundfarbe:|**Hintergrund**|  
    |Umrissfarbe|**Strich**|  
    |Textfarbe (der Buchstabe „f“ wird angezeigt, um das Ergebnis anzuzeigen)|**Vordergrundfarbe**|  
    |Symbol|**Symbole**|  
  
     Die **Farbpalettenauswahl** oder **Symbolsatzauswahl** im Dialogfeld zum Auswählen einer Farbe oder ein Symbol angezeigt wird.  
  
6.  In der **Farbpalettenauswahl** oder **Symbolsatzauswahl** (Dialogfeld), führen Sie einen der folgenden:  
  
    |**Anwenden einer**|**Auszuführende Schritte**|  
    |--------------------|-----------------------------|  
    |Farbsatz oder Symbolsatz|Öffnen Sie die **Farbe auswählen** (oder **Symbol**) **festlegen** Liste. Wählen Sie einen Farbsatz oder Symbolsatz aus.|  
    |Bestimmte Farbe oder bestimmtes Symbol|Öffnen Sie die Liste für Kategorie- bzw. Eigenschaftswerte. Wählen Sie eine Farbe oder ein Symbol aus.|  
  
    > [!NOTE]
    >  Sie neu anordnen, löschen oder vorübergehend deaktiviert Stile in der **Legende** Feld. Finden Sie unter [Feld Legende bearbeiten](#ModifyLegend).  
  
##  <a name="a-namemodifylegenda-edit-the-legend-box"></a><a name="ModifyLegend"></a>Bearbeiten Sie das Legende  
 Sie neu anordnen, löschen oder vorübergehend deaktiviert Stile in der **Legende** Feld:  
  
1.  Öffnen Sie das Kontextmenü für einen Stil in die **Legende** Feld.  
  
2.  Führen Sie eine der folgenden Aufgaben aus:  
  
    |**Aktion**|**Auswählen**|  
    |------------|----------------|  
    |Deaktivieren des Codeelements|**Deaktivieren**|  
    |Löschen des Codeelements|**Löschen**|  
    |Verschieben des Stils nach oben|**Nach oben verschieben**|  
    |Verschieben des Codeelements nach unten|**Nach unten verschieben**|  
  
##  <a name="a-namecopylegenda-copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a>Kopieren von Stilen aus einer Zuordnung zu einem anderen  
  
1.  Stellen Sie sicher, dass die **Legende** Feld in der quellübersicht angezeigt wird. Wenn sie nicht auf der Symbolleiste der Map angezeigt wird, klicken Sie auf **Legende**.  
  
2.  Öffnen Sie das Kontextmenü für die **Legende** Feld. Wählen Sie **Legende kopieren**.  
  
3.  Fügen Sie die Legende in der Zielübersicht ein.  
  
##  <a name="a-namemergemapsa-merge-code-maps"></a><a name="MergeMaps"></a>Zusammenführen von codeübersichten  
 Sie können Übersichten durch Kopieren und Einfügen von Codeelementen zwischen Übersichten zusammenführen. Wenn die Codeelementbezeichner übereinstimmen, entspricht das Einfügen von Codeelementen einem Zusammenführungsvorgang. Sie können diese Aufgabe vereinfachen, indem Sie alle zu visualisierenden Assemblys oder Binärdateien im selben Ordner ablegen, damit der vollständige Pfad jeder Assembly oder Binärdatei für jede Übersicht, die Sie zusammenführen möchten, gleich ist.  
  
 Alternativ können Sie diese Assemblys oder Binärdateien aus diesem Ordner in dieselbe Übersicht ziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)   
 [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Ermitteln Sie potenzieller Probleme mithilfe von Code Map-Analyzer](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md)   
 [Referenz zur Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)

