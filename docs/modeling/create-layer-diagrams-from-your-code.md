---
title: "Erstellen von Diagrammen Abhängigkeit aus Ihrem Code | Microsoft Docs"
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
caps.latest.revision: "64"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 2e98b690fb8ba87dabb7fd8aa76a9aa44c613a38
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="create-dependency-diagrams-from-your-code"></a>Erstellen von Diagrammen Abhängigkeit aus Ihrem code
Um das Softwaresystem auf hoher Ebene, die logische Architektur zu visualisieren, erstellen Sie eine *Abhängigkeit Diagramm* in Visual Studio. Um sicherzustellen, dass Ihr Code anhand dieses Aufbaus konsistent bleibt, Überprüfen von Code mit einem Diagramm Abhängigkeit. Sie können die Abhängigkeit Diagramme für Visual c# .NET- und Visual Basic-Projekte erstellen. Welche Versionen von Visual Studio dieses Feature unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Erstellen Sie ein Diagramm Abhängigkeit](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Eine Abhängigkeit Diagramm können Sie die Visual Studio-Projektmappenelemente in logische Gruppen an, die sog. organisieren *Ebenen*. Sie können die Ebenen zum Beschreiben der Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder zum Beschreiben der Hauptkomponenten des Systems verwenden. Jede Ebene kann andere Ebenen enthalten, die ausführlichere Aufgaben beschreiben. Sie können auch angeben, die vorgesehenen oder vorhandenen *Abhängigkeiten* zwischen Ebenen. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Geben Sie die beabsichtigten Abhängigkeiten im Diagramm an, um die Architektursteuerung für den Code beizubehalten, und überprüfen Sie anschließend den Code anhand des Diagramms.  
  
 [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 
  
##  <a name="CreateDiagram"></a>Erstellen Sie ein Diagramm zur Abhängigkeitseigenschaft  
 Bevor Sie eine Abhängigkeit Diagramm erstellen, stellen Sie sicher, dass Ihre Projektmappe ein Modellierungsprojekt enthält. 
  
> [!IMPORTANT]
>  Nicht hinzuzufügen Sie, ziehen Sie oder kopieren Sie ein vorhandene Abhängigkeit Diagramm aus einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an anderer Stelle in der Projektmappe. Dadurch werden die Verweise des ursprünglichen Diagramms beibehalten, auch wenn Sie das Diagramm ändern. Dies verhindert auch das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.  
>   
>  Fügen Sie stattdessen ein neues Abhängigkeit Diagramm das Modellierungsprojekt hinzu. Kopieren Sie die Elemente aus dem Quelldiagramm in das neue Diagramm. Speichern Sie das Modellierungsprojekt und das neue Diagramm der Abhängigkeit.  
  
#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Ein Modellierungsprojekt ein neues Diagramm der Abhängigkeit hinzu  
  
1.  Auf der **Architektur** Menü wählen **neue Abhängigkeit Diagramm**.  
  
2.  Klicken Sie unter **Vorlagen**, wählen Sie **Abhängigkeit Diagramm**.  
  
3.  Benennen Sie das Diagramm.  
  
4.  In **zu Modellierungsprojekt hinzufügen**, navigieren Sie zu, und wählen Sie in der Projektmappe ein vorhandenes Modellierungsprojekt aus.  
  
     - oder -   
  
     Wählen Sie **ein neues Modellierungsprojekt erstellen** der Projektmappe ein neues Modellierungsprojekt hinzu.  
  
    > [!NOTE]
    >  Das Diagramm Abhängigkeit muss in einem Modellierungsprojekt vorhanden sein. Sie können es allerdings mit Elementen an einer beliebigen Stelle in der Projektmappe verknüpfen.  
  
5.  Stellen Sie sicher, dass das Modellierungsprojekt und die Abhängigkeit Diagramm speichern.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Ziehen Sie und legen Sie ab, oder kopieren Sie und fügen Sie ein, aus einer Code Map

1. Generieren einer Code Map für die Projektmappe mit der **Architektur** Menü. 

2. Erwägen Sie eine Code Map-Filters um Projektmappenordner und "Test-Ressourcen" zu entfernen, wenn Sie nur die Abhängigkeiten im Produktcode erzwingen möchten.

3. Entfernen Sie in der generierten Codezuordnung den "Externen" Knoten oder Erweitern Sie ihn zum Anzeigen von externen Assemblys abhängig davon, ob die Namespace-Abhängigkeiten erzwungen werden sollen, und Löschen von nicht erforderlichen Assemblys aus der Code Map. 

4. Erstellen Sie ein neues Abhängigkeit-Diagramm für die Projektmappe mit der **Architektur** Menü

5. Wählen Sie alle Knoten in der Code Map (verwenden Sie _STRG_ + _ein_, oder verwenden Sie die Auswahl Kunststoff Band durch Drücken der _UMSCHALT_ Schlüssel vor dem ziehen, klicken Sie auf und lassen.

6. Drag und Drop, oder eine kopieren und einfügen, die ausgewählten Elemente in das neue Abhängigkeitsüberprüfung-Diagramm. 

7. Dies zeigt die aktuelle app-Architektur. Entscheiden, was die Architektur sein und das Diagramm Abhängigkeit entsprechend ändern.

![Abhängigkeit Diagramm aus einer Code Map generiert](media/dependency-validation-01.png)
  
##  <a name="CreateLayers"></a>Ebenen aus Artefakten erstellen  
 Ebenen können aus Visual Studio-Projektmappenelementen erstellt werden, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Dabei werden Verknüpfungen zwischen den Ebenen und den Elementen automatisch erstellt und im Ebenenvalidierungsprozess berücksichtigt.  
  
 Sie können Ebenen auch mit den Elementen verknüpfen, die die Validierung nicht unterstützen, wie Word-Dokumente oder PowerPoint-Präsentationen, sodass Sie eine Ebene Spezifikationen oder Plänen zuordnen können. Außerdem können Sie Ebenen mit Dateien in Projekten verknüpfen, die für mehrere Apps freigegeben sind. Im Validierungsprozess werden diese Ebenen, die mit generischen Namen wie „Layer 1“ und „Layer 2“ angezeigt werden, jedoch nicht berücksichtigt.  
  
 Um festzustellen, ob ein verknüpftes Element die Validierung unterstützt, öffnen Sie **Ebenen-Explorer** und untersuchen Sie die **unterstützt die Validierung** Eigenschaft des Elements. Finden Sie unter [Verwalten von Links zu Artefakten](#Managing).  
  
|**Aktion**|**Gehen Sie folgendermaßen vor**|  
|------------|----------------------------|  
|Erstellen einer Ebene für ein einzelnes Artefakt|<ol><li>Ziehen Sie das Element im Diagramm Abhängigkeit aus diesen Quellen:<br /><br /> <ul><li>**Projektmappen-Explorer**<br /><br />         Beispiele: Dateien oder Projekte.</li><li>Codezuordnungen<br /><br />         Finden Sie unter [Zuordnen von lösungsübergreifenden Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md) und [mit Code maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Klassenansicht** oder **Objektkatalog**</li></ul><br />     Im Diagramm wird eine Ebene angezeigt und mit dem Artefakt verknüpft.</li><li>Ändern Sie den Namen der Ebene, um die Aufgaben des zugeordneten Codes oder der Artefakte widerzuspiegeln.</li></ol> **Wichtig:** Ziehen der Binärdateien in das Diagramm Abhängigkeit wird nicht automatisch hinzugefügt ihre Verweise dem Modellierungsprojekt. Sie müssen die Binärdateien manuell hinzufügen, die Sie für das Modellierungsprojekt überprüfen möchten. **Das Modellierungsprojekt Binärdateien hinzu** <ol><li>In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Modellierungsprojekt, und wählen Sie dann **vorhandenes Element hinzufügen**.</li><li>In der **vorhandenes Element hinzufügen** (Dialogfeld), navigieren Sie zu den Binärdateien bereitgestellt, wählen Sie sie aus, und wählen Sie dann **OK**.     Die Binärdateien werden im Modellierungsprojekt angezeigt.</li><li>In **Projektmappen-Explorer**, wählen Sie eine binäre Datei, die Sie hinzugefügt haben, und drücken Sie dann die **F4** So öffnen die **Eigenschaften** Fenster.</li><li>Legen Sie für jeder Binärdatei die **Buildvorgang** Eigenschaft **Validate**.</li></ol>|  
|Erstellen einer einzelnen Ebene für alle ausgewählten Artefakte|Ziehen Sie alle Artefakte in das Diagramm Abhängigkeit zur gleichen Zeit.<br /><br /> Im Diagramm wird eine Ebene angezeigt und mit allen Artefakten verknüpft.|  
|Erstellen einer Ebene für jedes ausgewählte Artefakt|Halten Sie die **UMSCHALT** gedrückt, während alle Elemente in das Diagramm Abhängigkeit zur gleichen Zeit ziehen. **Hinweis:** bei Verwendung der **UMSCHALT** Taste, um einen Bereich von Elementen auswählen, lassen Sie die Taste nach dem Auswählen der Artefakte los. Halten Sie sie anschließend erneut gedrückt, wenn Sie die Artefakte in das Diagramm ziehen. <br /><br /> Im Diagramm wird für jedes Artefakt eine Ebene angezeigt und mit den einzelnen Artefakten verknüpft.|  
|Hinzufügen eines Artefakts zu einer Ebene|Ziehen Sie das Artefakt auf die Ebene.|  
|Erstellen einer neuen, nicht verknüpften Ebene|In der **Toolbox**, erweitern Sie die **Abhängigkeit Diagramm** Abschnitt, und ziehen Sie dann eine **Ebene** in das Diagramm Abhängigkeit.<br /><br /> Doppelklicken Sie zum Erstellen mehrerer Ebenen auf das Tool. Wenn Sie fertig sind, wählen Sie die **Zeiger** Tool oder drücken Sie die **ESC** Schlüssel.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für das Diagramm Abhängigkeit, wählen Sie **hinzufügen**, und wählen Sie dann **Ebene**.|  
|Erstellen geschachtelter Ebenen|Ziehen Sie eine vorhandene Ebene auf eine andere Ebene.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für eine Ebene, wählen Sie **hinzufügen**, und wählen Sie dann **Ebene**.|  
|Erstellen einer neuen Ebene, die mehrere vorhandene Ebenen enthält|Wählen Sie die Ebenen, öffnen Sie das Kontextmenü für die Auswahl, und wählen Sie dann **Gruppe**.|  
|Ändern der Farbe einer Ebene|Legen Sie dessen **Farbe** Eigenschaft, um die gewünschte Farbe fest.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene **verboten Namespace Abhängigkeiten** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
 Die Zahl auf einer Ebene gibt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch Folgendes, wenn Sie diese Zahl lesen:  
  
-   Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.  
  
     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.  
  
-   Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.  
  
##  <a name="Managing"></a>Links zwischen Ebenen und Artefakten verwalten  
  
1.  Im Diagramm Abhängigkeit, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **Links anzeigen**.  
  
     **Ebenen-Explorer** werden die Artefaktlinks für die ausgewählte Ebene.  
  
2.  Verwenden Sie zum Verwalten dieser Links die folgenden Aufgaben:  
  
|**Aktion**|**Im Ebenen-Explorer**|  
|------------|---------------------------|  
|Löschen des Links zwischen der Ebene und einem Artefakt|Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **löschen**.|  
|Verschieben des Links von einer Ebene auf eine andere Ebene|Ziehen Sie den Artefaktlink auf eine Ebene im Diagramm.<br /><br /> - oder -<br /><br /> 1.  Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **Ausschneiden**.<br />2.  Im Diagramm Abhängigkeit, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **einfügen**.|  
|Kopieren des Links von einer Ebene auf eine andere Ebene|1.  Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **Kopie**.<br />2.  Im Diagramm Abhängigkeit, öffnen Sie das Kontextmenü für die Ebene, und wählen Sie dann **einfügen**.|  
|Erstellen einer neuen Ebene aus einem vorhandenen Artefaktlink|Ziehen Sie den Artefaktlink in einen leeren Bereich des Diagramms.|  
|Stellen Sie sicher, dass ein verknüpftes Artefakt die Validierung anhand des Diagramms für die Abhängigkeitseigenschaft unterstützt wird.|Betrachten Sie die **unterstützt die Validierung** Spalte nach dem Artefaktlink.|  
  
##  <a name="Discovering"></a>Vorhandene Abhängigkeiten Rückentwicklung  
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Bei vorhandenen Abhängigkeiten von Artefakten, die mit Ebenen des Diagramms verknüpft sind, ist eine Rückentwicklung möglich.  
  
> [!NOTE]
>  Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um der Artefakte mit Abhängigkeiten anzuzeigen, dass Sie Rückentwicklung möglich, öffnen Sie das Kontextmenü für eine oder mehrere Ebenen aus, und wählen Sie dann **Links anzeigen**. In **Ebenen-Explorer**, überprüfen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **"false"**.  
  
-   Wählen Sie eine oder mehrere Ebenen, öffnen Sie das Kontextmenü für die ausgewählte Ebene, und wählen Sie dann **Abhängigkeiten generieren**.  
  
 In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.  
  
##  <a name="EditDependencies"></a>Bearbeiten von Ebenen und Abhängigkeiten, um den beabsichtigten Entwurf zu zeigen  
 Um die Änderungen zu beschreiben, die Sie an Ihrem System oder der vorgesehenen Architektur vornehmen möchten, bearbeiten Sie das Diagramm Abhängigkeit:  
  
|**Aktion**|**Führen Sie diese Schritte aus**|  
|------------|-----------------------------|  
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie dessen **Richtung** Eigenschaft.|  
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, wählen Sie die **Zeiger** Tool oder drücken Sie die **ESC** Schlüssel.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene **verboten Namespace Abhängigkeiten** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
##  <a name="EditLayout"></a>Ändern Sie, wie Elemente im Diagramm angezeigt werden  
 Sie können die Größe, Form, Farbe und Position von Ebenen oder die Farbe von Abhängigkeiten ändern, indem Sie ihre Eigenschaften bearbeiten.  
  
##  <a name="Codemaps"></a>Ermitteln von Mustern und Abhängigkeiten in codeübersichten  
 Sie können auch erstellen, beim Erstellen von Diagrammen für die Abhängigkeitseigenschaft, **codezuordnungen**. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe von Projektmappen-Explorer, Klassenansicht oder Objektkatalog können Assemblys, Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weitere Informationen zu Codezuordnungen finden Sie unter den folgenden Themen:  
  
-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Video: Überprüfen Sie Ihre Architektur Abhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Abhängigkeit Diagrammen: Referenz](../modeling/layer-diagrams-reference.md)   
 [Abhängigkeit Diagrammen: Richtlinien](../modeling/layer-diagrams-guidelines.md)   
 [Überprüfen von Code mit der Abhängigkeit-Diagramme](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualisieren von Code](../modeling/visualize-code.md)
