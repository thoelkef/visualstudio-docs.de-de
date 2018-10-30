---
title: Eigenschaften von Vorgängen in UML-Klassendiagrammen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a0a7c8147b465e932a3fc48701b70ba5f5336ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822526"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Eigenschaften von Vorgängen in UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können in einem UML-Klassendiagramm hinzufügen *Vorgänge* Klassen und Schnittstellen. Ein Vorgang ist eine Methode oder Funktion, die von einer Instanz einer Klasse oder Schnittstelle ausgeführt werden kann.  

 Um einen Vorgang hinzuzufügen, mit der rechten Maustaste die Klasse oder Schnittstelle, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Vorgang**.  

 Wenn die Vorgänge einer Klasse im Diagramm nicht sichtbar sind, klicken Sie auf das Erweiterungschevron am oberen Rand der Klasse oder Schnittstelle. Wenn Sie sehen die **Vorgang** -Header, klicken Sie auf **[+]** Abschnitt mit den Vorgängen zu erweitern.  

## <a name="signature-of-an-operation"></a>Signatur eines Vorgangs  
 Die Signatur eines Vorgangs ist die Textzeile, die ihn in einer Klasse oder Schnittstelle in einem UML-Klassendiagramm darstellt. Er hat das folgende Format:  

 \+ OperationName (parameter1: Type1 [*],...): ReturnType [\*]  

 \+ kennzeichnet öffentliche Sichtbarkeit. Die anderen zulässigen Werte sind - (privat), # (geschützt), ~ (Paket).  

 `OperationName` ist unterstrichen, wenn die **ist statisch** Eigenschaft ist "true", und kursiv Wenn die **Is Abstract** Eigenschaft ist "true".  

 `: ReturnType` wird weggelassen, wenn kein Rückgabetyp definiert ist.  

 `[*]` bezeichnet die Multiplizität eines Parameters oder Rückgabetyps. Es wird weggelassen, wenn die Multiplizität 1 ist.  

 Eine vollständige Beschreibung dieser Eigenschaften finden Sie im nächsten Abschnitt.  

## <a name="properties"></a>Eigenschaften  
 Dies sind die Eigenschaften eines Vorgangs in einer Klasse oder Schnittstelle in einem UML-Klassendiagramm.  

 Um die Eigenschaften eines Vorgangs anzuzeigen, mit der rechten Maustaste in des Vorgangs in der Klasse oder Schnittstelle im Diagramm, und klicken Sie dann auf **Eigenschaften**. Die Eigenschaften werden in der **Eigenschaften** Fenster.  


|      Eigenschaft       |   Standard    |                                                                                                                                                                                 Beschreibung                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Name**       | (ein neuer Name) |                                                                                                                                                                Sollte innerhalb des enthaltenden Typs eindeutig sein.                                                                                                                                                                 |
|   **Parameter**    |    (keine)    |      Eine Liste der Form <em>Namen</em>**:**<em>Typ</em>**,** <em>Namen</em>**:**  <em>Typ</em>**,...** Klicken Sie auf **[...]**  so bearbeiten Sie die Liste.<br /><br /> Die Typen können primitive Typen oder im Modell definierte Typen sein. Wenn Sie einen Namen für einen neuen Typ in dieser Eigenschaft eingeben, wird dem Abschnitt **Nicht spezifizierte Typen** des UML-Modell-Explorers ein Typ hinzugefügt.      |
|   **Rückgabetyp**   |    (keine)    |                                                                               **(keine)** , oder ein primitiver Typ oder ein Typ, der im Modell definiert ist. Wenn Sie einen Namen für einen neuen Typ in dieser Eigenschaft eingeben, wird dem Abschnitt **Nicht spezifizierte Typen** des UML-Modell-Explorers ein Typ hinzugefügt.                                                                                |
| **Nachbedingungen**  |    (keine)    |                                                                                                                         Eine optionale Bedingung, die eine Beziehung zwischen dem Zustand des Systems vor und nach der Ausführung des Vorgangs angibt.                                                                                                                         |
|  **Vorbedingungen**  |    (keine)    |                                                                                                                            Eine optionale Bedingung, die die Annahmen über den Zustand des Systems vor Beginn der Ausführung des Vorgangs angibt.                                                                                                                            |
| **Textbedingungen** |    (keine)    |                                                                                                                                                       Eine optionale Einschränkung der vom Vorgang zurückgegebenen Werte.                                                                                                                                                       |
|   **Sichtbarkeit**    |    Public    |                  Die zulässigen Werte und die Zeichen, die in der Signatur angezeigt werden, sind folgende:<br /><br /> **+ Öffentlich** – global sichtbar<br /><br /> **- Privat** – außerhalb des besitzenden Typs nicht sichtbar<br /><br /> **# Geschützt** – sichtbar für Typen, die vom Besitzer abgeleitet sind<br /><br /> **~ Paket** – sichtbar für andere Typen innerhalb des gleichen Pakets                   |
|    **Signatur**    |  +*Namen*)   |                                                                                      Fasst Sichtbarkeit, Name, Parameter und Rückgabetyp dieses Vorgangs zusammen. Sie können diese Eigenschaften ändern, indem Sie die Signatur im Diagramm oder die einzelnen Eigenschaften bearbeiten.                                                                                      |
|   **Typen von Arbeitselementen**    | 0 zugeordnet |                                                                                                  Anzahl von zugeordneten Arbeitsaufgaben. Schreibgeschützt.<br /><br /> Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Parallelität**   |  Sequenziell  | **Sequenzielle** -der Vorgang ist, oder wird ohne parallelitätssteuerung entworfen werden. Das gleichzeitige Aufrufen dieses Vorgangs kann zu Fehlern führen.<br /><br /> **Überwachte** -der Vorgang wird automatisch blockiert, bis andere Instanzen des abgeschlossen sind.<br /><br /> **Gleichzeitige** -Vorgangs ist so konzipiert, dass mehrere Aufrufe gleichzeitig ausgeführt werden können. |
|    **Ist Static**    |    False     |                                                                                                  Bei „true“ wird dieser Vorgang von allen Instanzen dieses Typs gemeinsam genutzt.<br /><br /> Bei „true“ wird der Name des Vorgangs im Diagramm unterstrichen.                                                                                                   |
|   **Ist abstrakt**   |    False     |                                                                                                                                        Bei „true“ ist mit diesem Vorgang kein Code verknüpft. Daher ist die besitzende Klasse abstrakt.                                                                                                                                         |
|     **Wird die Blattebene**     |    False     |                                                                                                                                              Der Designer beabsichtigt, dass dieser Vorgang in abgeleiteten Klassen nicht überschrieben werden kann.                                                                                                                                              |
|    **Abfrage**     |    False     |                                                                                                 Bei „true“ werden von diesem Vorgang keine bedeutenden Änderungen am Zustand des Systems vorgenommen. Aus diesem Grund kann er beispielsweise in einem Test zum Überprüfen des Status des Systems verwendet werden.                                                                                                  |
|  **Multiplizität**   |      1       |                                 **1** -einen einzelnen Wert des angegebenen Typs.<br /><br /> **0.. 1** -kann `null`.<br /><br /> \* -eine Auflistung von Werten des angegebenen Typs.<br /><br /> **1..\\**  \* – eine Auflistung, die mindestens einen Wert enthält.<br /><br /> *n* `..` *m* -eine Auflistung, die zwischen `n` und `m` Werte.                                  |
|   **Sortiert**    |    False     |                                                                                                                                             Bei „true“ bildet die Auflistung eine sequenzielle Liste. Für **Multiplizität** mehr als 1.                                                                                                                                              |
|    **Ist eindeutig**    |    False     |                                                                                                                                         Bei „true“ enthält die Auflistung keine doppelten Werte. Für **Multiplizität** mehr als 1.                                                                                                                                         |

## <a name="see-also"></a>Siehe auch  
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [Eigenschaften von Typen in UML-Klassendiagrammen](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)



