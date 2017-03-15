---
title: "Kontextmen&#252;s (XML-Schema-Explorer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Kontextmen&#252;s (XML-Schema-Explorer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden Kontextmenüelemente werden verwendet, um schemaspezifische Suchen und andere Vorgänge auszuführen.  
  
## Knotentyp: Schemaset  
 In der folgenden Tabelle werden die Optionen beschrieben, die für Schemasetknoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Wahrscheinlichste Stammelemente anzeigen**|Sucht nach allen globalen Elementen, auf die nicht von anderen globalen Elementen verwiesen wird, und hebt sie hervor.|  
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen im Schemaset und hebt sie hervor.|  
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen im Schemaset und hebt sie hervor.|  
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** \(sofern es noch nicht geöffnet ist\).In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## Knotentyp: Namespace  
 In der folgenden Tabelle werden die Optionen beschrieben, die für Namespaceknoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Alle eingehenden Verweise anzeigen**|Sucht nach Dateien, die den ausgewählten Namespace importieren, und hebt sie hervor.|  
|**Alle ausgehenden Verweise anzeigen**|Sucht und hebt für jede Datei im ausgewählten Namespace Folgendes hervor:<br /><br /> -   Alle Namespaces, auf die in den **import**\-Anweisungen ohne ein `schemaLocation`\-Attribut verwiesen wird.<br />-   Alle Dateien in Namespaces außer dem ausgewählten Namespace, die im `schemaLocation`\-Attribut in import\- und include\-Anweisungen angegeben sind.|  
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen im ausgewählten Namespace und hebt sie hervor.|  
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen im ausgewählten Namespace und hebt sie hervor.|  
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** \(sofern es noch nicht geöffnet ist\).In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## Knotentyp: Datei  
 In der folgenden Tabelle werden die Optionen beschrieben, die für Dateiknoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Alle eingehenden Verweise anzeigen**|Sucht nach allen Dateien, in denen die ausgewählte Datei in den `schemaLocation`\-Attributen der include\- und import\-Anweisungen angegeben ist, und hebt sie hervor.|  
|**Alle ausgehenden Verweise anzeigen**|Sucht und hebt Folgendes hervor:<br /><br /> -   Alle Namespaces, die in den Namespaceattributen aller **import**\-Anweisungen angegeben werden, die nicht über das `schemaLocation`\-Attribut verfügen.<br />-   Alle in den `schemaLocation`\-Attributen aller import\- und include\-Anweisungen angegebenen Dateien.|  
|**Globale Typen anzeigen**|Sucht nach allen globalen Typen in dieser Datei und hebt sie hervor.|  
|**Globale Elemente anzeigen**|Sucht nach allen globalen Elementen in dieser Datei und hebt sie hervor.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML\-Editor.Das im XML\-Schema\-Explorer ausgewählte Element wird auch im XML\-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** \(sofern es noch nicht geöffnet ist\).In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## Alle globalen Knotentypen  
 In der folgenden Tabelle werden die Optionen beschrieben, die für alle globalen Knoten verfügbar sind.  
  
|Option|Beschreibung|  
|------------|------------------|  
|**In Diagrammansicht anzeigen**|Öffnet die Diagrammansicht.Wenn der ausgewählte Knoten nicht im Arbeitsbereich vorhanden ist, wird er dem Arbeitsbereich hinzugefügt und ausgewählt.|  
|**In Inhaltsmodellansicht anzeigen**|Öffnet die Inhaltsmodellansicht.Wenn der ausgewählte Knoten nicht im Arbeitsbereich vorhanden ist, wird er dem Arbeitsbereich hinzugefügt und ausgewählt.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML\-Editor.Das im XML\-Schema\-Explorer ausgewählte Element wird auch im XML\-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** \(sofern es noch nicht geöffnet ist\).In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## Knotentyp: Element  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Elementknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Gehe zu Typdefinition**|Navigiert zur Typdefinition des ausgewählten Elements.Dies gilt, wenn der Typ, der für das Element verwendet wird, ein globaler Typ ist.|  
|**Gehe zum ursprünglichen Element**|Navigiert bei Elementverweisen zur eigentlichen Definition des Elements.|  
|**Alle Verweise anzeigen**|Sucht für globale Elemente nach allen Verweisen auf das ausgewählte Element \(Elemente mit `ref="selectedElement"`\) und hebt sie hervor.|  
|**Ersetzungsgruppenmitglieder anzeigen**|Bei Köpfen einer Ersetzungsgruppe werden alle Elemente gesucht und hervorgehoben, die Member der Ersetzungsgruppe sind, deren ausgewähltes Element ein Member ist.Dadurch werden direkte und indirekte Teilnehmer angezeigt.|  
|**Ersetzungsgruppenköpfe anzeigen**|Bei globalen Elementen, die Member einer Ersetzungsgruppe sind, werden alle direkten und indirekten Köpfe für ein Element wie das folgende gesucht und hervorgehoben:<br /><br /> -   Ein Ersetzungsgruppenkopf, der für das ausgewählte Element angegeben ist.<br />-   Ein Ersetzungsgruppenkopf, der für das Head\-Element angegeben ist.|  
|**Beispiel\-XML generieren**|Ist nur für globale Elemente verfügbar.Generiert eine Beispiel\-XML\-Datei für das globale Element.|  
  
## Knotentyp: Globale Typen  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für globale Typknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Basistyp anzeigen**|Navigiert zum Basistyp des ausgewählten Typs, wenn der ausgewählte Typ von einem globalen Typ abgeleitet ist.|  
|**Alle Verweise anzeigen**|Sucht und hebt alle Verweise auf den ausgewählten Typ hervor.Dazu gehören Elemente und Attribute des ausgewählten Typs und Typen, die vom ausgewählten Typ abgeleitet sind.|  
|**Alle abgeleiteten Typen anzeigen**|Sucht nach allen Typen, die direkt und indirekt vom ausgewählten Typ abgeleitet sind, und hebt sie hervor.|  
|**Alle Vorgänger anzeigen**|Zeigt alle übergeordneten \(Basis\-\)Typen an.|  
  
## Knotentyp: Attribut  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Attributknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Gehe zu Typdefinition**|Navigiert zur Typdefinition des ausgewählten Attributs, wenn der für das Attribut verwendete Typ ein globaler Typ ist.|  
|**Gehe zum ursprünglichen Attribut**|Bei Attributverweisen wird zur tatsächlichen Definition des Attributs navigiert.|  
|**Alle Verweise anzeigen**|Sucht für globale Attribute nach allen Verweisen auf das ausgewählte Attribut \(andere Attribute mit `ref="selectedAttribute"`\) und hebt sie hervor.|  
  
## Knotentyp: Attributgruppe  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für Attributgruppenknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Gehe zu Definition**|Navigiert für Verweise zur tatsächlichen Definition des Attributs.|  
|**Alle Mitglieder anzeigen**|Sucht nach allen Mitgliedern der Attributgruppe und hebt sie hervor.|  
|**Alle Verweise anzeigen**|Sucht nach allen Verweisen auf die ausgewählte Attributgruppe \(Attributgruppen mit `ref="selectedAttributeGroup"`\) und hebt sie hervor.|  
  
## Knotentyp: Benannte Gruppe  
 Neben den oben beschriebenen Optionen für globale Knoten enthält das Kontextmenü für benannte Gruppenknoten die folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Gehe zu Definition**|Navigiert für Verweise zur tatsächlichen Definition des Attributs.|  
|**Alle Mitglieder anzeigen**|Sucht nach allen Mitgliedern der benannten Gruppe und hebt sie hervor.|  
|**Alle Verweise anzeigen**|Sucht nach allen Verweisen auf die ausgewählte Gruppe \(Gruppen mit `ref="selectedGroup"`\) und hebt sie hervor.|  
  
## Siehe auch  
 [XML\-Schema\-Explorer](../xml-tools/xml-schema-explorer.md)   
 [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md)