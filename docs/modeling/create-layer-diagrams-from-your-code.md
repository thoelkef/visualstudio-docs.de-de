---
title: "Erstellen Sie Abhängigkeitsdiagramme aus dem Code | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
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
ms.sourcegitcommit: b17d12160920952170d042eb46191df66542c80a
ms.openlocfilehash: e51f32303496d20980d7442458cd35350db01687
ms.lasthandoff: 02/22/2017

---
# <a name="create-dependency-diagrams-from-your-code"></a>Erstellen Sie Abhängigkeitsdiagramme aus dem code
Um das Softwaresystem hochrangige, logische Architektur zu visualisieren, erstellen eine *Abhängigkeitsdiagramm* in Visual Studio. Um sicherzustellen, dass Ihr Code und Entwurf konsistent bleibt, können überprüfen Sie Ihren Code mit einem Abhängigkeitsdiagramm. Sie können Abhängigkeitsdiagramme für Visual c# .NET und Visual Basic-Projekte erstellen. Welche Versionen von Visual Studio dieses Feature unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Erstellen Sie ein Abhängigkeitsdiagramm](~/modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Ein Abhängigkeitsdiagramm können Sie die Visual Studio-Projektmappenelemente in logischen, abstrakten Gruppen, genannt organisieren *Ebenen*. Sie können die Ebenen zum Beschreiben der Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder zum Beschreiben der Hauptkomponenten des Systems verwenden. Jede Ebene kann andere Ebenen enthalten, die ausführlichere Aufgaben beschreiben. Sie können auch angeben, die vorgesehenen oder vorhandenen *Abhängigkeiten* zwischen Ebenen. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Geben Sie die beabsichtigten Abhängigkeiten im Diagramm an, um die Architektursteuerung für den Code beizubehalten, und überprüfen Sie anschließend den Code anhand des Diagramms.  
  
 [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 
  
##  <a name="a-namecreatediagrama-create-a-dependency-diagram"></a><a name="CreateDiagram"></a>Erstellen Sie ein Abhängigkeitsdiagramm  
 Bevor Sie ein Abhängigkeitsdiagramm erstellen, stellen Sie sicher, dass die Projektmappe ein Modellierungsprojekt enthält. 
  
> [!IMPORTANT]
>  Nicht fügen Sie hinzu, ziehen Sie oder kopieren Sie ein vorhandene Abhängigkeitsdiagramm aus einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an anderer Stelle in der Projektmappe. Dadurch werden die Verweise des ursprünglichen Diagramms beibehalten, auch wenn Sie das Diagramm ändern. Dies verhindert auch das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.  
>   
>  Fügen Sie ein neues Abhängigkeitsdiagramm stattdessen dem Modellierungsprojekt. Kopieren Sie die Elemente aus dem Quelldiagramm in das neue Diagramm. Speichern Sie das Modellierungsprojekt und dem neuen Abhängigkeitsdiagramm.  
  
#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Ein Modellierungsprojekt ein neues Abhängigkeitsdiagramm hinzu  
  
1.  Auf der **Architektur** Menü wählen **neues Abhängigkeitsdiagramm**.  
  
2.  Klicken Sie unter **Vorlagen**, wählen Sie **Abhängigkeitsdiagramm**.  
  
3.  Benennen Sie das Diagramm.  
  
4.  In **zu Modellierungsprojekt hinzufügen**, navigieren Sie zu, und wählen Sie in der Projektmappe ein vorhandenes Modellierungsprojekt aus.  
  
     - oder -   
  
     Wählen Sie **ein neues Modellierungsprojekt erstellen** der Projektmappe ein neues Modellierungsprojekt hinzu.  
  
    > [!NOTE]
    >  Das Abhängigkeitsdiagramm muss in einem Modellierungsprojekt vorhanden sein. Sie können es allerdings mit Elementen an einer beliebigen Stelle in der Projektmappe verknüpfen.  
  
5.  Stellen Sie sicher, dass das Modellierungsprojekt und die Abhängigkeitsdiagramm speichern.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Ziehen Sie und legen Sie ab, oder kopieren Sie und aus einer Code Map

1. Generieren Sie eine Code Map für die Projektmappe mit der **Architektur** Menü. 

2. Betrachten Sie eine Code Map-Filters zum Projektmappenordner und "Testobjekte" entfernen, wenn Sie nur die Abhängigkeiten im Produktcode erzwingen möchten.

3. Entfernen Sie in den generierten Code Map des Knotens "External" oder Erweitern Sie, um das Anzeigen von externen Assemblys abhängig davon, ob Sie die Namespace-Abhängigkeiten erzwingen möchten, und löschen Sie nicht erforderliche Assemblys aus dem Code Map. 

4. Erstellen Sie ein neues Abhängigkeitsdiagramm für die Projektmappe mit der **Architektur** Menü

5. Wählt alle Knoten in der Codezuordnung (verwenden Sie _STRG_ + _ein_, oder verwenden Sie die Auswahl lediglich über die _UMSCHALT_ Schlüssel, bevor Sie auf, ziehen und freigeben.

6. Ziehen und ablegen, oder ein kopieren und einfügen, die ausgewählten Elemente in das neue Abhängigkeitsüberprüfung-Diagramm. 

7. Dies zeigt die aktuelle app-Architektur. Entscheiden, was die Architektur, und ändern Sie das Abhängigkeitsdiagramm entsprechend.

![Abhängigkeitsdiagramm aus einer Code Map generiert](~/modeling/media/dependency-validation-01.png)
  
##  <a name="a-namecreatelayersa-create-layers-from-artifacts"></a><a name="CreateLayers"></a>Ebenen aus Artefakten erstellen  
 Ebenen können aus Visual Studio-Projektmappenelementen erstellt werden, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Dabei werden Verknüpfungen zwischen den Ebenen und den Elementen automatisch erstellt und im Ebenenvalidierungsprozess berücksichtigt.  
  
 Sie können Ebenen auch mit den Elementen verknüpfen, die die Validierung nicht unterstützen, wie Word-Dokumente oder PowerPoint-Präsentationen, sodass Sie eine Ebene Spezifikationen oder Plänen zuordnen können. Außerdem können Sie Ebenen mit Dateien in Projekten verknüpfen, die für mehrere Apps freigegeben sind. Im Validierungsprozess werden diese Ebenen, die mit generischen Namen wie „Layer 1“ und „Layer 2“ angezeigt werden, jedoch nicht berücksichtigt.  
  
 Öffnen Sie zum Überprüfen, ob ein verknüpftes Element die Validierung unterstützt, **Ebenen-Explorer** und untersuchen Sie die **unterstützt die Validierung** -Eigenschaft des Elements. Finden Sie unter [Verwalten von Links zu Artefakten](#Managing).  
  
|**Aktion**|**Gehen Sie folgendermaßen vor**|  
|------------|----------------------------|  
|Erstellen einer Ebene für ein einzelnes Artefakt|<ol><li>Ziehen Sie das Element in das Abhängigkeitsdiagramm aus diesen Quellen:<br /><br /> <ul><li>**Projektmappen-Explorer**<br /><br />         Beispiele: Dateien oder Projekte.</li><li>Codezuordnungen<br /><br />         Finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md) und [Verwenden von Code maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Klassenansicht:** oder **Objektbrowser**</li></ul><br />     Im Diagramm wird eine Ebene angezeigt und mit dem Artefakt verknüpft.</li><li>Ändern Sie den Namen der Ebene, um die Aufgaben des zugeordneten Codes oder der Artefakte widerzuspiegeln.</li></ol> **Wichtig:** durch Ziehen der Binärdateien in das Abhängigkeitsdiagramm nicht automatisch hinzugefügt deren Verweise dem Modellierungsprojekt. Sie müssen die Binärdateien manuell hinzufügen, die Sie für das Modellierungsprojekt überprüfen möchten. **Das Modellierungsprojekt Binärdateien hinzu** <ol><li>In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Modellierungsprojekt, und wählen Sie dann **vorhandenes Element hinzufügen**.</li><li>In der **vorhandenes Element hinzufügen** im Dialogfeld auf die Binärdateien, wählen Sie sie aus, und klicken Sie dann **OK**.     Die Binärdateien werden im Modellierungsprojekt angezeigt.</li><li>In **Projektmappen-Explorer**, wählen Sie eine binäre Datei, die Sie hinzugefügt haben, und drücken Sie dann die **F4** zum Öffnen der **Eigenschaften** Fenster.</li><li>Legen Sie für jeder Binärdatei die **Buildvorgang** -Eigenschaft **Validate**.</li></ol>|  
|Erstellen einer einzelnen Ebene für alle ausgewählten Artefakte|Ziehen Sie alle Artefakte in das Abhängigkeitsdiagramm zur gleichen Zeit.<br /><br /> Im Diagramm wird eine Ebene angezeigt und mit allen Artefakten verknüpft.|  
|Erstellen einer Ebene für jedes ausgewählte Artefakt|Halten Sie die **UMSCHALT** gedrückt, während Sie alle Artefakte gleichzeitig Abhängigkeit Diagramm ziehen. **Hinweis:** bei Verwendung der **UMSCHALT** -Taste, um einen Bereich von Elementen auswählen, lassen Sie die Taste nach dem Auswählen der Artefakte los. Halten Sie sie anschließend erneut gedrückt, wenn Sie die Artefakte in das Diagramm ziehen. <br /><br /> Im Diagramm wird für jedes Artefakt eine Ebene angezeigt und mit den einzelnen Artefakten verknüpft.|  
|Hinzufügen eines Artefakts zu einer Ebene|Ziehen Sie das Artefakt auf die Ebene.|  
|Erstellen einer neuen, nicht verknüpften Ebene|In der **Toolbox**, erweitern Sie die **Abhängigkeitsdiagramm** Abschnitt, und ziehen Sie dann eine **Ebene** in das Abhängigkeitsdiagramm.<br /><br /> Doppelklicken Sie zum Erstellen mehrerer Ebenen auf das Tool. Wenn Sie fertig sind, wählen Sie die **Zeiger** Tool oder drücken Sie die **ESC** Schlüssel.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für das Abhängigkeitsdiagramm, wählen **hinzufügen**, und wählen Sie dann **Ebene**.|  
|Erstellen geschachtelter Ebenen|Ziehen Sie eine vorhandene Ebene auf eine andere Ebene.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für eine Ebene, und wählen **hinzufügen**, und wählen Sie dann **Ebene**.|  
|Erstellen einer neuen Ebene, die mehrere vorhandene Ebenen enthält|Wählen Sie die Ebenen, öffnen Sie das Kontextmenü für die Auswahl, und wählen Sie dann **Gruppe**.|  
|Ändern der Farbe einer Ebene|Legen Sie die **Farbe** -Eigenschaft auf die gewünschte Farbe fest.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene **Forbidden Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
 Die Zahl auf einer Ebene gibt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch Folgendes, wenn Sie diese Zahl lesen:  
  
-   Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.  
  
     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.  
  
-   Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.  
  
##  <a name="a-namemanaginga-manage-links-between-layers-and-artifacts"></a><a name="Managing"></a>Verwalten von Links zwischen Ebenen und Artefakten  
  
1.  Das Abhängigkeitsdiagramm, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **Links anzeigen**.  
  
     **Ebenen-Explorer** werden die Artefaktlinks für die ausgewählte Ebene.  
  
2.  Verwenden Sie zum Verwalten dieser Links die folgenden Aufgaben:  
  
|**Aktion**|**Im Ebenen-Explorer**|  
|------------|---------------------------|  
|Löschen des Links zwischen der Ebene und einem Artefakt|Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **löschen**.|  
|Verschieben des Links von einer Ebene auf eine andere Ebene|Ziehen Sie den Artefaktlink auf eine Ebene im Diagramm.<br /><br /> - oder -<br /><br /> 1.  Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **Ausschneiden**.<br />2.  Das Abhängigkeitsdiagramm, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **einfügen**.|  
|Kopieren des Links von einer Ebene auf eine andere Ebene|1.  Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **Kopie**.<br />2.  Das Abhängigkeitsdiagramm, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **einfügen**.|  
|Erstellen einer neuen Ebene aus einem vorhandenen Artefaktlink|Ziehen Sie den Artefaktlink in einen leeren Bereich des Diagramms.|  
|Stellen Sie sicher, dass ein verknüpftes Artefakt die Validierung anhand des Diagramms Abhängigkeit unterstützt.|Sehen Sie sich die **unterstützt die Validierung** Spalte nach dem Artefaktlink.|  
  
##  <a name="a-namediscoveringa-reverse-engineer-existing-dependencies"></a><a name="Discovering"></a>Vorhandene Abhängigkeiten rückentwickeln  
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Bei vorhandenen Abhängigkeiten von Artefakten, die mit Ebenen des Diagramms verknüpft sind, ist eine Rückentwicklung möglich.  
  
> [!NOTE]
>  Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um anzuzeigen, welche Elemente abhängig sind, Sie Reverse-Engineering können, öffnen Sie das Kontextmenü für eine oder mehrere Ebenen aus, und wählen Sie dann **Links anzeigen**. In **Ebenen-Explorer**, untersuchen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **False**.  
  
-   Wählen Sie eine oder mehrere Ebenen, öffnen Sie das Kontextmenü für eine ausgewählte Ebene, und wählen Sie dann **Abhängigkeiten generieren**.  
  
 In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.  
  
##  <a name="a-nameeditdependenciesa-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a>Bearbeiten von Ebenen und Abhängigkeiten zum Anzeigen des beabsichtigten Entwurfs  
 Um die Änderungen zu beschreiben, die Sie an Ihrem System oder der vorgesehenen Architektur zu planen, bearbeiten Sie das Abhängigkeitsdiagramm:  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie die **Richtung** Eigenschaft.|  
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, wählen Sie die **Zeiger** Tool oder drücken Sie die **ESC** Schlüssel.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene **Forbidden Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
##  <a name="a-nameeditlayouta-change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a>Ändern der Anzeige von Elementen im Diagramm  
 Sie können die Größe, Form, Farbe und Position von Ebenen oder die Farbe von Abhängigkeiten ändern, indem Sie ihre Eigenschaften bearbeiten.  
  
##  <a name="a-namecodemapsa-discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a>Ermitteln von Mustern und Abhängigkeiten in codeübersichten  
 Sie können auch erstellen, und erstellen Abhängigkeitsdiagramme, **codezuordnungen**. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe von Projektmappen-Explorer, Klassenansicht oder Objektkatalog können Assemblys, Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weitere Informationen zu Codezuordnungen finden Sie unter den folgenden Themen:  
  
-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)   
 [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualisieren von Code](../modeling/visualize-code.md)

