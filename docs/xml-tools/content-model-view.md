---
title: Inhaltsmodellansicht im XML-Schema-Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7f04c482149cbc063a3788dd6be44c643bae6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751792"
---
# <a name="content-model-view"></a>Inhaltsmodellansicht

Die Inhaltsmodellansicht bietet eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten. Dazu zählen einfache und komplexe Typen, Elemente, Modellgruppen, Attribute und Attributgruppen. XML-Kommentare und -Verarbeitungsanweisungen können nicht in der Inhaltsmodellansicht angezeigt werden. Die Inhaltsmodellansicht enthält zwei Bereiche: einen **Arbeitsbereich** Bereich, der eine Liste der Knoten im enthält die [XML-Schema-Designer-Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md), und der Entwurfsoberfläche, die Sie, in dem das Inhaltsmodell des Schemas sehen die im ausgewählten Knoten die **Arbeitsbereich** Bereich. Die Inhaltsmodellansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.

 In der folgenden Abbildung ist die **Arbeitsbereich** Bereich enthält sechs Schemaknoten. Die `purchaseOrder` Knoten ausgewählt ist, der **Arbeitsbereich** Bereich und in der Entwurfsoberfläche angezeigt wird.

 ![Inhaltsmodellansicht im XML-Schema-Designer](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Arbeitsbereichspanels

 Nachdem Sie dem Arbeitsbereich Knoten hinzugefügt haben, erscheint die Liste der Knoten der **Arbeitsbereich** Bedienungsfeld der Inhaltsmodellansicht. Bei Auswahl von Knoten in der **Arbeitsbereich** Bereich, die sie auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt werden. Verwenden Sie zum Löschen von Knoten aus dem Arbeitsbereich der XSD-Designer-Symbolleiste die **Arbeitsbereich** Bereich Kontextmenü oder die **löschen** Schlüssel.

 Informationen zum Hinzufügen von Knoten finden Sie im Abschnitt "Hinzufügen von Knoten zum Arbeitsbereich" [XML-Schema-Designer-Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Entwurfsoberfläche

 Wenn ein Knoten aktiviert ist, der **Arbeitsbereich** Bereich, wird der Inhaltsmodellansicht-Entwurfsoberfläche, in dem Sie die Details des Knotens anzeigen können, hinzugefügt.

 Das Inhaltsmodell eines Knotens wird durch eine erweiterbare grafische Struktur mit Elementen und Attributen als Strukturknoten dargestellt. Standardmäßig wird nur eine Ebene erweitert. Weitere Informationen wie Compositors, Typnamen, Gruppen und andere Container werden (bei erweiterter Struktur) auf einer vertikalen Leiste neben den zugehörigen Elementen und Attributen angezeigt. Wenn Sie auf einen vertikalen Balken doppelklicken, wird er horizontal dargestellt, und die Struktur wird reduziert. Wenn Sie auf einen horizontalen Balken doppelklicken, wird er vertikal dargestellt, und die Struktur wird erweitert. Die Auswahl des vertikalen Balkens wählt alle Knoten im Container. Klicken Sie auf die rechts neben einem Knoten werden Erweiterungsschaltflächen angezeigt, wenn ein Element erweitert oder reduziert werden kann.

 Wenn die Entwurfsoberfläche leer ist, wird der XML-Editor die **XML-Schema-Explorer**, und das Wasserzeichen angezeigt werden. Die *Wasserzeichen* ist eine Liste mit Links zu allen Ansichten des XSD-Designer. Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt: "Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben."

## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste

 Die Breadcrumb-Leiste am unteren Rand der Inhaltsmodellansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet.

## <a name="context-menus"></a>Kontextmenüs

 Wenn Sie mit der rechten Maustaste auf die Entwurfsoberfläche ein Element oder **Arbeitsbereich** Bereich, wird ein Kontextmenü angezeigt. In der folgenden Tabelle werden die Optionen beschrieben, die für die Entwurfsoberfläche der Inhaltsmodellansicht verfügbar sind.

|Option|Beschreibung|
|------------|-----------------|
|**XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In der Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|
|**Diagramm als Bild exportieren**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das Element, das ausgewählt ist die **XML-Schema-Explorer** auch in der XML-Editor ausgewählt ist.|
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

 Die folgende Tabelle beschreibt die verfügbaren Optionen für die **Arbeitsbereich** Bereich.

|Option|Beschreibung|
|------------|-----------------|
|**XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In der Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Alle auswählen**|Wählt alle Knoten in der **Arbeitsbereich** Bereich.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das Element, das ausgewählt ist die **XML-Schema-Explorer** auch in der XML-Editor ausgewählt ist.|
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="properties-window"></a>Eigenschaftenfenster

 Verwenden Sie das Kontextmenü um zu Beginn zu öffnen die **Eigenschaften** Fenster. Wird standardmäßig die **Eigenschaften** Fenster wird in der unteren rechten Ecke von Visual Studio. Wenn Sie einen Knoten, die in der Inhaltsmodellansicht gerendert wird klicken, werden die Eigenschaften dieses Knotens angezeigt, der **Eigenschaften** Fenster.

## <a name="xsd-designer-toolbar"></a>XSD-Designer-Symbolleiste

 Die folgenden XSD-Designer-Symbolleistenschaltflächen sind aktiviert, wenn die Inhaltsmodellansicht aktiv ist.

 ![Symbolleiste für XML-Schema-Designer](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Option|Beschreibung|
|------------|-----------------|
|**Ausgangsansicht anzeigen**|Wechselt in den [Ausgangsansicht](../xml-tools/start-view.md). In dieser Ansicht kann mit der Tastenkombination zugegriffen werden: **STRG**+**1**.|
|**Inhaltsmodellansicht anzeigen**|Wechselt in den [Inhalte Modellansicht](../xml-tools/content-model-view.md). In dieser Ansicht kann mit der Tastenkombination zugegriffen werden: **STRG**+**2**.|
|**Diagrammansicht anzeigen**|Wechselt in den [Diagrammansicht](../xml-tools/graph-view.md). In dieser Ansicht kann mit der Tastenkombination zugegriffen werden: **STRG**+**3**.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|

## <a name="panscroll"></a>Schwenken/Bildlauf

 Sie können die Entwurfsoberfläche ziehen schwenken, mit den Bildlaufleisten oder durch halten die **STRG** gedrückt, während Sie klicken und die Maus ziehen. Wenn Sie auf die Entwurfsoberfläche mittels klicken und ziehen schwenken, nimmt der Cursor vier sich kreuzenden und in unterschiedliche Richtungen weisenden.

## <a name="undoredo"></a>Rückgängig/Wiederholen

 Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Inhaltsmodellansicht für folgende Aktionen aktiviert:

-   Hinzufügen eines einzelnen Knotens per Drag & Drop

-   Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer

-   Hinzufügen von Knoten aus der Ausgangsansicht

-   Löschen einzelner oder mehrerer Knoten

## <a name="zoom"></a>Zoom

 Zoom ist in der unteren rechten Ecke der Inhaltsmodellansicht verfügbar.

 Der Zoomfaktor kann wie folgt gesteuert werden:

-   Halten die **STRG** whell Schlüssel, und drehen Sie die Maus, wenn die Maus über die Oberfläche der Inhaltsmodellansicht bewegen.

-   Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.

Der Zoomschieberegler ist nicht transparent, wenn Sie wählen es, zeigen Sie darauf, oder verwenden **STRG** mit dem Mausrad Zoomen; in allen anderen Fällen ist er transparent.

## <a name="xml-editor-integration"></a>Integration des XML-editor

 Sie können zwischen hin und her wechseln der **XSD-Designers** und die XML-Editor über das Kontextmenü.

 Wenn Sie Änderungen am Schemaset im XML-Editor vornehmen werden die Änderungen in der Inhaltsmodellansicht synchronisiert. Weitere Informationen finden Sie unter [Integration in XML-Editor](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Siehe auch

- [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)