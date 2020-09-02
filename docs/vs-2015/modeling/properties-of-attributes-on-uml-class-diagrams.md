---
title: Eigenschaften von Attributen in UML-Klassendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652064"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Eigenschaften von Attributen in UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem UML-Klassendiagramm können Sie Klassen und Schnittstellen *Attribute* hinzufügen. Ein Attribut definiert Werte, die Instanzen der Klasse oder Schnittstelle zugeordnet werden können.

 Um ein Attribut hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Klasse oder Schnittstelle, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Attribut**.

 Wenn die Attribute einer Klasse im Diagramm nicht sichtbar sind, klicken Sie auf das Chevron am oberen Rand der Klasse oder Schnittstelle, um es zu erweitern. Wenn der Header **Attribute** angezeigt wird, klicken Sie auf **[+]** , um den Abschnitt mit den Attributen zu erweitern.

## <a name="signature-of-an-attribute"></a>Signatur eines Attributs
 Die Signatur eines Attributs ist die Zeile, die es in einer Klasse oder Schnittstelle in einem UML-Klassendiagramm darstellt. Sie hat die folgende Form:

```
+ AttributeName : TypeName [*]
```

 \+ bezeichnet öffentliche Sichtbarkeit. Die anderen zulässigen Werte sind - (privat), # (geschützt), ~ (Paket).

 `AttributeName` ist unterstrichen, wenn das Attribut statisch ist.

 `: TypeName` wird weggelassen, wenn das Attribut keinen Typ hat.

 `[*]` kennzeichnet die Multiplizität. Wird nicht angegeben, wenn die Multiplizität gleich 1 ist.

## <a name="properties"></a>Eigenschaften
 Die folgende Tabelle beschreibt die Eigenschaften eines Attributs in einer Klasse oder einer Schnittstelle in einem UML-Klassendiagramm.

 Um die Eigenschaften eines Attributs anzuzeigen, klicken Sie mit der rechten Maustaste auf das Attribut in der Klasse oder Schnittstelle im Diagramm, und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden im Eigenschaftenfenster angezeigt.

 Um die Eigenschaften eines Attributs anzuzeigen, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Eigenschaften**.

|   **Eigenschaft**    | **Standard**  |                                                                                                                                                                                                         BESCHREIBUNG                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Standardwert** |   (leer)    |                                                                                                                                                                               Der Wert des Attributs, wenn der Klassifizierer instanziiert wird.                                                                                                                                                                                |
| **Is Read Only**  |    Falsch     |                                                                                                                                                                                    Bei „true“ kann der Wert des Attributs nicht geändert werden.                                                                                                                                                                                    |
|   **Is Static**   |    Falsch     |                                                                                                                    Bei „true“ wird ein einzelner Wert für dieses Attribut zwischen allen Instanzen dieses Typs gemeinsam genutzt.<br /><br /> Bei „true“ wird der Name des Attributs dort, wo er im Diagramm angezeigt wird, unterstrichen.                                                                                                                    |
|     **Name**      | (ein neuer Name) |                                                                                                                                                                                        Sollte innerhalb des besitzenden Klassifizierers eindeutig sein.                                                                                                                                                                                        |
|     **Type**      |    (none)    |                                                Ein primitiver Typ wie **Integer**oder ein im Modell definierter Typ. Sie können keinen nicht primitiven Typ wie z. B. **Decimal** verwenden, weil der Wert in den Metadaten codiert werden muss. Wenn Sie einen Namen für einen neuen Typ in dieser Eigenschaft eingeben, wird dem Abschnitt **Nicht spezifizierte Typen** des UML-Modell-Explorers ein Typ hinzugefügt.                                                 |
|  **Sichtbarkeit**   |    Öffentlich    |                                     Die zulässigen Werte und die Zeichen, die in der Signatur angezeigt werden, sind folgende:<br /><br /> **+ Öffentlich** – global sichtbar<br /><br /> **- Privat** – außerhalb des besitzenden Typs nicht sichtbar<br /><br /> **# Geschützt** – sichtbar für Typen, die vom Besitzer abgeleitet sind<br /><br /> **~ Paket** – sichtbar für andere Typen innerhalb des gleichen Pakets                                      |
|  **Arbeitselemente**   | 0 zugeordnet |                                                                                                                          Anzahl von zugeordneten Arbeitselementen. Schreibgeschützt.<br /><br /> Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Is Leaf**    |    Falsch     |                                                                                                                                                                    Bei „true“ ist das Zulassen einer Neudefinition dieses Attributs in abgeleiteten Typen nicht beabsichtigt.                                                                                                                                                                     |
|  **Is Derived**   |    Falsch     |                                                                                                              Bei „true“ wird dieses Attribut aus anderen Attributen berechnet. Diagonal wird z. B. aus Breite und Höhe berechnet. Die Details sollten in die **Beschreibung** oder einen angefügten Kommentar eingegeben werden.                                                                                                              |
|  **Beschreibung**  |   (leer)    |                                                                                                                                                                        Für allgemeine Hinweise oder zum Definieren von Einschränkungen für die Werte im Attribut.                                                                                                                                                                        |
| **Multiplizität**  |      1       | **1** – Dieses Attribut hat einen einzigen Wert des angegebenen Typs.<br /><br /> **0..1** – Dieses Attribut kann den Wert `null`haben.<br /><br /> **\\**\* der Wert dieses Attributs ist eine Auflistung von Werten.<br /><br /> **1.. \\ ** \* -der Wert dieses Attributs ist eine Auflistung, die mindestens einen Wert enthält.<br /><br /> *n* **..** *m* – Der Wert dieses Attributs ist eine Auflistung, die zwischen *n* und *m* Werte enthält. |
|  **Is Ordered**   |    Falsch     |                                                                                                                                                                    Bei „true“ bildet die Auflistung eine sequenzielle Liste. Für **Multiplizität** größer als 1.                                                                                                                                                                     |
|   **Ist eindeutig**   |    Falsch     |                                                                                                                                                                Bei „true“ enthält die Auflistung keine doppelten Werte. Für **Multiplizität** größer als 1.                                                                                                                                                                |

## <a name="see-also"></a>Weitere Informationen
 [UML-Klassendiagramme: Verweis](../modeling/uml-class-diagrams-reference.md) [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md) [Eigenschaften von Operationen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md) [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md) [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)
