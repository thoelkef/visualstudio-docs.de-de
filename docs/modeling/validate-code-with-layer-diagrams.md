---
title: "Überprüfen von Code mit Abhängigkeitsdiagramme | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 82
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 831452f0c06a42550f64c84e88395ca7a1d3c85e
ms.openlocfilehash: 0c4368d0f88f6f5c508b9945abd89c5e94a53d8a
ms.lasthandoff: 02/22/2017

---
# <a name="validate-code-with-dependency-diagrams"></a>Überprüfen von Code mit Abhängigkeitsdiagramme

**Aktuelles**: finden Sie unter [in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/).

[Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>Gründe für die Verwendung von Abhängigkeitsdiagramme

Um sicherzustellen, dass der Code dem Entwurf nicht widerspricht, können überprüfen Sie Ihren Code mit Abhängigkeitsdiagramme in Visual Studio. Dadurch wird Folgendes ermöglicht:  
  
-   Suchen von Konflikten zwischen Abhängigkeiten im Code und Abhängigkeiten im Diagramm Abhängigkeit.  
  
-   Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind  
  
     Beispielsweise können Sie das Abhängigkeitsdiagramm, um potenzielle architekturänderungen darzustellen, und überprüfen Sie den Code, um die betroffenen Abhängigkeiten finden Sie unter Bearbeiten.  
  
-   Umgestalten oder Migrieren von Code in einen anderen Entwurf  
  
     Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen  
  
 **Anforderungen**  
  
-   Visual Studio  
  
-   Visual Studio auf dem Team Foundation Build-Server, um Code mit Team Foundation Build automatisch zu überprüfen  
  
-   Eine Lösung, die ein Modellierungsprojekt mit einem Abhängigkeitsdiagramm enthält. Diese Abhängigkeitsdiagramm muss mit Artefakten in Visual c# .NET oder Visual Basic-Projekten verknüpft werden, die Sie überprüfen möchten. Finden Sie unter [erstellen Sie Abhängigkeitsdiagramme aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Sie können den Code manuell aus einer geöffneten Abhängigkeitsdiagramm in Visual Studio oder über eine Befehlszeile überprüfen. Sie können Code beim Ausführen von lokalen Builds oder Team Foundation Build auch automatisch überprüfen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur mit Abhängigkeitsdiagramme](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Wenn Sie die Ebenenvalidierung mit Team Foundation Build ausführen möchten, muss auch Visual Studio auf dem Buildserver installiert werden.  
  
-   [Überprüfen Sie, ob ein Element die Validierung unterstützt](#SupportsValidation)  
  
-   [Andere .NET-Assemblys und Projekte zur Validierung einschließen](#IncludeReferences)  
  
-   [Code manuell überprüfen](#ValidateManually)  
  
-   [Code automatisch überprüfen](#ValidateAuto)  
  
-   [Ebenenvalidierungsprobleme](#TroubleshootingValidation)  
  
-   [Verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>Live abhängigkeitsüberprüfung

In dieser Version von Visual Studio abhängigkeitsüberprüfung tritt in Echtzeit und Fehler werden sofort im Fenster Fehlerliste von Visual Studio angezeigt.

* Live-Überprüfung wird für c# und Visual Basic.NET unterstützt. 

* Öffnen Sie die Optionen in der gold-Leiste, die in der Fehlerliste angezeigt wird, um vollständige Lösung Analyse aktivieren bei Verwendung von live abhängigkeitsüberprüfung. 
 - Wenn Sie nicht die architektonischen Probleme in Ihrer Lösung interessiert sind, können Sie diese Leiste gold dauerhaft verwerfen.
 - Wenn Sie die vollständige Lösung Analyse nicht aktivieren, erfolgt die Analyse nur für die Dateien, die bearbeitet wird.<p /> 

* Beim Aktualisieren von Projekten, um live-Überprüfung aktivieren zeigt ein Dialogfeld den Status der Konvertierung.

* Beim Aktualisieren eines Projekts für live abhängigkeitsüberprüfung die Version des NuGet-Paket wird aktualisiert, sodass für alle Projekte gleich, und die höchste Version verwendet wird. 

* Hinzufügen eines neuen Abhängigkeit Validierung Projekt löst ein Projekt aktualisieren. 
  
##  <a name="a-namesupportsvalidationa-see-if-an-item-supports-validation"></a><a name="SupportsValidation"></a>Überprüfen Sie, ob ein Element die Validierung unterstützt  
 Sie können Ebenen mit Websites, Office-Dokumenten, Nur-Text-Dateien und Dateien in Projekten verknüpfen, die von mehreren Apps gemeinsam verwendet werden, jedoch nicht im Validierungsprozess enthalten sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Überprüfungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.  
  
1.  Abhängigkeitsdiagramm, wählen Sie eine oder mehrere Ebenen rechten Maustaste auf die Auswahl, und klicken Sie dann auf **Links anzeigen**.  
  
2.  In **Ebenen-Explorer**, sehen Sie sich die **unterstützt die Validierung** Spalte. Wenn der Wert „false“ ist, wird die Validierung vom Element nicht unterstützt.  
  
##  <a name="a-nameincludereferencesa-include-other-net-assemblies-and-projects-for-validation"></a><a name="IncludeReferences"></a>Andere .NET-Assemblys und Projekte zur Validierung einschließen  
 Beim Ziehen von Elementen auf das Abhängigkeitsdiagramm werden automatisch Verweise auf die entsprechenden Assemblys oder Projekte hinzugefügt der **Ebenenverweise** Ordner im Modellierungsprojekt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Überprüfung analysiert werden. Sie können weitere .NET-Assemblys und Projekte zur Validierung einschließen, ohne sie manuell in das Abhängigkeitsdiagramm ziehen.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Modellierungsprojekts oder den **Ebenenverweise** Ordner, und klicken Sie dann auf **Verweis hinzufügen**.  
  
2.  In der **Verweis hinzufügen** klicken Sie im Dialogfeld Wählen Sie die Assemblys oder Projekte, und klicken Sie dann auf **OK**.  
  
##  <a name="a-namevalidatemanuallya-validate-code-manually"></a><a name="ValidateManually"></a>Code manuell überprüfen  
 Wenn Sie ein Abhängigkeitsdiagramm geöffnet, das mit Projektmappenelementen verknüpft ist haben, können Sie Ausführen der **Validate** Kurzbefehl aus dem Diagramm. Sie können auch die Befehlszeile zum Ausführen der **Msbuild** -Befehl mit der **ValidateArchitecture** benutzerdefinierten-Eigenschaft auf **True**. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>So überprüfen Sie Code aus einer geöffneten Abhängigkeitsdiagramm   
  
1.  Maustaste auf die Diagrammoberfläche, und klicken Sie dann auf **Architektur überprüfen**.  
  
    > [!NOTE]
    >  In der Standardeinstellung die **Buildvorgang** -Eigenschaft auf die Ebenendiagrammdatei (.layerdiagram) Abhängigkeitsdatei auf festgelegt ist **Validate** , damit das Diagramm in den Validierungsvorgang eingeschlossen wird.  
  
     Die **Fehlerliste** Fenster zeigt alle auftretenden Fehler. Weitere Informationen zu Überprüfungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).  
  
2.  Um die Quelle der einzelnen Fehler anzuzeigen, doppelklicken Sie auf den Fehler in der **Fehlerliste** Fenster.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zeigt möglicherweise anstelle der Quelle des Fehlers eine Code Map an. Dies tritt auf, wenn der Code hat eine Abhängigkeit zu einer Assembly, die nicht durch das Abhängigkeitsdiagramm oder der Code fehlt eine Abhängigkeit, die durch das Abhängigkeitsdiagramm angegeben wird. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu codezuordnungen finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Verwalten von Fehlern finden Sie unter [Validierungsfehler verwalten](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>So überprüfen Sie Code an der Eingabeaufforderung  
  
1.  Öffnen Sie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Eingabeaufforderung.  
  
2.  Wählen Sie eine der folgenden Optionen aus:  
  
    -   Wenn Sie Code anhand eines bestimmten Modellierungsprojekts in der Projektmappe überprüfen möchten, führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft aus.  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - ODER  
  
         Navigieren Sie zum Ordner mit der Modellierungsprojektdatei (.modelproj) und das Abhängigkeitsdiagramm Projekt, und führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft:  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   Wenn Sie Code anhand aller Modellierungsprojekte in der Projektmappe überprüfen möchten, führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft aus:  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - ODER  
  
         Navigieren Sie zu einem Projektmappenordner, der ein Modellierungsprojekt mit einem Abhängigkeitsdiagramm enthält, und führen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mit der folgenden benutzerdefinierten Eigenschaft:  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], finden Sie unter [MSBuild](../msbuild/msbuild1.md) und [MSBuild-Aufgabe](../msbuild/msbuild-task.md).  
  
 Weitere Informationen zu Überprüfungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).  
  
###  <a name="a-namemanageerrorsa-manage-validation-errors"></a><a name="ManageErrors"></a>Validierungsfehler verwalten  
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] eine Arbeitsaufgabe zu protokollieren.  
  
> [!WARNING]
>  Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um eine Arbeitsaufgabe zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, eine Arbeitsaufgabe zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>So erstellen Sie ein Arbeitselement für einen Validierungsfehler  
  
-   In der **Fehlerliste** -Fenster mit der rechten Maustaste des Fehlers, zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten.  
  
 Mithilfe dieser Aufgaben können Sie Validierungsfehler im der **Fehlerliste** Fenster:  
  
|**Aktion**|**Gehen Sie folgendermaßen vor**|  
|------------|----------------------------|  
|Unterdrücken von ausgewählten Fehlern während der Validierung|Mit der rechten Maustaste die einem oder mehreren ausgewählten Fehler, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückte Fehler werden in einer suppressions-Datei für die entsprechenden Diagramm Abhängigkeitsdatei nachverfolgt.|  
|Beenden der Unterdrückung von ausgewählten Fehlern|Mit der rechten Maustaste den oder die ausgewählten unterdrückten Fehler, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Fehler nicht mehr unterdrücken**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|  
|Wiederherstellen aller unterdrückten Fehler in der **Fehlerliste** Fenster|Mit der rechten Maustaste die **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Unterdrückte Fehler anzeigen**.|  
|Ausblenden aller unterdrückten Fehler aus der **Fehlerliste** Fenster|Mit der rechten Maustaste die **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Unterdrückte Fehler ausblenden**.|  
  
##  <a name="a-namevalidateautoa-validate-code-automatically"></a><a name="ValidateAuto"></a>Code automatisch überprüfen  
 Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Team Foundation Build von Ihrem Team verwendet wird, können Sie eine Ebenenvalidierung mit Gated-Check-Ins durchführen, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe erstellen und Überprüfungsfehler mithilfe von Buildberichten sammeln. Erstellen von abgegrenzten Eincheckbuilds finden Sie unter [verwenden Sie einen abgegrenzten Eincheckbuild Prozess zur Überprüfung von Änderungen](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds  
  
-   Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- oder –  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, das Abhängigkeitsdiagramm oder Diagramme enthält, und klicken Sie dann auf **Eigenschaften**.  
  
2.  In der **Eigenschaften** legen des Modellierungsprojekts **Architektur überprüfen** -Eigenschaft **True**.  
  
     Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.  
  
3.  In **Projektmappen-Explorer**, klicken Sie auf die Abhängigkeit Ebenendiagrammdatei (.layerdiagram)-Datei, die Sie für die Validierung verwenden möchten.  
  
4.  In der **Eigenschaften** Fenster, stellen Sie sicher, dass des Diagramms **Buildvorgang** -Eigenschaft auf festgelegt ist **überprüfen**.  
  
     Dazu gehören das Abhängigkeitsdiagramm des Validierungsprozesses.  
  
 Verwalten von Fehlern im Fenster Fehlerliste finden Sie unter [Validierungsfehler](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>So überprüfen Sie Code automatisch für einen Team Foundation Build  
  
1.  In **Team Explorer**, doppelklicken Sie auf die Builddefinition, und klicken Sie dann auf **Prozess**.  
  
2.  Klicken Sie unter **Buildprozessparameter**, erweitern Sie **Kompilierung**, und geben Sie Folgendes in die **MSBuild-Argumente** Parameter:  
  
     `/p:ValidateArchitecture=true`  
  
 Weitere Informationen zu Überprüfungsfehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors). Weitere Informationen über [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] finden Sie hier:  
  
-   [Erstellen der Anwendung](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Verwenden der Standardvorlage für den Buildprozess](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Ändern Sie die älteren Builddefinitionen, die auf UpgradeTemplate.xaml basieren](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Anpassen der Buildprozessvorlage](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Überwachen des Status eines ausgeführten Builds](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="a-nametroubleshootingvalidationa-troubleshoot-layer-validation-issues"></a><a name="TroubleshootingValidation"></a>Ebenenvalidierungsprobleme  
 In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter [verstehen und Lösen von Ebenenvalidierungsfehlern](#UnderstandingValidationErrors).  
  
|**Problem**|**Mögliche Ursache**|**Auflösung**|  
|---------------|------------------------|--------------------|  
|Validierungsfehler treten nicht wie erwartet auf.|Validierung funktioniert nicht Abhängigkeitsdiagramme, die aus anderen Diagrammen Abhängigkeit im Projektmappen-Explorer kopiert wurden und in der gleichen Modellierungsprojekt befinden. Abhängigkeitsdiagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Abhängigkeitsdiagramm auf.|Fügen Sie dem Modellierungsprojekt ein neues Abhängigkeitsdiagramm hinzu.<br /><br /> Kopieren Sie die Elemente des Quelldiagramms-Abhängigkeit in das neue Diagramm.|  
  
##  <a name="a-nameunderstandingvalidationerrorsa-understanding-and-resolving-layer-validation-errors"></a><a name="UnderstandingValidationErrors"></a>Verstehen und Lösen von Ebenenvalidierungsfehlern  
 Beim Überprüfen von Code mit einem Abhängigkeitsdiagramm treten Validierungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:  
  
-   Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.  
  
-   Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.  
  
 Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.  
  
 Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.  
  
|**Syntax**|**Beschreibung**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* ist ein Artefakt, das einer Ebene im Diagramm für die Abhängigkeitseigenschaft zugeordnet ist.<br /><br /> *ArtifactTypeN* ist der Typ des *ArtifactN*, wie z. B. ein **Klasse** oder **Methode**, beispielsweise:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|Der Name eines Namespace.|  
|*LayerNameN*|Der Name einer Ebene im Diagramm Abhängigkeit.|  
|*DependencyType*|Der Typ der abhängigkeitsbeziehung zwischen *Artifact1* und *Artifact2*. Beispielsweise *"Element1"* hat ein **Aufrufe** Beziehung mit *Element2*.|  
  
|**Fehler-Syntax**|**Beschreibung**|  
|----------------------|---------------------------|  
|DV0001: **ungültige Abhängigkeit**|Dieses Problem wird gemeldet, wenn ein Codeelement (Namespace, Typ, Member) eine Ebenenverweise ein Codeelement in eine andere Ebene zugeordnet zugeordnet, aber zwischen diesen Schichten im Diagramm Validierung Abhängigkeit, die diese Ebenen enthält keine Abhängigkeit Pfeil angezeigt wird. Dies ist eine einschränkungsverletzung Abhängigkeit.|  
|DV1001: **ungültigen Namespace-Namen**|Dieses Problem wird gemeldet, auf ein Codeelement zugeordnete einer Ebene die Eigenschaft "Namespace-Namen zulässige" nicht den Namespace enthält, in dem dieses Codeelement definiert ist. Dies ist die Benennung einer Verletzung einer Einschränkung. Beachten Sie, dass die Syntax des "Namespace-Namen zulässige" werden eine Liste der Namespaces, in welcher Code zugeordneten Ebene sind, dürfen definiert werden.|  
|DV1002: **Abhängigkeit unreferenceable Namespace**|Dieses Problem wird gemeldet, auf ein Codeelement einer Ebene zugeordnete und verweisen auf einem anderen Codeelement in einem Namespace definiert in der Eigenschaft "Namespace Unreferenceable" die Ebene definiert. Dies ist die Benennung einer Verletzung einer Einschränkung. Beachten Sie, dass die Eigenschaft "Unreferenceable Namespaces" als eine durch Semikolons getrennte Liste der Namespaces definiert, die nicht in dieser Ebene zugeordneten Code-Elemente verwiesen werden soll.|  
|DV1003: **Namespacenamen nicht erlaubt**|Dieses Problem wird gemeldet, auf ein Codeelement zugeordnete einer Ebene die Eigenschaft "Namespace-Namen nicht zulässig" der-Namespace enthält, in dem dieses Codeelement definiert ist. Dies ist die Benennung einer Verletzung einer Einschränkung. Beachten Sie, dass die Eigenschaft "Erlaubt-Namespace-Name" als eine durch Semikolons getrennte Liste der Namespaces definiert ist, in welcher Code dieser Ebene zugeordneten Elemente nicht definiert werden soll.|  
|DV3001: **fehlende Verknüpfung**|Ebene '*LayerName*"verknüpft"*Artefakt*', der nicht gefunden werden. Möglicherweise fehlt ein Assemblyverweis.|*Ebenenname* Verknüpfung mit einem Artefakt, das nicht gefunden werden kann. Ein Link zu einer Klasse kann beispielsweise fehlen, wenn im Modellierungsprojekt ein Verweis auf die Assembly mit der Klasse fehlt.|  
|DV9001: **Architektur Analyse interne Fehler gefunden.**|Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster.|Weitere Einzelheiten finden Sie im Buildereignisprotokoll oder im Ausgabefenster.|  

 
## <a name="see-also"></a>Siehe auch  
 [Überprüfen Sie das System während der Entwicklung](../modeling/validate-your-system-during-development.md)   
 [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   

