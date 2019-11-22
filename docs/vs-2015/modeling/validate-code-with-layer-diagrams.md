---
title: Validate code with layer diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 596711c5c59738d5356437bb761e80caeddfbd6b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301359"
---
# <a name="validate-code-with-layer-diagrams"></a>Überprüfen von Code mit Ebenendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um sicherzustellen, dass der Code dem Entwurf nicht widerspricht, können Sie Ihren Code in Visual Studio mit Ebenendiagrammen überprüfen. Dadurch wird Folgendes ermöglicht:

- Suchen von Konflikten zwischen Abhängigkeiten im Code und Abhängigkeiten im Ebenendiagramm

- Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind

   Sie können z. B. das Ebenendiagramm bearbeiten, um potenzielle Architekturänderungen darzustellen, und dann den Code überprüfen, um die betroffenen Abhängigkeiten zu ermitteln.

- Umgestalten oder Migrieren von Code in einen anderen Entwurf

   Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen

  **Voraussetzungen**

- Visual Studio

- Visual Studio auf dem Team Foundation Build-Server, um Code mit Team Foundation Build automatisch zu überprüfen

- Eine Projektmappe, die über ein Modellierungsprojekt mit einem Ebenendiagramm verfügt. Dieses Ebenendiagramm muss mit Artefakten in Visual C# .NET- oder Visual Basic .NET-Projekten verknüpft sein, die Sie überprüfen möchten. See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

  Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Sie können Code über ein geöffnetes Ebenendiagramm in Visual Studio oder eine Eingabeaufforderung manuell überprüfen. Sie können Code beim Ausführen von lokalen Builds oder Team Foundation Build auch automatisch überprüfen. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Wenn Sie die Ebenenvalidierung mit Team Foundation Build ausführen möchten, muss auch Visual Studio auf dem Buildserver installiert werden.

- [See if an item supports validation](#SupportsValidation)

- [Include other .NET assemblies and projects for validation](#IncludeReferences)

- [Validate code manually](#ValidateManually)

- [Validate code automatically](#ValidateAuto)

- [Troubleshoot layer validation issues](#TroubleshootingValidation)

- [Understand and resolve layer validation errors](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a> See if an item supports validation
 Sie können Ebenen mit Websites, Office-Dokumenten, Nur-Text-Dateien und Dateien in Projekten verknüpfen, die von mehreren Apps gemeinsam verwendet werden, jedoch nicht im Validierungsprozess enthalten sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Validierungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.

1. On the layer diagram, select one or more layers, right-click your selection, and then click **View Links**.

2. In **Layer Explorer**, look at the **Supports Validation** column. Wenn der Wert "false" ist, wird die Überprüfung vom Element nicht unterstützt.

## <a name="IncludeReferences"></a> Include other .NET assemblies and projects for validation
 When you drag items to the layer diagram, references to the corresponding .NET assemblies or projects are added automatically to the **Layer References** folder in the modeling project. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können weitere .NET-Assemblys und -Projekte zur Überprüfung hinzufügen, ohne diese manuell in das Ebenendiagramm zu ziehen.

1. In **Solution Explorer**, right-click the modeling project or the **Layer References** folder, and then click **Add Reference**.

2. In the **Add Reference** dialog box, select the assemblies or projects, and then click **OK**.

## <a name="ValidateManually"></a> Validate code manually
 If you have an open layer diagram that is linked to solution items, you can run the **Validate** shortcut command from the diagram. You can also use the command prompt to run the **msbuild** command with the **/p:ValidateArchitecture** custom property set to **True**. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>So überprüfen Sie Code in einem geöffneten Ebenendiagramm

1. Right-click the diagram surface, and then click **Validate Architecture**.

    > [!NOTE]
    > By default, the **Build Action** property on the layer diagram (.layerdiagram) file is set to **Validate** so that the diagram is included in the validation process.

     The **Error List** window reports any errors that occur. For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

2. To view the source of each error, double-click the error in the **Error List** window.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zeigt möglicherweise anstelle der Quelle des Fehlers eine Code Map an. Dies ist der Fall, wenn der Code eine Abhängigkeit von einer Assembly enthält, die nicht im Ebenendiagramm angegeben ist, oder wenn im Code eine im Ebenendiagramm angegebene Abhängigkeit fehlt. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. For more information about code maps, see [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

3. To manage errors, see [Manage validation errors](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>So überprüfen Sie Code an der Eingabeaufforderung

1. Öffnen Sie die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Eingabeaufforderung.

2. Wählen Sie eine der folgenden Optionen aus:

   - Wenn Sie Code anhand eines bestimmten Modellierungsprojekts in der Projektmappe überprüfen möchten, führen Sie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] mit der folgenden benutzerdefinierten Eigenschaft aus.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - ODER

       Navigieren Sie zum Ordner mit der Modellierungsprojektdatei (.modelproj) und dem Ebenendiagramm, und führen Sie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dann mit der folgenden benutzerdefinierten Eigenschaft aus:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Wenn Sie Code anhand aller Modellierungsprojekte in der Projektmappe überprüfen möchten, führen Sie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] mit der folgenden benutzerdefinierten Eigenschaft aus:

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - ODER

       Navigieren Sie zu einem Projektmappenordner, der ein Modellierungsprojekt mit einem Ebenendiagramm enthält, und führen Sie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dann mit der folgenden benutzerdefinierten Eigenschaft aus:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Alle aufgetretenen Fehler werden aufgelistet. For more information about [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], see [MSBuild](../msbuild/msbuild.md) and [MSBuild Task](../msbuild/msbuild-task.md).

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a> Manage validation errors
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../includes/esprfound-md.md)] eine Arbeitsaufgabe zu protokollieren.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>So erstellen Sie eine Arbeitsaufgabe für einen Validierungsfehler

- In the **Error List** window, right-click the error, point to **Create Work Item**, and then click the type of work item that you want to create.

  Use these tasks to manage validation errors in the **Error List** window:

|**Aktion**|**Follow these steps**|
|------------|----------------------------|
|Unterdrücken von ausgewählten Fehlern während der Validierung|Right-click the one or multiple selected errors, point to **Manage Validation Errors**, and then click **Suppress Errors**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückte Fehler werden in einer SUPPRESSIONS-Datei für die entsprechende Ebenendiagrammdatei nachverfolgt.|
|Beenden der Unterdrückung von ausgewählten Fehlern|Right-click the selected suppressed error or errors, point to **Manage Validation Errors**, and then click **Stop Suppressing Errors**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|
|Restore all suppressed errors in the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Show All Suppressed Errors**.|
|Hide all suppressed errors from the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Hide All Suppressed Errors**.|

## <a name="ValidateAuto"></a> Validate code automatically
 Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Team Foundation Build von Ihrem Team verwendet wird, können Sie eine Ebenenvalidierung mit abgegrenzten Eincheckvorgängen durchführen, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe erstellen und Überprüfungsfehler mithilfe von Buildberichten sammeln. To create gated check-in builds, see [Use a gated check-in build process to validate changes](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds

- Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- oder -

1. In **Solution Explorer**, right-click the modeling project that contains the layer diagram or diagrams, and then click **Properties**.

2. In the **Properties** window, set the modeling project's **Validate Architecture** property to **True**.

    Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.

3. In **Solution Explorer**, click the layer diagram (.layerdiagram) file that you want to use for validation.

4. In the **Properties** window, make sure that the diagram's **Build Action** property is set to **Validate**.

    Dadurch wird das Ebenendiagramm in den Validierungsprozess eingeschlossen.

   To manage errors in the Error List window, see [Manage Validation Errors](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>So überprüfen Sie Code automatisch für einen Team Foundation Build

1. In **Team Explorer**, double-click the build definition, and then click **Process**.

2. Under **Build process parameters**, expand **Compilation**, and type the following in the **MSBuild Arguments** parameter:

    `/p:ValidateArchitecture=true`

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors). Weitere Informationen über [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] finden Sie hier:

- [Erstellen der Anwendung](/azure/devops/pipelines/index)

- [Use the Default Template for your build process](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modify a Legacy Build that is Based on UpgradeTemplate.xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Anpassen der Buildprozessvorlage](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitor Progress of a Running Build](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a> Troubleshoot layer validation issues
 In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. For more information about these errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

|**Problem**|**Possible Cause**|**Auflösung**|
|---------------|------------------------|--------------------|
|Validierungsfehler treten nicht wie erwartet auf.|Die Validierung funktioniert nicht mit Ebenendiagrammen, die aus anderen Ebenendiagrammen im Projektmappen-Explorer kopiert wurden und sich im gleichen Modellierungsprojekt befinden. Ebenendiagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Ebenendiagramm.|Fügen Sie dem Modellierungsprojekt ein neues Ebenendiagramm hinzu.<br /><br /> Kopieren Sie die Elemente aus dem Quellebenendiagramm in das neue Diagramm.|

## <a name="UnderstandingValidationErrors"></a> Understanding and Resolving Layer Validation Errors
 Beim Überprüfen von Code anhand eines Ebenendiagramms treten Überprüfungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

  Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.

  Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.

|**Syntax**|**Beschreibung**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* is an artifact that is associated with a layer on the layer diagram.<br /><br /> *ArtifactTypeN* is the type of *ArtifactN*, such as a **Class** or **Method**, for example:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Der Name eines Namespace.|
|*LayerNameN*|Der Name einer Ebene im Ebenendiagramm.|
|*DependencyType*|The type of dependency relationship between *Artifact1* and *Artifact2*. For example, *Artifact1* has a **Calls** relationship with *Artifact2*.|

|**Error Syntax**|**Error Description**|
|----------------------|---------------------------|
|AV0001: Invalid Dependency: *Artifact1*(*ArtifactType1*) --> *Artifact2*(*ArtifactType2*)<br /><br /> Layers: *LayerName1*, *LayerName2* &#124; Dependencies: *DependencyType*|*Artifact1* in *LayerName1* should not have a dependency on *Artifact2* in *LayerName2* because *LayerName1* does not have a direct dependency on *LayerName2*.|
|AV1001: Invalid Namespace: *Artifact*<br /><br /> Layer: *LayerName* &#124; Required Namespace: *NamespaceName1* &#124; Current Namespace: *NamespaceName2*|*LayerName* requires that its associated artifacts must belong to *NamespaceName1*. *Artifact* is in *NamespaceName2*, not *NamespaceName1*.|
|AV1002: Depends on Forbidden Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName* &#124; Dependencies: *DependencyType*|*LayerName* requires that its associated artifacts must not depend on *NamespaceName*. *Artifact1* cannot depend on *Artifact2* because *Artifact2* is in *NamespaceName*.|
|AV1003: In Forbidden Namespace: *Artifact*(*ArtifactType*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName*|*LayerName* requires that its associated artifacts cannot belong to *NamespaceName*. *Artifact* belongs to *NamespaceName*.|
|AV3001: Missing Link: Layer '*LayerName*' links to '*Artifact*' which cannot be found. Möglicherweise fehlt ein Assemblyverweis.|*LayerName* links to an artifact that cannot be found. Ein Link zu einer Klasse kann beispielsweise fehlen, wenn im Modellierungsprojekt ein Verweis auf die Assembly mit der Klasse fehlt.|
|AV9001: Bei der Architekturvalidierung sind interne Fehler aufgetreten. Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster.|Weitere Einzelheiten finden Sie im Buildereignisprotokoll oder im Ausgabefenster.|

## <a name="security"></a>Sicherheit

## <a name="see-also"></a>Siehe auch
 [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
