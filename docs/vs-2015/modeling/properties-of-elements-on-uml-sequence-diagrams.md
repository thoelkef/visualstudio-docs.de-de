---
title: Eigenschaften von Elementen in UML-Sequenzdiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6de88572b685b5a432b4f73b125a464f125218b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961951"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Eigenschaften von Elementen in UML-Sequenzdiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Element in einem UML-Diagramm hat Eigenschaften. Um die Eigenschaften eines Elements anzuzeigen, die Maustaste des Elements im Diagramm oder im **UML-Modell-Explorer** , und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden in der **Eigenschaften** Fenster.  
  
> [!NOTE]
>  In diesem Thema werden die Eigenschaften von Elementen in UML-Sequenzdiagrammen behandelt. Weitere Informationen über das Lesen von UML-Sequenzdiagrammen finden Sie unter [UML Sequence Diagrams: Reference (Referenz zu UML-Klassendiagrammen)](../modeling/uml-sequence-diagrams-reference.md). Weitere Informationen über das Zeichnen von UML-Sequenzdiagrammen finden Sie unter [UML Sequence Diagrams: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Eigenschaften von Elementen  
  
|Eigenschaft|Standard|Element|Beschreibung|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Ein Standardname|Alle|Bezeichnet das Element.|  
|**Qualifizierter Name**|Paket:: Name|Alle|Bezeichnet das Element eindeutig. Mit dem qualifizierten Namen des Pakets, das es enthält, als Präfix.|  
|**Typen von Arbeitselementen**|0 zugeordnet|Alle|Die Anzahl von Arbeitsaufgaben, die diesem Element zugeordnet sind. Um Arbeitsaufgaben zu verknüpfen, finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).|  
|**Beschreibung**|(leer)|Alle|Sie können hier allgemeine Hinweise zum Element angeben.|  
|**Farbe**|(Standard für Elementtyp)|Lebenslinie, Meldung|Die Farbe der Form. Dies ist eine Eigenschaft der Form und nicht des angezeigten Elements.|  
|**Type**|(leer)|Lebenslinie|Der Typ der Instanz, die die Lebenslinie darstellt.<br /><br /> Wird in der Kopfzeile der Lebenslinie ein Referenzsymbol angezeigt, ist diese Klasse oder Schnittstelle separat im UML-Modell-Explorer vorhanden und kann in einem Klassendiagramm angezeigt werden.|  
|**Actor**|False|Lebenslinie|Gibt an, ob die Lebenslinie einen Benutzer, ein Gerät oder eine Softwarekomponente außerhalb der Komponente, mit der sich das Diagramm befasst, darstellt.|  
|**Kind**|**Vollständige** -eine Meldung mit Absender und Empfänger.<br /><br /> **Finden Sie** -eine Meldung mit einem nicht angegebenen Absender.<br /><br /> **Verlust** -eine Meldung mit einem nicht angegebenen Empfänger.|Meldung|Gibt an, welche Endungen einer Meldung an eine Lebenslinie angefügt sind.<br /><br /> Diese Eigenschaft kann nicht geändert werden. Sie wird festgelegt, wenn Sie die Meldung erstellen.|  
|**Sort**|**AsynchCall** – eine asynchrone Meldung.<br /><br /> **SynchCall** – eine synchrone Meldung.<br /><br /> **Antwort** – der Rückgabeteil einer synchronen Meldung.<br /><br /> **CreateMessage** – eine instanzerstellungsmeldung.|Meldung|Der Typ der Meldung. Diese Eigenschaft kann nicht geändert werden. Sie wird durch das Tool bestimmt, das Sie verwenden, um die Meldung zu erstellen.|  
|**Vorgang**|(leer)|Meldung|Eine Methode, die von der Meldung in der empfangenden Lebenslinie aufgerufen wird.<br /><br /> Nur sichtbar, wenn die empfangende Lebenslinie mit einer Schnittstelle oder einer Klasse verknüpft ist.|  
|**Bezieht sich auf**|Ein Sequenzdiagramm|Interaktionsverwendung|Das von dieser Interaktionsverwendung aufgerufene Sequenzdiagramm.|  
|**Interaktionsoperator**|Legen Sie bei der Verwendung der **Umschließen mit** Befehl|Kombiniertes Fragment|Der Operator, der durch dieses Fragment oder die Auflistung von Fragmenten dargestellt wird.|  
|**Guard**|(leer)|Interaktionsoperand in einem kombinierten Fragment|Die Sequenz im Fragment erfolgt nur, wenn der Wächter auf „true“ festgelegt ist.<br /><br /> Um das oberste Fragment eines beliebigen kombinierten Fragments auszuwählen, klicken Sie unterhalb des Fragmenttitels.|  
|**Min, Max**|(keine Einschränkung)|Kombiniertes Loop-Fragment|Die minimale und maximale Anzahl an Malen, die die Schleife ausgeführt wird.|  
|**Meldungen**|(leer)|Kombinierte Consider- und<br /><br /> Ignore-Fragmente|Die Meldungen, die in diesem Fragment berücksichtigt oder ignoriert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)   
 [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Beschreiben des Kontrollflusses mit Fragmenten in UML-Sequenzdiagrammen](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
