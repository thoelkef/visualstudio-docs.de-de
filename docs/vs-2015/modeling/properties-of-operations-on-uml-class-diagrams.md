---
title: Eigenschaften von Vorgängen in UML-Klassendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671351"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Eigenschaften von Vorgängen in UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem UML-Klassendiagramm können Sie Klassen und Schnittstellen *Vorgänge* hinzufügen. Ein Vorgang ist eine Methode oder Funktion, die von einer Instanz einer Klasse oder Schnittstelle ausgeführt werden kann.

 Zum Hinzufügen eines Vorgangs klicken Sie mit der rechten Maustaste auf die Klasse oder Schnittstelle, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorgang**

 Wenn die Vorgänge einer Klasse im Diagramm nicht sichtbar sind, klicken Sie auf das Erweiterungschevron am oberen Rand der Klasse oder Schnittstelle. Wenn der **Vorgangs** Header angezeigt wird, klicken Sie auf **[+]** , um den Abschnitt Vorgänge zu erweitern.

## <a name="signature-of-an-operation"></a>Signatur eines Vorgangs
 Die Signatur eines Vorgangs ist die Textzeile, die ihn in einer Klasse oder Schnittstelle in einem UML-Klassendiagramm darstellt. Es hat das folgende Format:

 \+ OperationName (Parameter1: Typ1 [*],...): ReturnType [ \* ]

 \+ bezeichnet öffentliche Sichtbarkeit. Die anderen zulässigen Werte sind - (privat), # (geschützt), ~ (Paket).

 `OperationName` wird unterstrichen, wenn die **ist static** -Eigenschaft den Wert true hat und kursiv ist, wenn die Eigenschaft **ist abstrakt** ist true ist.

 `: ReturnType` wird weggelassen, wenn kein Rückgabetyp definiert ist.

 `[*]` bezeichnet die Multiplizität eines Parameters oder Rückgabe Typs. Wird nicht angegeben, wenn die Multiplizität gleich 1 ist.

 Eine vollständige Beschreibung dieser Eigenschaften finden Sie im nächsten Abschnitt.

## <a name="properties"></a>Eigenschaften
 Dies sind die Eigenschaften eines Vorgangs in einer Klasse oder Schnittstelle in einem UML-Klassendiagramm.

 Um die Eigenschaften eines Vorgangs anzuzeigen, klicken Sie mit der rechten Maustaste auf den Vorgang in der Klasse oder Schnittstelle im Diagramm, und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

|      Eigenschaft       |   Standard    |                                                                                                                                                                                 BESCHREIBUNG                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Name**       | (ein neuer Name) |                                                                                                                                                                Sollte innerhalb des enthaltenden Typs eindeutig sein.                                                                                                                                                                 |
|   **Parameter**    |    (none)    |      Eine Liste mit dem Formular <em>Namen</em>**:**<em>Type</em>**,** <em>Name</em>**:**<em>Type</em>**,....** Klicken Sie auf **[...]** , um die Liste zu bearbeiten.<br /><br /> Die Typen können primitive Typen oder im Modell definierte Typen sein. Wenn Sie einen Namen für einen neuen Typ in dieser Eigenschaft eingeben, wird dem Abschnitt **Nicht spezifizierte Typen** des UML-Modell-Explorers ein Typ hinzugefügt.      |
|   **Rückgabetyp**   |    (none)    |                                                                               **(None)**, ein primitiver Typ oder ein Typ, der im Modell definiert ist. Wenn Sie einen Namen für einen neuen Typ in dieser Eigenschaft eingeben, wird dem Abschnitt **Nicht spezifizierte Typen** des UML-Modell-Explorers ein Typ hinzugefügt.                                                                                |
| **Nachbedingungen**  |    (none)    |                                                                                                                         Eine optionale Bedingung, die eine Beziehung zwischen dem Zustand des Systems vor und nach der Ausführung des Vorgangs angibt.                                                                                                                         |
|  **Preconditions**  |    (none)    |                                                                                                                            Eine optionale Bedingung, die die Annahmen über den Zustand des Systems vor Beginn der Ausführung des Vorgangs angibt.                                                                                                                            |
| **Textbedingungen** |    (none)    |                                                                                                                                                       Eine optionale Einschränkung der vom Vorgang zurückgegebenen Werte.                                                                                                                                                       |
|   **Sichtbarkeit**    |    Öffentlich    |                  Die zulässigen Werte und die Zeichen, die in der Signatur angezeigt werden, sind folgende:<br /><br /> **+ Öffentlich** – global sichtbar<br /><br /> **- Privat** – außerhalb des besitzenden Typs nicht sichtbar<br /><br /> **# Geschützt** – sichtbar für Typen, die vom Besitzer abgeleitet sind<br /><br /> **~ Paket** – sichtbar für andere Typen innerhalb des gleichen Pakets                   |
|    **Signatur**    |  +*Name*()   |                                                                                      Fasst Sichtbarkeit, Name, Parameter und Rückgabetyp dieses Vorgangs zusammen. Sie können diese Eigenschaften ändern, indem Sie die Signatur im Diagramm oder die einzelnen Eigenschaften bearbeiten.                                                                                      |
|   **Arbeitselemente**    | 0 zugeordnet |                                                                                                  Anzahl von zugeordneten Arbeitselementen. Schreibgeschützt.<br /><br /> Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Parallelität**   |  Sequenziell  | **Sequenziell** : der Vorgang ist oder wird ohne Parallelitäts Steuerung entworfen. Das gleichzeitige Aufrufen dieses Vorgangs kann zu Fehlern führen.<br /><br /> **Geschützt** : der Vorgang wird automatisch blockiert, bis andere Instanzen von ihm abgeschlossen sind.<br /><br /> **Gleich** zeitig: der Vorgang ist so konzipiert, dass mehrere Aufrufe gleichzeitig ausgeführt werden können. |
|    **Is Static**    |    Falsch     |                                                                                                  Bei „true“ wird dieser Vorgang von allen Instanzen dieses Typs gemeinsam genutzt.<br /><br /> Bei „true“ wird der Name des Vorgangs im Diagramm unterstrichen.                                                                                                   |
|   **Ist abstrakt**   |    Falsch     |                                                                                                                                        Bei „true“ ist mit diesem Vorgang kein Code verknüpft. Daher ist die besitzende Klasse abstrakt.                                                                                                                                         |
|     **Is Leaf**     |    Falsch     |                                                                                                                                              Der Designer beabsichtigt, dass dieser Vorgang in abgeleiteten Klassen nicht überschrieben werden kann.                                                                                                                                              |
|    **Is Query**     |    Falsch     |                                                                                                 Bei „true“ werden von diesem Vorgang keine bedeutenden Änderungen am Zustand des Systems vorgenommen. Aus diesem Grund kann er beispielsweise in einem Test zum Überprüfen des Status des Systems verwendet werden.                                                                                                  |
|  **Multiplizität**   |      1       |                                 **1** : ein einzelner Wert des angegebenen Typs.<br /><br /> **0.. 1** : kann sein `null` .<br /><br /> \* : eine Auflistung von Werten des angegebenen Typs.<br /><br /> **1.. \\ ** -eine Auflistung, die mindestens \* einen Wert enthält.<br /><br /> *n* `..` *m* : eine Auflistung, die zwischen `n` -und- `m` Werten enthält.                                  |
|   **Is Ordered**    |    Falsch     |                                                                                                                                             Bei „true“ bildet die Auflistung eine sequenzielle Liste. Für **Multiplicity** Multiplizität mehr als 1.                                                                                                                                              |
|    **Ist eindeutig**    |    Falsch     |                                                                                                                                         Bei „true“ enthält die Auflistung keine doppelten Werte. Für **Multiplicity** Multiplizität mehr als 1.                                                                                                                                         |

## <a name="see-also"></a>Weitere Informationen
 [UML-Klassendiagramme: Verweis](../modeling/uml-class-diagrams-reference.md) [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md) [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Eigenschaften von Zuordnungen in UML](../modeling/properties-of-associations-on-uml-class-diagrams.md) -Klassendiagrammen [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)
