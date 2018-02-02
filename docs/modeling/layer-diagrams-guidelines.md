---
title: "Diagramme von Abhängigkeit: Richtlinien | Microsoft Docs"
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 06eec90026054bf8081c1cd1727d6cbfc3f30bbe
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="dependency-diagrams-guidelines"></a>Abhängigkeit Diagrammen: Richtlinien
Beschreiben Sie die Architektur Ihrer app auf hoher Ebene durch Erstellen *Abhängigkeit Diagramme* in Visual Studio. Stellen Sie sicher, dass Ihr Code anhand dieses Aufbaus konsistent bleibt, durch Überprüfen von Code mit einem Diagramm Abhängigkeit. Sie können auch eine Ebenenvalidierung im Buildprozess einschließen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur von Abhängigkeit Diagrammen](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>Was ist ein Diagramm Abhängigkeit?  
 Wie einem herkömmlichen Architekturdiagramm identifiziert ein Diagramm der Abhängigkeit, die wichtigsten Komponenten oder Funktionseinheiten des Entwurfs sowie ihre Abhängigkeiten. Jeder Knoten im Diagramm mit der Bezeichnung eine *Ebene*, stellt eine logische Gruppe von Namespaces, Projekten oder anderen Artefakten dar. Sie können die Abhängigkeiten zeichnen, die im Entwurf vorhanden sein sollen. Anders als bei einem herkömmlichen Architekturdiagramm können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Quellcode den gewünschten Abhängigkeiten entsprechen, die Sie angegeben haben. Indem Sie die Validierung zu einem Bestandteil eines regulären Buildvorgangs in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] machen, stellen Sie sicher, dass der Programmcode auch in zukünftigen Änderungen mit der Architektur des Systems übereinstimmt. Finden Sie unter [Abhängigkeit Diagrammen: Verweis](../modeling/layer-diagrams-reference.md).  
  
##  <a name="Update"></a>So entwerfen oder aktualisieren Sie Ihre app mit Abhängigkeit-Diagramme  
 Die folgenden Schritte bieten einen Überblick über die Vorgehensweise Abhängigkeit Diagramme im Entwicklungsprozess verwenden. In späteren Abschnitten dieses Themas werden die einzelnen Schritte ausführlicher beschrieben. Wenn Sie einen neuen Entwurf entwickeln, lassen Sie die Schritte aus, die sich auf vorhandenen Code beziehen.  
  
> [!NOTE]
>  Die Schritte entsprechen ungefähr der tatsächlichen Reihenfolge. Wahrscheinlich werden Sie die Aufgaben überlappend ausführen, die Reihenfolge Ihrer eigenen Situation anpassen und am Anfang jeder Iteration im Projekt nochmals auf die Beschreibung der Schritte zurückkommen.  
  
1.  [Erstellen Sie ein Diagramm Abhängigkeit](#Create) für die gesamte Anwendung oder für eine Ebene in der Anwendung.  
  
2.  [Ebenen definieren, um die wichtigsten Funktionsbereiche oder Komponenten darzustellen](#CreateLayers) Ihrer Anwendung. Benennen Sie diese Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Haben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung können Sie jede Ebene mit einer Auflistung von zuordnen *Elemente*, z. B. Projekten, Namespaces, Dateien und So weiter.  
  
3.  [Ermitteln Sie die vorhandenen Abhängigkeiten](#Generate) zwischen Ebenen.  
  
4.  [Die Ebenen und Abhängigkeiten bearbeiten](#EditArchitecture) die aktualisierte anzuzeigende entwerfen, dass Sie den Code entsprechen soll.  
  
5.  [Entwerfen Sie neue Bereiche der Anwendung](#NewAreas) von Ebenen erstellen, um die wichtigsten architekturblöcke oder-Komponenten darzustellen und Abhängigkeiten definieren, um zu zeigen, wie jede Ebene die anderen verwendet.  
  
6.  [Bearbeiten Sie das Layout und die Darstellung des Diagramms](#EditLayout) können Sie es mit Kollegen erörtern.  
  
7.  [Überprüfen Sie den Code anhand des Diagramms Abhängigkeit](#Validate) um die Konflikte zwischen dem Code und der erforderlichen Architektur aufzuzeigen.  
  
8.  [Aktualisieren Sie den Code zum Anpassen an die neue Architektur](#UpdateCode). Führen Sie die Entwicklung und Umgestaltung von Code in Iterationen durch, bis bei der Validierung keine Konflikte auftreten.  
  
9. [Schließen Sie ebenenvalidierung im Buildprozess](#BuildValidation) um sicherzustellen, dass der Code weiterhin dem Entwurf entspricht.  
  
##  <a name="Create"></a>Erstellen Sie ein Diagramm zur Abhängigkeitseigenschaft  
 Eine Abhängigkeit Diagramm muss in einem Modellierungsprojekt erstellt werden. Sie können einem vorhandenen Modellierungsprojekt ein neues Diagramm der Abhängigkeit hinzufügen, erstellen ein neues Modellierungsprojekt für das Diagramm Abhängigkeit oder ein vorhandene Abhängigkeit Diagramm innerhalb der gleichen Modellierungsprojekt kopieren.  
  
> [!IMPORTANT]
>  Führen Sie nicht fügen Sie hinzu, ziehen Sie oder kopieren Sie ein vorhandene Abhängigkeit Diagramm aus einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an einen anderen Speicherort in der Projektmappe. Eine Abhängigkeit-Diagramm, die auf diese Weise kopiert werden müssen die gleichen Verweise wie das ursprüngliche Diagramm aus, auch wenn Sie das Diagramm ändern. Dies verhindert das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.  
  
 Finden Sie unter [Abhängigkeit Diagramme erstellen, aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="CreateLayers"></a>Definieren Sie Ebenen, um Funktionsbereiche oder Komponenten darzustellen  
 Ebenen stellen logische Gruppen von dar *Elemente*, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Sie können Ebenen aus Artefakten aus Visual c# und Visual Basic-Projekte erstellen, oder Sie können Spezifikationen oder Pläne an eine Ebene anfügen, indem Sie Dokumente verknüpfen, z. B. Word-Dateien oder PowerPoint-Präsentationen. Jede Ebene wird im Diagramm als Rechteck angezeigt und gibt Aufschluss über die Anzahl der mit ihr verknüpften Artefakte. Eine Ebene kann geschachtelte Ebenen enthalten, um spezielle Aufgaben zu beschreiben.  
  
 Benennen Sie als allgemeine Richtlinie Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Fügen Sie Artefakte in der gleichen Ebene ein, wenn zwischen ihnen eine enge Abhängigkeit besteht. Wenn die Artefakte getrennt voneinander aktualisiert oder in separaten Anwendungen verwendet werden können, sollten sie auf unterschiedlichen Ebenen eingefügt werden. Weitere Informationen zu Ebenenmuster finden Sie auf der Patterns & Practices-Website unter [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Es gibt bestimmte Arten von Artefakten, die Sie mit Ebenen verknüpft, aber, die Validierung anhand des Diagramms Abhängigkeit nicht unterstützt. Um festzustellen, ob das Artefakt die Validierung unterstützt, öffnen Sie **Ebenen-Explorer** Untersuchen der **unterstützt die Validierung** Eigenschaft des Artefaktlinks. Finden Sie unter [vorhandene Abhängigkeiten zwischen Ebenen ermitteln](#Generate).  
  
 Bei der Aktualisierung einer nicht vertrauten Anwendung können Sie auch Codezuordnungen erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe des Projektmappen-Explorers können Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weisen Sie diese Codeartefakte mit den Ebenen durch Ziehen im Projektmappen-Explorer an Abhängigkeit Diagramme. Sie können Abhängigkeit Diagramme klicken Sie dann verwenden, können Sie den Code aktualisieren, und bewahren Sie ihn mit Ihrem Entwurf konsistent.  
  
 Thema  
  
-   [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="Generate"></a>Vorhandene Abhängigkeiten zwischen Ebenen ermitteln  
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Vorhandene Abhängigkeiten können mittels Reverse Engineering (Zurückentwicklung) ermittelt werden.  
  
> [!NOTE]
>  Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um der Artefakte mit Abhängigkeiten anzuzeigen, dass Sie Rückentwicklung möglich, mit der rechten Maustaste eine oder mehrere Ebenen, und klicken Sie dann auf **Links anzeigen**. In **Ebenen-Explorer**, überprüfen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **"false"**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>So entwickeln Sie vorhandene Abhängigkeiten zwischen Ebenen zurück  
  
-   Wählen Sie eine Ebene oder mehrere Ebenen rechten Maustaste auf eine ausgewählte Ebene, und klicken Sie dann auf **Abhängigkeiten generieren**.  
  
 In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.  
  
##  <a name="EditArchitecture"></a>Bearbeiten von Ebenen und Abhängigkeiten, um den beabsichtigten Entwurf zu zeigen  
 Um die Änderungen zu beschreiben, die Sie an Ihrem System oder der vorgesehenen Architektur zu planen, verwenden Sie die folgenden Schritte aus, um das Dependency-Diagramm zu bearbeiten. Sie können vor dem Erweitern des Codes ggf. auch einige Refactoringänderungen vornehmen, um die Codestruktur zu verbessern. Finden Sie unter [Verbessern der Struktur des Codes](#Improving).  
  
|**Aktion**|**Führen Sie diese Schritte aus**|  
|------------|-----------------------------|  
|Löschen einer unerwünschten Abhängigkeit|Klicken Sie auf die Abhängigkeit, und drücken Sie dann die **löschen**.|  
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie dessen **Richtung** Eigenschaft.|  
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, klicken Sie auf die **Zeiger** Tool oder drücken Sie die **ESC** Schlüssel.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene **verboten Namespace Abhängigkeiten** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
###  <a name="Improving"></a>Verbessern der Struktur des Codes  
 Refactoringänderungen sind Verbesserungen, die das Verhalten der Anwendung nicht ändern, jedoch zukünftige Änderungen und Erweiterungen des Codes erleichtern. Gut strukturierter Code verfügt über ein Entwurf, der mit einem Diagramm Abhängigkeit abstrakten einfach ist.  
  
 Wenn Sie z. B. eine Ebene für jeden Namespace im Code erstellen und die Abhängigkeiten dann zurück entwickeln, sollte die Anzahl unidirektionaler Abhängigkeiten zwischen den Ebenen minimal sein. Wenn Sie ein detailliertes Diagramm mit Klassen oder Methoden als Ebenen zeichnen, sollte das Ergebnis dieselben Merkmale aufweisen.  
  
 Wenn dies nicht der Fall ist, wird der Code so ändern Sie während seiner Lebensdauer schwieriger und weniger eignet sich für die Validierung mithilfe von Diagrammen Abhängigkeit.  
  
##  <a name="NewAreas"></a>Entwerfen Sie neue Bereiche der Anwendung  
 Wenn Sie mit der Entwicklung eines neuen Projekts oder eines neuen Bereichs in einem neuen Projekt beginnen, können Sie Ebenen und Abhängigkeiten zeichnen, um die Hauptkomponenten zu identifizieren, bevor Sie mit dem Entwickeln des Codes beginnen.  
  
-   **Zeigen Sie identifizierbare architektonische Muster** in Abhängigkeit Diagrammen, falls möglich. Beispielsweise könnte eine Abhängigkeit-Diagramm, das eine Desktopanwendung beschreibt z. B. Präsentation, Domänenlogik und Datenspeicher enthalten. Eine Abhängigkeit-Diagramm, das eine einzelne innerhalb einer Anwendung Funktion kann die Ebenen z. B. Modell, Ansicht und Controller enthalten. Weitere Informationen zu Muster dieser Art finden Sie unter [Patterns & Practices: Anwendungsarchitektur](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
-   **Erstellen Sie ein Codeartefakt für jede Ebene** z. B. einen Namespace, eine Klasse oder eine Komponente. Dies vereinfacht das Verfolgen des Codes und das Verknüpfen der Codeartefakte mit den Ebenen. Verknüpfen Sie jedes Artefakt mit der entsprechenden Ebene, sobald Sie das Artefakt erstellen.  
  
-   **Sie müssen nicht die meisten Klassen und andere Artefakte mit Ebenen verknüpfen** , da sie zu größeren Artefakten z. B. Namespaces, gehören, die Sie bereits mit Ebenen verknüpft haben.  
  
-   **Erstellen Sie ein neues Diagramm für ein neues Feature**. In der Regel werden ein oder mehrere Abhängigkeit Diagramme, die die gesamte Anwendung beschreiben. Wenn Sie eine neue Funktion in der Anwendung entwerfen, ändern Sie nicht die vorhandenen Diagramme, und fügen Sie ihnen keine Elemente hinzu. Erstellen Sie stattdessen ein eigenes Diagramm, das die neuen Teile des Codes wiedergibt. Das neue Diagramm kann beispielsweise Ebenen für die Präsentation, Domänenlogik und Datenbank der neuen Funktion enthalten.  
  
     Wenn Sie die Anwendung erstellen, wird der Code sowohl anhand des allgemeinen Diagramms als auch anhand des ausführlicheren Funktionsdiagramms überprüft.  
  
##  <a name="EditLayout"></a>Das Layout für die Präsentation und Diskussion bearbeiten  
 Bearbeiten Sie Darstellung und Layout des Diagramms, um die Suche nach Ebenen und Abhängigkeiten sowie Diskussionen mit Teammitgliedern zu vereinfachen. Führen Sie hierzu die folgenden Schritte aus:  
  
-   Ändern der Größe, Formen und Positionen von Ebenen  
  
-   Ändern der Farben von Ebenen und Abhängigkeiten  
  
    -   Wählen Sie eine oder mehrere Ebenen oder Abhängigkeiten mit der rechten Maustaste, und klicken Sie dann auf **Eigenschaften**. In der **Eigenschaften** Fenster Bearbeiten der **Farbe** Eigenschaft.  
  
##  <a name="Validate"></a>Überprüfen Sie den Code anhand des Diagramms  
 Wenn Sie das Diagramm bearbeitet haben, können Sie es jederzeit manuell oder automatisch beim Ausführen eines lokalen Builds oder von [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] anhand des Codes überprüfen.  
  
 Thema  
  
-   [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Schließen Sie Ebenenvalidierung im Buildprozess](#BuildValidation)  
  
##  <a name="UpdateCode"></a>Aktualisieren Sie den Code zum Anpassen an die neue Architektur  
 In der Regel treten beim ersten, Überprüfen von Code anhand einer aktualisierten Abhängigkeit Diagramm. Diese Fehler können mehrere Ursachen haben:  
  
-   Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.  
  
-   Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.  
  
 Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Dies ist normalerweise ein iterativer Vorgang. Weitere Informationen zu diesen Fehlern finden Sie unter [Überprüfen von Code mit der Abhängigkeit Diagramme](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Beim Entwickeln oder des Codes Umgestalten müssen Sie möglicherweise neue Artefakte mit dem Diagramm Abhängigkeit zu verknüpfen. Dies ist jedoch möglicherweise nicht erforderlich, wenn Ebenen z. B. vorhandene Namespaces darstellen und diesen Namespaces mit dem neuen Code lediglich weitere Elemente hinzugefügt werden.  
  
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] eine Arbeitsaufgabe zu protokollieren. Um diese Aufgabe ausführen zu können, finden Sie unter [Überprüfen von Code mit der Abhängigkeit Diagramme](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="BuildValidation"></a>Schließen Sie ebenenvalidierung im Buildprozess  
 Um sicherzustellen, dass zukünftige Änderungen im Code auf die Abhängigkeit Diagramme entsprechen, einschließen von ebenenvalidierung standardmäßigen Buildprozess der Projektmappe. Wenn andere Teammitglieder die Projektmappe zu erstellen, werden keine Unterschiede zwischen den Abhängigkeiten im Code und das Diagramm für die Abhängigkeitseigenschaft als Buildfehler gemeldet. Weitere Informationen zum Einschließen von ebenenvalidierung im Buildprozess finden Sie unter [Überprüfen von Code mit der Abhängigkeit Diagramme](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abhängigkeit Diagrammen: Referenz](../modeling/layer-diagrams-reference.md)   
 [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
