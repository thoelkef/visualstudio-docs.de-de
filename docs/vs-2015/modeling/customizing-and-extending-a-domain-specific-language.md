---
title: Anpassen und Erweitern einer domänenspezifischen Sprache | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1dc596909862c2ebb490fa478e1f5f71f88dd7ac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106643"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Anpassen und Erweitern einer domänenspezifischen Sprache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Modellierung und Visualisierung SDK (VMSDK) bietet mehrere Ebenen, die an dem Sie die Tools zur Modellierung definieren können:  
  
1. Definieren Sie eine domänenspezifische Sprache (DSL) mithilfe von DSL-Definitionsdiagramm. Sie können schnell eine DSL erstellen, mit einer diagrammdarstellung, einem lesbaren XML-Format und die grundlegenden Tools, die zum Generieren von Code und andere Artefakte erforderlich sind.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  
  
2. Optimieren Sie die DSL, indem Sie mithilfe von erweiterten Funktionen von der DSL-Definition. Beispielsweise können Sie vornehmen, weitere Links werden angezeigt, wenn der Benutzer ein Element erstellt werden sollen. Diese Verfahren bestehen meist in der DSL-Definition, und einige erfordern einige Zeilen Programmcode.  
  
3. Erweitern Sie Ihre Modellierungstools mit Programmcode. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird.  Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Wenn Sie die DSL-Definitionen-Datei aktualisiert haben, vergessen Sie nicht auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer vor dem Neuerstellen der Projektmappe.  
  
## <a name="customShapes"></a> In diesem Abschnitt  
  
|Um diesen Effekt zu erzielen.|In diesem Thema finden Sie unter|  
|----------------------------|-------------------------|  
|Ermöglicht dem Benutzer zum Festlegen der Eigenschaften für Farbe und den Stil einer Form.|Mit der rechten Maustaste der Form oder einen Verbinder-Klasse, zeigen Sie auf **verfügbare hinzufügen**, und klicken Sie auf ein Element.<br /><br /> Finden Sie unter [Anpassen der Darstellung im Diagramm](../modeling/customizing-presentation-on-the-diagram.md).|  
|Verschiedene Klassen von Modellelement in etwa wie im Diagramm, das Freigeben von Eigenschaften wie die ursprüngliche Höhe und Breite, Farbe, QuickInfos aussehen.|Verwenden Sie die Vererbung zwischen Formen oder die Connector-Klassen. Zuordnungen zwischen abgeleiteten Formen und abgeleiteter Domänenklassen, die Details der Zuordnung von den übergeordneten Elementen erben.<br /><br /> Oder anderen Domänenklassen die gleiche formklasse zuordnen.|  
|Eine Klasse von Modellelement wird durch verschiedene Formen Kontexten angezeigt.|Ordnen Sie mehr als eine formklasse, mit der gleichen Domänenklasse. Wenn Sie die Projektmappe erstellen, führen Sie den Fehlerbericht, und geben Sie den angeforderten Code, um zu entscheiden, welche Form verwenden.|  
|Shape-Farbe oder andere Features wie z. B. Schriftart angeben, aktuellen Status.|Finden Sie unter [Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Erstellen Sie eine Regel, die verfügbar gemachten Eigenschaften aktualisiert. Finden Sie unter [Regeln propagieren Änderungen im Modell](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Oder verwenden Sie OnAssociatedPropertyChanged() zum Aktualisieren von Funktionen wie z. B. links-Taste oder die Schriftart nicht verfügbar gemacht werden.|  
|Symbol in Form von Änderungen an Zustand.|Legen Sie die Sichtbarkeit der Decorator-Zuordnung im DSL-Details-Fenster. Suchen Sie nach mehreren Image Decorator-Elemente auf der gleichen Position. Finden Sie unter [Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Oder, außer Kraft setzen `ImageField.GetDisplayImage()`. Siehe das Beispiel in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Festlegen eines Hintergrundbilds für eine beliebige Form|Überschreiben Sie InitializeInstanceResources(), um eine verankerten ImageField hinzuzufügen. Finden Sie unter [Anpassen der Darstellung im Diagramm](../modeling/customizing-presentation-on-the-diagram.md).|  
|Verschachteln von Formen in einer beliebigen Tiefe|Richten Sie eine rekursive Struktur einbetten. Definieren Sie BoundsRules um Formen enthalten. Finden Sie unter [Anpassen der Darstellung im Diagramm](../modeling/customizing-presentation-on-the-diagram.md).|  
|Fügen Sie Connectors, die an festen Positionen auf ein Element der Grenze.|Definieren Sie die eingebettete terminal Elementen, die durch kleine Ports im Diagramm dargestellt. Verwenden Sie BoundsRules, um die Ports an Stelle zu beheben. Finden Sie unter der Leitung Diagramm-Sample bei [Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Textfeld zeigt einen Wert aus anderen Werten abgeleitet.|Ordnen Sie das Text-Decorator-Element eine Eigenschaft "Domain" Calculated "oder" benutzerdefinierte Speicher. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).|  
|Weitergeben von Änderungen zwischen Modellelementen oder Formen|Finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).|  
|Weitergeben von Änderungen an Ressourcen wie z. B. andere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen außerhalb des Speichers.|Finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Klicken Sie im Eigenschaftenfenster werden Eigenschaften eines verwandten Elements angezeigt.|Richten Sie die Eigenschaft weiterleiten. Finden Sie unter [Anpassen des Eigenschaftenfensters](../modeling/customizing-the-properties-window.md).|  
|Eigenschaftenkategorien|Das Fenster "Eigenschaften" ist in Abschnitte namens Kategorien unterteilt. Legen Sie die **Kategorie** Ihrer Domäne-Eigenschaften. Eigenschaften mit dem gleichen Kategorienamen im gleichen Abschnitt angezeigt. Sie können auch Festlegen der **Kategorie** einer Rolle der Beziehung.|  
|Steuern des Zugriffs auf Domäneneigenschaften|Legen Sie **kann durchsucht werden** "false", um zu verhindern, dass eine Eigenschaft "Domain", die zur Laufzeit in das Fenster "Eigenschaften" angezeigt werden. Sie können immer noch, Text-Decorator-Elementen zuordnen.<br /><br /> **UI-schreibgeschützt ist** Benutzer daran gehindert, eine Eigenschaft "Domain" ändern.<br /><br /> Programm den Zugriff auf die Eigenschaft "Domain" ist nicht betroffen.|  
|Ändern Sie den Namen, Symbol und die Sichtbarkeit von Knoten in das DSL Modell-Explorer.|Finden Sie unter [Anpassen des Modell-Explorers](../modeling/customizing-the-model-explorer.md).|  
|Aktivieren Sie, kopieren, Ausschneiden und einfügen|Legen Sie die **Kopieren/Einfügen aktivieren** Eigenschaft der **Editor** Knoten im DSL-Explorer.|  
|Kopieren Sie Verweislinks und ihre Ziele aus, wenn ein Element kopiert wird. Kopieren Sie beispielsweise auf ein Element angefügten Kommentare.|Legen Sie die **überträgt Kopie** Eigenschaft der Rolle "Source" (dargestellt durch die Linie auf einer Seite der domänenbeziehung, in der DSL-Definitionsdiagramm).<br /><br /> Schreiben Sie Code zum Überschreiben von ProcessOnCopy, um komplexere Effekte zu erzielen.<br /><br /> Finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Löschen, Neuzuordnen des übergeordneten Elements oder verwandten Elemente neu verknüpfen, wenn ein Element gelöscht wird.|Legen Sie die **löschen weitergeben** Wert, der eine Rolle. Für komplexere Auswirkungen, außer Kraft setzen `ShouldVisitRelationship` und `ShouldVisitRolePlayer` Methoden in der `MyDslDeleteClosure` in definierte Klasse **"domainmodel.cs"**<br /><br /> Finden Sie unter [Anpassen des Löschverhaltens](../modeling/customizing-deletion-behavior.md)|  
|Behalten Sie die Shape-Layout und die Darstellung zu kopieren und Drag & Drop.|Hinzufügen von Formen und Konnektoren zu den kopierten `ElementGroupPrototype`. Ist die einfachste Methode zum Überschreiben `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Fügen Sie Formen an einer ausgewählten Stelle ein, beispielsweise an der aktuelle Cursorposition.|Außer Kraft setzen `ClipboardCommandSet.ProcessOnCopy()` verwenden die positionsspezifische Version von `ElementOperations.Merge().` finden Sie unter [Anpassen des Verhaltens beim Kopieren](../modeling/customizing-copy-behavior.md).|  
|Erstellen Sie weitere Links einfügen|Override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Aktivierung der Drag & ein, und legen Sie in diesem Diagramm andere DSLs oder UML-Diagramme und Windows-Elemente|Weitere Informationen finden Sie unter [How to: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Können Sie eine Form oder das Tool auf einer untergeordneten Form, wie z. B. einen Port, gezogen werden, als ob sie auf das übergeordnete Element gezogen wurden.|Definieren Sie eine Direktive für Elementzusammenführungen für die Klasse des Ziel-Objekt, das abgelegte Objekt an dem übergeordnete Element weitergeleitet. Finden Sie unter [Anpassen der Elementerstellung und-Verschiebung](../modeling/customizing-element-creation-and-movement.md).|  
|Ermöglichen einer Form oder ein Tool, um auf eine Form gezogen werden und verfügen über zusätzliche Links oder Objekte erstellt. Geben Sie beispielsweise Folgendes ein, um einen Kommentar an, auf ein Element abgelegt werden, für die sie verknüpft werden, wird, zu ermöglichen.|Definieren Sie auf die zieldomänenklasse eine Direktive für Elementzusammenführungen, und definieren Sie die Links generiert werden soll. In komplexen Fällen können Sie benutzerdefinierten Code hinzufügen. Finden Sie unter [Anpassen der Elementerstellung und-Verschiebung](../modeling/customizing-element-creation-and-movement.md).|  
|Erstellen Sie eine Gruppe von Elementen mit einem Tool aus. Z. B. eine Komponente mit einem festen Satz von Ports.|Überschreiben Sie die Toolbox Initialisierungsmethode in "toolboxhelper.cs". Erstellen Sie ein Element Gruppe Prototyp (EGP), die die Elemente und ihre beziehungslinks enthält. Finden Sie unter [Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Schließen Sie die Dienstprinzipal und die Portnummer Formen in der EGP oder definieren Sie BoundsRules, um die Anschluss-Formen zu positionieren, wenn die EGP instanziiert wird. Finden Sie unter [BoundsRules schränken Position und Größe](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Verwenden Sie ein Verbindungstool, um verschiedene Typen von Beziehungen zu instanziieren.|Fügen Sie den Verbindungs-Generator, der vom Tool aufgerufen wird Link verbinden Direktiven LCD-hinzu. Die LCDs bestimmen Sie den Typ der Beziehung aus den Typen der beiden Elemente. Um dies die Zustände der Elemente abhängig machen, können Sie benutzerdefinierten Code hinzufügen. Finden Sie unter [Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).|  
|Kurznotiz Tools – kann der Benutzer ein Tool zum Erstellen von vielen Formen oder-Verbinder in Folge doppelklicken.|Wählen Sie im DSL-Explorer die `Editor` Knoten. Legen Sie im Eigenschaftenfenster **Kurznotiz Toolboxelemente verwendet**.|  
|Definieren von Menübefehlen|Weitere Informationen finden Sie unter [How to: Ändern eines Standardmenübefehls](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Das Modell mit Validierungsregeln zu beschränken|Finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)|  
|Generieren Sie Code, Konfigurationsdateien oder Dokumenten aus einer DSL.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Anpassen, wie die Modelle gespeichert werden, die Datei.|Finden Sie unter [Anpassen von Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Speichern Sie Modelle, in Datenbanken oder andere Medien.|Außer Kraft setzen *Ihresprache*docdata-Objekt<br /><br /> Finden Sie unter [Anpassen von Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Mehrere DSLs integriert werden, damit sie als Teil einer Anwendung funktionieren.|Finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Ihre DSL von Drittanbietern erweitert werden können und die Erweiterung zu steuern.|[Erweitern von DSL mittels MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
