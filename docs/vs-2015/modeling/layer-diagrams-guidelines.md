---
title: 'Ebenendiagramme: Richtlinien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ad85ccb9e58b45b1e6354c7abf0cb5651aa6d92e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58962056"
---
# <a name="layer-diagrams-guidelines"></a>Ebenendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beschreiben Sie die Architektur Ihrer app auf einer hohen Ebene erstellen *Ebenendiagramme* in Visual Studio. Stellen Sie sicher, dass Code und Entwurf konsistent bleiben, indem Sie den Code mit einem Ebenendiagramm validieren. Sie können auch eine Ebenenvalidierung im Buildprozess einschließen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur mit Ebenendiagrammen](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-layer-diagram"></a>Was ist ein Ebenendiagramm?  
 In einem Ebenendiagramm werden wie in einem herkömmlichen Architekturdiagramm die wichtigsten Komponenten oder Funktionseinheiten des Entwurfs sowie ihre Abhängigkeiten identifiziert. Jeder Knoten im Diagramm mit der Bezeichnung eine *Ebene*, stellt eine logische Gruppe von Namespaces, Projekte oder andere Artefakte. Sie können die Abhängigkeiten zeichnen, die im Entwurf vorhanden sein sollen. Anders als bei einem herkömmlichen Architekturdiagramm können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Quellcode den gewünschten Abhängigkeiten entsprechen, die Sie angegeben haben. Indem Sie die Validierung zu einem Bestandteil eines regulären Buildvorgangs in [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] machen, stellen Sie sicher, dass der Programmcode auch in zukünftigen Änderungen mit der Architektur des Systems übereinstimmt. Finden Sie unter [Ebenendiagramme: Reference (Referenz zu UML-Klassendiagrammen)](../modeling/layer-diagrams-reference.md).  
  
##  <a name="Update"></a> So entwerfen oder aktualisieren Sie Ihre app mit Ebenendiagrammen  
 Die folgenden Schritte bieten einen Überblick über die Verwendung von Ebenendiagrammen im Entwicklungsprozess. In späteren Abschnitten dieses Themas werden die einzelnen Schritte ausführlicher beschrieben. Wenn Sie einen neuen Entwurf entwickeln, lassen Sie die Schritte aus, die sich auf vorhandenen Code beziehen.  
  
> [!NOTE]
>  Die Schritte entsprechen ungefähr der tatsächlichen Reihenfolge. Wahrscheinlich werden Sie die Aufgaben überlappend ausführen, die Reihenfolge Ihrer eigenen Situation anpassen und am Anfang jeder Iteration im Projekt nochmals auf die Beschreibung der Schritte zurückkommen.  
  
1.  [Erstellen Sie ein Ebenendiagramm](#Create) für die gesamte Anwendung oder für eine Ebene in der Anwendung.  
  
2.  [Ebenen definieren, um die wichtigsten Funktionsbereiche oder Komponenten darzustellen](#CreateLayers) Ihrer Anwendung. Benennen Sie diese Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Wenn Sie haben eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Lösung können Sie jede Ebene mit einer Auflistung von zuordnen *Artefakte*, z. B. Projekte, Namespaces, Dateien und So weiter.  
  
3.  [Ermitteln Sie die vorhandenen Abhängigkeiten](#Generate) zwischen Ebenen.  
  
4.  [Bearbeiten Sie die Ebenen und Abhängigkeiten](#EditArchitecture) anzuzeigenden der aktualisierten Entwurf, der den Code entsprechend angezeigt werden soll.  
  
5.  [Entwerfen Sie neue Bereiche der Anwendung](#NewAreas) Ebenen erstellen, um die wichtigsten architekturblöcke oder-Komponenten darzustellen, und Definieren von Abhängigkeiten, um anzuzeigen, wie jede Ebene die anderen verwendet.  
  
6.  [Bearbeiten Sie das Layout und die Darstellung des Diagramms](#EditLayout) können Sie es mit Kollegen erörtern.  
  
7.  [Überprüfen Sie den Code anhand des Ebenendiagramms](#Validate) um die Konflikte zwischen dem Code und die Architektur, die Sie benötigen.  
  
8.  [Aktualisieren Sie den Code der neuen Architektur entspricht](#UpdateCode). Führen Sie die Entwicklung und Umgestaltung von Code in Iterationen durch, bis bei der Validierung keine Konflikte auftreten.  
  
9. [Schließen Sie ebenenvalidierung im Buildprozess](#BuildValidation) , stellen Sie sicher, dass der Code weiterhin dem Entwurf entspricht.  
  
##  <a name="Create"></a> Ein Ebenendiagramm erstellen  
 Ein Ebenendiagramm muss in einem Modellierungsprojekt erstellt werden. Sie können einem vorhandenen Modellierungsprojekt ein neues Ebenendiagramm hinzufügen, ein Modellierungsprojekt für das neue Ebenendiagramm erstellen oder ein vorhandenes Ebenendiagramm innerhalb des gleichen Modellierungsprojekts kopieren.  
  
> [!IMPORTANT]
>  Fügen Sie Modellierungsprojekten oder anderen Speicherorten in der Projektmappe keine vorhandenen Ebenendiagramme aus Modellierungsprojekten hinzu, und kopieren bzw. verschieben Sie diese nicht. Ein Ebenendiagramm, das auf diese Weise kopiert wird, weist die gleichen Verweise wie das ursprüngliche Diagramm auf, auch wenn Sie das Diagramm ändern. Dies verhindert das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.  
  
 Finden Sie unter [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="CreateLayers"></a> Definieren Sie Ebenen, um Funktionsbereiche oder Komponenten darzustellen  
 Ebenen stellen logische Gruppen von dar *Artefakte*, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Sie können Ebenen aus Artefakten aus Visual C# .NET- und Visual Basic .NET-Projekten erstellen, oder Sie können Spezifikationen oder Pläne an eine Ebene anfügen, indem Sie Dokumente verknüpfen, z. B. Word-Dateien oder PowerPoint-Präsentationen. Jede Ebene wird im Diagramm als Rechteck angezeigt und gibt Aufschluss über die Anzahl der mit ihr verknüpften Artefakte. Eine Ebene kann geschachtelte Ebenen enthalten, um spezielle Aufgaben zu beschreiben.  
  
 Benennen Sie als allgemeine Richtlinie Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Fügen Sie Artefakte in der gleichen Ebene ein, wenn zwischen ihnen eine enge Abhängigkeit besteht. Wenn die Artefakte getrennt voneinander aktualisiert oder in separaten Anwendungen verwendet werden können, sollten sie auf unterschiedlichen Ebenen eingefügt werden. Informationen zu Ebenenmuster finden Sie auf der Patterns & Practices-Website unter [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Bestimmte Arten von Artefakten können mit Ebenen verknüpft, aber nicht anhand des Ebenendiagramms überprüft werden. Öffnen Sie zum Anzeigen, ob das Artefakt die Validierung unterstützt **Ebenen-Explorer** Untersuchen der **unterstützt die Validierung** Eigenschaft des Artefaktlinks. Finden Sie unter [vorhandene Abhängigkeiten zwischen Ebenen ermitteln](#Generate).  
  
 Bei der Aktualisierung einer nicht vertrauten Anwendung können Sie auch Codezuordnungen erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe des Projektmappen-Explorers können Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weisen Sie diese Codeartefakte Ebenen zu, indem Sie sie aus dem Projektmappen-Explorer in Ebenendiagramme ziehen. Sie können dann Ebenendiagramme verwenden, um den Code zu aktualisieren und ihn mit dem Entwurf konsistent zu halten.  
  
 Thema  
  
-   [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="Generate"></a> Vorhandene Abhängigkeiten zwischen Ebenen ermitteln  
 Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Vorhandene Abhängigkeiten können mittels Reverse Engineering (Zurückentwicklung) ermittelt werden.  
  
> [!NOTE]
>  Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um anzuzeigen, welche Elemente über Abhängigkeiten verfügen, können Sie die Reverse-Engineering, mit der rechten Maustaste in eine oder mehrere Ebenen aus, und klicken Sie dann auf **Links anzeigen**. In **Ebenen-Explorer**, überprüfen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **"false"**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>So entwickeln Sie vorhandene Abhängigkeiten zwischen Ebenen zurück  
  
- Wählen Sie eine Ebene oder mehrere Ebenen, mit der rechten Maustaste in der ausgewählten Ebene, und klicken Sie dann auf **Abhängigkeiten generieren**.  
  
  In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.  
  
##  <a name="EditArchitecture"></a> Bearbeiten von Ebenen und Abhängigkeiten auf den vorgesehenen Entwurf anzeigen  
 Um die die geplanten Änderungen an Ihrem System oder der vorgesehenen Architektur zu beschreiben, verwenden Sie die folgenden Schritte zum Bearbeiten des Ebenendiagramms. Sie können vor dem Erweitern des Codes ggf. auch einige Refactoringänderungen vornehmen, um die Codestruktur zu verbessern. Finden Sie unter [Verbessern der Struktur des Codes](#Improving).  
  
|**Aktion**|**Führen Sie diese Schritte aus**|  
|------------|-----------------------------|  
|Löschen einer unerwünschten Abhängigkeit|Klicken Sie auf die Abhängigkeit, und drücken Sie dann die **löschen**.|  
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie dessen **Richtung** Eigenschaft.|  
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, klicken Sie auf die **Zeiger** Tool, oder drücken Sie die **ESC** Schlüssel.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene des **verboten Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene des **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene des **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|  
  
###  <a name="Improving"></a> Verbessern der Struktur des Codes  
 Umgestaltungsänderungen sind Verbesserungen, die das Verhalten der Anwendung nicht ändern, jedoch zukünftige Änderungen und Erweiterungen des Codes erleichtern. Der Entwurf von gut strukturiertem Code lässt sich leicht in einem Ebenendiagramm abstrakt darstellen.  
  
 Wenn Sie z. B. eine Ebene für jeden Namespace im Code erstellen und die Abhängigkeiten dann zurück entwickeln, sollte die Anzahl unidirektionaler Abhängigkeiten zwischen den Ebenen minimal sein. Wenn Sie ein detailliertes Diagramm mit Klassen oder Methoden als Ebenen zeichnen, sollte das Ergebnis dieselben Merkmale aufweisen.  
  
 Falls dies nicht der Fall ist, sind Änderungen des Codes während seiner Lebensdauer schwieriger, und er eignet sich weniger für die Validierung mithilfe von Ebenendiagrammen.  
  
##  <a name="NewAreas"></a> Entwerfen Sie neue Bereiche der Anwendung  
 Wenn Sie mit der Entwicklung eines neuen Projekts oder eines neuen Bereichs in einem neuen Projekt beginnen, können Sie Ebenen und Abhängigkeiten zeichnen, um die Hauptkomponenten zu identifizieren, bevor Sie mit dem Entwickeln des Codes beginnen.  
  
-   **Zeigen Sie identifizierbare architektonische Muster** in den Ebenendiagrammen an, wenn möglich. Beispielsweise kann ein Ebenendiagramm, das eine Desktopanwendung beschreibt, die Ebenen Präsentation, Domänenlogik und Datenspeicher enthalten. Ein Ebenendiagramm für eine einzelne Funktion in einer Anwendung kann beispielsweise die Ebenen Modell, Ansicht und Controller enthalten. Weitere Informationen zu solchen Mustern finden Sie unter [Patterns & Practices: Anwendungsarchitektur](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Wenn Sie häufig ähnliche Muster entwerfen, erstellen Sie ein benutzerdefiniertes Tool. Finden Sie unter [Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Erstellen Sie ein Codeartefakt für jede Ebene** wie z. B. einen Namespace, Klasse oder Komponente. Dies vereinfacht das Verfolgen des Codes und das Verknüpfen der Codeartefakte mit den Ebenen. Verknüpfen Sie jedes Artefakt mit der entsprechenden Ebene, sobald Sie das Artefakt erstellen.  
  
-   **Sie müssen nicht die meisten Klassen und andere Artefakte mit Ebenen verknüpfen** , da sie zu größeren Artefakten z. B. Namespaces liegen, den Sie bereits mit Ebenen verknüpft haben.  
  
-   **Erstellen Sie ein neues Diagramm für ein neues Feature**. In der Regel sind ein oder mehrere Ebenendiagramme vorhanden, die die gesamte Anwendung beschreiben. Wenn Sie eine neue Funktion in der Anwendung entwerfen, ändern Sie nicht die vorhandenen Diagramme, und fügen Sie ihnen keine Elemente hinzu. Erstellen Sie stattdessen ein eigenes Diagramm, das die neuen Teile des Codes wiedergibt. Das neue Diagramm kann beispielsweise Ebenen für die Präsentation, Domänenlogik und Datenbank der neuen Funktion enthalten.  
  
     Wenn Sie die Anwendung erstellen, wird der Code sowohl anhand des allgemeinen Diagramms als auch anhand des ausführlicheren Funktionsdiagramms überprüft.  
  
##  <a name="EditLayout"></a> Das Layout für die Präsentation und Diskussion bearbeiten  
 Bearbeiten Sie Darstellung und Layout des Diagramms, um die Suche nach Ebenen und Abhängigkeiten sowie Diskussionen mit Teammitgliedern zu vereinfachen. Führen Sie hierzu die folgenden Schritte aus:  
  
-   Ändern der Größe, Formen und Positionen von Ebenen  
  
-   Ändern der Farben von Ebenen und Abhängigkeiten  
  
    -   Wählen Sie eine oder mehrere Ebenen oder Abhängigkeiten, mit der rechten Maustaste und klicken Sie dann auf **Eigenschaften**. In der **Eigenschaften** Fenster Bearbeiten der **Farbe** Eigenschaft.  
  
##  <a name="Validate"></a> Überprüfen Sie den Code anhand des Diagramms  
 Wenn Sie das Diagramm bearbeitet haben, können Sie es jederzeit manuell oder automatisch beim Ausführen eines lokalen Builds oder von [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] anhand des Codes überprüfen.  
  
 Thema  
  
-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Schließen Sie Ebenenvalidierung im Buildprozess](#BuildValidation)  
  
##  <a name="UpdateCode"></a> Aktualisieren Sie den Code, um ihn an die neue Architektur anzupassen  
 Normalerweise treten Fehler auf, wenn Sie den Code zum ersten Mal anhand eines aktualisierten Ebenendiagramms überprüfen. Diese Fehler können mehrere Ursachen haben:  
  
- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.  
  
- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.  
  
  Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Dies ist normalerweise ein iterativer Vorgang. Weitere Informationen zu diesen Fehlern finden Sie unter [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Beim Entwickeln oder Umgestalten des Codes müssen Sie möglicherweise neue Artefakte mit dem Ebenendiagramm verknüpfen. Dies ist jedoch möglicherweise nicht erforderlich, wenn Ebenen z. B. vorhandene Namespaces darstellen und diesen Namespaces mit dem neuen Code lediglich weitere Elemente hinzugefügt werden.  
  
 Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, in [!INCLUDE[esprfound](../includes/esprfound-md.md)] ein Arbeitselement zu protokollieren. Um diese Aufgabe ausführen zu können, finden Sie unter [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="BuildValidation"></a> Schließen Sie ebenenvalidierung im Buildprozess  
 Schließen Sie Ebenenvalidierung in den standardmäßigen Buildprozess der Projektmappe ein, um sicherzustellen, dass zukünftige Änderungen im Code den Ebenendiagrammen entsprechen. Jedes Mal, wenn andere Teammitglieder die Projektmappe erstellen, werden Unterschiede zwischen den Abhängigkeiten im Code und dem Ebenendiagramm als Buildfehler gemeldet. Weitere Informationen zum Einschließen von ebenenvalidierung im Buildprozess finden Sie unter [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)
