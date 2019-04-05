---
title: Überprüfen von Code mit Ebenendiagrammen | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 74c61beeae78fbf76ffee76ff930171ddbe8089a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960765"
---
# <a name="validate-code-with-layer-diagrams"></a>Überprüfen von Code mit Ebenendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um sicherzustellen, dass der Code dem Entwurf nicht widerspricht, können Sie Ihren Code in Visual Studio mit Ebenendiagrammen überprüfen. Dadurch wird Folgendes ermöglicht:  
  
- Suchen von Konflikten zwischen Abhängigkeiten im Code und Abhängigkeiten im Ebenendiagramm  
  
- Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind  
  
   Sie können z. B. das Ebenendiagramm bearbeiten, um potenzielle Architekturänderungen darzustellen, und dann den Code überprüfen, um die betroffenen Abhängigkeiten zu ermitteln.  
  
- Umgestalten oder Migrieren von Code in einen anderen Entwurf  
  
   Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen  
  
  **Anforderungen**  
  
- Visual Studio  
  
- Visual Studio auf dem Team Foundation Build-Server, um Code mit Team Foundation Build automatisch zu überprüfen  
  
- Eine Projektmappe, die über ein Modellierungsprojekt mit einem Ebenendiagramm verfügt. Dieses Ebenendiagramm muss mit Artefakten in Visual C# .NET- oder Visual Basic .NET-Projekten verknüpft sein, die Sie überprüfen möchten. Finden Sie unter [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
  Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
  Sie können Code über ein geöffnetes Ebenendiagramm in Visual Studio oder eine Eingabeaufforderung manuell überprüfen. Sie können Code beim Ausführen von lokalen Builds oder Team Foundation Build auch automatisch überprüfen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur mit Ebenendiagrammen](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Wenn Sie die Ebenenvalidierung mit Team Foundation Build ausführen möchten, muss auch Visual Studio auf dem Buildserver installiert werden.  
  
-   [Überprüfen Sie, ob ein Element die Validierung unterstützt](#SupportsValidation)  
  
-   [Sind andere .NET-Assemblys und-Projekte zur Validierung](#IncludeReferences)  
  
-   [Code manuell überprüfen](#ValidateManually)  
  
-   [Code automatisch überprüfen](#ValidateAuto)  
  
-   [Ebenenvalidierungsprobleme](#TroubleshootingValidation)  
  
-   [Verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors)  
  
##  <a name="SupportsValidation"></a> Überprüfen Sie, ob ein Element die Validierung unterstützt  
 Sie können Ebenen mit Websites, Office-Dokumenten, Nur-Text-Dateien und Dateien in Projekten verknüpfen, die von mehreren Apps gemeinsam verwendet werden, jedoch nicht im Validierungsprozess enthalten sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Überprüfungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.  
  
1.  Wählen Sie im Ebenendiagramm eine oder mehrere Ebenen, mit der rechten Maustaste in der Auswahl, und klicken Sie dann auf **Links anzeigen**.  
  
2.  In **Ebenen-Explorer**, sehen Sie sich die **unterstützt die Validierung** Spalte. Wenn der Wert „false“ ist, wird die Validierung vom Element nicht unterstützt.  
  
##  <a name="IncludeReferences"></a> Sind andere .NET-Assemblys und-Projekte zur Validierung  
 Wenn Sie Elemente in das Ebenendiagramm ziehen, werden automatisch Verweise auf die entsprechenden .NET-Assemblys oder Projekte hinzugefügt der **Ebenenverweise** Ordner im Modellierungsprojekt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können weitere .NET-Assemblys und -Projekte zur Validierung hinzufügen, ohne diese manuell in das Ebenendiagramm zu ziehen.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Modellierungsprojekts oder **Ebenenverweise** Ordner, und klicken Sie dann auf **Verweis hinzufügen**.  
  
2.  In der **Verweis hinzufügen** Dialogfeld Wählen Sie die Assemblys oder Projekte, und klicken Sie dann auf **OK**.  
  
##  <a name="ValidateManually"></a> Code manuell überprüfen  
 Wenn Sie ein geöffnetes Ebenendiagramm, das mit Projektmappenelementen verknüpft ist haben, können Sie Ausführen den **überprüfen** Kurzbefehl aus dem Diagramm. Sie können auch die Eingabeaufforderung verwenden, zum Ausführen der **Msbuild** -Befehl mit der **ValidateArchitecture** benutzerdefinierte Eigenschaft, die auf **"true"**. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.  
  
#### <a name="to-validate-code-from-an-open-layer-diagram"></a>So überprüfen Sie Code in einem geöffneten Ebenendiagramm  
  
1.  Mit der rechten Maustaste in der Diagrammoberfläche, und klicken Sie dann auf **Architektur überprüfen**.  
  
    > [!NOTE]
    >  In der Standardeinstellung die **Buildvorgang** auf die Ebenendiagrammdatei (.layerdiagram)-Eigenschaftensatz auf **überprüfen** , damit das Diagramm in den Validierungsprozess eingeschlossen wird.  
  
     Die **Fehlerliste** Fenster zeigt alle auftretenden Fehler. Weitere Informationen zu Validierungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).  
  
2.  Um die Quelle der einzelnen Fehler anzuzeigen, doppelklicken Sie auf den Fehler in der **Fehlerliste** Fenster.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zeigt möglicherweise anstelle der Quelle des Fehlers eine Code Map an. Dies ist der Fall, wenn der Code eine Abhängigkeit von einer Assembly enthält, die nicht im Ebenendiagramm angegeben ist, oder wenn im Code eine im Ebenendiagramm angegebene Abhängigkeit fehlt. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu codezuordnungen finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Verwalten von Fehlern finden Sie unter [Validierungsfehler verwalten](#ManageErrors).  
  
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
  
     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], finden Sie unter [MSBuild](../msbuild/msbuild.md) und [MSBuild-Aufgabe](../msbuild/msbuild-task.md).  
  
   Weitere Informationen zu Validierungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a> Validierungsfehler verwalten  
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../includes/esprfound-md.md)] ein Arbeitselement zu protokollieren.  
  
> [!WARNING]
>  Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>So erstellen Sie ein Arbeitselement für einen Validierungsfehler  
  
- In der **Fehlerliste** Fenster mit der rechten Maustaste in des Fehlers, zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten.  
  
  Mit diesen Tasks können Validierungsfehler im der **Fehlerliste** Fenster:  
  
|**Aktion**|**Gehen Sie folgendermaßen vor**|  
|------------|----------------------------|  
|Unterdrücken von ausgewählten Fehlern während der Validierung|Mit der rechten Maustaste in die eine oder mehrere ausgewählte Fehler, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückte Fehler werden in einer SUPPRESSIONS-Datei für die entsprechende Ebenendiagrammdatei nachverfolgt.|  
|Beenden der Unterdrückung von ausgewählten Fehlern|Mit der rechten Maustaste den oder die ausgewählten unterdrückten Fehler, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Fehler nicht mehr unterdrücken**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|  
|Wiederherstellen aller unterdrückten Fehler in der **Fehlerliste** Fenster|Mit der rechten Maustaste an einer beliebigen Stelle der **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Unterdrückte Fehler anzeigen**.|  
|Ausblenden aller unterdrückten Fehler aus der **Fehlerliste** Fenster|Mit der rechten Maustaste an einer beliebigen Stelle der **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Unterdrückte Fehler ausblenden**.|  
  
##  <a name="ValidateAuto"></a> Code automatisch überprüfen  
 Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Team Foundation Build von Ihrem Team verwendet wird, können Sie eine Ebenenvalidierung mit Gated-Check-Ins durchführen, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe erstellen und Überprüfungsfehler mithilfe von Buildberichten sammeln. Erstellen von abgegrenzten Eincheckbuilds finden Sie [verwenden Sie einen Buildprozess mit abgegrenztem Eincheckvorgang zur Überprüfung von Änderungen](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds  
  
-   Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- oder –  
  
1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, das Ebenendiagramm oder Diagramme enthält, und klicken Sie dann auf **Eigenschaften**.  
  
2. In der **Eigenschaften** legen des Modellierungsprojekts **Architektur überprüfen** Eigenschaft **"true"**.  
  
    Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.  
  
3. In **Projektmappen-Explorer**, klicken Sie auf die Ebenendiagrammdatei (.layerdiagram) an, die Sie für die Validierung verwenden möchten.  
  
4. In der **Eigenschaften** Fenster, stellen Sie sicher, dass des Diagramms **Buildvorgang** -Eigenschaftensatz auf **überprüfen**.  
  
    Dadurch wird das Ebenendiagramm in den Validierungsprozess eingeschlossen.  
  
   Verwalten von Fehlern in das Fenster "Fehlerliste" finden Sie unter [Validierungsfehler](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>So überprüfen Sie Code automatisch für einen Team Foundation Build  
  
1. In **Team Explorer**, doppelklicken Sie auf die Builddefinition, und klicken Sie dann auf **Prozess**.  
  
2. Klicken Sie unter **Buildprozessparameter**, erweitern Sie **Kompilierung**, und geben Sie Folgendes in die **MSBuild-Argumente** Parameter:  
  
    `/p:ValidateArchitecture=true`  
  
   Weitere Informationen zu Validierungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors). Weitere Informationen über [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] finden Sie hier:  
  
-   [Erstellen der Anwendung](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Verwenden der Standardvorlage für den Buildprozess](http://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Ändern Sie die älteren Builddefinitionen, die Upgradevorlage.XAML](http://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Anpassen der Buildprozessvorlage](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Überwachen Sie den Fortschritt eines Builds ausgeführt wird](http://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a> Ebenenvalidierungsprobleme  
 In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).  
  
|**Problem**|**Mögliche Ursache**|**Auflösung**|  
|---------------|------------------------|--------------------|  
|Validierungsfehler treten nicht wie erwartet auf.|Die Validierung funktioniert nicht mit Ebenendiagrammen, die aus anderen Ebenendiagrammen im Projektmappen-Explorer kopiert wurden und sich im gleichen Modellierungsprojekt befinden. Ebenendiagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Ebenendiagramm.|Fügen Sie dem Modellierungsprojekt ein neues Ebenendiagramm hinzu.<br /><br /> Kopieren Sie die Elemente aus dem Quellebenendiagramm in das neue Diagramm.|  
  
##  <a name="UnderstandingValidationErrors"></a> Verstehen und Lösen von Ebenenvalidierungsfehlern  
 Beim Überprüfen von Code anhand eines Ebenendiagramms treten Validierungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Überprüfungsfehler können beispielsweise unter folgenden Bedingungen auftreten:  
  
- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.  
  
- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.  
  
  Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.  
  
  Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.  
  
|**Syntax**|**Beschreibung**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* ist ein Artefakt, das einer Ebene im Ebenendiagramm zugeordnet ist.<br /><br /> *ArtifactTypeN* ist der Typ des *ArtifactN*, z. B. eine **Klasse** oder **Methode**, z.B.:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|Der Name eines Namespace.|  
|*LayerNameN*|Der Name einer Ebene im Ebenendiagramm.|  
|*DependencyType*|Der Typ der abhängigkeitsbeziehung zwischen *"Element1"* und *"Element2"*. Z. B. *"Element1"* verfügt über eine **Aufrufe** Beziehung mit *"Element2"*.|  
  
|**Fehlersyntax**|**Fehlerbeschreibung**|  
|----------------------|---------------------------|  
|AV0001: Ungültige Abhängigkeit: *Artifact1*(*ArtifactType1*) --> *Artifact2*(*ArtifactType2*)<br /><br /> Ebenen: *LayerName1*, *LayerName2* &#124; Dependencies: *DependencyType*|*"Element1"* in *LayerName1* sollte keine Abhängigkeit auf *"Element2"* in *LayerName2* da *LayerName1* hat keine direkte Abhängigkeit für *LayerName2*.|  
|AV1001: Ungültiger Namespace: *Artefakt*<br /><br /> Schicht: *LayerName* &#124; Namespace erforderlich: *NamespaceName1* &#124; aktuellen Namespace: *NamespaceName2*|*LayerName* erfordert, dass die zugeordneten Artefakte zu gehören müssen *NamespaceName1*. *Artefakt* befindet sich im *NamespaceName2*, nicht *NamespaceName1*.|  
|AV1002: Hängt von unzulässigem Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Schicht: *LayerName* &#124; Forbidden Namespace: *NamespaceName* &#124; Dependencies: *DependencyType*|*LayerName* erfordert, dass die zugeordneten Artefakte nicht abhängig müssen *NamespaceName*. *"Element1"* kann nicht von abhängen *"Element2"* da *"Element2"* befindet sich im *NamespaceName*.|  
|AV1003: In unzulässigem Namespace: *Artifact*(*ArtifactType*)<br /><br /> Schicht: *LayerName* &#124; Forbidden Namespace: *NamespaceName*|*LayerName* erfordert, dass die zugeordneten Artefakte nicht zu gehören *NamespaceName*. *Artefakt* gehört *NamespaceName*.|  
|AV3001: Fehlender Link: Ebene '*LayerName*"enthält links zu"*Artefakt*", der nicht gefunden werden. Möglicherweise fehlt ein Assemblyverweis.|*LayerName* Verknüpfung mit einem Artefakt, das nicht gefunden werden kann. Ein Link zu einer Klasse kann beispielsweise fehlen, wenn im Modellierungsprojekt ein Verweis auf die Assembly mit der Klasse fehlt.|  
|AV9001: Architektur-Analyse gefunden interne Fehler. Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster.|Weitere Einzelheiten finden Sie im Buildereignisprotokoll oder im Ausgabefenster.|  
  
## <a name="security"></a>Sicherheit  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
