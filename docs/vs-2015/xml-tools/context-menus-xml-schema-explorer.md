---
title: Kontextmenüs (XML-Schema-Explorer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4a59a20a13ac56e2ea779bf5df8f9d33979cc27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524542"
---
# <a name="context-menus-xml-schema-explorer"></a>Kontextmenüs (XML-Schema-Explorer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Kontextmenüs (XML-Schema-Explorer)](https://docs.microsoft.com/visualstudio/xml-tools/context-menus-xml-schema-explorer).  
  
  
Die folgenden Kontextmenüelemente werden verwendet, um schemaspezifische Suchen und andere Vorgänge auszuführen.  
  
## <a name="node-type-schema-set"></a>Knotentyp: Schemaset  
 In der folgenden Tabelle werden die Optionen beschrieben, die für Schemasetknoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Wahrscheinlichste Stammelemente anzeigen**|Sucht nach allen globalen Elementen, auf die nicht von anderen globalen Elementen verwiesen wird, und hebt sie hervor.|  
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen im Schemaset und hebt sie hervor.|  
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen im Schemaset und hebt sie hervor.|  
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** -Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## <a name="node-type-namespace"></a>Knotentyp: Namespace  
 In der folgenden Tabelle werden die Optionen beschrieben, die für Namespaceknoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Alle eingehenden Verweise anzeigen**|Sucht nach Dateien, die den ausgewählten Namespace importieren, und hebt sie hervor.|  
|**Alle ausgehenden Verweise anzeigen**|Sucht und hebt für jede Datei im ausgewählten Namespace Folgendes hervor:<br /><br /> – Alle Namespaces, die auf die verwiesen wird im import-Anweisungen ohne eine `schemaLocation` Attribut.<br />– Alle Dateien in anderen Namespaces als dem ausgewählten Namespace, die im angegebenen die `schemaLocation` -Attribut in Import- und include-Anweisungen.|  
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen im ausgewählten Namespace und hebt sie hervor.|  
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen im ausgewählten Namespace und hebt sie hervor.|  
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** -Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## <a name="node-type-file"></a>Knotentyp: Datei  
 In der folgenden Tabelle werden die Optionen beschrieben, die für Dateiknoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Alle eingehenden Verweise anzeigen**|Sucht nach allen Dateien, in denen die ausgewählte Datei in den `schemaLocation`-Attributen der include- und import-Anweisungen angegeben ist, und hebt sie hervor.|  
|**Alle ausgehenden Verweise anzeigen**|Sucht und hebt Folgendes hervor:<br /><br /> – Alle Namespaces, die in den Namespaceattributen aller angegebenen importanweisungen, denen keine das `schemaLocation` Attribut.<br />– Alle angegebenen Dateien in die `schemaLocation` -Attributen aller Import- und include-Anweisungen.|  
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen in dieser Datei und hebt sie hervor.|  
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen in dieser Datei und hebt sie hervor.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** -Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## <a name="all-global-node-types"></a>Alle globalen Knotentypen  
 In der folgenden Tabelle werden die Optionen beschrieben, die für alle globalen Knoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**In Diagrammansicht anzeigen**|Öffnet die Diagrammansicht. Wenn der ausgewählte Knoten nicht im Arbeitsbereich vorhanden ist, wird er dem Arbeitsbereich hinzugefügt und ausgewählt.|  
|**In Inhaltsmodellansicht anzeigen**|Öffnet die Inhaltsmodellansicht. Wenn der ausgewählte Knoten nicht im Arbeitsbereich vorhanden ist, wird er dem Arbeitsbereich hinzugefügt und ausgewählt.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** -Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## <a name="node-type-element"></a>Knotentyp: Element  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Elementknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Gehe zu Typdefinition**|Navigiert zur Typdefinition des ausgewählten Elements. Dies gilt, wenn der Typ, der für das Element verwendet wird, ein globaler Typ ist.|  
|**Wechseln Sie zum ursprünglichen Element**|Navigiert bei Elementverweisen zur eigentlichen Definition des Elements.|  
|**Alle Verweise anzeigen**|Sucht für globale Elemente nach allen Verweisen auf das ausgewählte Element (Elemente mit `ref="selectedElement"`) und hebt sie hervor.|  
|**Ersetzungsgruppenmitglieder anzeigen**|Bei Köpfen einer Ersetzungsgruppe werden alle Elemente gesucht und hervorgehoben, die Member der Ersetzungsgruppe sind, deren ausgewähltes Element ein Member ist. Dadurch werden direkte und indirekte Teilnehmer angezeigt.|  
|**Ersetzungsgruppenköpfe anzeigen**|Bei globalen Elementen, die Member einer Ersetzungsgruppe sind, werden alle direkten und indirekten Köpfe für ein Element wie das folgende gesucht und hervorgehoben:<br /><br /> -Ein ersetzungsgruppenkopf, der für das ausgewählte Element angegeben wird.<br />-Ein ersetzungsgruppenkopf, der auf seinem headelement angegeben wird.|  
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|  
  
## <a name="node-type-global-types"></a>Knotentyp: Globale Typen  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für globale Typknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Basistyp anzeigen**|Navigiert zum Basistyp des ausgewählten Typs, wenn der ausgewählte Typ von einem globalen Typ abgeleitet ist.|  
|**Alle Verweise anzeigen**|Sucht und hebt alle Verweise auf den ausgewählten Typ hervor. Dazu gehören Elemente und Attribute des ausgewählten Typs und Typen, die vom ausgewählten Typ abgeleitet sind.|  
|**Alle abgeleiteten Typen anzeigen**|Sucht und hebt alle Typen hervor, die direkt und indirekt vom ausgewählten Typ abgeleitet sind.|  
|**Vorgängerelemente anzeigen**|Zeigt alle übergeordneten (Basis-)Typen an.|  
  
## <a name="node-type-attribute"></a>Knotentyp: Attribut  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Attributknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Gehe zu Typdefinition**|Navigiert zur Typdefinition des ausgewählten Attributs, wenn der für das Attribut verwendete Typ ein globaler Typ ist.|  
|**Wechseln Sie zum ursprünglichen Attribut**|Bei Attributverweisen wird zur tatsächlichen Definition des Attributs navigiert.|  
|**Alle Verweise anzeigen**|Sucht für globale Attribute nach allen Verweisen auf das ausgewählte Attribut (andere Attribute mit `ref="selectedAttribute"`) und hebt sie hervor.|  
  
## <a name="node-type-attribute-group"></a>Knotentyp: Attributgruppe  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Attributgruppenknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Gehe zu Definition**|Navigiert bei Verweisen zur eigentlichen Definition des Attributs.|  
|**Alle Member anzeigen**|Sucht nach allen Mitgliedern der Attributgruppe und hebt sie hervor.|  
|**Alle Verweise anzeigen**|Sucht nach allen Verweisen auf die ausgewählte Attributgruppe (Attributgruppen mit `ref="selectedAttributeGroup"`) und hebt sie hervor.|  
  
## <a name="node-type-named-group"></a>Knotentyp: Benannte Gruppe  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für benannte Gruppenknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Gehe zu Definition**|Navigiert bei Verweisen zur eigentlichen Definition des Attributs.|  
|**Alle Member anzeigen**|Sucht nach allen Mitgliedern der benannten Gruppe und hebt sie hervor.|  
|**Alle Verweise anzeigen**|Sucht nach allen Verweisen auf die ausgewählte Gruppe (Gruppen mit `ref="selectedGroup"`) und hebt sie hervor.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)   
 [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md)



