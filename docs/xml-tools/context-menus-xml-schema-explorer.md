---
title: Kontextmenüs im XML-Schema-Explorer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e74bf2cdf2da8007af11875c018eebc86bd41cab
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926359"
---
# <a name="context-menus-xml-schema-explorer"></a>Kontextmenüs (XML-Schema-Explorer)

Ein Kontextmenü ist das Menü, das angezeigt wird, wenn Sie mit der rechten Maustaste auf etwas klicken. Die folgenden Kontextmenüelemente werden verwendet, um schemaspezifische Suchen und andere Vorgänge auszuführen.

## <a name="node-type-schema-set"></a>Knotentyp: Schemaset

In der folgenden Tabelle werden die Optionen beschrieben, die für Schemasetknoten verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**Wahrscheinlichste Stamm Elemente anzeigen**|Sucht nach allen globalen Elementen, auf die nicht von anderen globalen Elementen verwiesen wird, und hebt sie hervor.|
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen im Schemaset und hebt sie hervor.|
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen im Schemaset und hebt sie hervor.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="node-type-namespace"></a>Knotentyp: Namespace
In der folgenden Tabelle werden die Optionen beschrieben, die für Namespaceknoten verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**Alle eingehenden Verweise anzeigen**|Sucht nach Dateien, die den ausgewählten Namespace importieren, und hebt sie hervor.|
|**Alle ausgehenden Verweise anzeigen**|Sucht und hebt für jede Datei im ausgewählten Namespace Folgendes hervor:<br /><br /> -Alle Namespaces, auf die in Import- `schemaLocation` Anweisungen ohne ein-Attribut verwiesen wird.<br />-Alle Dateien in anderen Namespaces als der ausgewählte, die im `schemaLocation` -Attribut in Import-und include-Anweisungen angegeben sind.|
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen im ausgewählten Namespace und hebt sie hervor.|
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen im ausgewählten Namespace und hebt sie hervor.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="node-type-file"></a>Knotentyp: Datei
In der folgenden Tabelle werden die Optionen beschrieben, die für Dateiknoten verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**Alle eingehenden Verweise anzeigen**|Sucht nach allen Dateien, in denen die ausgewählte Datei in den `schemaLocation`-Attributen der include- und import-Anweisungen angegeben ist, und hebt sie hervor.|
|**Alle ausgehenden Verweise anzeigen**|Sucht und hebt Folgendes hervor:<br /><br /> -Alle Namespaces, die in den Namespace Attributen aller Import-Anweisungen angegeben sind, die `schemaLocation` nicht über das-Attribut verfügen.<br />-Alle Dateien, die in `schemaLocation` den Attributen aller Import-und include-Anweisungen angegeben sind.|
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen in dieser Datei und hebt sie hervor.|
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen in dieser Datei und hebt sie hervor.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten im XML-Editor enthält. Das Element, das im XML-Schema-Explorer ausgewählt wird, wird im XML-Editor ebenfalls ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="all-global-node-types"></a>Alle globalen Knoten Typen
In der folgenden Tabelle werden die Optionen beschrieben, die für alle globalen Knoten verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**In Diagramm Ansicht anzeigen**|Öffnet die Diagrammansicht. Wenn der ausgewählte Knoten nicht im Arbeitsbereich vorhanden ist, wird er dem Arbeitsbereich hinzugefügt und ausgewählt.|
|**In Inhalts Modell Ansicht anzeigen**|Öffnet die Inhaltsmodellansicht. Wenn der ausgewählte Knoten nicht im Arbeitsbereich vorhanden ist, wird er dem Arbeitsbereich hinzugefügt und ausgewählt.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten im XML-Editor enthält. Das Element, das im XML-Schema-Explorer ausgewählt wird, wird im XML-Editor ebenfalls ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="node-type-element"></a>Knotentyp: Element
Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Elementknoten die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Gehe zu Typdefinition**|Navigiert zur Typdefinition des ausgewählten Elements. Dies gilt, wenn der Typ, der für das Element verwendet wird, ein globaler Typ ist.|
|**Zum ursprünglichen Element wechseln**|Navigiert bei Elementverweisen zur eigentlichen Definition des Elements.|
|**Alle Verweise anzeigen**|Sucht für globale Elemente nach allen Verweisen auf das ausgewählte Element (Elemente mit `ref="selectedElement"`) und hebt sie hervor.|
|**Mitglieder der Ersetzungs Gruppe anzeigen**|Bei Köpfen einer Ersetzungsgruppe werden alle Elemente gesucht und hervorgehoben, die Member der Ersetzungsgruppe sind, deren ausgewähltes Element ein Member ist. Dadurch werden direkte und indirekte Teilnehmer angezeigt.|
|**Ersetzungs Gruppenköpfe anzeigen**|Bei globalen Elementen, die Member einer Ersetzungsgruppe sind, werden alle direkten und indirekten Köpfe für ein Element wie das folgende gesucht und hervorgehoben:<br /><br /> : Ein Ersetzungs Gruppenkopf, der für das ausgewählte Element angegeben ist.<br />: Ein Ersetzungs Gruppenkopf, der auf seinem Head-Element angegeben ist.|
|**Generieren von Beispiel-XML**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|

## <a name="node-type-global-types"></a>Knotentyp: Globale Typen
Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für globale Typknoten die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Basistyp anzeigen**|Navigiert zum Basistyp des ausgewählten Typs, wenn der ausgewählte Typ von einem globalen Typ abgeleitet ist.|
|**Alle Verweise anzeigen**|Sucht und hebt alle Verweise auf den ausgewählten Typ hervor. Dazu gehören Elemente und Attribute des ausgewählten Typs und Typen, die vom ausgewählten Typ abgeleitet sind.|
|**Alle abgeleiteten Typen anzeigen**|Sucht und hebt alle Typen hervor, die direkt und indirekt vom ausgewählten Typ abgeleitet sind.|
|**Alle Vorgänger anzeigen**|Zeigt alle übergeordneten (Basis-)Typen an.|

## <a name="node-type-attribute"></a>Knotentyp: Attribut
Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Attributknoten die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Gehe zu Typdefinition**|Navigiert zur Typdefinition des ausgewählten Attributs, wenn der für das Attribut verwendete Typ ein globaler Typ ist.|
|**Zum ursprünglichen Attribut wechseln**|Bei Attributverweisen wird zur tatsächlichen Definition des Attributs navigiert.|
|**Alle Verweise anzeigen**|Sucht für globale Attribute nach allen Verweisen auf das ausgewählte Attribut (andere Attribute mit `ref="selectedAttribute"`) und hebt sie hervor.|

## <a name="node-type-attribute-group"></a>Knotentyp: Attribut Gruppe
Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Attributgruppenknoten die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Gehe zu Definition**|Navigiert bei Verweisen zur eigentlichen Definition des Attributs.|
|**Alle Elemente anzeigen**|Sucht nach allen Mitgliedern der Attributgruppe und hebt sie hervor.|
|**Alle Verweise anzeigen**|Sucht nach allen Verweisen auf die ausgewählte Attributgruppe (Attributgruppen mit `ref="selectedAttributeGroup"`) und hebt sie hervor.|

## <a name="node-type-named-group"></a>Knotentyp: Benannte Gruppe
Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für benannte Gruppenknoten die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Gehe zu Definition**|Navigiert bei Verweisen zur eigentlichen Definition des Attributs.|
|**Alle Elemente anzeigen**|Sucht nach allen Mitgliedern der benannten Gruppe und hebt sie hervor.|
|**Alle Verweise anzeigen**|Sucht nach allen Verweisen auf die ausgewählte Gruppe (Gruppen mit `ref="selectedGroup"`) und hebt sie hervor.|

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
- [Durchsuchen des Schema Satzes](../xml-tools/searching-the-schema-set.md)