---
title: Diagramm Ansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba58777700ba34de3dc3b7a842f26462daf08c89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656362"
---
# <a name="graph-view"></a>Diagrammansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Diagrammansicht bietet eine grafische Darstellung der globalen Schemaknoten und der Beziehungen zwischen den Knoten. In der Diagrammansicht kann das Layout des Schemasets auf der Entwurfsoberfläche nicht geändert werden. Die Diagrammansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.

 Das folgende Bild zeigt die Diagrammansicht mit sechs globalen Knoten auf der Entwurfsoberfläche.

 ![Diagramm Ansicht im XML-Schema-Designer](../xml-tools/media/xsddesigner-graphview.gif "XSDDesigner_GraphView")

## <a name="design-surface"></a>Entwurfsoberfläche
 In der Entwurfs Oberfläche der Diagramm Ansicht wird der Inhalt des Arbeitsbereichs des [XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)angezeigt. Wenn der Arbeitsbereich globale Knoten aus dem Schemaset enthält, werden die Knoten auf der Entwurfsoberfläche der Diagrammansicht angezeigt, und zwischen Knoten mit Beziehungen werden Pfeile gezeichnet.

 Per Doppelklick auf einen Knoten in der Diagrammansicht öffnen Sie den XML-Editor.

 Verwenden Sie die XSD-Designer-Symbolleiste oder die ENTF-TASTE, um ausgewählte Knoten aus dem Arbeitsbereich zu löschen.

 Wenn die Entwurfsoberfläche leer ist, werden der XML-Editor, der XML-Schema-Explorer und das Wasserzeichen angezeigt. Das *Wasserzeichen* ist eine Liste mit Links zu allen Ansichten des XSD-Designers.

 ![XSD-Designer; Diagramm Ansicht](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")

 Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt: "Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben."

## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste
 Die Breadcrumb-Leiste am unteren Rand der Diagrammansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet. Wenn mehrere Elemente ausgewählt sind, ist die Breadcrumb-Leiste leer.

## <a name="context-menu"></a>Kontextmenü
 In der folgenden Tabelle werden die Optionen beschrieben, die für alle Knoten auf der Entwurfsoberfläche der Diagrammansicht verfügbar sind.

|Option|Beschreibung|
|------------|-----------------|
|**Im XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagramm Ansicht anzeigen**|Wechselt zur Diagrammansicht (abgeblendet).|
|**Generieren von Beispiel-XML**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Diagramm als Bild exportieren...**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|
|**Alle auswählen**|Wählt alle Knoten auf der Entwurfsoberfläche aus.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

 Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale Elemente die folgenden Optionen:

|Option|Beschreibung|
|------------|-----------------|
|**Typdefinition hinzufügen**|Fügt dem Diagramm den Basistyp hinzu.|
|**Alle Verweise hinzufügen**|Fügt alle Knoten, die auf das Element verweisen, hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|
|**Ersetzungs Gruppenmitglieder hinzufügen**|Fügt alle Ersetzungsgruppenelemente hinzu. Diese Option wird in der Ansicht angezeigt, wenn das Element der Kopf oder das Mitglied einer Ersetzungsgruppe ist.|
|**Generieren von Beispiel-XML**|Generiert eine Beispiel-XML-Datei für das globale Element.|

 Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale einfache und globale komplexe Typen die folgenden Optionen:

|Option|Beschreibung|
|------------|-----------------|
|**Basistyp hinzufügen**|Fügt den Basistyp des ausgewählten Typs hinzu, wenn der ausgewählte Typ von einem globalen Typ abgeleitet ist.|
|**Alle Verweise hinzufügen**|Fügt alle Verweise des ausgewählten Typs hinzu. Dazu zählen Elemente und Attribute des ausgewählten Typs und vom ausgewählten Typ abgeleitete Typen.|
|**Alle abgeleiteten Typen hinzufügen**|Fügt alle Typen hinzu, die direkt und indirekt vom ausgewählten Typ abgeleitet sind.|
|**Alle Vorgänger hinzufügen**|Fügt alle übergeordneten (Basis-)Typen hinzu.|

 Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale Gruppen und Attributgruppen die folgenden Optionen:

|Option|Beschreibung|
|------------|-----------------|
|**Alle Verweise hinzufügen**|Fügt alle Knoten, die auf die Gruppe verweisen, hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|
|**Alle Mitglieder hinzufügen**|Fügt alle Mitglieder der Gruppe hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|

 Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale Attribute die folgenden Optionen:

|Option|Beschreibung|
|------------|-----------------|
|**Alle Verweise hinzufügen**|Fügt alle Knoten, die auf die Gruppe verweisen, hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|

## <a name="properties-window"></a>Eigenschaftenfenster
 Verwenden Sie das Kontextmenü, um das Fenster **Eigenschaften** zu öffnen. Standardmäßig wird das Fenster **Eigenschaften** in der unteren rechten Ecke von Visual Studio angezeigt. Wenn Sie auf einen Knoten klicken, der in der Inhalts Modell Ansicht gerendert wird, werden die Eigenschaften dieses Knotens im **Eigenschaften** Fenster angezeigt.

## <a name="xsd-toolbar"></a>XSD-Symbolleiste
 Die folgenden XSD-Symbolleistenschaltflächen sind aktiviert, wenn die Diagrammansicht aktiv ist.

 ![XML-Schema-Designer](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")

|Option|Beschreibung|
|------------|-----------------|
|**Start Ansicht anzeigen**|Wechselt zur [Start Ansicht](../xml-tools/start-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG + 1**.|
|**Inhalts Modell Ansicht anzeigen**|Wechselt zur [Inhalts Modell Ansicht](../xml-tools/content-model-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG + 2**.|
|**Diagramm Ansicht anzeigen**|Wechselt zur [Diagramm Ansicht](../xml-tools/graph-view.md). Auf diese Sicht kann über die Tastenkombination zugegriffen werden: **STRG + 3**.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche. Diese Option ist in der Inhaltsmodellansicht und der Diagrammansicht aktiviert.|
|**Von links nach rechts**|Ändert das Layout in der Diagrammansicht in eine von links nach rechts angeordnete hierarchische Darstellung der Knoten. Auf diese Option kann über die Tastenkombination zugegriffen werden: **alt +** nach-rechts-Taste.|
|**Von rechts nach links**|Ändert das Layout in der Diagrammansicht in eine von rechts nach links angeordnete hierarchische Darstellung der Knoten. Auf diese Option kann mit der Tastenkombination zugegriffen werden: **alt +** nach-links-Taste.|
|**Von oben nach unten**|Ändert das Layout in der Diagrammansicht in eine von oben nach unten angeordnete hierarchische Darstellung der Knoten. Auf diese Option können Sie über die Tastenkombination zugreifen: **alt + nach-unten-Taste**.|
|**Unten nach oben**|Ändert das Layout in der Diagrammansicht in eine von unten nach oben angeordnete hierarchische Darstellung der Knoten. Auf diese Option können Sie über die Tastenkombination zugreifen: **alt +** nach-oben-Taste.|

## <a name="panscroll"></a>Schwenken/Bildlauf
 Sie können die Entwurfsoberfläche mit den Bildlaufleisten oder durch Drücken der STRG-TASTE und gleichzeitiges Klicken und Ziehen der Maus schwenken. Wenn Sie die Entwurfsoberfläche mittels Klicken und Ziehen schwenken, wird der Cursor als vier sich kreuzende und in unterschiedliche Richtungen weisende Pfeile angezeigt.

## <a name="undoredo"></a>Rückgängig/Wiederholen
 Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Diagrammansicht für folgende Aktionen aktiviert:

- Hinzufügen eines einzelnen Knotens per Drag &amp; Drop

- Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer oder Abfragen in der Ausgangsansicht

- Löschen einzelner oder mehrerer Knoten

## <a name="zoom"></a>Zoom
 Die Zoomfunktion befindet sich in der unteren rechten Ecke der Diagrammansicht.

 Der Zoomfaktor kann wie folgt gesteuert werden:

- Halten Sie die STRG-TASTE gedrückt, und drehen Sie das Mausrad, während Sie die Maus über die Oberfläche der Diagrammansicht bewegen.

- Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.

  Der Zoomschieberegler ist nicht transparent, wenn Sie ihn auswählen, mit der Maus darauf zeigen oder mit der STRG-TASTE und dem Mausrad zoomen. Ansonsten ist er transparent.

## <a name="xml-editor-integration"></a>Integration des XML-Editors
 Klicken Sie auf einen Knoten, und wählen Sie das Kontextmenüelement "Code anzeigen" aus, um zwischen der Diagrammansicht und dem XML-Editor hin- und herzuwechseln.

 Wenn Sie im XML-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Diagrammansicht synchronisiert. Weitere Informationen finden Sie unter [Integration in den XML-Editor](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Siehe auch
 [Designoberfläche](../xml-tools/xml-schema-designer-workspace.md)
