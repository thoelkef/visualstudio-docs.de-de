---
title: Edit UML models and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295531"
---
# <a name="edit-uml-models-and-diagrams"></a>Bearbeiten von UML-Modellen und -Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein UML-Modell über die durch die verschiedenen Diagrammtypen bereitgestellten Ansichten erstellen und bearbeiten. Durch Bereitstellen von unterschiedlichen Perspektiven auf Ihrem System helfen Ihnen diese Diagramme dabei, verschiedene Aspekte des Degins und Anforderungen zu verstehen. Visual Studio stellt Vorlagen für fünf der am häufigsten verwendeten UML-Diagrammtypen bereit:

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Dieses Thema beschreibt Verfahren zum Bearbeiten des Modells, das bei den verschiedenen Diagrammtypen gleich ist. For more information that is specific to particular types of diagrams, see [Create models for your app](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>In diesem Thema

- [UML Diagrams are Views of a UML Model](#Views)

- [Creating UML Modeling Diagrams](#Creating)

- [Drawing UML Modeling Diagrams](#Drawing)

- [Editing Shapes and Connectors](#Editing)

- [Undoing Changes to the Model](#Undo)

- [Sharing Elements between Diagrams](#Sharing)

- [Copying Elements and Groups of Related Elements](#Copying)

- [Deleting a Model Element or its Views](#Deleting)

- [Searching text in a diagram](#Searching)

- [Preparing a Diagram for Presentation](#presentation)

- [Extending the UML Designers](#extensions)

## <a name="Views"></a> UML Diagrams are Views of a UML Model
 Sie können UML-Diagramme nur in Modellierungsprojekten erstellen und verwenden. For more information about how to create diagrams and projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Ein Modellierungsprojekt enthält ein einzelnes UML-Modell. Jedes UML-Diagramm im Projekt ist eine Ansicht des UML-Modells.

- You can see the model in **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

- Jede Form in einem Diagramm ist eine Ansicht eines Elements im Modell. Wenn Sie eine neue Form in einem Diagramm platzieren, erstellen Sie ein neues Element im Modell.

- When you save any diagram, Visual Studio saves the whole model, all its diagrams, and the modeling project file.

## <a name="Creating"></a> Creating UML Modeling Diagrams

1. On the **Architecture** menu in Visual Studio, click **New UML or Layer Diagram**.

2. Wählen Sie Ihr Diagramm aus, und benennen Sie es.

3. In **Add to modeling project**, select an existing modeling project, or select **Create a new modeling project**.

   > [!NOTE]
   > Im Modellierungsprojekt muss ein Modellierungsdiagramm vorhanden sein.

   Sie können auch im Projektmappen-Explorer einem vorhandenen Modellierungsprojekt ein Diagramm hinzufügen. Right-click the modeling project, point to **Add**, and then click **New Item**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Erstellen eines leeren UML-Modellierungsprojekts

- On the **File** menu, point to **New**, click **Project**, and in the **New Project** dialog box, double-click **Modeling Projects**.

  For more information about how to manage modeling projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a> Drawing UML Modeling Diagrams
 Ein Modellierungsdiagramm zeigt eine Auflistung von Modellelementen, die durch Beziehungen verknüpft sind. Jedes Element wird als Form, und jede Beziehung als Konnektor zwischen zwei Formen angezeigt.

 Es gibt zwei Arten von Tools, eines für Elemente und eines für Beziehungen. For example, in the UML class diagram Toolbox, **Class** is an element tool, and **Association** is a relationship tool.

> [!NOTE]
> If you want information that is specific to particular diagram types, see [Create models for your app](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Erstellen von Elementen und Beziehungen in einem UML-Modellierungsdiagramm

1. Um ein Modellelement zu erstellen, klicken Sie auf ein Element in der Toolbox, und klicken Sie dann auf das Diagramm, in dem es angezeigt werden soll. Nachdem Sie das Element erstellt haben, passen Sie die Größe und Form durch Ziehen der Ziehpunkte an.

    In einigen Fällen können Sie ein neues Element in einem anderen Element platzieren. Beispielsweise können Sie eine Klasse in einem Paket in einem UML-Klassendiagramm platzieren.

   > [!NOTE]
   > If you cannot see the toolbox, click **Toolbox** on the **View** menu.

2. Um eine Beziehung zu erstellen, klicken Sie auf ein Beziehungstool, klicken Sie auf das Element, in dem die Beziehung gestartet werden soll und klicken Sie dann auf das Element, in dem sie enden soll.

    Verschiedene Typen von Beziehungen können bei verschiedene Arten von Elementen beginnen oder enden. Beispielsweise kann eine Zuordnungsbeziehung in einem UML-Klassendiagramm nicht bei einem Kommentarelement beginnen oder enden.

   > [!NOTE]
   > Um das gleiche Tool mehrmals zu verwenden, doppelklicken Sie auf das Tool. When you have finished, click the **Pointer** tool.

   Bei einigen Arten von Diagrammen können Sie auch einfache Formen zeichnen. Diese Formen sind nicht Teil des Modells, Sie können sie jedoch verwenden, um Teile des Diagramms hervorzuheben oder in verschiedene Bereiche zu unterteilen.

## <a name="Editing"></a> Editing Shapes and Connectors
 Beim Ändern der Größe oder Farbe einer Form oder dem erneuten Erstellen eines Konnektors gibt es keine Auswirkungen auf das zugrunde liegende Modell. Wenn Sie eine Form im Diagramm oder im UML-Modell-Explorer umbenennen, wird das entsprechende Element im UML-Modell-Explorer und allen anderen Diagrammen, die dieses Element darstellen, umbenannt.

> [!NOTE]
> Es ist eine einfache Möglichkeit, neue Toolboxelemente zu erzeugen, aus denen Sie Gruppen von Elementen oder Elemente mit Eigenschaften Ihrer Wahl erstellen können. For more information, see [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

 Die folgende Abbildung zeigt, wie Sie die Größe einer Form oder ihren Namen ändern.

 ![Adjusting a model element](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Die integrierten Befehle enthalten keinen Befehl zum übersichtlichen Ausrichten von Formen. However, you can easily create your own alignment command by copying the code in the example in [Display a UML model on diagrams](../modeling/display-a-uml-model-on-diagrams.md).

 Die folgende Abbildung zeigt, wie die Route und Position eines Konnektors oder seiner Bezeichnungen angepasst werden.

 ![Adjusting a connector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>So verschieben Sie ein Ende der Verbindung zu einer anderen Form

1. Führen Sie einen der folgenden Schritte aus:

   - Press **CTRL** and move the end.

     \- oder -

   - Right-click the connector and then click **Reconnect**.

2. Klicken Sie auf das Ende des Konnektors, das Sie verschieben möchten.

3. Klicken Sie auf die Form, zu der Sie den Konnektor verschieben möchten.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Ändern der Farbe oder anderer Eigenschaften eines Elements, einer Beziehung oder eines Diagramms

- Click the element and set the fields in the **Properties** window.

     If you cannot see the **Properties** window, right-click the element, and then click **Properties.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Vergrößern und Verkleinern in einem Modellierungsdiagramm

- Press and hold the **CTRL** key while you rotate the mouse wheel.

     \- oder -

- Press and hold **CTRL+SHIFT**, and then click the left or right mouse button.

     \- oder -

- On the **Architecture Designers** toolbar, click the plus sign ( **+** ) or minus sign ( **-** ), or choose a zoom level.

## <a name="Searching"></a> Searching in a Diagram
 Die Schnellsuche-Funktion sucht nach Elementen in einem Diagramm. You must set **Look in:** to **Current Document**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Suchen nach Text in einem Modellierungsdiagramm

1. Press **CTRL+F**.

     \- oder -

     On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find**.

    > [!NOTE]
    > In the **Find and Replace** dialog box, you must leave the **Look in** field set to **Current Document**. Die anderen Optionen werden nicht unterstützt.

2. Type the text that you want to find, and then click **Find Next**.

    > [!NOTE]
    > Wenn der gesuchte Text in einer reduzierten Form enthalten ist, wird die Form hervorgehoben. Expand the shape, and then click **Find Next** again.

## <a name="Undo"></a> Undoing Changes to the Model
 You can undo and redo changes that you have made to the model and diagrams by using the **Undo** and **Redo** commands on the **Edit** menu.

 **Each modeling project has a single stack of changes.** Alle Änderungen, die Sie am Modell und den Diagrammen vornehmen, werden in diesem Stapel gespeichert. Der Stapel enthält außerdem Änderungen am Fokus zwischen Diagrammen. Durch den Befehl „Rückgängig“ werden die Änderungen in diesem Stapel rückgängig gemacht.

 Nehmen wir beispielsweise an, dass Sie diese Operationen ausführen: Ändern von Diagramm1; Ändern Sie den Fokus in Diagramm 2. Ändern Sie Diagram2. Wenn Sie Änderungen rückgängig machen, wird die letzte Änderung durch das erste Rückgängig machen rückgängig gemacht; duch das nächste Rückgängig machen wird der Fokus wieder auf Diagramm 1 gelegt; und durch das dritte Rückgängig machen wird die Änderung an Diagramm 1 rückgänig gemacht.

 **Closing a diagram truncates the stack of changes.** Wenn Sie ein Diagramm schließen, können Sie die an dem Diagramm vorgenommene Änderungen nicht rückgängig machen, außerdem können Sie zuvor am Modell oder dazugehörigen Diagrammen vorgenommene Änderungen nicht rückgängig machen.

 **You cannot undo while you are editing a property.** Während der Bearbeitung einer Eigenschaft im Eigenschaftenfenster oder in einer Bezeichnung in einem Diagramm können Sie nur Änderungen rückgängig machen, die Sie in dieser Eigenschaft vorgenommen haben. Schließen Sie Ihre Änderung in der Eigenschaft ab, indem Sie die EINGABETASTE drücken, oder brechen Sie den Vorgang ab, indem Sie ESC drücken. Anschließend können Sie Änderungen im Modell und den Diagrammen rückgängig machen.

 **Closing a diagram without saving might not have the effect you expect.** Wenn Sie Änderungen vornehmen und dann ein Diagramm schließen, ohne es zu speichern, werden die Änderungen im Modell weiterhin beibehalten. Es wird empfohlen, das gesamte Modell zu schließen, wenn Sie dies machen möchten, ohne es zu speichern.

## <a name="Sharing"></a> Sharing Elements between Diagrams
 Sie können eine spezielle Instanz eines Modellelements mehrmals in den Diagrammen angezeigen. Dies gilt für Klassen, Schnittstellen, Komponenten, Anwendungsfälle und Akteure.

 Dies ist hilfreich, wenn Sie unterschiedliche Gruppen von Beziehungen in unterschiedlichen Diagrammen anzeigen möchten. In einem Diagramm können Sie z. B. die Zuordnungen zwischen Customer- und Address-Klassen anzeigen. In einem anderen Diagramm können Sie die Address-Klasse mit der Zuordnung zum Postal-Bereich erneut anzeigen.

 Sie können die Eigenschaften eines Modellelements, wie z. B. den Namen ändern, indem Sie seine Ansichten in einem beliebigen Diagramm auswählen oder indem Sie sie im UML-Modell-Explorer auswählen.

 Jede Art von Diagramm kann nur einige Arten von Modellelementen anzeigen. Sie können beispielsweise keinen Anwendungsfall in einem Komponentendiagramm anzeigen. Daher funktionieren die folgenden Verfahren nur für einige Kombinationen von Modellelement und Diagramm.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>So fügen Sie eine neue Ansicht eines Modellelements mithilfe des UML-Modell-Explorers hinzu

1. To open **UML Model Explorer**, on the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Drag the model element from **UML Model Explorer** to a compatible diagram in the same project.

     Es wird eine Form angezeigt, die eine Ansicht des Modellelements bereitstellt, die zusätzlich zu Ansichten in anderen Diagrammen oder dem gleichen Diagramm angezeigt werden können.

    > [!NOTE]
    > Der Effekt unterscheidet sich, wenn Sie eine Klasse oder eine Komponente in ein Sequenzdiagramm ziehen. In diesem Fall wird eine neue Lebenslinie erstellt, deren Typ diese Klasse oder eine Komponente ist. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>So fügen Sie eine neue Ansicht eines Modellelements mithilfe der Funktion „Verweis einfügen“

1. Right-click an existing element, and then click **Copy**.

    - Sie können mehrere Elemente gleichzeitig kopieren. Hold down the CTRL key while you click each element, right-click one of them, and then click **Copy**.

2. Right-click an empty part of a compatible diagram, and then click **Paste Reference**.

     Es wird eine andere Ansicht des gleichen Elements angezeigt.

    > [!NOTE]
    > This differs from the **Paste** command, which creates a new element in the model. For more information, see [Copying Elements and Groups of Related Elements](#Copying).

> [!NOTE]
> Wenn Sie Diagrammansichten von zwei Modellelementen hinzufügen, die bereits durch eine Beziehung verbunden sind, wird eine Ansicht der Beziehung auch im Diagramm angezeigt. Sie können diese Ansicht nur eines der Elemente aus dem Diagramm entfernen oder Löschen der Beziehung aus dem Modell löschen.

## <a name="Copying"></a> Copying Elements and Groups of Related Elements
 Sie können Modellelemente und Elementgruppen zusammen mit den Beziehungen zwischen ihnen kopieren und einfügen.

> [!NOTE]
> The **Paste** and **Paste Reference** commands have different effects. **Paste** creates new elements whose properties are like those of the copied elements. **Paste Reference** creates new views of the same elements.

#### <a name="to-copy-elements-and-their-relationships"></a>Kopieren von Elementen und Beziehungen

1. Wählen Sie ein oder mehrere Elemente im Diagramm mit den Elementen, die Sie kopieren möchten.

    > [!NOTE]
    > Sie können Beziehungen nur als Teil einer Gruppe von Elementen kopieren.

2. On the **Edit** menu, click **Copy**.

3. Wenn Sie die Elemente in ein anderes Diagramm kopieren möchten, erstellen Sie das neue Diagramm, oder öffnen Sie das vorhandene Diagramm.

4. On the **Edit** menu, click **Paste**.

    - Kopien der Elemente werden zusammen mit Kopien von Beziehungen zueinander angezeigt.

    - Bei jedem neuen Element wird automatisch ein neuer Name generiert.

5. Passen Sie die Positionen, Namen und andere Eigenschaften der neuen Elemente und Beziehungen an.

> [!NOTE]
> Sie können kein Modellelement aus einem Modell in ein anderes Modell kopieren, z. B. wenn Sie zwei Modelle in der gleichen Projektmappe haben. Sie können jedoch Elemente aus einem Diagramm in ein anderes kopieren.

#### <a name="to-copy-an-entire-diagram"></a>Kopieren eines gesamten Diagramms

1. Erstellen Sie ein neues Diagramm.

2. Wählen Sie alle Elemente in einem vorhandenen Diagramm, kopieren Sie sie, und fügen Sie sie in die neue Zeile ein.

   Sie können ein Diagramm nicht durch Kopieren und Einfügen im Projektmappen-Explorer replizieren.

## <a name="Deleting"></a> Deleting a Model Element or its Views
 Einige Elementarten, insbesondere Klassifizierer, können aus einem Diagramm gelöscht werden, ohne sie aus dem Modell zu löschen. Klassifizierer sind die Hauptelemente, die in Klassendiagrammen, Komponentendiagrammen und Anwendungsfalldiagrammen angezeigt werden. Sie können in mehr als einem Diagramm angezeigt werden. For these types of elements, there are two separate commands: **Remove from Diagram** and **Delete from Model**.

 Im Gegensatz dazu wird beim Löschen einer Beziehung aus einem Diagramm die Beziehung immer auch aus dem Modell gelöscht.

> [!NOTE]
> Bestimmte Arten von Elementen in einem UML-Diagramm besitzen Bezeichnungen. Wenn Sie solche Elemente auswählen, indem Sie ein Rechteck darum zeichnen, können Bezeichnungen ausgewählt werden, jedoch nicht die dazugehörigen Elemente. Das Löschen einer Teilmenge von Elementen, die auf diese Weise ausgewählt werden, wird nicht unterstützt. To select a subset of these elements, press and hold the **CTRL** key while you click each element.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>So entfernen Sie eine Klassifizierungsansicht aus einem Diagramm

- Right-click the element on the diagram, and then click **Remove from Diagram**.

  \- oder -

- Click the element on the diagram and then press the **DELETE** key.

  - Diese Ansicht des Elements wird ausgeblendet. However, the element remains in the model, and you can still find it in **UML Model Explorer**. Andere Ansichten des gleichen Elements werden ebenfalls beibehalten.

  - Jeder Konnektor, der an dieser Form endet, wird aus dem Diagramm entfernt, die Beziehung bleibt jedoch im Modell. You can see the relationship in **UML Model Explorer** under **Relationships**, under each element that it connects.

#### <a name="to-delete-an-element-from-the-model"></a>Löschen eines Elements aus dem Modell

- Right-click the element either in **UML Model Explorer** or on a diagram, and then click **Delete from Model**.

  - Das Element wird aus jedem Diagramm gelöscht, in dem es angezeigt wird.

  - Jede Beziehung, die an diesem Element endet, wird ebenfalls aus dem Modell gelöscht.

#### <a name="to-delete-a-relationship-from-the-model"></a>So löschen Sie eine Beziehung aus dem Modell

- Right-click the relationship on a diagram or in **UML Model Explorer**, and then click **Delete from Model**.

    > [!CAUTION]
    > Sie können keine Beziehung aus einem Diagramm entfernen, ohne sie aus dem Modell entfernen.

     Die Beziehung wird aus dem Modell gelöscht und aus jedem Diagramm, in dem sie angezeigt wird.

## <a name="presentation"></a> Preparing a Diagram for Presentation
 Mithilfe der folgenden Funktionen können Sie bestimmte Teile des Diagramms hervorheben, Erläuterungen hinzufügen oder ein Diagramm in unterschiedliche relevante Bereiche unterteilen.

- Sie können einen beliebigen Teil eines Diagramms in ein Word-, PowerPoint- oder anderes Dokument kopieren. Select the shapes and connectors you want, right-click and then click **Copy**.

- Die Farbe der Formen und Konnectoren kann geändert werden. Select one or more shapes and change the **Color** property. Wenn Sie das Fenster **Eigenschaften** nicht sehen, drücken Sie **F4**.

- On diagrams of some kinds, you can draw lines, rectangles and ellipses from the **Simple Shapes** section of the Toolbox. Diese Formen bilden keinen Teil des UML-Modells.

- To label an area, you can drag a Comment from the Toolbox and then set its **Transparent** property to **True**. Genau wie einfache Formen sind Kommentare kein Bestandteil des UML-Modells und werden nicht im UML-Modell-Explorer angezeigt.

- Um Hinweise und Erläuterungen zu Modellelementen hinzuzufügen, können Sie Kommentare erstellen und diese dann mit den Elementen verknüpfen.

### <a name="to-export-a-diagram-as-an-image"></a>Exportieren eines Diagramms als Bild
 For more information, see [Export diagrams as images](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a> Extending the UML Designers
 Sie können neue Funktionalität zu den UML-Tools hinzufügen und die Diagramm-Notation an Ihre eigenen Anforderungen anpassen. For more information, see [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>Siehe auch
 [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md)
