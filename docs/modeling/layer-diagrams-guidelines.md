---
title: "Abhängigkeitsdiagramme: Richtlinien | Microsoft-Dokumentation"
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
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 55
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 8233d0d6ce81a0869e99f5baf45b7ef7b3fc9019
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-guidelines"></a>Abhängigkeitsdiagramme: Richtlinien
Beschreiben Sie Ihre app-Architektur auf hoher Ebene durch Erstellen *Abhängigkeitsdiagramme* in Visual Studio. Stellen Sie sicher, dass Code und Entwurf konsistent bleiben, indem Sie Code mit einem Abhängigkeitsdiagramm überprüfen. Sie können auch eine Ebenenvalidierung im Buildprozess einschließen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur mit Abhängigkeitsdiagramme](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>Was ist ein Abhängigkeitsdiagramm?  
 Wie in einem herkömmlichen Architektur identifiziert ein Abhängigkeitsdiagramm an die wichtigsten Komponenten oder Funktionseinheiten des Entwurfs sowie ihre Abhängigkeiten. Jeder Knoten im Diagramm mit der Bezeichnung eine *Ebene*, stellt eine logische Gruppe von Namespaces, Projekten oder anderen Artefakten dar. Sie können die Abhängigkeiten zeichnen, die im Entwurf vorhanden sein sollen. Anders als bei einem herkömmlichen Architekturdiagramm können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Quellcode den gewünschten Abhängigkeiten entsprechen, die Sie angegeben haben. Indem Sie die Validierung zu einem Bestandteil eines regulären Buildvorgangs in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] machen, stellen Sie sicher, dass der Programmcode auch in zukünftigen Änderungen mit der Architektur des Systems übereinstimmt. Finden Sie unter [Abhängigkeitsdiagramme: Verweis](../modeling/layer-diagrams-reference.md).  
  
##  <a name="a-nameupdatea-how-to-design-or-update-your-app-with-dependency-diagrams"></a><a name="Update"></a>So entwerfen oder Aktualisieren Ihrer app mit Abhängigkeitsdiagramme  
 Die folgenden Schritte enthalten eine Übersicht über die Verwendung von Abhängigkeitsdiagramme im Entwicklungsprozess. In späteren Abschnitten dieses Themas werden die einzelnen Schritte ausführlicher beschrieben. Wenn Sie einen neuen Entwurf entwickeln, lassen Sie die Schritte aus, die sich auf vorhandenen Code beziehen.  
  
> [!NOTE]
>  Die Schritte entsprechen ungefähr der tatsächlichen Reihenfolge. Wahrscheinlich werden Sie die Aufgaben überlappend ausführen, die Reihenfolge Ihrer eigenen Situation anpassen und am Anfang jeder Iteration im Projekt nochmals auf die Beschreibung der Schritte zurückkommen.  
  
1.  [Erstellen Sie ein Abhängigkeitsdiagramm](#Create) für die gesamte Anwendung oder für eine Ebene in der Anwendung.  
  
2.  [Ebenen definieren, um die wichtigsten Funktionsbereiche oder Komponenten darzustellen](#CreateLayers) Ihrer Anwendung. Benennen Sie diese Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Wenn noch ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Lösung können Sie jede Ebene zuordnen, mit einer Auflistung von *Elemente*, z. B. Projekten, Namespaces, Dateien usw..  
  
3.  [Ermitteln Sie die vorhandenen Abhängigkeiten](#Generate) zwischen Ebenen.  
  
4.  [Bearbeiten Sie die Ebenen und Abhängigkeiten](#EditArchitecture) an den aktualisierten Entwurf, der Sie den Code entsprechen soll.  
  
5.  [Entwerfen Sie neue Bereiche der Anwendung](#NewAreas) durch Erstellen von Ebenen, um die wichtigsten architekturblöcke oder-Komponenten darzustellen und Abhängigkeiten definieren, um anzuzeigen, wie jede Ebene die anderen verwendet.  
  
6.  [Bearbeiten Sie das Layout und die Darstellung des Diagramms](#EditLayout) Sie es mit Kollegen erörtern können.  
  
7.  [Überprüfen Sie den Code anhand des Diagramms Abhängigkeit](#Validate) um die Konflikte zwischen dem Code und der erforderlichen Architektur aufzuzeigen.  
  
8.  [Aktualisieren Sie den Code, damit er der neuen Architektur entspricht](#UpdateCode). Führen Sie die Entwicklung und Umgestaltung von Code in Iterationen durch, bis bei der Validierung keine Konflikte auftreten.  
  
9. [Schließen Sie ebenenvalidierung im Buildprozess](#BuildValidation) um sicherzustellen, dass der Code weiterhin dem Entwurf entspricht.  
  
##  <a name="a-namecreatea-create-a-dependency-diagram"></a><a name="Create"></a>Erstellen Sie ein Abhängigkeitsdiagramm  
 Ein Abhängigkeitsdiagramm muss in einem Modellierungsprojekt erstellt werden. Sie können einem vorhandenen Modellierungsprojekt ein neues Abhängigkeitsdiagramm hinzuzufügen, erstellen ein neues Modellierungsprojekt für das Abhängigkeitsdiagramm oder ein vorhandenes Diagramm der Beziehung innerhalb des gleichen Modellierungsprojekts kopieren.  
  
> [!IMPORTANT]
>  Führen Sie nicht fügen Sie hinzu, ziehen Sie oder kopieren Sie ein vorhandene Abhängigkeitsdiagramm aus einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an einen anderen Speicherort in der Projektmappe. Ein Abhängigkeitsdiagramm, die auf diese Weise kopiert wird, müssen die gleichen Verweise wie das ursprüngliche Diagramm auf, selbst wenn Sie das Diagramm ändern. Dies verhindert das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.  
  
 Finden Sie unter [erstellen Sie Abhängigkeitsdiagramme aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="a-namecreatelayersa-define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a>Definieren Sie Ebenen, um Funktionsbereiche oder Komponenten darzustellen  
 Ebenen stellen logische Gruppen von dar *Elemente*, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Sie können Ebenen aus Artefakten aus Visual C# .NET- und Visual Basic .NET-Projekten erstellen, oder Sie können Spezifikationen oder Pläne an eine Ebene anfügen, indem Sie Dokumente verknüpfen, z. B. Word-Dateien oder PowerPoint-Präsentationen. Jede Ebene wird im Diagramm als Rechteck angezeigt und gibt Aufschluss über die Anzahl der mit ihr verknüpften Artefakte. Eine Ebene kann geschachtelte Ebenen enthalten, um spezielle Aufgaben zu beschreiben.  
  
 Benennen Sie als allgemeine Richtlinie Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Fügen Sie Artefakte in der gleichen Ebene ein, wenn zwischen ihnen eine enge Abhängigkeit besteht. Wenn die Artefakte getrennt voneinander aktualisiert oder in separaten Anwendungen verwendet werden können, sollten sie auf unterschiedlichen Ebenen eingefügt werden. Weitere Informationen zu Ebenenmuster finden Sie auf der Patterns & Practices-Website unter [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Es gibt bestimmte Arten von Artefakten, die Sie mit Ebenen verknüpft, aber Validierung anhand des Diagramms Abhängigkeit nicht unterstützen. Öffnen Sie zum Anzeigen, ob das Artefakt die Validierung unterstützt **Ebenen-Explorer** Untersuchen der **unterstützt die Validierung** Eigenschaft des Artefaktlinks. Finden Sie unter [vorhandene Abhängigkeiten zwischen Ebenen ermitteln](#Generate).  
  
 Bei der Aktualisierung einer nicht vertrauten Anwendung können Sie auch Codezuordnungen erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe des Projektmappen-Explorers können Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weisen Sie diese Codeartefakte Ebenen durch Ziehen aus dem Projektmappen-Explorer zu Abhängigkeitsdiagramme. Sie können Abhängigkeitsdiagramme dann verwenden, können Sie den Code aktualisieren, und halten Sie es mit dem Entwurf konsistent.  
  
 Thema  
  
-   [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="a-namegeneratea-discover-existing-dependencies-between-layers"></a><a name="Generate"></a>Vorhandene Abhängigkeiten zwischen Ebenen ermitteln  
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Vorhandene Abhängigkeiten können mittels Reverse Engineering (Zurückentwicklung) ermittelt werden.  
  
> [!NOTE]
>  Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um anzuzeigen, welche Elemente abhängig sind, Sie Reverse-Engineering können, mit der rechten Maustaste eine oder mehrere Ebenen, und klicken Sie dann auf **Links anzeigen**. In **Ebenen-Explorer**, untersuchen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>So entwickeln Sie vorhandene Abhängigkeiten zwischen Ebenen zurück  
  
-   Wählen Sie eine Ebene oder mehrere Ebenen rechten Maustaste auf eine ausgewählte Ebene, und klicken Sie dann auf **Abhängigkeiten generieren**.  
  
 In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.  
  
##  <a name="a-nameeditarchitecturea-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a>Bearbeiten von Ebenen und Abhängigkeiten zum Anzeigen des beabsichtigten Entwurfs  
 Um die Änderungen zu beschreiben, die Sie an Ihrem System oder der vorgesehenen Architektur zu planen, verwenden Sie die folgenden Schritte aus, um das Abhängigkeitsdiagramm zu bearbeiten. Sie können vor dem Erweitern des Codes ggf. auch einige Refactoringänderungen vornehmen, um die Codestruktur zu verbessern. Finden Sie unter [Verbessern der Struktur des Codes](#Improving).  
  
|**Aktion**|**Auszuführende Schritte**|  
|------------|-----------------------------|  
|Löschen einer unerwünschten Abhängigkeit|Klicken Sie auf die Abhängigkeit, und drücken Sie dann die **löschen**.|  
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie die **Richtung** Eigenschaft.|  
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, klicken Sie auf die **Zeiger** Tool oder drücken Sie die **ESC** Schlüssel.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene **Forbidden Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
###  <a name="a-nameimprovinga-improving-the-structure-of-the-code"></a><a name="Improving"></a>Verbessern der Struktur des Codes  
 Refactoringänderungen sind Verbesserungen, die das Verhalten der Anwendung nicht ändern, jedoch zukünftige Änderungen und Erweiterungen des Codes erleichtern. Gut strukturierter Code verfügt über einen Entwurf, der leicht in einem Abhängigkeitsdiagramm abstrakt ist.  
  
 Wenn Sie z. B. eine Ebene für jeden Namespace im Code erstellen und die Abhängigkeiten dann zurück entwickeln, sollte die Anzahl unidirektionaler Abhängigkeiten zwischen den Ebenen minimal sein. Wenn Sie ein detailliertes Diagramm mit Klassen oder Methoden als Ebenen zeichnen, sollte das Ergebnis dieselben Merkmale aufweisen.  
  
 Wenn dies nicht der Fall ist, wird der Code so ändern Sie während seiner Lebensdauer schwieriger und weniger eignet sich für die Validierung mithilfe von Abhängigkeitsdiagramme.  
  
##  <a name="a-namenewareasa-design-new-areas-of-your-application"></a><a name="NewAreas"></a>Entwerfen Sie neue Bereiche der Anwendung  
 Wenn Sie mit der Entwicklung eines neuen Projekts oder eines neuen Bereichs in einem neuen Projekt beginnen, können Sie Ebenen und Abhängigkeiten zeichnen, um die Hauptkomponenten zu identifizieren, bevor Sie mit dem Entwickeln des Codes beginnen.  
  
-   **Zeigen Sie identifizierbare architektonische Muster** in Abhängigkeit Diagrammen, falls möglich. Beispielsweise kann ein Abhängigkeitsdiagramm, die eine desktop-Anwendung beschreibt Ebenen Präsentation, Domänenlogik und Datenspeicher enthalten. Ein Abhängigkeitsdiagramm, die eine einzelne in einer Anwendung Funktion möglicherweise die Ebenen Modell, Ansicht und Controller. Weitere Informationen zu solchen Mustern finden Sie unter [Muster & Practices: Application Architecture](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Wenn Sie häufig ähnliche Muster entwerfen, erstellen Sie ein benutzerdefiniertes Tool. Finden Sie unter [Definieren eines benutzerdefinierten modellierungstoolboxelements](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Erstellen Sie ein Codeartefakt für jede Ebene** wie z. B. einen Namespace, eine Klasse oder eine Komponente. Dies vereinfacht das Verfolgen des Codes und das Verknüpfen der Codeartefakte mit den Ebenen. Verknüpfen Sie jedes Artefakt mit der entsprechenden Ebene, sobald Sie das Artefakt erstellen.  
  
-   **Sie müssen nicht die meisten Klassen und andere Artefakte mit Ebenen verknüpfen** , da sie zu größeren Artefakten z. B. Namespaces, gehören, die Sie bereits mit Ebenen verknüpft haben.  
  
-   **Erstellen Sie ein neues Diagramm für eine neue Funktion**. In der Regel werden ein oder mehrere Abhängigkeitsdiagramme, die gesamte Anwendung beschreiben. Wenn Sie eine neue Funktion in der Anwendung entwerfen, ändern Sie nicht die vorhandenen Diagramme, und fügen Sie ihnen keine Elemente hinzu. Erstellen Sie stattdessen ein eigenes Diagramm, das die neuen Teile des Codes wiedergibt. Das neue Diagramm kann beispielsweise Ebenen für die Präsentation, Domänenlogik und Datenbank der neuen Funktion enthalten.  
  
     Wenn Sie die Anwendung erstellen, wird der Code sowohl anhand des allgemeinen Diagramms als auch anhand des ausführlicheren Funktionsdiagramms überprüft.  
  
##  <a name="a-nameeditlayouta-edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a>Das Layout für die Präsentation und Diskussion bearbeiten  
 Bearbeiten Sie Darstellung und Layout des Diagramms, um die Suche nach Ebenen und Abhängigkeiten sowie Diskussionen mit Teammitgliedern zu vereinfachen. Führen Sie hierzu die folgenden Schritte aus:  
  
-   Ändern der Größe, Formen und Positionen von Ebenen  
  
-   Ändern der Farben von Ebenen und Abhängigkeiten  
  
    -   Wählen Sie eine oder mehrere Ebenen oder Abhängigkeiten, mit der rechten Maustaste und klicken Sie dann auf **Eigenschaften**. In der **Eigenschaften** Fenster Bearbeiten der **Farbe** Eigenschaft.  
  
##  <a name="a-namevalidatea-validate-the-code-against-the-diagram"></a><a name="Validate"></a>Überprüfen Sie den Code anhand des Diagramms  
 Wenn Sie das Diagramm bearbeitet haben, können Sie es jederzeit manuell oder automatisch beim Ausführen eines lokalen Builds oder von [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] anhand des Codes überprüfen.  
  
 Thema  
  
-   [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Schließen Sie Ebenenvalidierung im Buildprozess](#BuildValidation)  
  
##  <a name="a-nameupdatecodea-update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a>Aktualisieren Sie den Code, damit er der neuen Architektur entspricht  
 In der Regel treten Fehler beim ersten, Sie Code für ein aktualisiertes Abhängigkeitsdiagramm überprüfen. Diese Fehler können mehrere Ursachen haben:  
  
-   Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.  
  
-   Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.  
  
 Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Dies ist normalerweise ein iterativer Vorgang. Weitere Informationen zu diesen Fehlern finden Sie unter [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Beim Entwickeln oder des Codes Umgestalten müssen Sie möglicherweise neue Artefakte mit dem Abhängigkeitsdiagramm verknüpfen. Dies ist jedoch möglicherweise nicht erforderlich, wenn Ebenen z. B. vorhandene Namespaces darstellen und diesen Namespaces mit dem neuen Code lediglich weitere Elemente hinzugefügt werden.  
  
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] eine Arbeitsaufgabe zu protokollieren. Um diese Aufgabe auszuführen, finden Sie unter [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="a-namebuildvalidationa-include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a>Schließen Sie ebenenvalidierung im Buildprozess  
 Schließen Sie ebenenvalidierung standardmäßigen Buildprozess der Projektmappe, um sicherzustellen, dass zukünftige Änderungen im Code die Abhängigkeitsdiagramme entsprechen. Wenn andere Teammitglieder die Projektmappe zu erstellen, werden keine Unterschiede zwischen den Abhängigkeiten im Code und das Abhängigkeitsdiagramm als Buildfehler gemeldet werden. Weitere Informationen zum Einschließen von ebenenvalidierung im Buildprozess finden Sie unter [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)

