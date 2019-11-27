---
title: Überprüfen von Code mit ebenendiagrammen | Microsoft-Dokumentation
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

- Visual Studio

- Visual Studio auf dem Team Foundation Build-Server, um Code mit Team Foundation Build automatisch zu überprüfen

- Eine Projektmappe, die über ein Modellierungsprojekt mit einem Ebenendiagramm verfügt. Dieses Ebenendiagramm muss mit Artefakten in Visual C# .NET- oder Visual Basic .NET-Projekten verknüpft sein, die Sie überprüfen möchten. Siehe [Erstellen von ebenendiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).

  Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Sie können Code über ein geöffnetes Ebenendiagramm in Visual Studio oder eine Eingabeaufforderung manuell überprüfen. Sie können Code beim Ausführen von lokalen Builds oder Team Foundation Build auch automatisch überprüfen. Weitere Informationen finden [Sie unter Channel 9-Video: Entwerfen und validieren ihrer Architektur mit ebenendiagrammen](https://go.microsoft.com/fwlink/?LinkID=252073)

> [!IMPORTANT]
> Wenn Sie die Ebenenvalidierung mit Team Foundation Build ausführen möchten, muss auch Visual Studio auf dem Buildserver installiert werden.

- [Überprüfen, ob ein Element die Validierung unterstützt](#SupportsValidation)

- [Andere .NET-Assemblys und Projekte zur Validierung einbeziehen](#IncludeReferences)

- [Code manuell überprüfen](#ValidateManually)

- [Code automatisch überprüfen](#ValidateAuto)

- [Beheben von ebenenvalidierungsproblemen](#TroubleshootingValidation)

- [Verstehen und Beheben von ebenenvalidierungsfehlern](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a>Überprüfen, ob ein Element die Validierung unterstützt
 Sie können Ebenen mit Websites, Office-Dokumenten, Nur-Text-Dateien und Dateien in Projekten verknüpfen, die von mehreren Apps gemeinsam verwendet werden, jedoch nicht im Validierungsprozess enthalten sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Validierungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.

1. Wählen Sie im ebenendiagramm eine oder mehrere Ebenen aus, klicken Sie mit der rechten Maustaste auf Ihre Auswahl, und klicken Sie dann auf **Links anzeigen**.

2. Sehen Sie sich im **ebenenexplorer**die Spalte **unterstützt Validierung** an. Wenn der Wert "false" ist, wird die Überprüfung vom Element nicht unterstützt.

## <a name="IncludeReferences"></a>Andere .NET-Assemblys und Projekte zur Validierung einbeziehen
 Wenn Sie Elemente in das ebenendiagramm ziehen, werden die Verweise auf die entsprechenden .NET-Assemblys oder-Projekte automatisch dem Ordner für **ebenenverweise** im Modellierungsprojekt hinzugefügt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können weitere .NET-Assemblys und -Projekte zur Überprüfung hinzufügen, ohne diese manuell in das Ebenendiagramm zu ziehen.

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt oder den Ordner **ebenenverweise** , und klicken Sie dann auf **Verweis hinzufügen**.

2. Wählen Sie im Dialogfeld **Verweis hinzufügen** die Assemblys oder Projekte aus, und klicken Sie dann auf **OK**.

## <a name="ValidateManually"></a>Code manuell überprüfen
 Wenn Sie über ein geöffnetes ebenendiagramm verfügen, das mit Projektmappenelementen verknüpft ist, können Sie den Befehl **"Verknüpfung überprüfen" im Diagramm** ausführen. Sie können auch die Eingabeaufforderung verwenden, um den **MSBuild** -Befehl auszuführen, bei dem die benutzerdefinierte Eigenschaft **/p: ValidateArchitecture** auf **true**festgelegt ist. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>So überprüfen Sie Code in einem geöffneten Ebenendiagramm

1. Klicken Sie mit der rechten Maustaste auf die Diagramm Oberfläche, und klicken Sie auf **Architektur**überprüfen.

    > [!NOTE]
    > Standardmäßig ist die **Eigenschaft** Buildvorgang in der ebenendiagrammdatei (. layerdiagram) auf **Validate** festgelegt, damit das Diagramm im Überprüfungsprozess enthalten ist.

     Das **Fehlerliste** Fenster meldet alle auftretenden Fehler. Weitere Informationen zu Validierungs Fehlern finden Sie unter [verstehen und Beheben von ebenenvalidierungsfehlern](#UnderstandingValidationErrors).

2. Wenn Sie die Quelle der einzelnen Fehler anzeigen möchten, doppelklicken Sie im Fenster **Fehlerliste** auf den Fehler.

    > [!NOTE]
    > in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird möglicherweise eine Code Map anstelle der Fehlerquelle angezeigt. Dies ist der Fall, wenn der Code eine Abhängigkeit von einer Assembly enthält, die nicht im Ebenendiagramm angegeben ist, oder wenn im Code eine im Ebenendiagramm angegebene Abhängigkeit fehlt. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu Code Maps finden Sie unterzuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md).

3. Informationen zum Verwalten von Fehlern finden Sie unter [Verwalten von Validierungs Fehlern](#ManageErrors).

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

     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]finden Sie unter [MSBuild](../msbuild/msbuild.md) und [MSBuild-Aufgabe](../msbuild/msbuild-task.md).

   Weitere Informationen zu Validierungs Fehlern finden Sie unter [verstehen und Beheben von ebenenvalidierungsfehlern](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a>Verwalten von Validierungs Fehlern
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../includes/esprfound-md.md)] eine Arbeitsaufgabe zu protokollieren.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>So erstellen Sie eine Arbeitsaufgabe für einen Validierungsfehler

- Klicken Sie im **Fehlerliste** Fenster mit der rechten Maustaste auf den Fehler, zeigen Sie auf **Arbeits Element erstellen**, und klicken Sie dann auf den Typ des Arbeits Elements, das Sie erstellen möchten.

  Verwenden Sie diese Tasks, um Validierungs Fehler im Fenster **Fehlerliste** zu verwalten:

|**Aktion**|**Befolgen Sie diese Schritte.**|
|------------|----------------------------|
|Unterdrücken von ausgewählten Fehlern während der Validierung|Klicken Sie mit der rechten Maustaste auf einen oder mehrere ausgewählte Fehler, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückte Fehler werden in einer SUPPRESSIONS-Datei für die entsprechende Ebenendiagrammdatei nachverfolgt.|
|Beenden der Unterdrückung von ausgewählten Fehlern|Klicken Sie mit der rechten Maustaste auf den ausgewählten Fehler oder Fehler, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **Fehler nicht mehr unterdrücken**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|
|Alle unterdrückten Fehler im Fenster " **Fehlerliste** " Wiederherstellen|Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im **Fehlerliste** Fenster, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **alle unterdrückten Fehler anzeigen**.|
|Alle unterdrückten Fehler im Fenster " **Fehlerliste** " ausblenden|Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im **Fehlerliste** Fenster, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **alle unterdrückten Fehler ausblenden**.|

## <a name="ValidateAuto"></a>Code automatisch überprüfen
 Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Team Foundation Build von Ihrem Team verwendet wird, können Sie eine Ebenenvalidierung mit abgegrenzten Eincheckvorgängen durchführen, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe erstellen und Überprüfungsfehler mithilfe von Buildberichten sammeln. Informationen zum Erstellen von abgegrenzten Eincheckbuilds finden Sie unter [Verwenden eines Gated-Check-in-Buildprozesses zum Überprüfen von Änderungen](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds

- Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- oder –

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, das das ebenendiagramm oder die Diagramme enthält, und klicken Sie dann auf **Eigenschaften**.

2. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Architektur validieren** des Modellierungs Projekts auf **true**fest.

    Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.

3. Klicken Sie in **Projektmappen-Explorer**auf die ebenendiagrammdatei (. layerdiagram), die Sie für die Validierung verwenden möchten.

4. Stellen Sie im **Eigenschaften** Fenster sicher, dass **die Eigenschaft Buildvorgang des** Diagramms auf **überprüfen**festgelegt ist.

    Dadurch wird das Ebenendiagramm in den Validierungsprozess eingeschlossen.

   Informationen zum Verwalten von Fehlern im Fenster Fehlerliste finden Sie unter [Verwalten von Validierungs Fehlern](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>So überprüfen Sie Code automatisch für einen Team Foundation Build

1. Doppelklicken Sie in **Team Explorer**auf die Builddefinition, und klicken Sie dann auf **verarbeiten**.

2. Erweitern Sie unter **buildprozessparameter**die Option **Kompilierung**, und geben Sie im Parameter **MSBuild-Argumente** Folgendes ein:

    `/p:ValidateArchitecture=true`

   Weitere Informationen zu Validierungs Fehlern finden Sie unter [verstehen und Beheben von ebenenvalidierungsfehlern](#UnderstandingValidationErrors). Weitere Informationen zu [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] finden Sie unter:

- [Erstellen der Anwendung](/azure/devops/pipelines/index)

- [Verwenden der Standardvorlage für den Buildprozess](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Ändern eines Legacy Builds, der auf "Upgrade Template. XAML" basiert](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Anpassen der Buildprozessvorlage](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Überwachen des Fortschritts eines laufenden Builds](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a>Beheben von ebenenvalidierungsproblemen
 In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter [verstehen und Beheben von ebenenvalidierungsfehlern](#UnderstandingValidationErrors).

|**Problem**|**Mögliche Ursache**|**Auflösung**|
|---------------|------------------------|--------------------|
|Validierungsfehler treten nicht wie erwartet auf.|Die Validierung funktioniert nicht mit Ebenendiagrammen, die aus anderen Ebenendiagrammen im Projektmappen-Explorer kopiert wurden und sich im gleichen Modellierungsprojekt befinden. Ebenendiagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Ebenendiagramm.|Fügen Sie dem Modellierungsprojekt ein neues Ebenendiagramm hinzu.<br /><br /> Kopieren Sie die Elemente aus dem Quellebenendiagramm in das neue Diagramm.|

## <a name="UnderstandingValidationErrors"></a>Verstehen und Beheben von ebenenvalidierungsfehlern
 Beim Überprüfen von Code anhand eines Ebenendiagramms treten Überprüfungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

  Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.

  Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.

|**Syntax**|**Beschreibung**|
|----------------|---------------------|
|*Artifaktn*(*artifakttypen*)|*Artifacetten TN* ist ein Artefakt, das einer Ebene im ebenendiagramm zugeordnet ist.<br /><br /> *Artifacttypen* ist der Typ von *artifactn*, z. b. eine **Klasse** oder **Methode**, z. b.:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*Namespacenamen*|Der Name eines Namespace.|
|*Layer-Namen*|Der Name einer Ebene im Ebenendiagramm.|
|*DependencyType*|Der Typ der Abhängigkeitsbeziehung zwischen *Element1* und *Artifact2*. Beispielsweise hat *Element1* eine Beziehung zum **aufrufen** von *Artifact2*.|

|**Fehler Syntax**|**Fehlerbeschreibung**|
|----------------------|---------------------------|
|AV0001: Ungültige Abhängigkeit: *Element1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> Ebenen: *LayerName1*, *LayerName2* &#124; Abhängigkeiten: *DependencyType*|*Element1* in *LayerName1* sollte nicht von *Artifact2* in *LayerName2* abhängig sein, da *LayerName1* keine direkte Abhängigkeit von *LayerName2*hat.|
|AV1001: Ungültiger Namespace: *artefaktelement*<br /><br /> Ebene: *Layername* &#124; erforderlicher Namespace: *NamespaceName1* &#124; aktueller Namespace: *NamespaceName2*|*Layername* erfordert, dass die zugehörigen Artefakte zu *NamespaceName1*gehören. Das *Element befindet sich* in *NamespaceName2*, nicht in *NamespaceName1*.|
|AV1002: abhängig von unzulässigem Namespace: *Element1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Layer: *Layername* &#124; unzulässiger Namespace: *Namespace* &#124; Name Abhängigkeiten: *DependencyType*|*Layername* erfordert, dass die zugehörigen Artefakte nicht von *Namespacename*abhängen. *Element1* kann nicht von *Artifact2* abhängen, weil *Artifact2* in *Namespacename*ist.|
|AV1003: in unzulässigem Namespace: *Artefakt*(*artifakttype*)<br /><br /> Ebene: *Layername* &#124; unzulässiger Namespace: *Namespacename*|*Layername* erfordert, dass die zugehörigen Artefakte nicht zu *Namespace*Name gehören. Das *Element gehört zu* *Namespacename*.|
|AV3001: fehlender Link: Layer '*Layername*' ist mit '*artefakt'* verknüpft, das nicht gefunden werden kann. Möglicherweise fehlt ein Assemblyverweis.|*Layername* ist mit einem artefaktelement verknüpft, das nicht gefunden werden kann. Ein Link zu einer Klasse kann beispielsweise fehlen, wenn im Modellierungsprojekt ein Verweis auf die Assembly mit der Klasse fehlt.|
|AV9001: Bei der Architekturvalidierung sind interne Fehler aufgetreten. Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster.|Weitere Einzelheiten finden Sie im Buildereignisprotokoll oder im Ausgabefenster.|

## <a name="security"></a>Sicherheit

## <a name="see-also"></a>Siehe auch
 [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
