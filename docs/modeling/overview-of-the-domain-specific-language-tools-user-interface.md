---
title: "&#220;bersicht &#252;ber die Benutzeroberfl&#228;che f&#252;r dom&#228;nenspezifische Sprachtools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.editor"
helpviewer_keywords: 
  - "Domänenspezifische Sprachtools, Benutzeroberfläche"
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# &#220;bersicht &#252;ber die Benutzeroberfl&#228;che f&#252;r dom&#228;nenspezifische Sprachtools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie zuerst eine Projektmappe für die domänenspezifischen Sprachtoole \(DSL\-Toole\) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]öffnen, ähnelt der Benutzeroberfläche der folgenden Abbildung.  
  
 ![DSL&#45;Designer](../modeling/media/dsl_designer.png "dsl\_designer")  
  
 In der folgenden Tabelle wird erläutert, wie die Teile der Benutzeroberfläche verwendet werden.  
  
|**Element**|**Definition**|  
|-----------------|--------------------|  
|Diagramm|Das Diagramm wird im Domänenmodell an.<br /><br /> Das Diagramm verfügt über zwei Seiten.  Eine Seite definiert die Typen der Elemente in den Modellen.  Die andere Seite definiert, wie die Modelle auf dem Bildschirm angezeigt werden.|  
|Toolbox|Ziehen Sie in der Toolbox auf Tools von Klassen und Typen von Domänen im Diagramm hinzugefügt werden soll.  Um Verbindungen und Beziehungen hinzuzufügen, klicken Sie auf das Tool Form ist, und anschließend den Quellknoten des Diagramms, und klicken Sie dann auf den Zielknoten.|  
|DSL\-Explorer|**DSL\-Explorer** tritt auf, wenn eine DSL\-Definition das aktive Fenster ist.  Es zeigt das DSL als Struktur an.  DSL\-Explorer können Sie Funktionen des Modells bearbeiten, die nicht im Diagramm angezeigt werden.  Sie können z. B. von Toolboxelementen und Schalter für den Validierungsprozess hinzufügen, indem Sie **DSL\-Explorer**verwenden.|  
|Fenster DSL\-Detail|Das Fenster wird **DSL\-Details**\-Eigenschaften der Elemente des Domänenmodells modells an, die es Ihnen ermöglichen, um zu steuern, wie Elemente angezeigt werden und wie Elemente kopiert und gelöscht werden.<br /><br /> -   In der Standardeinstellung wird das Fenster **DSL\-Details** neben den **Fehlerliste** und **Ausgabe** Fenster.|  
  
## Das Domänen\-Modell\-Diagramm  
 Domänenmodell Das Diagramm wird aus zwei Teilen.  Eine Seite des Diagramms wird die Elemente und Beziehungen im Modell an.  Die anderen Nebenvorstellungen, wie das Modell angezeigt werden soll, und schließt die Formen, die verwendet werden, um Elemente und Eigenschaften für den Diagramms anzuzeigen.  Das folgende Bild zeigt die Elemente des Diagramms an.  
  
 ![DSL&#45;Designer mit Verantwortlichkeitsbereich](../modeling/media/dsl_desinger.png "dsl\_desinger")  
  
 In der folgenden Tabelle werden einige der Elemente des Domänenmodells diagramms.  
  
|**Begriff**|**Definition**|  
|-----------------|--------------------|  
|Domänen\-Klasse|Domänen Klassen sind die Typen von Elementen in Modellen.<br /><br /> Eine Domänenklasse kann mehrmals in einem Diagramm angezeigt werden, wenn das Ziel aus mehr als einer Beziehung ist.<br /><br /> Um eine Domänenklasse hinzuzufügen, ziehen Sie das Tool von **Toolbox**\-Klassen für Domänen zur **Klassen und Beziehungen** Seite des Diagramms.|  
|Domänen\-Verhältnis|Domänen\-Verhältnisse sind die Typen von Links zwischen Elementen in den Modellen.<br /><br /> Ein *Einbettungs\-Verhältnis* gibt an, dass das Zielelement einen Besitzer hat oder über das Quellelement enthalten ist, und wird als durchgehende Linie.  Jedes Element in einem Modell sollte das Ziel eines einbettenden Beziehung sein, damit die Formulare Modell einer Struktur.  Ein *Bezugs\-Verhältnis* gibt einen allgemeinen Link zwischen Modellelementen an und wird als gestrichelte Linie.  Jedes Element kann beliebig viele Verweise gelassen haben.<br /><br /> Erstellen Sie eine Beziehung, indem Sie auf das Tool klicken Sie auf **Toolbox**klicken, auf die Quellspalten domänen Class und dann auf die Zielklasse klicken.|  
|Formen und Konnektoren|Forms geben, wie Modellelemente in einem DSL\-Diagramm angezeigt werden sollen. Zeilen angeben, Konnektoren in einem DSL\-Diagramm an, das verwendet werden kann, um Beziehungen anzuzeigen.<br /><br /> Um eine Form oder einen Konnektor zu erstellen, ziehen Sie das Tool zur **Diagrammelemente** Seite des Diagramms.|  
|Form\-Karten|Eine Form zugeordnet wird während eine Zeile im Domänenmodell der im Diagramm und eine Domänenklasse, die sie anzeigt, oder um einen Konnektor Domänen\-Verhältnis verknüpft ist, das sie anzeigt.|  
  
## Siehe auch  
 [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)