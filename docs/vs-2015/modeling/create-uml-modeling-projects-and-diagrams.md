---
title: Create UML modeling projects and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5884dcd3f9e3cb8f1910d2e23ec80f910ed2fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301010"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Erstellen von UML-Modellierungsprojekten und -diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML-Modelle helfen Ihnen, Softwaresysteme zu verstehen, zu besprechen und zu entwerfen. Visual Studio stellt Vorlagen für fünf der am häufigsten verwendeten UML-Diagramme bereit: Aktivität, Klasse, Komponente, Sequenz und Anwendungsfall. Darüber hinaus können Sie Ebenendiagramme erstellen, mit deren Hilfe Sie die Struktur des Systems definieren.

 UML-Modellierungsdiagramme und Ebenendiagramme können nur in einem Modellierungsprojekt vorhanden sein. Jedes Modellierungsprojekt enthält ein freigegebenes UML-Modell und mehrere UML-Diagramme. Jedes Diagramm ist eine Teilansicht des Modells. Das UML-Modell enthält alle Elemente der UML-Diagramme und kann mit dem UML-Modell-Explorer angezeigt werden. For information about models and their relationship to diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md). For information about modeling projects under version control, see [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md) and [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Es gibt eine andere Art von Diagramm, das .NET Klassendiagramm, das verwendet wird, um Programmcode visuell darzustellen. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a> Create a Diagram in a Modeling Project
 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>So erstellen Sie ein Diagramm und fügen es zu einem Projekt hinzu

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. In the **Add New Diagram** dialog box, click the type of modeling diagram that you want.

    ![Add New Diagram dialog](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Geben Sie einen Namen für das neue Diagramm ein.

4. In the **Add to modeling project** box:

   - Select a modeling project that already exists in your solution, and then click **OK**.

     \- oder -

   1. Select **Create a new modeling project**, and then click **OK**.

   2. In the **Create New Modeling Project** dialog box, type a name and location for the new project, and then click **OK**.

        ![Create New Modeling Project dialog](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Wenn die Projektmappe geöffnet ist, wird das neue Projekt hinzugefügt. Wenn Sie keine Projektmappe geöffnet haben, können Sie einen Namen für eine neue Projektmappe eingeben.

   Wenn Sie bereits ein Modellierungsprojekt haben, können Sie auch das folgende Verfahren einsetzen.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Einem vorhandenen Modellierungsprojekt ein Diagramm hinzufügen

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. In the **Add New Item -** *\<project name>* dialog box, under **Templates**, click the modeling diagram type, for example, **UML Component Diagram**.

4. Type a name for the diagram, and then click **Add**.

     Das Modellierungsdiagramm wird geöffnet und im Modellierungsprojekt angezeigt.

    > [!CAUTION]
    > Vorhandene Diagrammdateien dürfen nicht hinzugefügt, kopiert oder zu anderen Modellierungsprojekten oder anderen Speicherorten in der Projektmappe gezogen werden. Dies bewirkt, dass Elemente aus den kopierten Diagrammen ausgeblendet werden oder Fehler auftreten, wenn Sie die Diagramme öffnen. Die Diagrammdatei muss im Modellierungsprojekt geöffnet werden, in dem es erstellt wurde. Ein UML-Diagramm ist eine Ansicht des Modells, das zum zum zugehörigen Modellierungsprojekt gehört. Um eine Diagrammdatei zu kopieren, erstellen Sie ein neues Diagramm, und kopieren Sie die Elemente des Quelldiagramms in das neue Diagramm. For more information, see [Troubleshooting Modeling Projects and Diagrams](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>So erstellen Sie ein leeres Modellierungsprojekt

1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

2. In the **New Project** dialog box, under **Installed Templates**, click **Modeling Projects**.

3. In the middle window, click **Modeling Project**.

4. Name the project and specify a location in the **Name** and **Location** boxes.

5. In the **Solution** box, select **Add to Solution** to add the new project to a solution you already have open; or **Create new Solution** to close any open solution and add the project to a new solution.

## <a name="RemovingModelingDiagrams"></a> Removing Modeling Diagrams from a Project
 Sie können ein Diagramm dauerhaft löschen, oder Sie können vorübergehend ein Diagramm aus einem Projekt ausschließen und dann wiederherstellen.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Dauerhaftes Löschen ein Diagramms aus einem Projekt

- In **Solution Explorer**, right-click the main file that represents the diagram, and then click **Delete**.

     Das Diagramm wird aus dem Projekt und dem Dateisystem entfernt. The elements shown on the diagram are not removed from **UML Model Explorer**.

    > [!NOTE]
    > Jedes Diagramm weist zwei Dateien auf, von denen eine der anderen untergeordnet ist. Wenn Sie z. B. ein Komponentendiagramm mit dem Namen `CD1` haben, sollten Sie die Datei mit dem Namen `CD1.componentdiagram` löschen. Die untergeordnete Datei mit dem Namen `CD1.componentdiagram.layout` wird automatisch gelöscht.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Vorübergehendes Ausschließen eines Diagramms aus einem Projekt

- In **Solution Explorer**, right-click the diagram file, and then click **Exclude from Project**.

     Das Diagramm wird aus dem Projekt entfernt. Es wird nicht aus dem Dateisystem entfernt.

    > [!NOTE]
    > The elements shown on the diagram are not removed from **UML Model Explorer**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Ein vorübergehend ausgeschlossenes Diagramm in einem Projekt wiederherstellen

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. On the **Project** menu, click **Add Existing Item**.

3. In the **Add Existing Item** dialog box, locate the diagram file, select the file, and then click **Add**.

     Das Modellierungsdiagramm wird geöffnet und im Modellierungsprojekt angezeigt.

    > [!NOTE]
    > Jedes Diagramm verfügt über ein Paar von Dateien im Dateisystem. Wählen Sie keine Datei mit der Erweiterung `.layout`. Darüber hinaus bietet Visual Studio keine Unterstützung für das Hinzufügen vorhandener UML-Diagramme zu mehreren Modellierungsprojekten. Jede Diagrammdatei muss im Modellierungsprojekt geöffnet werden, in dem sie erstellt wurde. Ein UML-Diagramm ist eine Ansicht eines Modells, das zum zum zugehörigen Modellierungsprojekt gehört.

## <a name="NonModelDiagrams"></a> Diagrams that Do Not Require Modeling Projects
 Die folgenden Arten von Diagrammen sind nicht Teil eines Modellierungsprojekts:

- Klassendiagramme, die als Ansichten des Quellcodes erstellt werden. Diese beziehen sich nicht auf UML-Klassendiagramme. For more information, see [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md).

- Code Maps. Siehe [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Diagramme, die keine UML-Diagramme oder Ebenendiagramme sind, z. B. domänenspezifische Sprachen.

## <a name="TroubleshootingModelingProjects"></a> Troubleshooting Modeling Projects and Diagrams
 In der folgende Tabelle werden Probleme, die mit Modellierungsprojekten oder Diagrammen und deren Behebung auftreten können, beschrieben:

|**Problem**|**Causes**|**Auflösung**|
|---------------|----------------|--------------------|
|Das Modellierungsprojekt kann nicht geöffnet oder in der Projektmappe geladen werden.<br /><br /> Folgende Meldung wird angezeigt:<br /><br /> "Ein oder mehrere Projekte in der Projektmappe wurden nicht ordnungsgemäß geladen. Details finden Sie im Ausgabefenster."<br /><br /> Im Ausgabefenster wird die folgende Meldung angezeigt:<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: error: Unrecognized Guid format."|Ein Modellierungsprojekt enthält Verweise auf Projekte, die den gleichen Namen haben und in der gleichen Projektmappe vorkommen.<br /><br /> Beispielsweise ist eine Ebene mit Projekten verknüpft, die den gleichen Namen haben und in der gleichen Projektmappe vorhanden sind.|Verwenden Sie einen Text-Editor, öffnen Sie die Datei, entfernen Sie die Verweise, und versuchen Sie erneut, das Modellierungsprojekt zu öffnen.<br /><br /> Um dieses Problem zu vermeiden, fügen Sie keine Verweise auf Projekte hinzu, die den gleichen Namen haben. Stellen Sie sicher, dass Projekte über eindeutige Namen verfügen.|
|Es fehlen Elemente aus Diagrammen, die hinzugefügt, kopiert oder zu anderen Modellierungsprojekten oder anderen Speicherorten in der Projektmappe gezogen werden.<br /><br /> - oder -<br /><br /> Wenn Sie versuchen, ein Diagramm zu öffnen, werden die folgenden Meldungen angezeigt:<br /><br /> -   "Some shapes or connectors on the diagram are missing because their definitions do not exist in this project. Entweder die Definitionen wurden aus dem Modell gelöscht, während das Diagramm geschlossen war, oder das Diagramm wurde in ein anderes Projekt kopiert, das diese Definitionen nicht enthält."<br /><br /> - oder -<br /><br /> -   "This document is opened by another project."|Die Diagrammdatei wurde hinzugefügt, gezogen oder aus einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an einen anderen Speicherort in der Projektmappe kopiert.|Um eine Diagrammdatei zu kopieren, erstellen Sie ein neues Diagramm, und kopieren Sie die Elemente des Quelldiagramms in das neue Diagramm.|

## <a name="see-also"></a>Siehe auch
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)
