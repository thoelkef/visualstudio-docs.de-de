---
title: Inhaltsmodellansicht im XML-Schema-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 830dbdda0027551a25747235e6ad9dffbbc11b23
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592912"
---
# <a name="content-model-view"></a>Inhaltsmodellansicht

Die Inhaltsmodellansicht bietet eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten. Dazu zählen einfache und komplexe Typen, Elemente, Modellgruppen, Attribute und Attributgruppen. XML-Kommentare und -Verarbeitungsanweisungen können nicht in der Inhaltsmodellansicht angezeigt werden. Die Inhalts Modell Ansicht enthält zwei Bereiche: einen **Arbeitsbereich** mit einer Liste der Knoten im [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)und die Entwurfs Oberfläche, auf der Sie das Inhalts Modell von Schema Knoten sehen können, die im **Arbeitsbereich** ausgewählt sind. Die Inhaltsmodellansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.

In der folgenden Abbildung enthält der **Arbeitsbereichs Bereich** sechs Schema Knoten. Der Knoten `purchaseOrder` ist im **Arbeitsbereich** ausgewählt und wird auf der Entwurfs Oberfläche angezeigt.

![Inhaltsmodellansicht im XML-Schema-Designer](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Arbeitsbereichs Panel

Nachdem Sie dem Arbeitsbereich Knoten hinzugefügt haben, wird die Liste der Knoten im **Arbeitsbereich** der Inhalts Modell Ansicht angezeigt. Wenn Sie Knoten im **Arbeitsbereich** auswählen, werden Sie in der Entwurfs Oberfläche der Inhalts Modell Ansicht angezeigt. Um Knoten aus dem Arbeitsbereich zu löschen, verwenden Sie die XSD-Designer-Symbolleiste, den **Arbeitsbereich** mit **der rechten** Maustaste oder die ENTF-Taste.

Weitere Informationen zum Hinzufügen von Knoten finden Sie im Abschnitt "Hinzufügen von Knoten zum Arbeitsbereich" im [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Entwurfsoberfläche

Wenn ein Knoten im **Arbeitsbereich** ausgewählt ist, wird er zur Entwurfs Oberfläche der Inhalts Modell Ansicht hinzugefügt, auf der Sie die Details des Knotens anzeigen können.

Das Inhaltsmodell eines Knotens wird durch eine erweiterbare grafische Struktur mit Elementen und Attributen als Strukturknoten dargestellt. Standardmäßig wird nur eine Ebene erweitert. Weitere Informationen wie Compositors, Typnamen, Gruppen und andere Container werden (bei erweiterter Struktur) auf einer vertikalen Leiste neben den zugehörigen Elementen und Attributen angezeigt. Wenn Sie auf einen vertikalen Balken doppelklicken, wird er horizontal dargestellt, und die Struktur wird reduziert. Wenn Sie auf einen horizontalen Balken doppelklicken, wird er vertikal dargestellt, und die Struktur wird erweitert. Wenn Sie den senkrechten Strich auswählen, werden alle Knoten im Container ausgewählt. Expander werden auf der rechten Seite eines Knotens angezeigt, wenn ein Element erweitert oder reduziert werden kann.

Wenn die Entwurfs Oberfläche leer ist, werden der XML-Editor, der **XML-Schema-Explorer**und das Wasserzeichen angezeigt. Das *Wasserzeichen* ist eine Liste mit Links zu allen Ansichten des XSD-Designers. Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt: "Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben."

## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste

Die Breadcrumb-Leiste am unteren Rand der Inhaltsmodellansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet.

## <a name="context-menus"></a>Kontextmenüs

Wenn Sie auf der Entwurfs Oberfläche oder im **Arbeitsbereich** mit der rechten Maustaste auf ein Element klicken, wird ein Kontextmenü angezeigt. In der folgenden Tabelle werden die Optionen beschrieben, die für die Entwurfsoberfläche der Inhaltsmodellansicht verfügbar sind.

|-Option|Beschreibung|
|-|-----------------|
|**Im XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagramm Ansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Generieren von Beispiel-XML**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|
|**Diagramm als Bild exportieren**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten im XML-Editor enthält. Das Element, das im XML- **Schema-Explorer** ausgewählt ist, wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

In der folgenden Tabelle werden die Optionen beschrieben, die für den **Arbeitsbereich** verfügbar sind.

|-Option|Beschreibung|
|-|-----------------|
|**Im XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagramm Ansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Generieren von Beispiel-XML**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Alles markieren**|Wählt alle Knoten im **Arbeitsbereich** aus.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten im XML-Editor enthält. Das Element, das im XML- **Schema-Explorer** ausgewählt ist, wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="properties-window"></a>Fenster Eigenschaften

Verwenden Sie das Kontextmenü (Kontextmenü), um das Fenster **Eigenschaften** zu öffnen. Standardmäßig wird das Fenster **Eigenschaften** in der unteren rechten Ecke von Visual Studio angezeigt. Wenn Sie auf einen Knoten klicken, der in der Inhalts Modell Ansicht gerendert wird, werden die Eigenschaften dieses Knotens im **Eigenschaften** Fenster angezeigt.

## <a name="xsd-designer-toolbar"></a>XSD-Designer-Symbolleiste

Die folgenden XSD-Designer-Symbolleistenschaltflächen sind aktiviert, wenn die Inhaltsmodellansicht aktiv ist.

![Symbolleiste für XML-Schema-Designer](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|-Option|Beschreibung|
|-|-----------------|
|**Start Ansicht anzeigen**|Wechselt zur [Start Ansicht](../xml-tools/start-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG**+**1**.|
|**Inhalts Modell Ansicht anzeigen**|Wechselt zur [Inhalts Modell Ansicht](../xml-tools/content-model-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG**+**2**.|
|**Diagramm Ansicht anzeigen**|Wechselt zur [Diagramm Ansicht](../xml-tools/graph-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG**+**3**.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|

## <a name="panscroll"></a>Schwenken/Bildlauf

Sie können die Entwurfs Oberfläche schwenken, indem Sie die Scrollleisten verwenden oder indem Sie die **STRG** -Taste gedrückt halten, während Sie auf die Maus klicken und die Maus ziehen. Wenn Sie die Entwurfs Oberfläche mithilfe von Click und Drag schwenken, ändert sich der Cursor in vier durchgezogene Pfeile, die in vier Richtungen zeigen.

## <a name="undoredo"></a>Rückgängig/Wiederholen

Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Inhaltsmodellansicht für folgende Aktionen aktiviert:

- Hinzufügen eines einzelnen Knotens per Drag &amp; Drop

- Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer

- Hinzufügen von Knoten aus der Ausgangsansicht

- Löschen einzelner oder mehrerer Knoten

## <a name="zoom"></a>Zoom

Zoom steht in der unteren rechten Ecke der Inhalts Modell Ansicht zur Verfügung.

Der Zoomfaktor kann wie folgt gesteuert werden:

- Indem Sie die **STRG** -Taste gedrückt halten und das Mausrad drehen, wenn der Mauszeiger auf die Oberfläche der Inhalts Modell Ansicht zeigt.

- Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.

Der Zoom Schieberegler ist nicht transparent, wenn Sie ihn auswählen, darauf zeigen oder mit dem Mausrad **STRG** drücken, um zu zoomen. zu allen anderen Zeiten ist er transparent.

## <a name="xml-editor-integration"></a>Integration des XML-Editors

Über das Kontextmenü (Kontextmenü) können Sie zwischen dem **XSD-Designer** und dem XML-Editor hin-und herwechseln.

Wenn Sie im XML-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Inhalts Modell Ansicht synchronisiert. Weitere Informationen finden Sie unter [Integration in den XML-Editor](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Siehe auch

- [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)
