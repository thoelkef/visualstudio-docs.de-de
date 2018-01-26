---
title: "Anpassen und Erweitern einer domänenspezifischen Sprache | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 581d4e907185339aa16bacce19a9bf31ff4d121d
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Anpassen und Erweitern einer domänenspezifischen Sprache
Visual Studio zu modellieren und Visualisierung SDK (VMSDK) bietet mehrere Ebenen, die an dem Sie Modellierungstools definieren können:  
  
1.  Definieren Sie eine domänenspezifische Sprache (DSL) mit der DSL-Definitionsdiagramm. Sie können schnell eine DSL erstellen, mit einer Verbindungskabel als Diagramm Notation, einem lesbaren Format der XML- und der grundlegenden Tools, die erforderlich sind, um Code und andere Artefakte generieren.  
  
     Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Optimieren Sie die DSL, indem Sie mithilfe von erweiterten Funktionen der DSL-Definition. Beispielsweise können Sie zusätzliche Links angezeigt werden, wenn der Benutzer ein Element erstellt vornehmen. Diese Techniken werden hauptsächlich erzielt, in der DSL-Definition, und einige wenige Zeilen des Programmcodes erfordern.  
  
3.  Erweitern Sie Ihre Modellierungstools mithilfe von Programmcode. VMSDK wurde speziell dafür entwickelt, die Integration Ihrer Erweiterungen in den Code zu vereinfachen, der aus der DSL-Definition generiert wird.  Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Wenn Sie die Definitionen der DSL-Datei aktualisiert haben, vergessen Sie nicht auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer vor dem Neuerstellen der Projektmappe.  
  
##  <a name="customShapes"></a>In diesem Abschnitt  
  
|Um diesen Effekt zu erzielen.|In diesem Thema finden Sie unter|  
|----------------------------|-------------------------|  
|Ermöglicht dem Benutzer zum Festlegen der Farbe und des Stils Eigenschaften einer Form.|Mit der rechten Maustaste der Form oder den Verbinder-Klasse, zeigen Sie auf **hinzufügen verfügbar gemachten**, und klicken Sie auf ein Element.<br /><br /> Finden Sie unter [Anpassen der Darstellung des Diagramms](../modeling/customizing-presentation-on-the-diagram.md).|  
|Verschiedene Klassen von Modellelement in etwa wie im Diagramm, z. B. die anfängliche Höhe und Breite, Farbe, QuickInfos Freigabeeigenschaften aussehen.|Verwenden Sie Vererbung zwischen Formen oder konnektorklassen. Zuordnungen zwischen abgeleiteten Formen und von abgeleiteten Domänenklassen erben die Zuordnungsdetails von den übergeordneten Elementen.<br /><br /> Oder anderen Domäne Zuordnungsklassen auf die gleiche formenklasse.|  
|Eine Klasse von Modellelement wird durch die Kontexte für unterschiedliche Formen angezeigt.|Ordnen Sie mehr als eine Form "-Klasse, auf die gleiche Domänenklasse. Wenn Sie die Projektmappe zu erstellen, führen Sie den Fehlerbericht, und geben Sie den angeforderte Code, um zu entscheiden, welche Form verwendet.|  
|Geben Sie Shape-Farbe oder andere Features wie z. B. Schriftart aktuellen Status an.|Finden Sie unter [Aktualisieren von Formen und Konnektoren entsprechend das Modell](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Erstellen Sie eine Regel, die die verfügbar gemachten Eigenschaften aktualisiert. Finden Sie unter [Regeln Weitergeben von Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Oder verwenden Sie OnAssociatedPropertyChanged() Funktionen nicht verfügbar gemacht werden, z. B. Link Pfeile oder Schriftart zu aktualisieren.|  
|Symbol "in Form von Änderungen zur Angabe des Status.|Legen Sie die Sichtbarkeit der Decorator Zuordnung im Fenster DSL-Detailfenster. Suchen Sie nach mehreren Image Decorator-Elementen auf der gleichen Position. Finden Sie unter [Aktualisieren von Formen und Konnektoren entsprechend das Modell](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Oder außer Kraft setzen `ImageField.GetDisplayImage()`. Siehe das Beispiel in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Legen Sie ein Hintergrundbild für jede Form|Zum Hinzufügen einer verankerten ImageField InitializeInstanceResources() zu überschreiben. Finden Sie unter [Anpassen der Darstellung des Diagramms](../modeling/customizing-presentation-on-the-diagram.md).|  
|Verschachteln von Formen in einer beliebigen Tiefe|Richten Sie eine rekursive Struktur einbetten. Definieren Sie BoundsRules um Formen enthalten. Finden Sie unter [Anpassen der Darstellung des Diagramms](../modeling/customizing-presentation-on-the-diagram.md).|  
|Fügen Sie Connectors an festen Positionen auf ein Element Grenze.|Definieren Sie eingebettete terminal Elementen, die durch kleine Ports im Diagramm dargestellt. Verwenden Sie BoundsRules, um die Ports Problem zu beheben. Finden Sie unter dem Diagramm Circuit-Beispiel in [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Textfeld "zeigt einen Wert aus anderen Werten abgeleitet.|Ordnen Sie den Text Decorator-Element eine Eigenschaft "Domain" berechnet oder einen benutzerdefinierten Speicher. Weitere Informationen finden Sie unter [berechnet und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).|  
|Weitergeben von Änderungen zwischen Modellelementen oder zwischen Formen|Finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).|  
|Weitergeben von Änderungen an Ressourcen, z. B. andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen außerhalb des Informationsspeichers.|Finden Sie unter [Ereignishandler Weitergeben von Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Klicken Sie im Eigenschaftenfenster zeigt die Eigenschaften eines verknüpften Elements.|Richten Sie die Eigenschaft weiterleiten. Finden Sie unter [Anpassen des Eigenschaftenfensters](../modeling/customizing-the-properties-window.md).|  
|Eigenschaftenkategorien|Das Eigenschaftenfenster ist in Abschnitte Kategorien unterteilt. Legen Sie die **Kategorie** Ihrer Domäne-Eigenschaften. Eigenschaften mit dem gleichen Kategorienamen werden im gleichen Abschnitt angezeigt. Sie können auch Festlegen der **Kategorie** einer Beziehung-Rolle.|  
|Steuern des Zugriffs auf Domäneneigenschaften|Legen Sie **durchsuchbar ist** "false", um zu verhindern, dass eine Eigenschaft "Domain" im Eigenschaftenfenster angezeigt wird, zur Laufzeit. Sie können weiterhin auf Text Decorators zuordnen.<br /><br /> **Read Only-Benutzeroberfläche ist** verhindert, dass Benutzer am Ändern einer Eigenschaft "Domain".<br /><br /> Programm den Zugriff auf die Eigenschaft "Domain" wird nicht beeinflusst.|  
|Ändern Sie den Namen, Symbol und Sichtbarkeit der Knoten in der DSL-Modell-Explorer.|Finden Sie unter [Anpassen der Modell-Explorer](../modeling/customizing-the-model-explorer.md).|  
|Aktivieren Sie kopieren, Ausschneiden und einfügen|Festlegen der **aktivieren Kopieren Einfügen** Eigenschaft von der **Editor** Knoten im Explorer für DSL.|  
|Kopieren Sie Ressourcenlinks und ihre Ziele aus, wenn ein Element kopiert wird. Kopieren Sie z. B. Kommentare, die ein Element angefügt.|Legen Sie die **weitergibt Kopie** Eigenschaft von der Rolle "Quelle" (dargestellt durch die Zeile mit einer Seite der domänenbeziehung in der DSL-Definitionsdiagramm).<br /><br /> Schreiben Sie Code zum Überschreiben von ProcessOnCopy, um komplexere Effekte erzielen.<br /><br /> Finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Löschen Sie, neu zuordnen Sie, oder verknüpfen Sie verwandte Elemente aus, wenn ein Element gelöscht wird.|Legen Sie die **weitergibt löschen** Wert einer Beziehung-Rolle. Für komplexere Effekte überschreiben `ShouldVisitRelationship` und `ShouldVisitRolePlayer` Methoden in der `MyDslDeleteClosure` in definierte Klasse **DomainModel.cs**<br /><br /> Finden Sie unter [Anpassen des Verhaltens löschen](../modeling/customizing-deletion-behavior.md)|  
|Behalten Sie die Form Layout und die Darstellung auf Kopieren und Drag & Drop.|Fügen Sie die Formen und Konnektoren zu den kopierten `ElementGroupPrototype`. Ist die einfachste Methode zum Überschreiben`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).|  
|Fügen Sie Formen an einer ausgewählten Stelle ein, beispielsweise an der aktuelle Cursorposition.|Überschreiben Sie `ClipboardCommandSet.ProcessOnCopy()` die standortspezifische Version von `ElementOperations.Merge().` finden Sie unter [Kopierverhalten anpassen](../modeling/customizing-copy-behavior.md).|  
|Erstellen Sie zusätzliche Links einfügen|ClipboardCommandSet.ProcessOnPasteCommand() überschreiben|  
|Enable ziehen und Ablegen in diesem Diagramm andere konzentriert und die Windows-Elemente|Finden Sie unter [wie: Hinzufügen eines Drag-and-Drop-Ereignishandlers](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Zulassen einer Form oder ein Tool, um auf eine Form "Kind", beispielsweise ein Anschluss gezogen werden, als wäre er auf das übergeordnete Element gezogen wurden.|Definieren Sie eine Merge-Element-Direktive für die Ziel-Objektklasse, das gelöschte Objekt an dem übergeordnete Element weitergeleitet. Finden Sie unter [anpassen Element erstellen und die Bewegung](../modeling/customizing-element-creation-and-movement.md).|  
|Zulassen einer Form oder ein Tool, um auf eine Form gezogen werden und verfügen über zusätzliche Links oder Objekte erstellt. Geben Sie beispielsweise Folgendes ein, um einen Kommentar an, auf ein Element abgelegt werden, ist es verknüpft sein, können.|Definieren Sie eine Element-Direktive zusammenführen, für die Zielklasse für die Domäne, und definieren Sie die Links generiert werden soll. In komplexen Fällen können Sie benutzerdefinierten Code hinzufügen. Finden Sie unter [anpassen Element erstellen und die Bewegung](../modeling/customizing-element-creation-and-movement.md).|  
|Erstellen Sie eine Gruppe von Elementen mit einem einzigen Tool. Angenommen, eine Komponente mit einem festen Satz von Ports.|Überschreiben Sie die Toolbox Initialisierungsmethode in ToolboxHelper.cs. Erstellen Sie ein Element Gruppe Prototyp (EGP), die Elemente und deren beziehungslinks enthält. Finden Sie unter [Anpassen von Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Schließen Sie die Formen Prinzipalobjekten und den Port in der EGP, oder definieren Sie BoundsRules, um die Port-Formen zu positionieren, bei der Instanziierung der EGP. Finden Sie unter [BoundsRules schränken Position und Größe](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Verwenden Sie eine Verbindungstool, um mehrere Typen von Beziehung zu instanziieren.|Fügen Sie Link verbinden Direktiven (LCD) des Verbindung-Generators, der vom Tool aufgerufen wird. Die LCDs bestimmen den Typ der Beziehung zwischen den zwei Elementen. Um dies die Zustände der Elemente abhängig machen, können Sie benutzerdefinierten Code hinzufügen. Finden Sie unter [Anpassen von Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md).|  
|Persistente Tools – der Benutzer kann jedes Tool zum Erstellen von vielen Formen oder-Verbinder nacheinander doppelklicken.|Wählen Sie im Explorer für DSL, die `Editor` Knoten. Legen Sie im Fenster Eigenschaften **Kurznotiz Toolboxelemente verwendet**.|  
|Definieren Sie Befehle im Menü|Finden Sie unter [Vorgehensweise: Ändern Sie einen Standardmenü-Befehl](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Das Modell mit Validierungsregeln zu beschränken|Finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)|  
|Generieren Sie Code, Konfigurationsdateien oder Dokumente von DSL.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Anpassen, wie die Modelle gespeichert werden, die Datei.|Finden Sie unter [anpassen, Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Speichern Sie Modelle in Datenbanken oder ein anderes Medium.|Überschreiben Sie *YourLanguage*DocData<br /><br /> Finden Sie unter [anpassen, Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrieren Sie mehrere konzentriert, damit sie als Teil einer Anwendung zusammenarbeiten.|Finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Zulassen Sie der DSL von Drittanbietern erweitert werden, und steuern Sie die Erweiterung zu.|[Erweitern von DSL mittels MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>Siehe auch

[Gewusst wie: definieren eine domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
[Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
[Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]