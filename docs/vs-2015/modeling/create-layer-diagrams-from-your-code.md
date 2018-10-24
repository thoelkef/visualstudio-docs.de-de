---
title: Erstellen von Ebenendiagrammen aus Ihrem Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 27fb58e0219dd05c623a553c65e577834ee4a05f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833485"
---
# <a name="create-layer-diagrams-from-your-code"></a>Erstellen von Ebenendiagrammen aus Ihrem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die hochrangige, logische-Architektur des Softwaresystems visuell darzustellen, erstellen Sie eine *Ebenendiagramm* in Visual Studio. Um sicherzustellen, dass Code und Entwurf konsistent bleiben, validieren Sie den Code mit einem Ebenendiagramm. Sie können Ebenendiagramme für Visual C# .NET- und Visual Basic. NET-Projekte erstellen. Welche Versionen von Visual Studio dieses Feature unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Erstellen Sie ein Ebenendiagramm](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Ein Ebenendiagramm können Sie die Visual Studio-Projektmappenelemente in logische, abstrakte Gruppen aufgerufen organisieren *Ebenen*. Sie können die Ebenen zum Beschreiben der Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder zum Beschreiben der Hauptkomponenten des Systems verwenden. Jede Ebene kann andere Ebenen enthalten, die ausführlichere Aufgaben beschreiben. Sie können auch angeben, die vorgesehenen oder vorhandenen *Abhängigkeiten* zwischen Ebenen. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Geben Sie die beabsichtigten Abhängigkeiten im Diagramm an, um die Architektursteuerung für den Code beizubehalten, und überprüfen Sie anschließend den Code anhand des Diagramms.  
  
##  <a name="CreateDiagram"></a> Ein Ebenendiagramm erstellen  
 Bevor Sie ein Ebenendiagramm erstellen, vergewissern Sie sich, dass die Projektmappe ein Modellierungsprojekt enthält. Finden Sie unter [Erstellen von UML-Modellierungsprojekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
> [!IMPORTANT]
>  Fügen Sie anderen Modellierungsprojekten oder anderen Speicherorten in der Projektmappe keine vorhandenen Ebenendiagramme aus Modellierungsprojekten hinzu, und kopieren bzw. verschieben Sie diese nicht. Dadurch werden die Verweise des ursprünglichen Diagramms beibehalten, auch wenn Sie das Diagramm ändern. Dies verhindert auch die ordnungsgemäße Funktion der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.  
>   
>  Fügen Sie stattdessen dem Modellierungsprojekt ein neues Ebenendiagramm hinzu. Kopieren Sie die Elemente aus dem Quelldiagramm in das neue Diagramm. Speichern Sie das Modellierungsprojekt und das neue Ebenendiagramm.  
  
#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>So fügen Sie einem Modellierungsprojekt ein neues Ebenendiagramm hinzu  
  
1.  Auf der **Architektur** Menü wählen **neues UML- oder Ebenendiagramm**.  
  
2.  Klicken Sie unter **Vorlagen**, wählen Sie **Ebenendiagramm**.  
  
3.  Benennen Sie das Diagramm.  
  
4.  In **zu Modellierungsprojekt hinzufügen**, navigieren Sie zu, und wählen Sie in der Projektmappe ein vorhandenes Modellierungsprojekt aus.  
  
     - oder -   
  
     Wählen Sie **ein neues Modellierungsprojekt erstellen** auf die Projektmappe ein neues Modellierungsprojekt hinzuzufügen.  
  
    > [!NOTE]
    >  Das Ebenendiagramm muss in einem Modellierungsprojekt vorhanden sein. Sie können es allerdings mit Elementen an einer beliebigen Stelle in der Projektmappe verknüpfen.  
  
5.  Vergewissern Sie sich, dass Sie das Modellierungsprojekt und das Ebenendiagramm gespeichert haben.  
  
##  <a name="CreateLayers"></a> Ebenen aus Artefakten erstellen  
 Ebenen können aus Visual Studio-Projektmappenelementen erstellt werden, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Dabei werden Verknüpfungen zwischen den Ebenen und den Elementen automatisch erstellt und im Ebenenvalidierungsprozess berücksichtigt.  
  
 Sie können Ebenen auch mit den Elementen verknüpfen, die die Validierung nicht unterstützen, wie Word-Dokumente oder PowerPoint-Präsentationen, sodass Sie eine Ebene Spezifikationen oder Plänen zuordnen können. Außerdem können Sie Ebenen mit Dateien in Projekten verknüpfen, die für mehrere Apps freigegeben sind. Im Validierungsprozess werden diese Ebenen, die mit generischen Namen wie „Layer 1“ und „Layer 2“ angezeigt werden, jedoch nicht berücksichtigt.  
  
 Um festzustellen, ob ein verknüpftes Element die Validierung unterstützt, öffnen Sie **Ebenen-Explorer** und untersuchen Sie die **unterstützt die Validierung** -Eigenschaft des Elements. Finden Sie unter [Verwalten von Links zu Artefakten](#Managing).  
  
|**Aktion**|**Gehen Sie folgendermaßen vor**|  
|------------|----------------------------|  
|Erstellen einer Ebene für ein einzelnes Artefakt|<ol><li>Ziehen Sie das Element aus diesen Quellen in das Ebenendiagramm:<br /><br /> <ul><li>**Projektmappen-Explorer**<br /><br />         Beispiele: Dateien oder Projekte.</li><li>Codezuordnungen<br /><br />         Finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md) und [Verwenden von Code maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Klassenansicht** oder **Objektkatalog**</li></ul><br />     Im Diagramm wird eine Ebene angezeigt und mit dem Artefakt verknüpft.</li><li>Ändern Sie den Namen der Ebene, um die Aufgaben des zugeordneten Codes oder der Artefakte widerzuspiegeln.</li></ol> **Wichtig:** durch Ziehen der Binärdateien in das Ebenendiagramm werden nicht automatisch hinzugefügt ihre Verweise dem Modellierungsprojekt. Sie müssen die Binärdateien manuell hinzufügen, die Sie für das Modellierungsprojekt überprüfen möchten. **Das Modellierungsprojekt Binärdateien hinzu** <ol><li>In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Modellierungsprojekt aus, und wählen Sie dann **vorhandenes Element hinzufügen**.</li><li>In der **vorhandenes Element hinzufügen** navigieren Sie zu den Binärdateien bereitgestellt, wählen Sie sie aus und wählen Sie dann im Dialogfeld **OK**.     Die Binärdateien werden im Modellierungsprojekt angezeigt.</li><li>In **Projektmappen-Explorer**, wählen Sie eine binäre Datei, die Sie hinzugefügt haben, und drücken Sie dann die **F4** zum Öffnen der **Eigenschaften** Fenster.</li><li>Legen Sie für jeder Binärdatei die **Buildvorgang** Eigenschaft **überprüfen**.</li></ol>|  
|Erstellen einer einzelnen Ebene für alle ausgewählten Artefakte|Ziehen Sie alle Artefakte gleichzeitig in das Ebenendiagramm.<br /><br /> Im Diagramm wird eine Ebene angezeigt und mit allen Artefakten verknüpft.|  
|Erstellen einer Ebene für jedes ausgewählte Artefakt|Halten Sie die **UMSCHALT** gedrückt, während Sie alle Artefakte gleichzeitig in das Ebenendiagramm ziehen. **Hinweis:** bei Verwendung der **UMSCHALT** -Taste, um einen Bereich von Elementen auswählen, lassen Sie die Taste aus, nachdem Sie die Elemente ausgewählt. Halten Sie sie anschließend erneut gedrückt, wenn Sie die Artefakte in das Diagramm ziehen. <br /><br /> Im Diagramm wird für jedes Artefakt eine Ebene angezeigt und mit den einzelnen Artefakten verknüpft.|  
|Hinzufügen eines Artefakts zu einer Ebene|Ziehen Sie das Artefakt auf die Ebene.|  
|Erstellen einer neuen, nicht verknüpften Ebene|In der **Toolbox**, erweitern Sie die **Ebenendiagramm** aus, und ziehen Sie dann eine **Ebene** in das Ebenendiagramm.<br /><br /> Doppelklicken Sie zum Erstellen mehrerer Ebenen auf das Tool. Wenn Sie fertig sind, wählen Sie die **Zeiger** Tool, oder drücken Sie die **ESC** Schlüssel.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für das Ebenendiagramm, und wählen **hinzufügen**, und wählen Sie dann **Ebene**.|  
|Erstellen geschachtelter Ebenen|Ziehen Sie eine vorhandene Ebene auf eine andere Ebene.<br /><br /> - oder -<br /><br /> Öffnen Sie das Kontextmenü für eine Ebene, und wählen **hinzufügen**, und wählen Sie dann **Ebene**.|  
|Erstellen einer neuen Ebene, die mehrere vorhandene Ebenen enthält|Wählen Sie die Ebenen, öffnen Sie das Kontextmenü für die Auswahl, und wählen Sie dann **Gruppe**.|  
|Ändern der Farbe einer Ebene|Legen Sie dessen **Farbe** Eigenschaft, um die gewünschte Farbe fest.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene des **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene des **verboten Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene des **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
 Die Zahl auf einer Ebene gibt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch Folgendes, wenn Sie diese Zahl lesen:  
  
-   Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.  
  
     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.  
  
-   Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.  
  
##  <a name="Managing"></a> Verwalten von Links zwischen Ebenen und Artefakten  
  
1.  Öffnen Sie das Kontextmenü für die Ebene im Ebenendiagramm, und wählen Sie dann **Links anzeigen**.  
  
     **Ebenen-Explorer** werden die Artefaktlinks für die ausgewählte Ebene.  
  
2.  Verwenden Sie zum Verwalten dieser Links die folgenden Aufgaben:  
  
|**Aktion**|**Im Ebenen-Explorer**|  
|------------|---------------------------|  
|Löschen des Links zwischen der Ebene und einem Artefakt|Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **löschen**.|  
|Verschieben des Links von einer Ebene auf eine andere Ebene|Ziehen Sie den Artefaktlink auf eine Ebene im Diagramm.<br /><br /> - oder -<br /><br /> 1.  Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **Ausschneiden**.<br />2.  Öffnen Sie das Kontextmenü für die Ebene im Ebenendiagramm, und wählen Sie dann **einfügen**.|  
|Kopieren des Links von einer Ebene auf eine andere Ebene|1.  Öffnen Sie das Kontextmenü für den Artefaktlink, und wählen Sie dann **Kopie**.<br />2.  Öffnen Sie das Kontextmenü für die Ebene im Ebenendiagramm, und wählen Sie dann **einfügen**.|  
|Erstellen einer neuen Ebene aus einem vorhandenen Artefaktlink|Ziehen Sie den Artefaktlink in einen leeren Bereich des Diagramms.|  
|Überprüfen, ob ein verknüpftes Artefakt die Validierung anhand des Ebenendiagramms unterstützt|Sehen Sie sich die **unterstützt die Validierung** Spalte für den Artefaktlink.|  
  
##  <a name="Discovering"></a> Vorhandene Reverse-Engineering-Abhängigkeiten  
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Bei vorhandenen Abhängigkeiten von Artefakten, die mit Ebenen des Diagramms verknüpft sind, ist eine Rückentwicklung möglich.  
  
> [!NOTE]
>  Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um anzuzeigen, welche Elemente über Abhängigkeiten verfügen, können Sie die Reverse-Engineering, öffnen Sie das Kontextmenü für eine oder mehrere Ebenen aus, und wählen Sie dann **Links anzeigen**. In **Ebenen-Explorer**, überprüfen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **"false"**.  
  
- Wählen Sie eine oder mehrere Ebenen, öffnen Sie das Kontextmenü für die ausgewählte Ebene, und wählen Sie dann **Abhängigkeiten generieren**.  
  
  In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.  
  
##  <a name="EditDependencies"></a> Bearbeiten von Ebenen und Abhängigkeiten auf den vorgesehenen Entwurf anzeigen  
 Um die geplanten Änderungen an Ihrem System oder der vorgesehenen Architektur zu beschreiben, bearbeiten Sie das Ebenendiagramm:  
  
|**Aktion**|**Führen Sie diese Schritte aus**|  
|------------|-----------------------------|  
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie dessen **Richtung** Eigenschaft.|  
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, wählen Sie die **Zeiger** Tool, oder drücken Sie die **ESC** Schlüssel.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene des **verboten Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene des **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene des **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
##  <a name="EditLayout"></a> Ändern Sie, wie Elemente im Diagramm angezeigt werden  
 Sie können die Größe, Form, Farbe und Position von Ebenen oder die Farbe von Abhängigkeiten ändern, indem Sie ihre Eigenschaften bearbeiten.  
  
##  <a name="Codemaps"></a> Ermitteln von Mustern und Abhängigkeiten in einer Code map  
 Beim Erstellen von Ebenendiagrammen können Sie auch erstellen **von code Maps**. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe von Projektmappen-Explorer, Klassenansicht oder Objektkatalog können Assemblys, Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weitere Informationen zu Codezuordnungen finden Sie unter den folgenden Themen:  
  
-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Channel 9-Video: Entwerfen und Überprüfen der Architektur mit Ebenendiagrammen](http://go.microsoft.com/fwlink/?LinkID=252073)   
 [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)   
 [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualisieren von Code](../modeling/visualize-code.md)