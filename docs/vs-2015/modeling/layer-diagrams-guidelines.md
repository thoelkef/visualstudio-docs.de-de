---
title: 'Layer Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51cb71d4bc2f66377b677d5be292c4eafa1dbd18
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299467"
---
# <a name="layer-diagrams-guidelines"></a>Ebenendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Describe your app's architecture at a high level by creating *layer diagrams* in Visual Studio. Stellen Sie sicher, dass Code und Entwurf konsistent bleiben, indem Sie den Code mit einem Ebenendiagramm validieren. Sie können auch eine Ebenenvalidierung im Buildprozess einschließen. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>Was ist ein Ebenendiagramm?
 In einem Ebenendiagramm werden wie in einem herkömmlichen Architekturdiagramm die wichtigsten Komponenten oder Funktionseinheiten des Entwurfs sowie ihre Abhängigkeiten identifiziert. Each node on the diagram, called a *layer*, represents a logical group of namespaces, projects, or other artifacts. Sie können die Abhängigkeiten zeichnen, die im Entwurf vorhanden sein sollen. Anders als bei einem herkömmlichen Architekturdiagramm können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Quellcode den gewünschten Abhängigkeiten entsprechen, die Sie angegeben haben. Indem Sie die Validierung zu einem Bestandteil eines regulären Buildvorgangs in [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] machen, stellen Sie sicher, dass der Programmcode auch in zukünftigen Änderungen mit der Architektur des Systems übereinstimmt. See [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).

## <a name="Update"></a> How to design or update your app with layer diagrams
 Die folgenden Schritte bieten einen Überblick über die Verwendung von Ebenendiagrammen im Entwicklungsprozess. In späteren Abschnitten dieses Themas werden die einzelnen Schritte ausführlicher beschrieben. Wenn Sie einen neuen Entwurf entwickeln, lassen Sie die Schritte aus, die sich auf vorhandenen Code beziehen.

> [!NOTE]
> Die Schritte entsprechen ungefähr der tatsächlichen Reihenfolge. Wahrscheinlich werden Sie die Aufgaben überlappend ausführen, die Reihenfolge Ihrer eigenen Situation anpassen und am Anfang jeder Iteration im Projekt nochmals auf die Beschreibung der Schritte zurückkommen.

1. [Create a layer diagram](#Create) for the whole application, or for a layer within it.

2. [Define layers to represent primary functional areas or components](#CreateLayers) of your application. Benennen Sie diese Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". If you have a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution, you can associate each layer with a collection of *artifacts*, such as projects, namespaces, files, and so on.

3. [Discover the existing dependencies](#Generate) between layers.

4. [Edit the layers and dependencies](#EditArchitecture) to show the updated design that you want the code to reflect.

5. [Design new areas of your application](#NewAreas) by creating layers to represent the principal architectural blocks or components and defining dependencies to show how each layer uses the others.

6. [Edit the layout and appearance of the diagram](#EditLayout) to help you discuss it with colleagues.

7. [Validate the code against the layer diagram](#Validate) to highlight the conflicts between the code and the architecture you require.

8. [Update the code to conform to your new architecture](#UpdateCode). Führen Sie die Entwicklung und Umgestaltung von Code in Iterationen durch, bis bei der Validierung keine Konflikte auftreten.

9. [Include layer validation in the build process](#BuildValidation) to ensure that the code continues to adhere to your design.

## <a name="Create"></a> Create a layer diagram
 Ein Ebenendiagramm muss in einem Modellierungsprojekt erstellt werden. Sie können einem vorhandenen Modellierungsprojekt ein neues Ebenendiagramm hinzufügen, ein Modellierungsprojekt für das neue Ebenendiagramm erstellen oder ein vorhandenes Ebenendiagramm innerhalb des gleichen Modellierungsprojekts kopieren.

> [!IMPORTANT]
> Fügen Sie Modellierungsprojekten oder anderen Speicherorten in der Projektmappe keine vorhandenen Ebenendiagramme aus Modellierungsprojekten hinzu, und kopieren bzw. verschieben Sie diese nicht. Ein Ebenendiagramm, das auf diese Weise kopiert wird, weist die gleichen Verweise wie das ursprüngliche Diagramm auf, auch wenn Sie das Diagramm ändern. Dies verhindert das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.

 See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Define layers to represent functional areas or components
 Layers represent logical groups of *artifacts*, such as projects, code files, namespaces, classes, and methods. Sie können Ebenen aus Artefakten aus Visual C# .NET- und Visual Basic .NET-Projekten erstellen, oder Sie können Spezifikationen oder Pläne an eine Ebene anfügen, indem Sie Dokumente verknüpfen, z. B. Word-Dateien oder PowerPoint-Präsentationen. Jede Ebene wird im Diagramm als Rechteck angezeigt und gibt Aufschluss über die Anzahl der mit ihr verknüpften Artefakte. Eine Ebene kann geschachtelte Ebenen enthalten, um spezielle Aufgaben zu beschreiben.

 Benennen Sie als allgemeine Richtlinie Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Fügen Sie Artefakte in der gleichen Ebene ein, wenn zwischen ihnen eine enge Abhängigkeit besteht. Wenn die Artefakte getrennt voneinander aktualisiert oder in separaten Anwendungen verwendet werden können, sollten sie auf unterschiedlichen Ebenen eingefügt werden. To learn about layering patterns, visit the Patterns & Practices site at [http://go.microsoft.com/fwlink/?LinkId=145794](https://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Bestimmte Arten von Artefakten können mit Ebenen verknüpft, aber nicht anhand des Ebenendiagramms überprüft werden. To see whether the artifact supports validation, open **Layer Explorer** to examine the **Supports Validation** property of the artifact link. See [Discover existing dependencies between layers](#Generate).

 Bei der Aktualisierung einer nicht vertrauten Anwendung können Sie auch Codezuordnungen erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe des Projektmappen-Explorers können Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weisen Sie diese Codeartefakte Ebenen zu, indem Sie sie aus dem Projektmappen-Explorer in Ebenendiagramme ziehen. Sie können dann Ebenendiagramme verwenden, um den Code zu aktualisieren und ihn mit dem Entwurf konsistent zu halten.

 Thema

- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Discover existing dependencies between layers
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Vorhandene Abhängigkeiten können mittels Reverse Engineering (Zurückentwicklung) ermittelt werden.

> [!NOTE]
> Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. To see which artifacts have dependencies that you can reverse-engineer, right-click one or multiple layers, and then click **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>So entwickeln Sie vorhandene Abhängigkeiten zwischen Ebenen zurück

- Select one layer or multiple layers, right-click a selected layer, and then click **Generate Dependencies**.

  In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.

## <a name="EditArchitecture"></a> Edit layers and dependencies to show the intended design
 Um die die geplanten Änderungen an Ihrem System oder der vorgesehenen Architektur zu beschreiben, verwenden Sie die folgenden Schritte zum Bearbeiten des Ebenendiagramms. Sie können vor dem Erweitern des Codes ggf. auch einige Refactoringänderungen vornehmen, um die Codestruktur zu verbessern. See [Improving the structure of the code](#Improving).

|**Aktion**|**Perform these steps**|
|------------|-----------------------------|
|Löschen einer unerwünschten Abhängigkeit|Click the dependency, and then press **DELETE**.|
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Set its **Direction** property.|
|Erstellen von neuen Abhängigkeiten|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. When you are finished, click the **Pointer** tool or press the **ESC** key.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

### <a name="Improving"></a> Improving the structure of the code
 Umgestaltungsänderungen sind Verbesserungen, die das Verhalten der Anwendung nicht ändern, jedoch zukünftige Änderungen und Erweiterungen des Codes erleichtern. Der Entwurf von gut strukturiertem Code lässt sich leicht in einem Ebenendiagramm abstrakt darstellen.

 Wenn Sie z. B. eine Ebene für jeden Namespace im Code erstellen und die Abhängigkeiten dann zurück entwickeln, sollte die Anzahl unidirektionaler Abhängigkeiten zwischen den Ebenen minimal sein. Wenn Sie ein detailliertes Diagramm mit Klassen oder Methoden als Ebenen zeichnen, sollte das Ergebnis dieselben Merkmale aufweisen.

 Falls dies nicht der Fall ist, sind Änderungen des Codes während seiner Lebensdauer schwieriger, und er eignet sich weniger für die Validierung mithilfe von Ebenendiagrammen.

## <a name="NewAreas"></a> Design new areas of your application
 Wenn Sie mit der Entwicklung eines neuen Projekts oder eines neuen Bereichs in einem neuen Projekt beginnen, können Sie Ebenen und Abhängigkeiten zeichnen, um die Hauptkomponenten zu identifizieren, bevor Sie mit dem Entwickeln des Codes beginnen.

- **Show identifiable architectural patterns** in your layer diagrams, if possible. Beispielsweise kann ein Ebenendiagramm, das eine Desktopanwendung beschreibt, die Ebenen Präsentation, Domänenlogik und Datenspeicher enthalten. Ein Ebenendiagramm für eine einzelne Funktion in einer Anwendung kann beispielsweise die Ebenen Modell, Ansicht und Controller enthalten. For more information about such patterns, see [Patterns & Practices: Application Architecture](https://go.microsoft.com/fwlink/?LinkId=145794).

     Wenn Sie häufig ähnliche Muster entwerfen, erstellen Sie ein benutzerdefiniertes Tool. See [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Create a code artifact for each layer** such as a namespace, class, or component. Dies vereinfacht das Verfolgen des Codes und das Verknüpfen der Codeartefakte mit den Ebenen. Verknüpfen Sie jedes Artefakt mit der entsprechenden Ebene, sobald Sie das Artefakt erstellen.

- **You do not have to link most classes and other artifacts to layers** because they fall within larger artifacts such as namespaces that you have already linked to layers.

- **Create a new diagram for a new feature**. In der Regel sind ein oder mehrere Ebenendiagramme vorhanden, die die gesamte Anwendung beschreiben. Wenn Sie eine neue Funktion in der Anwendung entwerfen, ändern Sie nicht die vorhandenen Diagramme, und fügen Sie ihnen keine Elemente hinzu. Erstellen Sie stattdessen ein eigenes Diagramm, das die neuen Teile des Codes wiedergibt. Das neue Diagramm kann beispielsweise Ebenen für die Präsentation, Domänenlogik und Datenbank der neuen Funktion enthalten.

     Wenn Sie die Anwendung erstellen, wird der Code sowohl anhand des allgemeinen Diagramms als auch anhand des ausführlicheren Funktionsdiagramms überprüft.

## <a name="EditLayout"></a> Edit the layout for presentation and discussion
 Bearbeiten Sie Darstellung und Layout des Diagramms, um die Suche nach Ebenen und Abhängigkeiten sowie Diskussionen mit Teammitgliedern zu vereinfachen. Führen Sie hierzu die folgenden Schritte aus:

- Ändern der Größe, Formen und Positionen von Ebenen

- Ändern der Farben von Ebenen und Abhängigkeiten

  - Select one or more layers or dependencies, right-click, and then click **Properties**. In the **Properties** window, edit the **Color** property.

## <a name="Validate"></a> Validate the code against the diagram
 Wenn Sie das Diagramm bearbeitet haben, können Sie es jederzeit manuell oder automatisch beim Ausführen eines lokalen Builds oder von [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] anhand des Codes überprüfen.

 Thema

- [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)

- [Include Layer Validation in the Build Process](#BuildValidation)

## <a name="UpdateCode"></a> Update the code to conform to the new architecture
 Normalerweise treten Fehler auf, wenn Sie den Code zum ersten Mal anhand eines aktualisierten Ebenendiagramms überprüfen. Diese Fehler können mehrere Ursachen haben:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

  Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Dies ist normalerweise ein iterativer Vorgang. For more information about these errors, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Beim Entwickeln oder Umgestalten des Codes müssen Sie möglicherweise neue Artefakte mit dem Ebenendiagramm verknüpfen. Dies ist jedoch möglicherweise nicht erforderlich, wenn Ebenen z. B. vorhandene Namespaces darstellen und diesen Namespaces mit dem neuen Code lediglich weitere Elemente hinzugefügt werden.

 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../includes/esprfound-md.md)] eine Arbeitsaufgabe zu protokollieren. To perform this task, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Include layer validation in the build process
 Schließen Sie Ebenenvalidierung in den standardmäßigen Buildprozess der Projektmappe ein, um sicherzustellen, dass zukünftige Änderungen im Code den Ebenendiagrammen entsprechen. Jedes Mal, wenn andere Teammitglieder die Projektmappe erstellen, werden Unterschiede zwischen den Abhängigkeiten im Code und dem Ebenendiagramm als Buildfehler gemeldet. For more information about including layer validation in the build process, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Siehe auch
 [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)
