---
title: Integrate UML models with other models and tools | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: caecb85392170559a860a7dc334570880d6e76f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301475"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrieren von UML-Modellen in andere Modelle und Tools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML-Modelle können in andere Modelle und domänenspezifische Sprachen integriert sein.

 Sie können die Modelle wie folgt integrieren, indem Sie Erweiterungscode für eine Vielzahl von Funktionen schreiben:

 Anfügen von Verweisen von einem beliebigen Element an andere Elemente, z. B. an Dateien oder Elemente in anderen Modellen.
In einem UML-Element können Sie Links zu anderen UML-Elementen, Dateien oder anderen Objekten speichern, indem Sie deren Identitäten als Zeichenfolgen codieren.

 Sie können z. B. eine Erweiterung schreiben, mit der eine beliebige UML-Aktion (das heißt, ein Element in einem Aktivitätsdiagramm) mit einem anderen Aktivitätsdiagramm verknüpft werden kann. Wenn der Benutzer auf die Aktion doppelklickt, wird das andere Diagramm geöffnet. So kann der Benutzer eine ausführlichere Ansicht der Aktion bereitstellen.

 Zwei Möglichkeiten sind verfügbar, um Zeichenfolgen und andere Daten in einem beliebigen Element zu speichern:

- **Stereotype properties.** Sie können ein UML-Profil definieren, in dem Sie ein Stereotyp definieren, das Eigenschaften zu bestimmten Arten von UML-Elementen hinzufügt. For example, you could define a profile that adds a property named **MoreDetail** to a UML action. Sie können Erweiterungscode schreiben, mit dem Linkdaten in einer Aktion gespeichert werden, indem das Stereotyp auf die Aktion angewendet wird und anschließend die Daten in der Eigenschaft gespeichert werden.

   Das Stereotyp und dessen Eigenschaften sind für Benutzer im Eigenschaftenfenster sichtbar.

   Zum Bereitstellen dieser Erweiterung packen Sie die Profildefinition und den Erweiterungscode in einer einzelnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterung.

   For more information, see [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md).

   For a sample project in which a profile is deployed together with menu commands and gesture handlers, see [Sample: UML Profiles](https://go.microsoft.com/fwlink/?LinkID=213811).

- **References.** An jedes UML-Element können Sie einen Satz von Zeichenfolgen anfügen. Sie können Code schreiben, in dem die Informationen gespeichert werden, z. B. ein Dateiname oder die GUID eines anderen Elements. Dazu müssen Sie keine weiteren Definitionen bereitstellen. Verweise sind für Benutzer nicht direkt sichtbar.

   For more information, see [Attach reference strings to UML model elements](../modeling/attach-reference-strings-to-uml-model-elements.md). For a sample, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

  Es gibt zwei Möglichkeiten, Verweise auf Modellelemente zu codieren:

- **GUID and Filename** of the target model element and the model that contains it, or a particular diagram that displays it.

   For an example, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

- **ModelBus References.** ModelBus ist ein Framework zum Erstellen und Auflösen von Verweisen zwischen Modellen. Enthalten ist die ModelBus-Auswahl, mit der Benutzer ein Element in einem Modell auswählen können. Zudem können Verweise leichter aufgelöst werden, die aufgrund von Änderungen im Zielmodell verloren gehen.

   For more information, see [Integrating Models by using Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Weitergeben von Änderungen von einem Modell an ein anderes.
  Sie können z. B. den Namen eines Elements mit dem Namen des verknüpften Diagramms synchronisieren, damit bei Änderungen des einen der andere ebenfalls geändert wird. Dafür sind zwei Mechanismen verfügbar:

1. **VMSDK Rules** can be used to propagate changes inside the same model.

    For an example, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

2. **VMSDK Events** can be used to propagate changes outside the model – for example, to change the filename of a linked document, or to change an element in another model.

   For information about both these mechanisms, see [How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Drag elements to copy them from one model to another You can let the user create elements by dragging items onto a UML diagram. Das erstellte Element muss keine Kopie des Originals sein. Sie können es den Benutzern beispielsweise ermöglichen, ein Aktivitätsdiagramm aus dem Projektmappen-Explorer in ein anderes Aktivitätsdiagramm zu ziehen, um eine neue Aktion zu erstellen.

   For more information see [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) and [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="samples"></a>Proben
 Please see the code sample [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813). Anhand des Beispiels können Benutzer eine Datei auf ein beliebiges UML-Element ziehen und die Datei später durch Doppelklicken auf das Element öffnen. Sie können z. B. ein Aktivitätsdiagramm mit einem Anwendungsfallelement verknüpfen. Ein Symbol gibt an, welche Elemente über Links verfügen.

 Diese Verfahren werden im folgenden Codebeispiel veranschaulicht:

- [Anfügen von Referenzzeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md)

   Im Beispielcode werden Dateipfade und Element-GUIDs in dem Element zugeordneten Verweiszeichenfolgen gespeichert.

- Hinzufügen von Decorator-Elementen zu UML-Elementen. For general information about decorators, see [Customizing Text and Image Fields](../modeling/customizing-text-and-image-fields.md).

   Im Beispiel wird den UML-Formen ein Decorator-Bildelement hinzugefügt.

- [Gewusst wie: Reagieren auf Änderungen in einem UML-Modell](../misc/how-to-respond-to-changes-in-a-uml-model.md)

   Das Beispiel veranschaulicht das Definieren einer Regel, die auf neu in einem Diagramm angezeigte Formen reagiert.

- [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Definieren eines Gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)

   Das Beispiel zeigt, wie die Elemente behandelt werden, die von Windows-Explorer (oder von Datei-Explorer), dem Projektmappen-Explorer und anderen UML-Elementen gezogen werden.

  For an example in which a UML model is be read by a DSL, see [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Siehe auch
 [Define a menu command on a modeling diagram](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md) [Sample: UML Profiles](https://go.microsoft.com/fwlink/?LinkID=213811) [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813)
