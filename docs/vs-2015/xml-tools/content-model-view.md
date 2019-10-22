---
title: Inhalts Modell Ansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47f4703b90446dc615df350ee0641678996196c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657542"
---
# <a name="content-model-view"></a>Inhaltsmodellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Inhaltsmodellansicht bietet eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten. Dazu zählen einfache und komplexe Typen, Elemente, Modellgruppen, Attribute und Attributgruppen. XML-Kommentare und -Verarbeitungsanweisungen können nicht in der Inhaltsmodellansicht angezeigt werden. Die Inhalts Modell Ansicht enthält zwei Bereiche: einen **Arbeitsbereich** mit einer Liste der Knoten im [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)und die Entwurfs Oberfläche, auf der Sie das Inhalts Modell von Schema Knoten sehen können, die im **Arbeitsbereich ausgewählt sind.** Bereich. Die Inhaltsmodellansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.

 Das folgende Bild zeigt den Arbeitsbereich mit sechs Schemaknoten. Der `purchaseOrder`-Knoten ist im Arbeitsbereich ausgewählt und wird auf der Entwurfsoberfläche angezeigt.

 ![Inhalts Modell Ansicht im XML-Schema-Designer](../xml-tools/media/xsddesigner-contentmodelview.gif "XSDDesigner_ContentModelView")

## <a name="workspace-panel"></a>Arbeitsbereich
 Nachdem Sie dem Arbeitsbereich Knoten hinzugefügt haben, wird die Liste der Knoten im **Arbeitsbereich** der Inhalts Modell Ansicht angezeigt. Wenn Sie Knoten im **Arbeitsbereich** auswählen, werden Sie in der Entwurfs Oberfläche der Inhalts Modell Ansicht angezeigt. Verwenden Sie die XSD-Designer-Symbolleiste, das Kontextmenü des Arbeitsbereichs oder die ENTF-Taste, um Knoten aus dem Arbeits **Bereich** zu löschen.

 Weitere Informationen zum Hinzufügen von Knoten finden Sie im Abschnitt "Hinzufügen von Knoten zum Arbeitsbereich" im [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Entwurfsoberfläche
 Wenn Sie einen Knoten im Arbeitsbereich auswählen, wird er der Entwurfsoberfläche der Inhaltsmodellansicht hinzugefügt, wo Sie die Details des Knotens anzeigen können.

 Das Inhaltsmodell eines Knotens wird durch eine erweiterbare grafische Struktur mit Elementen und Attributen als Strukturknoten dargestellt. Standardmäßig wird nur eine Ebene erweitert. Weitere Informationen wie Compositors, Typnamen, Gruppen und andere Container werden (bei erweiterter Struktur) auf einer vertikalen Leiste neben den zugehörigen Elementen und Attributen angezeigt. Wenn Sie auf einen vertikalen Balken doppelklicken, wird er horizontal dargestellt, und die Struktur wird reduziert. Wenn Sie auf einen horizontalen Balken doppelklicken, wird er vertikal dargestellt, und die Struktur wird erweitert. Durch Auswahl des vertikalen Balkens werden alle Knoten im Container ausgewählt. Rechts neben einem Knoten werden Erweiterungsschaltflächen angezeigt, wenn ein Element erweitert oder reduziert werden kann.

 Wenn die Entwurfsoberfläche leer ist, werden der XML-Editor, der XML-Schema-Explorer und das Wasserzeichen angezeigt. Das *Wasserzeichen* ist eine Liste mit Links zu allen Ansichten des XSD-Designers. Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt: "Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben."

## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste
 Die Breadcrumb-Leiste am unteren Rand der Inhaltsmodellansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet.

## <a name="context-menus"></a>Kontextmenüs
 Wenn Sie auf der Entwurfsoberfläche oder im Arbeitsbereich mit der rechten Maustaste auf ein Element klicken, wird ein Kontextmenü angezeigt. In der folgenden Tabelle werden die Optionen beschrieben, die für die Entwurfsoberfläche der Inhaltsmodellansicht verfügbar sind.

|Option|Beschreibung|
|------------|-----------------|
|**Im XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagramm Ansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Generieren von Beispiel-XML**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|
|**Diagramm als Bild exportieren...**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

 In der folgenden Tabelle werden die Optionen beschrieben, die für den Arbeitsbereich verfügbar sind.

|Option|Beschreibung|
|------------|-----------------|
|**Im XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagramm Ansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Generieren von Beispiel-XML**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Alle auswählen**|Wählt alle Knoten im Arbeitsbereich aus.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="properties-window"></a>Eigenschaftenfenster
 Verwenden Sie das Kontextmenü, um das Fenster **Eigenschaften** zu öffnen. Standardmäßig wird das Fenster **Eigenschaften** in der unteren rechten Ecke von Visual Studio angezeigt. Wenn Sie auf einen Knoten klicken, der in der Inhalts Modell Ansicht gerendert wird, werden die Eigenschaften dieses Knotens im **Eigenschaften** Fenster angezeigt.

## <a name="xsd-designer-toolbar"></a>XSD-Designer-Symbolleiste
 Die folgenden XSD-Designer-Symbolleistenschaltflächen sind aktiviert, wenn die Inhaltsmodellansicht aktiv ist.

 ![XML-Schema-Designer](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")

|Option|Beschreibung|
|------------|-----------------|
|**Start Ansicht anzeigen**|Wechselt zur [Start Ansicht](../xml-tools/start-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG + 1**.|
|**Inhalts Modell Ansicht anzeigen**|Wechselt zur [Inhalts Modell Ansicht](../xml-tools/content-model-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG + 2**.|
|**Diagramm Ansicht anzeigen**|Wechselt zur [Diagramm Ansicht](../xml-tools/graph-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG + 3**.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|

## <a name="panscroll"></a>Schwenken/Bildlauf
 Sie können die Entwurfsoberfläche mit den Bildlaufleisten oder durch Drücken der STRG-TASTE und gleichzeitiges Klicken und Ziehen der Maus schwenken. Wenn Sie die Entwurfsoberfläche mittels Klicken und Ziehen schwenken, wird der Cursor als vier sich kreuzende und in unterschiedliche Richtungen weisende Pfeile angezeigt.

## <a name="undoredo"></a>Rückgängig/Wiederholen
 Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Inhaltsmodellansicht für folgende Aktionen aktiviert:

- Hinzufügen eines einzelnen Knotens per Drag &amp; Drop

- Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer

- Hinzufügen von Knoten aus der Ausgangsansicht

- Löschen einzelner oder mehrerer Knoten

## <a name="zoom"></a>Zoom
 Die Zoomfunktion befindet sich in der unteren rechten Ecke der Inhaltsmodellansicht.

 Der Zoomfaktor kann wie folgt gesteuert werden:

- Halten Sie die STRG-TASTE gedrückt, und drehen Sie das Mausrad, während Sie die Maus über die Oberfläche der Inhaltsmodellansicht bewegen.

- Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.

  Der Zoomschieberegler ist nicht transparent, wenn Sie ihn auswählen, mit der Maus darauf zeigen oder mit der STRG-TASTE und dem Mausrad zoomen. Ansonsten ist er transparent.

## <a name="xml-editor-integration"></a>Integration des XML-Editors
 Sie können über das Kontextmenü zwischen dem XSD-Designer und dem XML-Editor hin- und herwechseln.

 Wenn Sie im XML-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Inhaltsmodellansicht synchronisiert. Weitere Informationen finden Sie unter [Integration in den XML-Editor](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Siehe auch
 [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)
