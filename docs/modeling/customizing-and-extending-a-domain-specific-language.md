---
title: "Anpassen und Erweitern einer domänenspezifischen Sprache | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Anpassen und Erweitern einer domänenspezifischen Sprache
Visual Studio zu modellieren und Visualisierung SDK (VMSDK) bietet mehrere Ebenen, die an dem Sie Modellierungstools definieren können:  
  
1.  Definieren Sie eine domänenspezifische Sprache (DSL) mit der DSL-Definitionsdiagramm. Sie können schnell eine DSL erstellen, mit einer diagrammdarstellung, einem lesbaren XML-Format und die grundlegenden Tools, die erforderlich sind, um Code und andere Artefakte generieren.  
  
     Weitere Informationen finden Sie unter [wie eine domänenspezifische Sprache definiert](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Optimieren Sie die DSL mit erweiterten Funktionen von DSL-Definition. Beispielsweise können Sie zusätzliche Links angezeigt werden, wenn der Benutzer ein Element erstellt vornehmen. Diese Techniken werden meist in der DSL-Definition, und einige erfordern einige Zeilen Programmcode.  
  
3.  Erweitern Sie Ihre Modellierungstools mit Programmcode. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird.  Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Wenn Sie die DSL-Definitionsdatei aktualisiert haben, vergessen Sie nicht, klicken Sie auf **alle Vorlagen transformieren** in der Symbolleiste des Projektmappen-Explorer vor der erneuten Erstellung der Projektmappe.  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>In diesem Abschnitt  
  
|Um diesen Effekt zu erzielen|In diesem Thema finden Sie unter|  
|----------------------------|-------------------------|  
|Kann der Benutzer die Farbe und den Stil Eigenschaften einer Form festlegen.|Mit der rechten Maustaste in der Klasse Form oder den Verbinder, zeigen Sie auf **verfügbare hinzufügen**, und klicken Sie auf ein Element.<br /><br /> Finden Sie unter [Anpassen der Darstellung im Diagramm](../modeling/customizing-presentation-on-the-diagram.md).|  
|Verschiedene Klassen von Modellelement, das im Diagramm, wie z. B. die anfängliche Höhe und Breite, Farbe, QuickInfos Freigabeeigenschaften ähnlich aussehen.|Verwenden Sie Vererbung zwischen Formen oder Connector-Klassen. Zuordnungen zwischen abgeleiteten Formen und abgeleiteter Domänenklassen, die Zuordnungsdetails von den übergeordneten Elementen erben.<br /><br /> Oder anderen Domänenklassen in die gleiche formklasse zuordnen.|  
|Eine Klasse von Modellelement wird von verschiedenen Formen Kontexten angezeigt.|Ordnen Sie mehrere Shape-Klasse auf die gleiche Domänenklasse. Wenn Sie die Projektmappe zu erstellen, führen Sie den Bericht, und enthalten Sie den Code, um zu entscheiden, welche Form des angeforderten.|  
|Shape-Farbe oder andere Features wie z. B. Schriftart geben die aktuellen Zustand.|Finden Sie unter [Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Erstellen Sie eine Regel, die die verfügbar gemachten Eigenschaften aktualisiert. Finden Sie unter [Regeln propagieren Änderungen im Modell](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Oder verwenden Sie OnAssociatedPropertyChanged() Funktionen nicht verfügbar gemacht werden, z. B. Link Pfeile oder Schriftart zu aktualisieren.|  
|Symbol zur Angabe des Status, Form geändert wird.|Legen Sie die Sichtbarkeit eines Decorator-Zuordnung im DSL-Details-Fenster. Suchen Sie nach mehrere Bild Decorator-Elemente auf der gleichen Position. Finden Sie unter [Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Oder überschreiben `ImageField.GetDisplayImage()`. Siehe das Beispiel in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>|  
|Festlegen eines Hintergrundbildes für ein beliebiges shape|Überschreiben Sie InitializeInstanceResources() um eine verankerte ImageField hinzuzufügen. Finden Sie unter [Anpassen der Darstellung im Diagramm](../modeling/customizing-presentation-on-the-diagram.md).|  
|Verschachteln von Formen in einer beliebigen Tiefe|Richten Sie eine rekursive Struktur einbetten. Definieren Sie BoundsRules um Formen enthalten. Finden Sie unter [Anpassen der Darstellung im Diagramm](../modeling/customizing-presentation-on-the-diagram.md).|  
|Fügen Sie Connectors an festen Positionen auf ein Element.|Definieren Sie eingebettete terminal Elemente durch kleine Ports im Diagramm dargestellt. Verwenden Sie BoundsRules, um die Ports an Stelle zu beheben. Finden Sie im Beispiel Verbindung Diagramm am [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Textfeld zeigt einen Wert von anderen Werten abgeleitet.|Ordnen Sie die Text-Decorator einer Domäneneigenschaft berechnet oder benutzerdefinierten Speicher. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).|  
|Weitergeben von Änderungen zwischen Modellelementen oder Formen|Finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).|  
|Weitergeben von Änderungen an Ressourcen wie andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen außerhalb des Speichers.|Finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Im Eigenschaftenfenster werden die Eigenschaften eines verwandten Elements angezeigt.|Richten Sie die Eigenschaft weiterleiten. Finden Sie unter [Anpassen des Eigenschaftenfensters](../modeling/customizing-the-properties-window.md).|  
|Eigenschaftenkategorien|Das Eigenschaftenfenster ist in Abschnitte Kategorien unterteilt. Legen Sie die **Kategorie** Ihrer Domäne-Eigenschaften. Eigenschaften mit dem gleichen Kategorienamen werden im selben Bereich angezeigt. Zudem lassen sich die **Kategorie** der Rolle in der Geschäftsbeziehung.|  
|Steuern des Zugriffs auf Domäneneigenschaften|Legen Sie **kann durchsucht werden** "false", um zu verhindern, dass eine Domäneneigenschaft im Eigenschaftenfenster angezeigt wird, zur Laufzeit. Sie können weiterhin auf Text-Decorator-Elementen zuordnen.<br /><br /> **UI-schreibgeschützt ist** verhindert, dass Benutzer eine Domäneneigenschaft ändern.<br /><br /> Programm den Zugriff auf die Domäneneigenschaft ist nicht betroffen.|  
|Ändern Sie den Namen, Symbol und die Sichtbarkeit von Knoten in der DSL-Modell-Explorer.|Finden Sie unter [im Modell-Explorer anpassen](../modeling/customizing-the-model-explorer.md).|  
|Kopieren, Ausschneiden und Einfügen aktivieren|Legen Sie die **Kopieren/Einfügen aktivieren** Eigenschaft der **Editor** Knoten im DSL-Explorer.|  
|Kopieren Sie Ressourcenlinks und ihre Ziele, wenn ein Element kopiert wird. Kopieren Sie z. B. Kommentare, die ein Element angefügt.|Legen Sie die **überträgt Kopie** Eigenschaft der Quellrolle (dargestellt durch die Linie auf einer Seite der domänenbeziehung in der DSL-Definitionsdiagramm).<br /><br /> Schreiben Sie Code zum Überschreiben von ProcessOnCopy, um komplexere Effekte zu erzielen.<br /><br /> Finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Löschen, neu zuordnen oder Verknüpfen von verwandten Elementen, wenn ein Element gelöscht wird.|Legen Sie die **überträgt Löschung** Wert, der eine Rolle. Für komplexere Effekte überschreiben `ShouldVisitRelationship` und `ShouldVisitRolePlayer` Methoden in der `MyDslDeleteClosure` -Klasse, definiert **"domainmodel.cs"**<br /><br /> Finden Sie unter [Anpassen des Löschverhaltens](../modeling/customizing-deletion-behavior.md)|  
|Shape-Layout und die Darstellung zu kopieren und Drag & Drop zu erhalten.|Hinzufügen von Formen und Konnektoren, die kopierte `ElementGroupPrototype`. Ist die einfachste Methode zum Überschreiben`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Fügen Sie Formen an einer ausgewählten Stelle ein, beispielsweise an der aktuelle Cursorposition.|Überschreiben Sie `ClipboardCommandSet.ProcessOnCopy()` verwenden die Speicherort-spezifische Version des `ElementOperations.Merge().` finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Erstellen Sie weitere Links einfügen|Überschreiben von ClipboardCommandSet.ProcessOnPasteCommand()|  
|Enable Elemente ziehen und Ablegen in diesem Diagramm andere DSLs und Windows|Finden Sie unter [Gewusst wie: hinzufügen einen Drag & Drop-Handler](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Ermöglichen einer Form oder ein Tool, um auf eine untergeordnete Form, wie z. B. einen Port gezogen werden, als es auf das übergeordnete Element gezogen wurden.|Definieren Sie eine Direktive für Elementzusammenführungen für Ziel Object-Klasse, das gelöschte Objekt an dem übergeordnete Element weiterleiten. Finden Sie unter [Anpassen der Elementerstellung und-Verschiebung](../modeling/customizing-element-creation-and-movement.md).|  
|Zulassen einer Form oder ein Tool, um auf eine Form gezogen werden und verfügen über zusätzliche Links oder Objekte erstellt werden. Geben Sie beispielsweise Folgendes ein, um einen Kommentar für ein Element abgelegt werden, es ist verknüpft werden, können.|Definieren Sie eine Direktive für Elementzusammenführungen für die zieldomänenklasse, und definieren Sie die Links generiert werden. In komplexen Fällen können Sie benutzerdefinierten Code hinzufügen. Finden Sie unter [Anpassen der Elementerstellung und-Verschiebung](../modeling/customizing-element-creation-and-movement.md).|  
|Erstellen Sie eine Gruppe von Elementen mit einem Tool. Angenommen, eine Komponente mit einer festen Anzahl von Ports.|Überschreiben Sie die Toolbox Initialisierungsmethode in "toolboxhelper.cs". Erstellen Sie ein Element Gruppe Prototyp (EGP), die Elemente und deren beziehungslinks enthält. Finden Sie unter [Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Schließen Sie die Prinzipal- und Port-Formen in der EGP oder definieren Sie BoundsRules um Anschluss-Formen zu positionieren, wenn der EGP instanziiert wird. Finden Sie unter [BoundsRules schränken Position und Größe](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Verwenden Sie ein Verbindungstool, um verschiedene Typen von Beziehungen zu instanziieren.|Der Verbindungs-Generator, der aufgerufen wird, indem Sie das Tool Link verbinden Direktiven (LCD) hinzugefügt. Die LCDs bestimmen den Typ der Beziehung der beiden Elemente aus. Um dies die Zustände der Elemente abhängig machen, können Sie benutzerdefinierten Code hinzufügen. Finden Sie unter [Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).|  
|Kurznotiz Tools – der Benutzer kann ein Tool zum Erstellen von vielen Formen oder Verbindungen in Folge doppelklicken.|Wählen Sie im DSL-Explorer die `Editor` Knoten. Legen Sie im Fenster Eigenschaften **Kurznotiz Toolboxelemente verwendet**.|  
|Definieren von Menübefehlen|Finden Sie unter [Gewusst wie: ändern ein Standardmenübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Beschränken Sie das Modell mit Validierungsregeln|Finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)|  
|Generieren Sie Code, Konfigurationsdateien oder Dokumente aus einer DSL.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Anpassen, wie die Modelle gespeichert werden, die Datei.|Finden Sie unter [Anpassen von Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Speichern Sie Modelle in Datenbanken oder anderen Medien.|Überschreiben Sie *Ihresprache*DocData<br /><br /> Finden Sie unter [Anpassen von Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Mehrere DSLs integriert werden, damit sie als Teil einer Anwendung zusammenarbeiten.|Finden Sie unter [Integrieren von Modellen mit Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Ihre DSL von Drittanbietern erweitert werden können und die Erweiterung steuern.|[Erweitern von DSL mittels MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: definieren eine domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


