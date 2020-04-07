---
title: Überprüfen von Code mit Abhängigkeitsdiagrammen
ms.date: 09/28/2018
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759704"
---
# <a name="validate-code-with-dependency-diagrams"></a>Überprüfen von Code mit Abhängigkeitsdiagrammen

## <a name="why-use-dependency-diagrams"></a>Warum Abhängigkeitsdiagramme verwenden?

Um sicherzustellen, dass Code nicht mit seinem Entwurf in Konflikt steht, überprüfen Sie den Code mit Abhängigkeitsdiagrammen in Visual Studio. Dadurch wird Folgendes ermöglicht:

- Suchen von Konflikten zwischen Abhängigkeiten im Code und Abhängigkeiten im Abhängigkeitsdiagramm.

- Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind

   Sie können z. B. das Abhängigkeitsdiagramm bearbeiten, um potenzielle Architekturänderungen anzuzeigen, und dann den Code überprüfen, um die betroffenen Abhängigkeiten anzuzeigen.

- Umgestalten oder Migrieren von Code in einen anderen Entwurf

   Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen

**Anforderungen**

- Visual Studio

  Um ein Abhängigkeitsdiagramm für ein .NET Core-Projekt zu erstellen, benötigen Sie Visual Studio 2019 Version 16.2 oder höher.

- Eine Projektmappe mit einem Modellierungsprojekt mit einem Abhängigkeitsdiagramm. Dieses Abhängigkeitsdiagramm muss mit Artefakten in C- oder Visual Basic-Projekten verknüpft sein, die Sie überprüfen möchten. Weitere Informationen finden Sie unter [Erstellen von Abhängigkeitsdiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).

Informationen dazu, welche Editionen von Visual Studio diese Funktion unterstützen, finden Sie unter [Editionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Sie können Code manuell aus einem geöffneten Abhängigkeitsdiagramm in Visual Studio oder über eine Eingabeaufforderung überprüfen. Sie können Code auch automatisch überprüfen, wenn Sie lokale Builds oder Azure Pipelines-Builds ausführen. Siehe [Channel 9 Video: Entwerfen und Validieren Ihrer Architektur mithilfe von Abhängigkeitsdiagrammen](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Wenn Sie die Layer-Validierung mit Team Foundation Server (TFS) ausführen möchten, müssen Sie auch dieselbe Version von Visual Studio auf dem Buildserver installieren.

## <a name="live-dependency-validation"></a>Live-Abhängigkeitsvalidierung

Die Abhängigkeitsüberprüfung erfolgt in Echtzeit, und Fehler werden sofort in der **Fehlerliste**angezeigt.

* Die Live-Validierung wird für C-Code und Visual Basic unterstützt.

* Um eine vollständige Lösungsanalyse bei Verwendung der Live-Abhängigkeitsüberprüfung zu aktivieren, öffnen Sie die Optionseinstellungen aus dem Goldbalken, der in der **Fehlerliste**angezeigt wird.

  - Sie können den Goldbarren dauerhaft schließen, wenn Sie nicht daran interessiert sind, alle architektonischen Probleme in Ihrer Lösung zu sehen.
  - Wenn Sie die vollständige Lösungsanalyse nicht aktivieren, wird die Analyse nur für die bearbeiteten Dateien durchgeführt.

* Beim Aktualisieren von Projekten zur Aktivierung der Livevalidierung wird in einem Dialogfeld der Fortschritt der Konvertierung angezeigt.

* Beim Aktualisieren eines Projekts für die Überprüfung der Liveabhängigkeit wird die Version des NuGet-Pakets aktualisiert, sodass sie für alle Projekte gleich ist und die höchste Version ist, die verwendet wird.

* Das Hinzufügen eines neuen Abhängigkeitsvalidierungsprojekts löst eine Projektaktualisierung aus.

## <a name="see-if-an-item-supports-validation"></a>Sehen, ob ein Element die Validierung unterstützt

Sie können Layer mit Websites, Office-Dokumenten, Nur-Text-Dateien und Dateien in Projekten verknüpfen, die für mehrere Apps freigegeben sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Validierungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.

1. Wählen Sie im Abhängigkeitsdiagramm einen oder mehrere Layer aus, klicken Sie mit der rechten Maustaste auf Ihre Auswahl, und klicken Sie dann auf **Verknüpfungen anzeigen**.

2. Sehen Sie sich im **Layer-Explorer**die Spalte **Supports Validation** an. Wenn der Wert "false" ist, wird die Überprüfung vom Element nicht unterstützt.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Andere .NET-Assemblys und Projekte zur Validierung einschließen

Wenn Sie Elemente in das Abhängigkeitsdiagramm ziehen, werden Verweise auf die entsprechenden .NET-Assemblys oder -Projekte automatisch dem Ordner **Layer-Referenzen** im Modellierungsprojekt hinzugefügt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können andere .NET-Assemblys und -Projekte zur Validierung einschließen, ohne sie manuell in das Abhängigkeitsdiagramm zu ziehen.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt oder den Ordner **Layer-Referenzen,** und klicken Sie dann auf **Referenz hinzufügen**.

2. Wählen Sie im Dialogfeld **Referenz hinzufügen** die Baugruppen oder Projekte aus, und klicken Sie dann auf **OK**.

## <a name="validate-code-manually"></a>Code manuell überprüfen

Wenn Sie über ein geöffnetes Abhängigkeitsdiagramm verfügen, das mit Lösungselementen verknüpft ist, können Sie den Befehl Shortcut **überprüfen** aus dem Diagramm ausführen. Sie können auch die Eingabeaufforderung verwenden, um den Befehl **msbuild** mit der benutzerdefinierten **Eigenschaft /p:ValidateArchitecture** auf **True**auszuführen. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Überprüfen von Code aus einem geöffneten Abhängigkeitsdiagramm

1. Klicken Sie mit der rechten Maustaste auf die Diagrammoberfläche, und klicken Sie dann auf **Architektur überprüfen**.

    > [!NOTE]
    > Standardmäßig ist die **Build Action-Eigenschaft** in der Abhängigkeitsdiagrammdatei (.layerdiagram) auf **Überprüfen** festgelegt, sodass das Diagramm in den Validierungsprozess einbezogen wird.

     Im Fenster **Fehlerliste** werden alle auftretenden Fehler angezeigt. Weitere Informationen zu Validierungsfehlern finden Sie unter Beheben von [Layer-Validierungsproblemen](#troubleshoot-layer-validation-issues).

2. Um die Ursache jedes Fehlers anzuzeigen, doppelklicken Sie im Fenster **Fehlerliste** auf den Fehler.

    > [!NOTE]
    > Visual Studio zeigt möglicherweise eine Codezuordnung anstelle der Fehlerquelle an. Dies tritt auf, wenn entweder der Code eine Abhängigkeit von einer Assembly hat, die nicht vom Abhängigkeitsdiagramm angegeben wird, oder wenn der Code eine Abhängigkeit fehlt, die durch das Abhängigkeitsdiagramm angegeben wird. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu Codezuordnungen finden Sie unter [Zuordnen von Abhängigkeiten in Ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md).

3. Informationen zum Verwalten von Fehlern finden Sie unter [Layer-Validierungsfehler auflösen](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Überprüfen des Codes an der Eingabeaufforderung

1. Öffnen Sie die Eingabeaufforderung für die Visual Studio-Eingabeaufforderung.

2. Wählen Sie eine der folgenden Optionen aus:

   - Um Code anhand eines bestimmten Modellierungsprojekts in der Projektmappe zu überprüfen, führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - oder –

       Navigieren Sie zu dem Ordner, der die Modellierungsprojektdatei (.modelproj) und das Abhängigkeitsdiagramm enthält, und führen Sie MSBuild dann mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Um Code für alle Modellierungsprojekte in der Projektmappe zu überprüfen, führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - oder –

       Navigieren Sie zum Projektmappenordner, der ein Modellierungsprojekt enthalten muss, das ein Abhängigkeitsdiagramm enthält, und führen Sie MSBuild dann mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu MSBuild finden Sie unter [MSBuild](../msbuild/msbuild.md) und [MSBuild Task](../msbuild/msbuild-task.md).

   Weitere Informationen zu Validierungsfehlern finden Sie unter Beheben von [Layer-Validierungsproblemen](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Validierungsfehler verwalten

Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, ist es sinnvoll, eine Arbeitsaufgabe in Team Foundation zu protokollieren.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

#### <a name="create-a-work-item-for-a-validation-error"></a>Erstellen einer Arbeitsaufgabe für einen Validierungsfehler

- Klicken Sie im Fenster **Fehlerliste** mit der rechten Maustaste auf den Fehler, zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten.

Verwenden Sie diese Aufgaben, um Validierungsfehler im Fenster **Fehlerliste** zu verwalten:

|**An**|**Führen Sie diese Schritte aus**|
|-|-|
|Unterdrücken von ausgewählten Fehlern während der Validierung|Klicken Sie mit der rechten Maustaste auf einen oder mehrere ausgewählte Fehler, zeigen Sie auf **Validierungsfehler verwalten**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückte Fehler werden in einer .suppressions-Datei für die entsprechende Abhängigkeitsdiagrammdatei nachverfolgt.|
|Beenden der Unterdrückung von ausgewählten Fehlern|Klicken Sie mit der rechten Maustaste auf den ausgewählten unterdrückten Fehler oder Fehler, zeigen Sie auf **Validierungsfehler verwalten**, und klicken Sie dann auf **Unterdrücken von Fehlern beenden**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|
|Wiederherstellen aller unterdrückten Fehler im Fenster **Fehlerliste**|Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Fenster **Fehlerliste,** zeigen Sie auf **Validierungsfehler verwalten**, und klicken Sie dann auf **Alle unterdrückten Fehler anzeigen**.|
|Alle unterdrückten Fehler aus dem Fenster **Fehlerliste** ausblenden|Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Fenster **Fehlerliste,** zeigen Sie auf **Validierungsfehler verwalten**, und klicken Sie dann auf **Alle unterdrückten Fehler ausblenden**.|

## <a name="validate-code-automatically"></a>Code automatisch überprüfen

Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Ihr Team Azure DevOps verwendet, können Sie die Layer-Validierung mit gated check-ins durchführen, die Sie durch Erstellen einer benutzerdefinierten MSBuild-Aufgabe angeben können, und Buildberichte verwenden, um Validierungsfehler zu sammeln. Informationen zum Erstellen von Gated-Check-In-Builds finden Sie unter [TFVC-Gated Check-in](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds

Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- oder -

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, das das Abhängigkeitsdiagramm oder die Abhängigkeitsdiagramme enthält, und klicken Sie dann auf **Eigenschaften**.

2. Legen Sie im **Fenster Eigenschaften** die **Validate Architecture-Eigenschaft** des Modellierungsprojekts auf **True**fest.

    Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.

3. Klicken Sie im **Projektmappen-Explorer**auf die Abhängigkeitsdiagrammdatei (.layerdiagram), die Sie für die Validierung verwenden möchten.

4. Stellen Sie im **Eigenschaftenfenster** sicher, dass die **Buildaktionseigenschaft** des Diagramms auf **Überprüfen**festgelegt ist.

    Dies schließt das Abhängigkeitsdiagramm im Validierungsprozess ein.

Informationen zum Verwalten von Fehlern im Fenster Fehlerliste finden Sie unter Auflösen von [Layer-Validierungsfehlern](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Ebenenvalidierungsprobleme beheben

In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter Beheben von [Layer-Validierungsproblemen](#troubleshoot-layer-validation-issues).

|**Problem**|**Mögliche Ursache**|**Lösung**|
|-|-|-|
|Validierungsfehler treten nicht wie erwartet auf.|Die Validierung funktioniert nicht für Abhängigkeitsdiagramme, die aus anderen Abhängigkeitsdiagrammen im Projektmappen-Explorer kopiert werden und sich im gleichen Modellierungsprojekt befinden. Abhängigkeitsdiagramme, die auf diese Weise kopiert werden, enthalten dieselben Verweise wie das ursprüngliche Abhängigkeitsdiagramm.|Fügen Sie dem Modellierungsprojekt ein neues Abhängigkeitsdiagramm hinzu.<br /><br /> Kopieren Sie die Elemente aus dem Quellabhängigkeitsdiagramm in das neue Diagramm.|

## <a name="resolve-layer-validation-errors"></a>Beheben von Layer-Validierungsfehlern

Wenn Sie Code anhand eines Abhängigkeitsdiagramms überprüfen, treten Validierungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.

Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.

|**Syntax**|**Beschreibung**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* ist ein Artefakt, das einem Layer im Abhängigkeitsdiagramm zugeordnet ist.<br /><br /> *ArtifactTypeN* ist der Typ von *ArtifactN*, z. B. einer **Klasse** oder **Methode:**<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Der Name eines Namespace.|
|*LayerNameN*|Der Name eines Layers im Abhängigkeitsdiagramm.|
|*DependencyType*|Der Typ der Abhängigkeitsbeziehung zwischen *Artifact1* und *Artifact2*. *Artefakt1* hat z. B. eine **Call-Beziehung** mit *Artifact2*.|

| **Fehlersyntax** | **Fehlerbeschreibung** |
|-|-|
| DV0001: **Ungültige Abhängigkeit** | Dieses Problem wird gemeldet, wenn ein Codeelement (Namespace, Typ, Member), das einem Layer zugeordnet ist, auf ein Codeelement verweist, das einem anderen Layer zugeordnet ist, aber es gibt keinen Abhängigkeitspfeil zwischen diesen Layern im Abhängigkeitsüberprüfungsdiagramm, das diese Layer enthält. Dies ist eine Verletzung der Abhängigkeitseinschränkung. |
| DV1001: **Ungültiger Namespacename** | Dieses Problem wird über ein Codeelement gemeldet, das einem Layer zugeordnet ist, dessen Eigenschaft "Allowed Namespace Names" nicht den Namespace enthält, in dem dieses Codeelement definiert ist. Dies ist eine Namenseinschränkungsverletzung. Beachten Sie, dass die Syntax von "Allowed Namespace Names" eine Semikolonliste von Namespaces sein soll, in denen Codeelemente, denen Layer zugeordnet sind, definiert werden dürfen. |
| DV1002: **Abhängigkeit von nicht referenzierbarem Namespace** | Dieses Problem wird über ein Codeelement gemeldet, das einem Layer zugeordnet ist und auf ein anderes Codeelement verweist, das in einem Namespace definiert ist, der in der Eigenschaft "Nicht referenzierbarer Namespace" des Layers definiert ist. Dies ist eine Namenseinschränkungsverletzung. Beachten Sie, dass die Eigenschaft "Unreferenceable Namespaces" als eine durch Semikolons getrennte Liste von Namespaces definiert ist, auf die in Codeelementen, die diesem Layer zugeordnet sind, nicht verwiesen werden sollte. |
| DV1003: **Unzulässiger Namespacename** | Dieses Problem wird über ein Codeelement gemeldet, das einem Layer zugeordnet ist, dessen Eigenschaft "Nicht zulässige Namespacenamen" den Namespace enthält, in dem dieses Codeelement definiert ist. Dies ist eine Namenseinschränkungsverletzung. Beachten Sie, dass die Eigenschaft "Nicht zulässiger Namespacename" als eine durch Semikolons getrennte Liste von Namespaces definiert ist, in denen Codeelemente, die diesem Layer zugeordnet sind, nicht definiert werden sollen. |
| DV2001: **Schichtdiagramm-Präsenz** | Dieses Problem wird in einem Projekt gemeldet, das keine Abhängigkeitsdiagrammdatei enthält, sich aber auf die Analyseder der Abhängigkeitsüberprüfung bezieht. Wenn die Abhängigkeitsüberprüfung nicht verwendet wurde, können Sie "Microsoft.DependencyValidation.Analyzers" direkt aus dem Projektmappen-Explorer entfernen oder diese Warnung unterdrücken. So fügen Sie ein [Abhängigkeitsdiagramm hinzu unter Erstellen von Abhängigkeitsdiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Basis für nicht zugeordnete Typen** | Dieses Problem wird gemeldet, wenn ein Codeelement keinem Layer zugeordnet ist. |
| DV3001: **Fehlende Verbindung** | Layer '*LayerName*' links zu '*Artifact*', die nicht gefunden werden können. Möglicherweise fehlt ein Assemblyverweis. |
| DV9001: **Architekturanalyse fand interne Fehler** | Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster. |

## <a name="see-also"></a>Weitere Informationen

- [Live-Abhängigkeitsüberprüfung in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
- [Video: Überprüfen Ihrer Architekturabhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
