---
title: Create layer diagrams from your code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e6cd77e785adb59fc8b2cf3b28724ed0efe1ae3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300275"
---
# <a name="create-layer-diagrams-from-your-code"></a>Erstellen von Ebenendiagrammen aus Ihrem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To visualize your software system's high-level, logical architecture, create a *layer diagram* in Visual Studio. Um sicherzustellen, dass Code und Entwurf konsistent bleiben, validieren Sie den Code mit einem Ebenendiagramm. Sie können Ebenendiagramme für Visual C# .NET- und Visual Basic. NET-Projekte erstellen. To see which versions of Visual Studio support this feature, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Create a layer diagram](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 A layer diagram lets you organize Visual Studio solution items into logical, abstract groups called *layers*. Sie können die Ebenen zum Beschreiben der Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder zum Beschreiben der Hauptkomponenten des Systems verwenden. Jede Ebene kann andere Ebenen enthalten, die ausführlichere Aufgaben beschreiben. You can also specify the intended or existing *dependencies* between layers. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Geben Sie die beabsichtigten Abhängigkeiten im Diagramm an, um die Architektursteuerung für den Code beizubehalten, und überprüfen Sie anschließend den Code anhand des Diagramms.

## <a name="CreateDiagram"></a> Create a layer diagram
 Bevor Sie ein Ebenendiagramm erstellen, vergewissern Sie sich, dass die Projektmappe ein Modellierungsprojekt enthält. See [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Fügen Sie anderen Modellierungsprojekten oder anderen Speicherorten in der Projektmappe keine vorhandenen Ebenendiagramme aus Modellierungsprojekten hinzu, und kopieren bzw. verschieben Sie diese nicht. Dadurch werden die Verweise des ursprünglichen Diagramms beibehalten, auch wenn Sie das Diagramm ändern. Dies verhindert auch das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.
>
> Fügen Sie stattdessen dem Modellierungsprojekt ein neues Ebenendiagramm hinzu. Kopieren Sie die Elemente aus dem Quelldiagramm in das neue Diagramm. Speichern Sie das Modellierungsprojekt und das neue Ebenendiagramm.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>So fügen Sie einem Modellierungsprojekt ein neues Ebenendiagramm hinzu

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **Layer Diagram**.

3. Benennen Sie das Diagramm.

4. In **Add to Modeling Project**, browse to and select an existing modeling project in your solution.

     - oder -

     Choose **Create a new modeling project** to add a new modeling project to the solution.

    > [!NOTE]
    > Das Ebenendiagramm muss in einem Modellierungsprojekt vorhanden sein. Sie können es allerdings mit Elementen an einer beliebigen Stelle in der Projektmappe verknüpfen.

5. Vergewissern Sie sich, dass Sie das Modellierungsprojekt und das Ebenendiagramm gespeichert haben.

## <a name="CreateLayers"></a> Create layers from artifacts
 Ebenen können aus Visual Studio-Projektmappenelementen erstellt werden, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Dabei werden Verknüpfungen zwischen den Ebenen und den Elementen automatisch erstellt und im Ebenenvalidierungsprozess berücksichtigt.

 Sie können Ebenen auch mit den Elementen verknüpfen, die die Validierung nicht unterstützen, wie Word-Dokumente oder PowerPoint-Präsentationen, sodass Sie eine Ebene Spezifikationen oder Plänen zuordnen können. Außerdem können Sie Ebenen mit Dateien in Projekten verknüpfen, die für mehrere Apps freigegeben sind. Im Validierungsprozess werden diese Ebenen, die mit generischen Namen wie "Layer 1" und "Layer 2" angezeigt werden, jedoch nicht berücksichtigt.

 To see if a linked item supports validation, open **Layer Explorer** and examine the **Supports Validation** property of the item. See [Managing links to artifacts](#Managing).

|**Aktion**|**Follow these steps**|
|------------|----------------------------|
|Erstellen einer Ebene für ein einzelnes Artefakt|<ol><li>Ziehen Sie das Element aus diesen Quellen in das Ebenendiagramm:<br /><br /> <ul><li>**Projektmappen-Explorer**<br /><br />         Beispiele: Dateien oder Projekte.</li><li>Codezuordnungen<br /><br />         See [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) and [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Class View** or **Object Browser**</li></ul><br />     Im Diagramm wird eine Ebene angezeigt und mit dem Artefakt verknüpft.</li><li>Ändern Sie den Namen der Ebene, um die Aufgaben des zugeordneten Codes oder der Artefakte widerzuspiegeln.</li></ol> **Important:**  Dragging binary files to the layer diagram does not automatically add their references to modeling project. Sie müssen die Binärdateien manuell hinzufügen, die Sie für das Modellierungsprojekt überprüfen möchten. **To add binary files to the modeling project** <ol><li>In **Solution Explorer**, open the shortcut menu for the modeling project, and then choose **Add Existing Item**.</li><li>In the **Add Existing Item** dialog box, browse to the binary files, select them, and then choose **OK**.     Die Binärdateien werden im Modellierungsprojekt angezeigt.</li><li>In **Solution Explorer**, choose a binary file that you added, and then press **F4** to open the **Properties** window.</li><li>On each binary file, set the **Build Action** property to **Validate**.</li></ol>|
|Erstellen einer einzelnen Ebene für alle ausgewählten Artefakte|Ziehen Sie alle Artefakte gleichzeitig in das Ebenendiagramm.<br /><br /> Im Diagramm wird eine Ebene angezeigt und mit allen Artefakten verknüpft.|
|Erstellen einer Ebene für jedes ausgewählte Artefakt|Press and hold the **SHIFT** key while you drag all of the artifacts to the layer diagram at the same time. **Note:**  If you use the **SHIFT** key to select a range of items, release the key after you select the artifacts. Halten Sie sie anschließend erneut gedrückt, wenn Sie die Artefakte in das Diagramm ziehen. <br /><br /> Im Diagramm wird für jedes Artefakt eine Ebene angezeigt und mit den einzelnen Artefakten verknüpft.|
|Hinzufügen eines Artefakts zu einer Ebene|Ziehen Sie das Artefakt auf die Ebene.|
|Erstellen einer neuen, nicht verknüpften Ebene|In the **Toolbox**, expand the **Layer Diagram** section, and then drag a **Layer** to the layer diagram.<br /><br /> Doppelklicken Sie zum Erstellen mehrerer Ebenen auf das Tool. When you are finished, choose the **Pointer** tool or press the **ESC** key.<br /><br /> - oder -<br /><br /> Open the shortcut menu for the layer diagram, choose **Add**, and then choose **Layer**.|
|Erstellen geschachtelter Ebenen|Ziehen Sie eine vorhandene Ebene auf eine andere Ebene.<br /><br /> - oder -<br /><br /> Open the shortcut menu for a layer, choose **Add**, and then choose **Layer**.|
|Erstellen einer neuen Ebene, die mehrere vorhandene Ebenen enthält|Select the layers, open the shortcut menu for your selection, and then choose **Group**.|
|Ändern der Farbe einer Ebene|Set its **Color** property to the color that you want.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

 Die Zahl auf einer Ebene gibt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch Folgendes, wenn Sie diese Zahl lesen:

- Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

- Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

## <a name="Managing"></a> Manage links between layers and artifacts

1. On the layer diagram, open the shortcut menu for the layer, and then choose **View Links**.

     **Layer Explorer** shows the artifact links for the selected layer.

2. Verwenden Sie zum Verwalten dieser Links die folgenden Aufgaben:

|**Aktion**|**In Layer Explorer**|
|------------|---------------------------|
|Löschen des Links zwischen der Ebene und einem Artefakt|Open the shortcut menu for the artifact link, and then choose **Delete**.|
|Verschieben des Links von einer Ebene auf eine andere Ebene|Ziehen Sie den Artefaktlink auf eine Ebene im Diagramm.<br /><br /> - oder -<br /><br /> 1.  Open the shortcut menu for the artifact link, and then choose **Cut**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|Kopieren des Links von einer Ebene auf eine andere Ebene|1.  Open the shortcut menu for the artifact link, and then choose **Copy**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|Erstellen einer neuen Ebene aus einem vorhandenen Artefaktlink|Ziehen Sie den Artefaktlink in einen leeren Bereich des Diagramms.|
|Überprüfen, ob ein verknüpftes Artefakt die Validierung anhand des Ebenendiagramms unterstützt|Look at the **Supports Validation** column for the artifact link.|

## <a name="Discovering"></a> Reverse-engineer existing dependencies
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Bei vorhandenen Abhängigkeiten von Artefakten, die mit Ebenen des Diagramms verknüpft sind, ist eine Rückentwicklung möglich.

> [!NOTE]
> Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. To see which artifacts have dependencies that you can reverse-engineer, open the shortcut menu for one or multiple layers, and then choose **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

- Select one or multiple layers, open the shortcut menu for a selected layer, and then choose **Generate Dependencies**.

  In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.

## <a name="EditDependencies"></a> Edit layers and dependencies to show the intended design
 Um die geplanten Änderungen an Ihrem System oder der vorgesehenen Architektur zu beschreiben, bearbeiten Sie das Ebenendiagramm:

|**Aktion**|**Perform these steps**|
|------------|-----------------------------|
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Set its **Direction** property.|
|Erstellen von neuen Abhängigkeiten|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. When you are finished, choose the **Pointer** tool or press the **ESC** key.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

## <a name="EditLayout"></a> Change how elements appear on the diagram
 Sie können die Größe, Form, Farbe und Position von Ebenen oder die Farbe von Abhängigkeiten ändern, indem Sie ihre Eigenschaften bearbeiten.

## <a name="Codemaps"></a> Discover patterns and dependencies on a code map
 While creating layer diagrams, you might also create **code maps**. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe von Projektmappen-Explorer, Klassenansicht oder Objektkatalog können Assemblys, Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weitere Informationen zu Codezuordnungen finden Sie unter den folgenden Themen:

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Siehe auch
 [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073) [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md) [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md) [Visualize code](../modeling/visualize-code.md)