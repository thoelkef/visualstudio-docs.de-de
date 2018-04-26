---
title: Überprüfen von Code mit der Abhängigkeit-Diagramme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 63dc6c6b1307ae5d8b8be880815f5de5e782c6f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="validate-code-with-dependency-diagrams"></a>Überprüfen von Code mit der Abhängigkeit-Diagramme

**Neueste**: finden Sie unter [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/).

[Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="why-use-dependency-diagrams"></a>Gründe für die Verwendung von Diagrammen Abhängigkeit

Um sicherzustellen dass der Code mit dem Entwurf nicht widerspricht., überprüfen Sie Code mit der Abhängigkeit Diagramme in Visual Studio. Dadurch wird Folgendes ermöglicht:

-   Suchen Sie Konflikte zwischen Abhängigkeiten im Code und Abhängigkeiten im Diagramm Abhängigkeit.

-   Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind

     Beispielsweise können Sie das Diagramm Abhängigkeit, um potenzielle architekturänderungen darzustellen, und überprüfen Sie den Code, um die betroffenen Abhängigkeiten finden Sie unter Bearbeiten.

-   Umgestalten oder Migrieren von Code in einen anderen Entwurf

     Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen

 **Anforderungen**

-   Visual Studio

-   Visual Studio auf dem Team Foundation Build-Server, um Code mit Team Foundation Build automatisch zu überprüfen

-   Eine Lösung, die ein Modellierungsprojekt mit einem Diagramm Abhängigkeit enthält. Dieses Diagramm Abhängigkeit muss mit Artefakten in c# oder Visual Basic-Projekten verknüpft werden, die Sie überprüfen möchten. Finden Sie unter [Abhängigkeit Diagramme erstellen, aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Sie können Code manuell aus einem Diagramm öffnen Abhängigkeit in Visual Studio oder über eine Eingabeaufforderung überprüfen. Sie können Code beim Ausführen von lokalen Builds oder Team Foundation Build auch automatisch überprüfen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur von Abhängigkeit Diagrammen](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
>  Wenn Sie die Ebenenvalidierung mit Team Foundation Build ausführen möchten, muss auch Visual Studio auf dem Buildserver installiert werden.

-   [Überprüfen Sie, ob ein Element die Validierung unterstützt](#SupportsValidation)

-   [Andere .NET-Assemblys und Projekte zur Validierung einschließen](#IncludeReferences)

-   [Code manuell überprüfen](#ValidateManually)

-   [Code automatisch überprüfen](#ValidateAuto)

-   [Ebenenvalidierungsprobleme](#TroubleshootingValidation)

-   [Verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors)

## <a name="live-dependency-validation"></a>Live abhängigkeitsüberprüfung

In dieser Version von Visual Studio Abhängigkeit Überprüfungen in Echtzeit, und Fehler werden im Fenster Fehlerliste von Visual Studio sofort angezeigt.

* Live-Überprüfung wird für c# und Visual Basic.NET unterstützt.

* Öffnen Sie die optionseinstellungen aus der gold-Leiste, die in der Fehlerliste angezeigt wird, um vollständige projektmappenanalyse aktivieren bei Verwendung von live abhängigkeitsüberprüfung.
 - Diese gold Leiste können dauerhaft verworfen werden, wenn Sie nicht alle architektonische Probleme, die in der Projektmappe interessiert sind.
 - Wenn Sie nicht vollständige projektmappenanalyse aktivieren, erfolgt die Analyse nur für die Dateien, die bearbeitet wird.<p />

* Beim Aktualisieren von Projekten für live-Überprüfung aktivieren zeigt ein Dialogfeld den Status der Konvertierung.

* Beim Aktualisieren eines Projekts für live abhängigkeitsüberprüfung die Version des NuGet-Pakets wird aktualisiert, um für alle Projekte gleich sein, und die höchste Version verwendet wird.

* Hinzufügen eine neue Abhängigkeit Überprüfung Projekt Trigger ein Update des Projekts.

##  <a name="SupportsValidation"></a> Überprüfen Sie, ob ein Element die Validierung unterstützt
 Sie können Ebenen mit Websites, Office-Dokumenten, Nur-Text-Dateien und Dateien in Projekten verknüpfen, die von mehreren Apps gemeinsam verwendet werden, jedoch nicht im Validierungsprozess enthalten sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Überprüfungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.

1.  Wählen Sie auf das Diagramm Abhängigkeit eine oder mehrere Ebenen rechten Maustaste auf die Auswahl, und klicken Sie dann auf **Links anzeigen**.

2.  In **Ebenen-Explorer**, sehen Sie sich die **unterstützt die Validierung** Spalte. Wenn der Wert „false“ ist, wird die Validierung vom Element nicht unterstützt.

##  <a name="IncludeReferences"></a> Andere .NET-Assemblys und Projekte zur Validierung einschließen
 Wenn Sie Elemente in das Dependency-Diagramm ziehen, werden automatisch zu Verweise auf die entsprechenden .NET-Assemblys oder Projekte hinzugefügt der **Ebenenverweise** Ordner im Modellierungsprojekt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können weitere .NET-Assemblys und Projekte zur Validierung einschließen, ohne Sie sie manuell das Dependency-Diagramm ziehen.

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Modellierungsprojekts oder den **Ebenenverweise** Ordner, und klicken Sie dann auf **Verweis hinzufügen**.

2.  In der **Verweis hinzufügen** (Dialogfeld), wählen Sie die Assemblys oder Projekte aus, und klicken Sie dann auf **OK**.

##  <a name="ValidateManually"></a> Code manuell überprüfen
 Wenn Sie ein Diagramm öffnen Abhängigkeit, das mit Projektmappenelementen verknüpft ist verfügen, können Sie Ausführen den **Validate** Kurzbefehl aus dem Diagramm. Sie können auch die Befehlszeile zum Ausführen der **Msbuild** -Befehl mit der **ValidateArchitecture** benutzerdefinierte Eigenschaft auf festgelegt **"true"**. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.

#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>So überprüfen Sie Code aus einem Diagramm öffnen Abhängigkeit

1.  Maustaste auf die Diagrammoberfläche, und klicken Sie dann auf **Architektur überprüfen**.

    > [!NOTE]
    >  Wird standardmäßig die **Buildvorgang** Eigenschaft für die Abhängigkeitseigenschaft Ebenendiagrammdatei (.layerdiagram)-Datei wird festgelegt, um **Validate** , damit das Diagramm in den Validierungsvorgang eingeschlossen wird.

     Die **Fehlerliste** Fenster zeigt aufgetretene Fehler. Weitere Informationen zu Überprüfungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).

2.  Um die Quelle der einzelnen Fehler anzuzeigen, doppelklicken Sie auf den Fehler in der **Fehlerliste** Fenster.

    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zeigt möglicherweise anstelle der Quelle des Fehlers eine Code Map an. Dies tritt auf, wenn der Code hat eine Abhängigkeit zu einer Assembly, die durch das Diagramm Abhängigkeit nicht angegeben wird, oder der Code fehlt eine Abhängigkeit, die durch das Diagramm Abhängigkeit angegeben wird. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu Code Maps finden Sie unter [Zuordnen von lösungsübergreifenden Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md).

3.  Verwalten von Fehlern finden Sie unter [Validierungsfehler verwalten](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>So überprüfen Sie Code an der Eingabeaufforderung

1.  Öffnen Sie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Eingabeaufforderung.

2.  Wählen Sie eine der folgenden Optionen aus:

    -   Wenn Sie Code anhand eines bestimmten Modellierungsprojekts in der Projektmappe überprüfen möchten, führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft aus.

        ```
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
        ```

         - ODER

         Navigieren Sie zum Ordner mit der Modellierungsprojektdatei (.modelproj) und die Abhängigkeit Diagramm, und klicken Sie dann führen [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft:

        ```
        msbuild /p:ValidateArchitecture=true
        ```

    -   Wenn Sie Code anhand aller Modellierungsprojekte in der Projektmappe überprüfen möchten, führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft aus:

        ```
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
        ```

         - ODER

         Navigieren Sie zu einem Projektmappenordner, der ein Modellierungsprojekt, das eine Abhängigkeit-Diagramm enthält, und führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft:

        ```
        msbuild /p:ValidateArchitecture=true
        ```

     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], finden Sie unter [MSBuild](../msbuild/msbuild.md) und [MSBuild-Aufgabe](../msbuild/msbuild-task.md).

 Weitere Informationen zu Überprüfungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).

###  <a name="ManageErrors"></a> Validierungsfehler verwalten
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] eine Arbeitsaufgabe zu protokollieren.

> [!WARNING]
>  Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um eine Arbeitsaufgabe zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, eine Arbeitsaufgabe zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>So erstellen Sie ein Arbeitselement für einen Validierungsfehler

-   In der **Fehlerliste** Fenster mit der rechten Maustaste des Fehlers, zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten.

 Mithilfe dieser Aufgaben können Sie Validierungsfehler im die **Fehlerliste** Fenster:

|**Aktion**|**Gehen Sie folgendermaßen vor**|
|------------|----------------------------|
|Unterdrücken von ausgewählten Fehlern während der Validierung|Mit der rechten Maustaste die einem oder mehreren ausgewählten Fehler, zeigen Sie auf **Validierungsfehler unterdrücken**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückten Fehler werden in einer suppressions-Datei für die entsprechende Beziehung Diagrammdatei nachverfolgt.|
|Beenden der Unterdrückung von ausgewählten Fehlern|Mit der rechten Maustaste den oder die ausgewählten unterdrückten Fehler, zeigen Sie auf **Validierungsfehler unterdrücken**, und klicken Sie dann auf **Fehler nicht mehr unterdrücken**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|
|Wiederherstellen aller unterdrückten Fehler in der **Fehlerliste** Fenster|Mit der rechten Maustaste an einer beliebigen Stelle der **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler unterdrücken**, und klicken Sie dann auf **Unterdrückte Fehler anzeigen**.|
|Ausblenden aller unterdrückten Fehler aus der **Fehlerliste** Fenster|Mit der rechten Maustaste an einer beliebigen Stelle der **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler unterdrücken**, und klicken Sie dann auf **Unterdrückte Fehler ausblenden**.|

##  <a name="ValidateAuto"></a> Code automatisch überprüfen
 Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Team Foundation Build von Ihrem Team verwendet wird, können Sie eine Ebenenvalidierung mit Gated-Check-Ins durchführen, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe erstellen und Überprüfungsfehler mithilfe von Buildberichten sammeln. Zum Erstellen von abgegrenzten Eincheckbuilds finden Sie unter [verwenden ein abgegrenzten eincheckbuildprozesses zur Überprüfung von Änderungen](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds

-   Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- oder –

1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, das die Abhängigkeit Ebenendiagramme enthält, und klicken Sie dann auf **Eigenschaften**.

2.  In der **Eigenschaften** legen des Modellierungsprojekts **Architektur überprüfen** Eigenschaft **"true"**.

     Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.

3.  In **Projektmappen-Explorer**, klicken Sie auf die Abhängigkeit Ebenendiagrammdatei (.layerdiagram)-Datei, die Sie für die Validierung verwenden möchten.

4.  In der **Eigenschaften** Fenster, stellen Sie sicher, dass des Diagramms **Buildvorgang** -Eigenschaftensatz auf **Validate**.

     Dies schließt das Dependency-Diagramm in den Validierungsprozess.

 Verwalten von Fehlern im Fenster "Fehlerliste" finden Sie unter [Validierungsfehler unterdrücken](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>So überprüfen Sie Code automatisch für einen Team Foundation Build

1.  In **Team Explorer**, doppelklicken Sie auf die Builddefinition, und klicken Sie dann auf **Prozess**.

2.  Klicken Sie unter **Buildprozessparameter**, erweitern Sie **Kompilierung**, und geben Sie Folgendes in die **MSBuild-Argumente** Parameter:

     `/p:ValidateArchitecture=true`

 Weitere Informationen zu Überprüfungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors). Weitere Informationen über [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] finden Sie hier:

-   [Build und Release](/vsts/build-release/index)

-   [Verwenden Sie die Standardvorlage für den Buildprozess](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)

-   [Ändern Sie die Vorgängerversion erstellen, die auf UpgradeTemplate.xaml basieren](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

-   [Anpassen der Buildprozessvorlage](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

-   [Überwachen des Status eines Builds ausgeführt wird](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

##  <a name="TroubleshootingValidation"></a> Ebenenvalidierungsprobleme
 In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).

|**Problem**|**Mögliche Ursache**|**Auflösung**|
|---------------|------------------------|--------------------|
|Validierungsfehler treten nicht wie erwartet auf.|Die Validierung funktioniert nicht in Abhängigkeit von Diagrammen, die aus anderen Diagrammen Abhängigkeit im Projektmappen-Explorer kopiert wurden und sich im gleichen Modellierungsprojekt. Abhängigkeit Diagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Abhängigkeit Diagramm.|Fügen Sie dem Modellierungsprojekt ein neues Diagramm der Abhängigkeit hinzu.<br /><br /> Kopieren Sie die Elemente des Quelldiagramms-Abhängigkeit an, in das neue Diagramm.|

##  <a name="UnderstandingValidationErrors"></a> Verstehen und Lösen von Ebenenvalidierungsfehlern
 Beim Überprüfen von Code anhand eines Diagramms Abhängigkeit treten Validierungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:

-   Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

-   Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

 Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.

 Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.

|**Syntax**|**Beschreibung**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* ist ein Artefakt, das einer Ebene im Diagramm für die Abhängigkeitseigenschaft zugeordnet ist.<br /><br /> *ArtifactTypeN* ist der Typ des *ArtifactN*, z. B. eine **Klasse** oder **Methode**, beispielsweise:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Der Name eines Namespace.|
|*LayerNameN*|Der Name einer Ebene im Diagramm Abhängigkeit.|
|*DependencyType*|Der Typ der abhängigkeitsbeziehung zwischen *"Element1"* und *Artifact2*. Beispielsweise *"Element1"* verfügt über eine **Aufrufe** Beziehung mit *Artifact2*.|

|**Fehlersyntax**|**Fehlerbeschreibung**|
|----------------------|---------------------------|
|DV0001: **ungültige Abhängigkeit**|Dieses Problem wird gemeldet, wenn ein Codeelement ("Namespace", "Typ", "Member") eine Ebenenverweise ein Codeelement, das auf einer anderen Ebene zugeordnet zugeordnet, aber es keine Abhängigkeitspfeils zwischen diesen Ebenen im Diagramm Überprüfung Abhängigkeit ist, die diese Ebenen enthält. Dies ist eine einschränkungsverletzung Abhängigkeit.|
|DV1001: **Ungültiger Namespacename.**|Dieses Problem wird gemeldet, auf ein Codeelement zugeordneten einer Schicht bereit, die "Zulässige Namespace-Namen"-Eigenschaft nicht den Namespace enthält, in dem dieser Code-Element definiert ist. Dies ist eine einschränkungsverletzung Benennungskonventionen. Beachten Sie, dass die Syntax von "Namespace-Namen zulässig" ist eine durch Semikolons Liste der Namespaces, die in welcher Code Elemente, die zu Ebene befinden, sind zulässig, definiert werden.|
|DV1002: **Abhängigkeit unreferenceable Namespace**|Dieses Problem wird gemeldet, auf ein Codeelement, einer Ebene zugeordnete und verweisen auf eine andere Code-Element definiert, die in einem Namespace, die in der Eigenschaft "Unreferenceable Namespace" der Ebene definiert ist. Dies ist eine einschränkungsverletzung Benennungskonventionen. Beachten Sie, dass die Eigenschaft "Unreferenceable Namespaces" als eine durch Semikolons getrennte Liste der Namespaces definiert, die nicht in Codeelemente, die dieser Ebene zugeordneten verwiesen werden soll.|
|DV1003: **Namespacenamen nicht erlaubt**|Dieses Problem wird gemeldet, auf ein Codeelement verknüpft sind, zu einer Ebene die "Unzulässiger Namespace-Namen"-Eigenschaft den Namespace enthält, in dem dieser Code-Element definiert ist. Dies ist eine einschränkungsverletzung Benennungskonventionen. Beachten Sie, dass die Eigenschaft "Nicht erlaubt-Namespace-Name" als eine durch Semikolons getrennte Liste der Namespaces definiert wird im Code dieser Ebene zugeordneten Elemente nicht definiert werden soll.|
|DV3001: **fehlender Link**|Ebene "*LayerName*"enthält eine Verknüpfung zum"*Artefakt*", der nicht gefunden werden. Möglicherweise fehlt ein Assemblyverweis.|*Ebenenname* Verknüpfung mit einem Artefakt, das nicht gefunden werden kann. Ein Link zu einer Klasse kann beispielsweise fehlen, wenn im Modellierungsprojekt ein Verweis auf die Assembly mit der Klasse fehlt.|
|DV9001: **architektonische Analyse interner Fehler gefunden.**|Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster.|Weitere Einzelheiten finden Sie im Buildereignisprotokoll oder im Ausgabefenster.|


## <a name="see-also"></a>Siehe auch

- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
- [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
