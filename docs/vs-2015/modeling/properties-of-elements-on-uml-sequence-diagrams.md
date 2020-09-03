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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671428"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Eigenschaften von Elementen in UML-Sequenzdiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Element in einem UML-Diagramm hat Eigenschaften. Um die Eigenschaften eines Elements anzuzeigen, klicken Sie mit der rechten Maustaste auf das Element im Diagramm oder im **UML-Modell-Explorer** , und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

> [!NOTE]
> In diesem Thema werden die Eigenschaften von Elementen in UML-Sequenzdiagrammen behandelt. Weitere Informationen zum Lesen von UML-Sequenzdiagrammen finden Sie unter [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md). Weitere Informationen zum Zeichnen von UML-Sequenzdiagrammen finden Sie unter [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Eigenschaften von Elementen

|Eigenschaft|Standard|Element|BESCHREIBUNG|
|--------------|-------------|-------------|-----------------|
|**Name**|Ein Standardname|All|Bezeichnet das Element.|
|**Qualifizierter Name**|Paket :: Name|All|Bezeichnet das Element eindeutig. Mit dem qualifizierten Namen des Pakets, das es enthält, als Präfix.|
|**Arbeitselemente**|0 zugeordnet|All|Die Anzahl von Arbeitselemente, die diesem Element zugeordnet sind. Informationen zum Zuordnen von Arbeitsaufgaben finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).|
|**Beschreibung**|(leer)|All|Sie können hier allgemeine Hinweise zum Element angeben.|
|**Farbe**|(Standard für Elementtyp)|Lebenslinie, Meldung|Die Farbe der Form. Dies ist eine Eigenschaft der Form und nicht des angezeigten Elements.|
|**Type**|(leer)|Lebenslinie|Der Typ der Instanz, die die Lebenslinie darstellt.<br /><br /> Wird in der Kopfzeile der Lebenslinie ein Referenzsymbol angezeigt, ist diese Klasse oder Schnittstelle separat im UML-Modell-Explorer vorhanden und kann in einem Klassendiagramm angezeigt werden.|
|**Actor** (Schauspieler)|Falsch|Lebenslinie|Gibt an, ob die Lebenslinie einen Benutzer, ein Gerät oder eine Softwarekomponente außerhalb der Komponente, mit der sich das Diagramm befasst, darstellt.|
|**Kind**|**Complete** : eine Nachricht, die Absender und Empfänger enthält.<br /><br /> **Gefunden** -eine Meldung mit einem nicht angegebenen Absender.<br /><br /> **Lost** -eine Nachricht, die einen nicht angegebenen Empfänger aufweist.|`Message`|Gibt an, welche Endungen einer Meldung an eine Lebenslinie angefügt sind.<br /><br /> Diese Eigenschaft kann nicht geändert werden. Sie wird festgelegt, wenn Sie die Meldung erstellen.|
|**Sort**|**AsynchCall, eine asynchrone** Meldung.<br /><br /> **Synchroncalla** : eine synchrone Meldung.<br /><br /> **Reply** -der Rückgabe Teil einer synchronen Nachricht.<br /><br /> " **Kreatemess** ": eine Meldung zur Instanzerstellung.|`Message`|Der Typ der Meldung. Diese Eigenschaft kann nicht geändert werden. Sie wird durch das Tool bestimmt, das Sie verwenden, um die Meldung zu erstellen.|
|**Vorgang**|(leer)|`Message`|Eine Methode, die von der Meldung in der empfangenden Lebenslinie aufgerufen wird.<br /><br /> Nur sichtbar, wenn die empfangende Lebenslinie mit einer Schnittstelle oder einer Klasse verknüpft ist.|
|**Bezieht sich auf**|Ein Sequenzdiagramm|Interaktionsverwendung|Das von dieser Interaktionsverwendung aufgerufene Sequenzdiagramm.|
|**Interaktionsoperator**|Festlegen, wenn Sie den Befehl **Umschließen mit** verwendet haben|Kombiniertes Fragment|Der Operator, der durch dieses Fragment oder die Auflistung von Fragmenten dargestellt wird.|
|**Torschütze**|(leer)|Interaktionsoperand in einem kombinierten Fragment|Die Sequenz im Fragment erfolgt nur, wenn der Wächter auf „true“ festgelegt ist.<br /><br /> Um das oberste Fragment eines beliebigen kombinierten Fragments auszuwählen, klicken Sie unterhalb des Fragmenttitels.|
|**Min., max.**|(keine Einschränkung)|Kombiniertes Loop-Fragment|Die minimale und maximale Anzahl an Malen, die die Schleife ausgeführt wird.|
|**Meldungen**|(leer)|Kombinierte Consider- und<br /><br /> Ignore-Fragmente|Die Meldungen, die in diesem Fragment berücksichtigt oder ignoriert werden.|

## <a name="see-also"></a>Weitere Informationen
 [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md) UML-Sequenzdiagramme [: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md) [beschreiben die Ablauf Steuerung mit Fragmenten in UML-Sequenzdiagrammen](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
