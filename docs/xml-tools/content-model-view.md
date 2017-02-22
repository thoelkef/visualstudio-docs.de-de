---
title: "Inhaltsmodellansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Inhaltsmodellansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Inhaltsmodellansicht bietet eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten. Dazu zählen einfache und komplexe Typen, Elemente, Modellgruppen, Attribute und Attributgruppen.XML\-Kommentare und \-Verarbeitungsanweisungen können nicht in der Inhaltsmodellansicht angezeigt werden.Die Inhaltsmodellansicht enthält zwei Bereiche: einen **Arbeitsbereich** mit einer Liste der Knoten im [Arbeitsbereich des XML\-Schema\-Designers](../xml-tools/xml-schema-designer-workspace.md) und die Entwurfsoberfläche, auf der das Inhaltsmodell der im **Arbeitsbereich** ausgewählten Schemaknoten angezeigt wird.Die Inhaltsmodellansicht enthält auch die Symbolleiste des XML\-Schema\-Designers und die Breadcrumb\-Leiste.  
  
 Das folgende Bild zeigt den Arbeitsbereich mit sechs Schemaknoten.Der `purchaseOrder`\-Knoten ist im Arbeitsbereich ausgewählt und wird auf der Entwurfsoberfläche angezeigt.  
  
 ![Inhaltsmodellansicht im XML&#45;Schema&#45;Designer](../xml-tools/media/xsddesigner_contentmodelview.gif "XSDDesigner\_ContentModelView")  
  
## Arbeitsbereich  
 Nachdem Sie dem Arbeitsbereich Knoten hinzugefügt haben, wird die Liste der Knoten im **Arbeitsbereich** der Inhaltsmodellansicht angezeigt.Wenn Sie im **Arbeitsbereich** Knoten auswählen, werden sie auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.Verwenden Sie die XSD\-Designer\-Symbolleiste, das Kontextmenü des **Arbeitsbereichs** oder die ENTF\-TASTE, um Knoten aus dem Arbeitsbereich zu löschen.  
  
 Informationen zum Hinzufügen von Knoten finden Sie im Abschnitt "Hinzufügen von Knoten zum Arbeitsbereich" unter [Arbeitsbereich des XML\-Schema\-Designers](../xml-tools/xml-schema-designer-workspace.md).  
  
## Entwurfsoberfläche  
 Wenn Sie einen Knoten im Arbeitsbereich auswählen, wird er der Entwurfsoberfläche der Inhaltsmodellansicht hinzugefügt, wo Sie die Details des Knotens anzeigen können.  
  
 Das Inhaltsmodell eines Knotens wird durch eine erweiterbare grafische Struktur mit Elementen und Attributen als Strukturknoten dargestellt.Standardmäßig wird nur eine Ebene erweitert.Weitere Informationen wie Compositors, Typnamen, Gruppen und andere Container werden \(bei erweiterter Struktur\) auf einer vertikalen Leiste neben den zugehörigen Elementen und Attributen angezeigt.Wenn Sie auf einen vertikalen Balken doppelklicken, wird er horizontal dargestellt, und die Struktur wird reduziert.Wenn Sie auf einen horizontalen Balken doppelklicken, wird er vertikal dargestellt, und die Struktur wird erweitert.Durch Auswahl des vertikalen Balkens werden alle Knoten im Container ausgewählt.Rechts neben einem Knoten werden Erweiterungsschaltflächen angezeigt, wenn ein Element erweitert oder reduziert werden kann.  
  
 Wenn die Entwurfsoberfläche leer ist, werden der XML\-Editor, der XML\-Schema\-Explorer und das Wasserzeichen angezeigt.Das *Wasserzeichen* ist eine Liste von Links zu allen Ansichten des XSD\-Designers.Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt: "Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben."  
  
## Breadcrumb\-Leiste  
 Die Breadcrumb\-Leiste am unteren Rand der Inhaltsmodellansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet.  
  
## Kontextmenüs  
 Wenn Sie auf der Entwurfsoberfläche oder im Arbeitsbereich mit der rechten Maustaste auf ein Element klicken, wird ein Kontextmenü angezeigt.In der folgenden Tabelle werden die Optionen beschrieben, die für die Entwurfsoberfläche der Inhaltsmodellansicht verfügbar sind.  
  
|Option|Beschreibung|  
|------------|------------------|  
|**In XML\-Schema\-Explorer anzeigen**|Legt den Fokus auf den Schema\-Explorer und hebt den Schemasetknoten hervor.|  
|**In Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|  
|**Beispiel\-XML generieren**|Ist nur für globale Elemente verfügbar.Generiert eine Beispiel\-XML\-Datei für das globale Element.|  
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs\-\/Dokumentationsknoten ein bzw. aus.|  
|**Diagramm als Bild exportieren…**|Speichert die Entwurfsoberfläche in einer XPS\-Datei.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML\-Editor.Das im XML\-Schema\-Explorer ausgewählte Element wird auch im XML\-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** \(sofern es noch nicht geöffnet ist\).In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
 In der folgenden Tabelle werden die Optionen beschrieben, die für den Arbeitsbereich verfügbar sind.  
  
|Option|Beschreibung|  
|------------|------------------|  
|**In XML\-Schema\-Explorer anzeigen**|Legt den Fokus auf den Schema\-Explorer und hebt den Schemasetknoten hervor.|  
|**In Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|  
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|  
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Beispiel\-XML generieren**|Ist nur für globale Elemente verfügbar.Generiert eine Beispiel\-XML\-Datei für das globale Element.|  
|**Alle auswählen**|Wählt alle Knoten im Arbeitsbereich aus.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML\-Editor.Das im XML\-Schema\-Explorer ausgewählte Element wird auch im XML\-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** \(sofern es noch nicht geöffnet ist\).In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## Eigenschaftenfenster  
 Verwenden Sie das Kontextmenü, um das Fenster **Eigenschaften** zu Beginn zu öffnen.Das Fenster **Eigenschaften** wird standardmäßig in der rechten unteren Ecke von Visual Studio angezeigt.Wenn Sie auf einen in der Inhaltsmodellansicht gerenderten Knoten klicken, werden die Eigenschaften dieses Knotens im Fenster **Eigenschaften** angezeigt.  
  
## XSD\-Designer\-Symbolleiste  
 Die folgenden XSD\-Designer\-Symbolleistenschaltflächen sind aktiviert, wenn die Inhaltsmodellansicht aktiv ist.  
  
 ![Symbolleiste für XML&#45;Schema&#45;Designer](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Ausgangsansicht anzeigen**|Wechselt zur [Ausgangsansicht](../xml-tools/start-view.md).Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG\+1**.|  
|**Inhaltsmodellansicht anzeigen**|Wechselt zur [Inhaltsmodellansicht](../xml-tools/content-model-view.md).Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG\+2**.|  
|**Diagrammansicht anzeigen**|Wechselt zur [Diagrammansicht](../xml-tools/graph-view.md).Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG\+3**.|  
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|  
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs\-\/Dokumentationsknoten ein bzw. aus.|  
  
## Schwenken\/Bildlauf  
 Sie können die Entwurfsoberfläche mit den Bildlaufleisten oder durch Drücken der STRG\-TASTE und gleichzeitiges Klicken und Ziehen der Maus schwenken.Wenn Sie die Entwurfsoberfläche mittels Klicken und Ziehen schwenken, wird der Cursor als vier sich kreuzende und in unterschiedliche Richtungen weisende Pfeile angezeigt.  
  
## Rückgängig\/Wiederholen  
 Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Inhaltsmodellansicht für folgende Aktionen aktiviert:  
  
-   Hinzufügen eines einzelnen Knotens per Drag & Drop  
  
-   Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema\-Explorer  
  
-   Hinzufügen von Knoten aus der Ausgangsansicht  
  
-   Löschen einzelner oder mehrerer Knoten  
  
## Zoom  
 Die Zoomfunktion befindet sich in der unteren rechten Ecke der Inhaltsmodellansicht.  
  
 Der Zoomfaktor kann wie folgt gesteuert werden:  
  
-   Halten Sie die STRG\-TASTE gedrückt, und drehen Sie das Mausrad, während Sie die Maus über die Oberfläche der Inhaltsmodellansicht bewegen.  
  
-   Verwenden Sie das Schieberegler\-Steuerelement.Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.  
  
 Der Zoomschieberegler ist nicht transparent, wenn Sie ihn auswählen, mit der Maus darauf zeigen oder mit der STRG\-TASTE und dem Mausrad zoomen. Ansonsten ist er transparent.  
  
## Integration des XML\-Editors  
 Sie können über das Kontextmenü zwischen dem XSD\-Designer und dem XML\-Editor hin\- und herwechseln.  
  
 Wenn Sie im XML\-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Inhaltsmodellansicht synchronisiert.Weitere Informationen finden Sie unter [Integration in den XML\-Editor](../xml-tools/integration-with-xml-editor.md).  
  
## Siehe auch  
 [Arbeitsbereich des XML\-Schema\-Designers](../xml-tools/xml-schema-designer-workspace.md)