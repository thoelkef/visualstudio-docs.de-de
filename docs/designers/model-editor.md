---
title: "Modell-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.designer.3dscene"
  - "vs.graphics.modelviewer"
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 36
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 36
---
# Modell-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dokument wird beschrieben, wie Sie mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Model\-Editor 3D\-Modelle anzuzeigen, erstellen und ändern können.  
  
 Sie können den Model\-Editor verwenden, um einfache 3D\-Modelle von Grund auf zu erstellen, oder komplexere 3D\-Modelle, die mithilfe vollwertiger 3D\-Modellierungstools erstellt wurden, anzuzeigen und zu ändern.  Der Model\-Editor unterstützt mehrere 3D\-Modellformate, die in der Entwicklung von DirectX\-Apps verwendet werden.  
  
## Unterstützte Formate  
 Der Model\-Editor unterstützt folgende Modellformate:  
  
|Formatname|Dateierweiterung|Unterstützte Vorgänge \(Anzeigen, Bearbeiten, Erstellen\)|  
|----------------|----------------------|---------------------------------------------------------------|  
|AutoDesk\-FBX\-Austauschdatei|FBX|Anzeigen, Bearbeiten, Erstellen|  
|Collada DAE\-Datei|DAE|Anzeigen, Bearbeiten \(Änderungen an Collada DAE\-Dateien werden im FBX\-Format gespeichert\).|  
|OBJ|OBJ|Anzeigen, Bearbeiten \(Änderungen an OBJ\-Dateien werden im FBX\-Format gespeichert\).|  
  
## Erste Schritte  
 In diesem Abschnitt wird beschrieben, wie Sie Ihrem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt ein 3D\-Modell hinzufügen. Außerdem erhalten Sie grundlegende Informationen über die ersten Schritte bei der Erstellung von 3D\-Modellen.  
  
#### So fügen Sie Ihrem Projekt ein 3D\-Modell hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü des Projekts, zu dem Sie das Bild hinzufügen möchten, und wählen Sie dann **Hinzufügen** und **Neues Element** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Installiert** die Option **Grafiken** und anschließend **3D\-Szene \(.fbx\)** aus.  
  
3.  Geben Sie den **Namen** der Modelldatei und den **Speicherort** an, in dem sie erstellt werden soll.  
  
4.  Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
### Achsenausrichtung  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt jede Ausrichtung der 3D\-Achse und lädt Informationen zur Achsenausrichtung aus den unterstützten Modelldateiformaten.  Wird keine Achsenausrichtung angegeben, verwendet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] standardmäßig das rechtshändige Koordinatensystem.  Der **Achsenindikator** zeigt die aktuelle Achsenausrichtung in der rechten unteren Ecke der Entwurfsoberfläche an.  Der **Achsenindikator** stellt die X\-Achse in Rot dar, die y\-Achse in Grün und die z\-Achse in Blau.  
  
### Erste Schritte bei der Erstellung eines 3D\-Modells  
 Im Modell\-Editor wird jedes neue Objekt zuerst immer in einer der grundlegenden 3D\-Formen \(*Primitive*\) erstellt, die in den Modell\-Editor integriert sind.  Fügen Sie der Szene ein Primitiv hinzu, um neue und eindeutige Objekte zu erstellen, und ändern Sie dann dessen Form durch Verschieben der Scheitelpunkte.  Bei komplexen Formen können Sie zusätzliche Scheitelpunkte hinzufügen, indem Sie Extrusionen oder Unterteilungen verwenden und diese dann ändern.  Unter [3D-Objekte erstellen und Importieren](#Adding3DObjects) finden Sie Informationen, wie Sie ein Primitiv\-Objekt zu Ihrer Szene hinzufügen.  Unter [Freies Ändern von Objekten auf der Zeichenfläche](#ModifyingObjects) finden Sie Informationen, wie Sie weitere Scheitelpunkte zu einem Objekt hinzufügen.  
  
## Arbeiten mit dem Model\-Editor  
 In den folgenden Abschnitten wird beschrieben, wie Sie den Model\-Editor für die Arbeit mit 3D\-Modellen verwenden können.  
  
### Symbolleisten des Model\-Editors  
 Die Symbolleisten des Model\-Editors enthalten Befehle, die Ihnen die Arbeit mit 3D\-Modellen erleichtern.  
  
 Befehle, die den Zustand des Model\-Editors beeinflussen, finden Sie auf der Symbolleiste **Model\-Editor\-Modus** im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Hauptfenster.  Modellierungstools und vorbereitete Befehle befinden sich auf der Symbolleiste **Model\-Editor** der Entwurfsoberfläche des Model\-Editors.  
  
 Die Symbolleiste **Model\-Editor\-Modus**:  
  
 ![Gebundene Symbolleiste des Modell&#45;Viewers](../designers/media/digit-mre-modal-toolbar.png "Digit\-MRE\-Modal\-Toolbar")  
  
 In dieser Tabelle werden die Elemente der Symbolleiste **Model\-Editor\-Modus** beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von links nach rechts angezeigt werden.  
  
|Element der Symbolleiste|Beschreibung|  
|------------------------------|------------------|  
|**Auswählen**|Ermöglicht, abhängig vom aktiven Auswahlmodus, das Auswählen von Punkten, Rändern, Flächen oder Objekten in der Szene.|  
|**Schwenken**|Ermöglicht das Bewegen einer 3D\-Szene relativ zum Fensterrahmen.  Wählen Sie zum Schwenken einen Punkt in der Szene aus und verschieben Sie ihn.<br /><br /> Im **Auswahl**\-Modus können Sie den **Schwenken**\-Modus durch Gedrückthalten der STRG\-TASTE vorübergehend aktivieren.|  
|**Zoom**|Ermöglicht das Anzeigen von mehr oder weniger Szenendetails relativ zum Fensterrahmen.  Wählen Sie im **Zoom**\-Modus einen Punkt in der Szene aus und verschieben Sie ihn; zum Vergrößern nach rechts oder nach unten, und zum Verkleinern nach links oder nach oben.<br /><br /> Im **Auswählen**\-Modus können Sie zum Vergrößern oder Verkleinern das Mausrad verwenden. Drücken Sie dazu gleichzeitig STRG.|  
|**Orbit**|Positioniert die Ansicht auf einem kreisförmigen Pfad um das ausgewählte Objekt.  Ist kein Objekt ausgewählt, wird der Pfad auf den Szenenursprung zentriert. **Note:**  Dieser Modus hat keine Auswirkungen, wenn die Projektionsoption **Orthografisch** aktiviert ist.|  
|**WorldLocal**|Ist dieses Element aktiviert, werden Transformationen am ausgewählten Objekt im Welt\-Raum umgesetzt.  Andernfalls werden Transformationen am ausgewählten Objekt in lokalem Raum umgesetzt.|  
|**Pivot\-Modus**|Ist dieses Element aktiviert, beeinflussen Transformationen den Ort und die Ausrichtung des *Pivotpunkts* des ausgewählten Objekts \(der Pivotpunkt definiert den Mittelpunkt der Verschiebungs\-, der Skalierungs\- und der Drehungsvorgänge.\) Andernfalls beeinflussen Transformationen den Ort und die Ausrichtung der Geometrie des Objekts relativ zum Pivotpunkt.|  
|**X\-Achse sperren**|Beschränkt die Bearbeitung des Objekts auf die X\-Achse.  Gilt nur bei Verwendung des mittleren Teils des Manipulator\-Widgets.|  
|**Y\-Achse sperren**|Beschränkt die Bearbeitung des Objekts auf die Y\-Achse.  Gilt nur bei Verwendung des mittleren Teils des Manipulator\-Widgets.|  
|**Z\-Achse sperren**|Beschränkt die Bearbeitung des Objekts auf die Z\-Achse.  Gilt nur bei Verwendung des mittleren Teils des Manipulator\-Widgets.|  
|**Rahmenobjekt**|Rahmt das ausgewählte Objekt ein, sodass es sich in der Mitte der Ansicht befindet.|  
|**Ansicht**|Legt die Ausrichtung der Ansicht fest.  Im Folgenden finden Sie die verfügbaren Ausrichtungen:<br /><br /> **Front**<br /> Positioniert die Ansicht vor der Szene.<br /><br /> **Back**<br /> Positioniert die Ansicht hinter die Szene.<br /><br /> **Links**<br /> Positioniert die Ansicht links von der Szene.<br /><br /> **Right**<br /> Positioniert die Ansicht rechts von der Szene.<br /><br /> **Top**<br /> Positioniert die Ansicht über der Szene.<br /><br /> **Bottom**<br /> Positioniert die Ansicht unter der Szene. **Note:**  Das ist die einzige Möglichkeit, die Ansichtsrichtung zu ändern, wenn die Projektionsoption **Orthografisch** aktiviert ist.|  
|**Projection**|Legt die Projektionsart fest, die zum Zeichnen der Szene verwendet wird.  Im Folgenden finden Sie die verfügbaren Projektionsarten:<br /><br /> **Perspektive**<br /> In der perspektivischen Projektion erscheinen weiter vom Blickpunkt entfernte Objekte kleiner und laufen letztendlich in der Entfernung zu einem Punkt zusammen.<br /><br /> **Orthografisch**<br /> In der ortographischen Projektion erscheinen Objekte unabhängig von ihrer Entfernung zum Blickpunkt gleich Groß.  Es wird keine Konvergenz angezeigt.  Ist die Projektionsoption **Orthografisch** aktiviert, können Sie den **Orbit**\-Modus nicht zum Positionieren der Ansicht verwenden.|  
|**Zeichenstil**|Legt fest, wie Objekte in der Szene gerendert werden.  Im Folgenden finden Sie die verfügbaren Stile:<br /><br /> **Drahtmodell**<br /> Ist diese Option aktiviert, werden Objekte als Drahtmodelle gerendert.<br /><br /> **Überzeichnen**<br /> Ist diese Option aktiviert, werden Objekte durch Additive Blending gerendert.  Sie können diese Option verwenden, um darzustellen, wie ausgeprägt die Überzeichnung in der Szene ist.<br /><br /> **Flach schattiert**<br /> Ist diese Option aktiviert, werden Objekte mithilfe eines einfachen flach schattierten Beleuchtungsmodells gerendert.  Verwenden Sie diese Option, um die Flächen eines Objekts leichter zu erkennen.<br /><br /> Wenn keine dieser Optionen aktiviert ist, wird jedes Objekt in dem darauf angewendeten Material gerendert.|  
|**Real\-Time Rendering Mode**|Bei aktiviertem Real\-Time Rendering, zeichnet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Entwurfsoberfläche auch dann neu, wenn keine Benutzeraktion ausgeführt wird.  Ein hilfreicher Modus, bei der Arbeit mit Shadern, die sich im Laufe der Zeit ändern.|  
|**Raster umschalten**|Ist dieses Element aktiviert, wird ein Raster angezeigt.  Andernfalls wird das Raster nicht angezeigt.|  
|**Toolbox**|Zeigt den **Werkzeugkasten** an oder blendet ihn aus.|  
|**Dokumentgliederung**|Zeigt das Fenster **Dokumentgliederung** entweder an oder blendet es aus.|  
|**Eigenschaften**|Zeigt das Fenster **Eigenschaften** entweder an oder blendet es aus.|  
|**Erweitert**|Enthält erweiterte Befehle und Optionen.<br /><br /> **Grafik\-Engine**<br /><br /> **Mit D3D11 rendern**<br /> Verwendet Direct3D 11 zum Rendern der Model\-Editor\-Entwurfsoberfläche.<br /><br /> **Mit D3D11WARP rendern**<br /> Verwendet Direct3D 11 Windows Advanced Rasterization Platform \(WARP\) zum Rendern der Entwurfsoberfläche des Model\-Editors.<br /><br /> **Szenenverwaltung**<br /><br /> **Importieren**<br /> Importiert Objekte von einer anderen 3D\-Modelldatei in die aktuelle Szene.<br /><br /> **Übergeordnetes Element festlegen**<br /> Definiert das erste mehrerer ausgewählter Objekte als übergeordnetes Element der verbleibenden ausgewählten Objekte.<br /><br /> **Übergeordnetes Element entfernen**<br /> Trennt das ausgewählte Objekt von seinem übergeordneten Element.  Das ausgewählte Objekt wird zu einem *Stammobjekt* in der Szene.  Ein Stammobjekt verfügt über kein übergeordnetes Objekt.<br /><br /> **Gruppe erstellen**<br /> Gruppiert die ausgewählten Objekte als gleichgeordnete Objekte.<br /><br /> **Objekte zusammenführen**<br /> Kombiniert die ausgewählten Objekte in einem Objekt.<br /><br /> **Objekt aus Polygonauswahl erstellen**<br /> Entfernt die ausgewählten Oberflächen aus dem aktuellen Objekt und fügt der Szene ein neues Objekt hinzu, das die entsprechenden Oberflächen enthält.<br /><br /> **Tools**<br /><br /> **Polygonwicklung spiegeln**<br /> Kippt die ausgewählten Polygone in der Weise, dass ihre Wicklungsreihenfolgen und Oberflächennormale umgekehrt werden.<br /><br /> **Alle Animationen entfernen**<br /> Entfernt Animationsdaten aus den Objekten.<br /><br /> **Triangulieren**<br /> Konvertiert das ausgewählte Objekt in Dreiecke.<br /><br /> **Ansicht**<br /><br /> Backface Culling<br /> Aktiviert oder deaktiviert Backface Culling.<br /><br /> **Frame Rate**<br /> Zeigt in der rechten oberen Ecke der Entwurfsoberfläche die Einzelbildrate an.  Die Einzelbildrate ist die Anzahl von Bildern, die pro Sekunde gezeichnet werden.<br /><br /> Eine hilfreiche Option, wenn Sie die Option **Real\-Time Rendering Mode** aktivieren.<br /><br /> **Alle anzeigen**<br /> Zeigt alle Objekte in der Szene an.  Dadurch wird die Eigenschaft **Ausgeblendet** für jedes Objekts auf **False** zurückgesetzt.<br /><br /> **Flächennormale anzeigen**<br /> Zeigt die Normale jeder einzelnen Fläche an.<br /><br /> **Fehlende Materialien anzeigen**<br /> Zeigt auf Objekten, denen kein Material zugewiesen wurde, eine spezielle Textur an.<br /><br /> **Pivot anzeigen**<br /> Aktiviert oder deaktiviert das Anzeigen eines 3D\-Achsenmarkers am Pivotpunkt der aktiven Auswahl.<br /><br /> **Platzhalterknoten anzeigen**<br /> Platzhalterknoten anzeigen  Ein Platzhalterknoten wird erstellt, wenn Sie Objekte gruppieren.<br /><br /> **Vertexnormale anzeigen**<br /> Zeigt die Normale jedes Vertex an. **Tip:**  Sie können die Schaltfläche **Skripts** wählen, um das letzte Skript erneut auszuführen.|  
  
 Die Symbolleiste **Model\-Editor**:  
  
 ![Symbolleiste des Modell&#45;Viewers](~/docs/designers/media/digit-mre-toolbar.png "Digit\-MRE\-Toolbar")  
  
 In der folgenden Tabelle werden die Elemente der Symbolleiste **Model\-Editor\-Modus** beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von oben nach unten angezeigt werden.  
  
|Element der Symbolleiste|Beschreibung|  
|------------------------------|------------------|  
|**Translation**|Verschiebt die Markierung.|  
|**Skalieren**|Ändert die Größe der Auswahl.|  
|**Drehen**|Dreht die Auswahl.|  
|**Punkt auswählen**|Legt den **Auswahlmodus** auf die Auswahl einzelner Punkte in einem Objekt fest.|  
|**Rand auswählen**|Legt den **Auswahlmodus** auf die Auswahl eines Randes \(eine Linie zwischen zwei Schnittpunkten\) an einem Objekt fest.|  
|**Seite auswählen**|Legt den **Auswahlmodus** auf die Auswahl einer Fläche eines Objekts fest.|  
|**Objekt auswählen.**|Legt den **Auswahlmodus** auf die Auswahl eines kompletten Objekts fest.|  
|**Extrudieren**|Erstellt eine zusätzliche Fläche und verbindet sie mit der ausgewählten Fläche.|  
|**Unterteilen**|Unterteilt jede ausgewählte Fläche in mehrere Flächen.  Zum Erstellen der neuen Flächen werden neue Schnittpunkte hinzugefügt. Einer im Mittelpunkt der ursprünglichen Fläche und jeweils ein weiterer mitten auf jedem Rand. Sie werden dann mit den ursprünglichen Schnittpunkten verknüpft.  Die Anzahl der hinzugefügten Flächen entspricht der Anzahl Rändern der ursprünglichen Fläche.|  
  
### Steuern der Ansicht  
 Die 3D\-Szene wird entsprechend der Ansicht gerendert, die Sie sich als eine Art virtueller Kamera vorstellen können, mit einer Position und einer Ausrichtung.  Ändern Sie Position und Ausrichtung, mit den Ansichtssteuerelementen auf der Symbolleiste **Model\-Editor\-Modus**.  
  
 In der folgenden Tabelle werden die Hauptsteuerelemente der Ansicht beschrieben.  
  
|Ansichtsteuerung|Beschreibung|  
|----------------------|------------------|  
|**Schwenken**|Ermöglicht das Bewegen einer 3D\-Szene relativ zum Fensterrahmen.  Wählen Sie zum Schwenken einen Punkt in der Szene aus und verschieben Sie ihn.<br /><br /> Im **Auswahl**\-Modus können Sie den **Schwenken**\-Modus durch Gedrückthalten der STRG\-TASTE vorübergehend aktivieren.|  
|**Zoom**|Ermöglicht das Anzeigen von mehr oder weniger Szenendetails relativ zum Fensterrahmen.  Wählen Sie im **Zoom**\-Modus einen Punkt in der Szene aus und verschieben Sie ihn; zum Vergrößern nach rechts oder nach unten, und zum Verkleinern nach links oder nach oben.<br /><br /> Im **Auswählen**\-Modus können Sie zum Vergrößern oder Verkleinern das Mausrad verwenden. Drücken Sie dazu gleichzeitig STRG.|  
|**Orbit**|Positioniert die Ansicht auf einem kreisförmigen Pfad um das ausgewählte Objekt.  Ist kein Objekt ausgewählt, wird der Pfad auf den Szenenursprung zentriert. **Note:**  Dieser Modus hat keine Auswirkungen, wenn die Projektionsoption **Orthografisch** aktiviert ist.|  
|**Rahmenobjekt**|Rahmt das ausgewählte Objekt ein, sodass es sich in der Mitte der Ansicht befindet.|  
  
 Die Ansicht wird zwar von der virtuellen Kamera erstellt, ist jedoch auch durch eine Projektion definiert.  Die Projektion definiert, wie Formen und Objekte in der Ansicht auf der Entwurfsoberfläche in Pixel übersetzt werden.  Sie können auf der Symbolleiste **Model\-Editor** zwischen der Projektionsoption **Perspektive** oder **Orthografisch** wählen.  
  
|Projection|Beschreibung|  
|----------------|------------------|  
|**Perspektive**|In der perspektivischen Projektion erscheinen weiter vom Blickpunkt entfernte Objekte kleiner und laufen letztendlich in der Entfernung zu einem Punkt zusammen.|  
|**Orthografisch**|In der ortographischen Projektion erscheinen Objekte unabhängig von ihrer Entfernung zum Blickpunkt gleich Groß.  Es wird keine Konvergenz angezeigt.  Ist die Projektionsoption **Orthografisch** aktiviert, können Sie den **Orbit**\-Modus nicht beliebig zum Positionieren der Ansicht verwenden.|  
  
 Es kann hilfreich sein, eine 3D\-Szene von einer bekannten Position aus und in einem bekannten Winkel anzuzeigen zu lassen. Zum Beispiel bei einem Vergleich von zwei ähnlichen Szenen.  In so einem Fall stellt der Model\-Editor mehrere vordefinierte Ansichten zur Verfügung.  Zum Verwenden einer vordefinierte Ansicht, klicken Sie auf der Symbolleiste **Model\-Editor\-Modus** auf die Option **Ansicht** und wählen anschließend die gewünschte vordefinierte Ansicht aus: vorne, hinten, links, rechts, oben oder unten.  Die virtuelle Kamera ist in diesen Ansichten direkt auf den Ursprung der Szene ausgerichtet.  Wenn Sie beispielsweise **Oberseite anzeigen** auswählen, zeigt die virtuelle Kamera direkt von oben auf den Ursprung der Szene.  
  
### Anzeigen zusätzlicher Geometriedetails  
 Zum besseren Verständnis eines 3D\-Objekts oder einer 3D\-Szene, können Sie zusätzliche Geometriedetails wie die vertexspezifische oder flächenspezifische Normale oder Pivotpunkte der aktuellen Auswahl und weitere Details anzeigen.  Um sie auf der Symbolleiste **Model\-Editor** zu aktivieren oder zu deaktivieren, klicken Sie auf **Skripts** und **Ansicht** und wählen anschließend die gewünschte Option aus.  
  
###  <a name="Adding3DObjects"></a> 3D\-Objekte erstellen und Importieren  
 Um der Szene eine vordefinierte 3D\-Form hinzuzufügen, wählen Sie im **Werkzeugkasten** die gewünschte Form aus und verschieben Sie sie dann auf die Entwurfsoberfläche.  Neue Formen werden am Ursprung der Szene positioniert.  Der Model\-Editor stellt sieben Formen zur Verfügung: **Kegel**, **Würfel**, **Zylinder**, **Scheibe**, **Ebene**, **Kugel** und **Teekanne**.  
  
 Um ein 3D\-Objekt von einer Datei zu importieren, klicken Sie auf der Symbolleiste **Model\-Editor** auf **Erweitert**, **Szenenverwaltung**, **Importieren**, und geben Sie dann die Datei an die Sie importieren möchten.  
  
### Transformieren von Objekten  
 Sie können ein Objekt *transformieren,* indem Sie die Eigenschaften **Drehung**, **Skalierung** und **Übersetzung** ändern.  *Drehung* richtet ein Objekt aus, indem es nacheinander um die durch den Pivotpunkt des Objekts definierte x\-Achse, y\-Achse und z\-Achse gedreht wird.  Jede Drehungsspezifikation verfügt über drei Komponenten: x, y und z; in dieser Reihenfolge. Die Komponenten werden in Grad angegeben.  **Skalierung** ändert die Größe eines Objekts. Dabei wird das Objekt entlang einer oder mehrerer auf dem Pivotpunkt zentrierter Achsen um einen angegebenen Faktor gestreckt.  *Übersetzung* legt ein Objekt im dreidimensionalen Raum relativ zu seinem übergeordneten Element anstatt relativ zu seinem Pivotpunkt fest.  
  
 Sie können ein Objekt entweder mithilfe der Modellierungstools transformieren oder, indem Sie Eigenschaften festlegen.  
  
##### So transformieren Sie ein Objekt mithilfe der Modellingtools  
  
1.  Wählen Sie im **Auswahlmodus** das Objekt aus, das Sie transformieren möchten.  Eine Drahtmodellüberlappung zeigt an, dass das Objekt ausgewählt ist.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** und wählen Sie das Tool **Verschieben**, **Skalierung** oder **Drehen** aus.  Ein Übersetzungs\-, Skalierungs\- oder ein Drehungsmanipulator wird angezeigt.  
  
3.  Verwenden Sie den Manipulator, um die Transformation durchzuführen.  Der Manipulator für Übersetzungs\- und Skalierungstransformationen ist ein Achsenindikator.  Sie können eine Achse nacheinander ändern oder, mithilfe des weißen Würfels in der Mitte des Indikators, alle Achsen gleichzeitig.  Der Manipulator für Drehung ist eine Kugel aus farbcodierten Kreisen, entsprechend der x\-Achse \(rot\), der y\-Achse \(grün\) und der z\-Achse \(blau\).  Für eine gewünschte Drehung müssen Sie jede Achse einzeln ändern.  
  
##### So transformieren Sie ein Objekt durch Festlegen der Eigenschaften  
  
1.  Wählen Sie im **Auswahlmodus** das Objekt aus, das Sie transformieren möchten.  Eine Drahtmodellüberlappung zeigt an, dass das Objekt ausgewählt ist.  
  
2.  Geben Sie im Fenster **Eigenschaften** Werte für die Eigenschaften **Drehung**, **Skalierung** und **Übersetzung** an.  
  
    > [!IMPORTANT]
    >  Geben Sie für die Eigenschaft **Drehung** den Grad der Drehung um jede der drei Achsen an.  Drehungen werden nach der Reihe ausgeführt. Planen Sie daher eine Drehung zuerst in Hinblick auf die Drehung der x\-Achse, dann die der Y\-Achse und anschließend die der z\-Achse.  
  
 Mithilfe der Modellierungstools können Sie schnell Transformationen erstellen, die jedoch nicht genau sind.  Durch Festlegen der Objekteigenschaften, können Sie Transformationen genau allerdings nicht schnell angeben.  Es wird empfohlen, die Modellierungstools zu verwenden, um sich so weit wie möglich an die gewünschte Transformationen anzunähern und die Feinabstimmung anschließend über die Eigenschaftswerte vorzunehmen.  
  
 Wenn Sie keine Manipulatoren verwenden möchten, können Sie den Freihandform\-Modus aktivieren.  Klicken Sie zum Aktivieren \(oder Deaktivieren\) des Freihandform\-Modus auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Tools**, **Freihandform Manipulation**.  Im Freihandform\-Modus können Sie an jedem Punkt auf der Entwurfsoberfläche mit einer Manipulation beginnen, anstatt an einem Punkt auf dem Manipulator.  Im Freihandform\-Modus können Sie Änderungen an bestimmten Achsen einschränken, indem Sie diejenigen sperren, die Sie nicht ändern möchten.  Klicken Sie auf der Symbolleiste **Model\-Editor\-Modus** auf eine beliebige Kombination aus den Schaltflächen **LockX**, **LockY** und **LockZ**.  
  
 Es ist es möglicherweise hilfreich, Objekte zum Arbeiten am Raster auszurichten.  Klicken Sie zum Aktivieren \(oder Deaktivieren\) der Ausrichtung am Raster auf der Symbolleiste **Model\-Editor\-Modus** auf **Ausrichten**.  Bei aktivierter Ausrichtung am Raster, sind die Transformationenen Verschiebung, Drehung und Skalierung auf vordefinierte Schritte beschränkt.  
  
### Arbeiten mit dem Pivotpunkt  
 Der Pivotpunkt eines Objekts definiert seinen Drehungs\- und Skalierungsmittelpunkt.  Sie können den Pivotpunkt eines Objekts ändern, um die Auswirkungen von Drehungs\- und Skalierungstransformationen auf das Objekt zu ändern.  Klicken Sie zum Aktivieren \(oder Deaktivieren\) des Pivotmodus auf der Symbolleiste **Model\-Editor\-Modus** auf **Pivot\-Modus**.  Bei aktiviertem Pivotmodus wird ein kleiner Achsenindikator am Pivotpunkt des ausgewählten Objekts angezeigt.  Sie können die Tools **Übersetzung** und **Drehung** dann zur Bearbeitung des Pivotpunkts verwenden.  
  
 Ein Beispiel für die Verwendung des Pivotpunkts finden Sie unter [Gewusst wie: Ändern des Pivotpunkts eines 3D\-Modells](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).  
  
### Welt\-Modus und lokaler Modus  
 Verschiebung und Drehung lassen sich im lokalen Koordinatensystem \(oder *lokaler Verweisrahmen*\) des Objekts oder im Koordinatensystem der Welt \(oder *Weltverweisrahmen*\) umsetzen.  Der Weltverweisrahmen ist von der Drehung des Objekts unabhängig.  Die Standardeinstellung ist der lokale Modus.  Klicken Sie zum Aktivieren \(oder Deaktivieren\) des Weltmodus auf der Symbolleiste **Model\-Editor\-Modus** auf die Schaltfläche **WorldLocal**.  
  
###  <a name="ModifyingObjects"></a> Freies Ändern von Objekten auf der Zeichenfläche  
 Sie können die Form eines 3D\-Objekts ändern, indem Sie die Schnittpunkte, Ränder und Flächen verschieben oder löschen.  Standardmäßig ist der Model\-Editor auf *Objektmodus* eingestellt, damit Sie komplette Objekte auswählen und transformieren können.  Wählen Sie Punkte, Ränder oder Flächen mithilfe des entsprechenden Auswahlmodus aus.  Klicken Sie auf der Symbolleiste **Model\-Editor\-Modus** auf **Auswahlmodi** und wählen Sie dann den gewünschten Modus aus.  
  
 Mithilfe von Extrusionen oder Unterteilungen können Sie zusätzliche Schnittpunkte erstellen.  Extrusion dupliziert die Vertices einer Fläche \(ein koplanarer Satz von Vertices\), die durch die duplizierten Vertices verbunden bleiben.  Mit Unterteilung werden Schnittpunkte hinzugefügt, um aus einer Fläche mehrere Flächen zu erstellen.  Zum Erstellen der neuen Flächen werden neue Schnittpunkte hinzugefügt. Einer im Mittelpunkt der ursprünglichen Fläche und jeweils ein weiterer mitten auf jedem Rand. Sie werden dann mit den ursprünglichen Schnittpunkten verknüpft.  Die Anzahl der hinzugefügten Flächen entspricht der Anzahl Rändern der ursprünglichen Fläche.  In beiden Fällen können Sie die neuen Schnittpunkte übersetzen, drehen und anpassen, um die Geometrie des Objekts zu ändern.  
  
##### So extrudieren Sie eine Fläche aus einem Objekt  
  
1.  Wählen Sie im Flächenauswahlmodus die Fläche aus, die Sie extrudieren möchten.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Tools** und **Extrudieren**.  
  
##### So unterteilen Sie Flächen.  
  
1.  Wählen Sie im Flächenauswahlmodus die Flächen aus, die Sie unterteilen möchten.  Da das Unterteilen neue Randdaten erstellt, erhalten Sie mit einer Unterteilung aller Flächen auf einmal konsistentere Ergebnisse, sofern die Flächen aneinandergrenzen.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Tools** und **Unterteilen**.  
  
 Sie können Flächen auch triangulieren, Objekte zusammenfügen und ausgewählte Polygone in neue Objekte konvertieren.  Triangulation erstellt zusätzliche Ränder, indem Flächen, die nicht dreieckig sind, in die optimale Anzahl von Dreiecken konvertiert werden. Es werden jedoch keine zusätzlichen geometrischen Details bereitgestellt.  Zusammenführen kombiniert die ausgewählten Objekte in einem Objekt.  Neue Objekte können aus einer Polygon\-Auswahl erstellt werden.  
  
##### So triangulieren Sie eine Fläche  
  
1.  Wählen Sie im Flächenauswahlmodus die Fläche aus, die Sie triangulieren möchten.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Tools** und **Triangulieren**.  
  
##### So führen Sie Objekte zusammen  
  
1.  Wählen Sie im Modus "Objektauswahl" die Objekte, die Sie zusammenführen möchten.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Tools** und **Objekte zusammenführen**.  
  
##### So erstellen Sie ein Objekt aus einer Polygon\-Auswahl  
  
1.  Wählen Sie im Flächenauswahlmodus die Fläche aus, aus der Sie in ein neues Objekt erstellen möchten.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Tools** und **Objekt aus Polygonauswahl erstellen**.  
  
### Arbeiten mit Materialien und Shadern  
 Die Darstellung eines Objekts wird durch das Zusammenwirken der Beleuchtung in der Szene und dem Material des Objekts bestimmt.  Materialien werden über Eigenschaften definiert, die beschreiben, wie die Oberfläche auf unterschiedliche Lichtarten reagiert und über ein Shaderprogramm, das die endgültige Farbe jedes Pixels auf der Objektoberfläche auf Grundlage von Beleuchtungsinformationen, Strukturschemas, normalen Schemas und anderen Daten berechnet.  
  
 Der Model\-Editor stellt folgende Standardmaterialien bereit:  
  
|Material|Beschreibung|  
|--------------|------------------|  
|Unbeleuchtet|Rendert eine Oberfläche ohne simulierte Beleuchtung.|  
|Lambert|Rendert eine Oberfläche mit simulierter umgebender und diffuser Beleuchtung.|  
|Phong|Rendert eine Oberfläche mit simulierter umgebender und diffuser Beleuchtung und mit Lichtreflexen.|  
  
 Jedes dieser Materialien stellt eine Textur auf der Oberfläche eines Objekts.  Sie können für jedes Objekt, von dem das Material verwendet wird, eine andere Textur festlegen.  
  
 Um die Reaktion eines bestimmten Objekts auf verschiedenen Lichtquellen in der Szene zu ändern, können Sie die Beleuchtungseigenschaften des Materials unabhängig von anderen Objekten ändern, bei denen das Material verwendet wird.  Die folgende Tabelle beschreibt allgemeine Beleuchtungseigenschaften:  
  
|Beleuchtungseigenschaft|Beschreibung|  
|-----------------------------|------------------|  
|Umgebend|Beschreibt die Auswirkung von umgebenden Beleuchtung auf die Oberfläche.|  
|Diffus|Beschreibt die Auswirkung direktionaler Punktlichter auf die Oberfläche.|  
|Selbstleuchtend|Beschreibt die Abgabe von Licht durch die Oberfläche unabhängig von anderer Beleuchtung.|  
|Glänzend|Beschreibt die Reflektion von ausgerichtetem Licht und von Punktlichtern durch die Oberfläche.|  
|Glanzkraft|Beschreibt die Breite und Intensität von Glanzlichtern.|  
  
 Abhängig von den vom Material unterstützten Möglichkeiten, können Sie seine Beleuchtungseigenschaften, Texturen und andere Daten ändern.  Wählen Sie im **Auswahl**\-Modus das Objekt aus, dessen Material Sie ändern möchten. Ändern Sie anschließend im Fenster **Eigenschaften** die Optionen **MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower** oder andere verfügbare Eigenschaften.  Ein Material kann bis zu acht Texturen tragen, deren Eigenschaften nacheinander als **Texture1** bis **Texture8** bezeichnet werden.  
  
 Um alle Materialien von einem Objekt zu entfernen, klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Material**, **Materialien entfernen**.  
  
 Sie können den **Shader\-Designer** verwenden, um benutzerdefinierte Shadermaterialien zu erstellen, die Sie auf Objekte in der 3D\-Szene anwenden können.  Informationen zum Erstellen benutzerdefinierter Shadermaterialien finden Sie unter [Shader\-Designer](../designers/shader-designer.md).  Weitere Informationen zur Anwendung benutzerdefinierter Shadermaterialien auf ein Objekt finden Sie unter [Gewusst wie: Anwenden eines Shaders auf ein 3D\-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
### Szenenverwaltung  
 Sie können Szenen wie eine Hierarchie von Objekten verwalten.  Werden mehrere Objekte in einer Hierarchie angeordnet, wirkt sich jede Übersetzung, Skalierung oder Drehung eines übergeordneten Knotens auch auf die untergeordneten Elemente aus.  Das ist hilfreich, wenn Sie aus grundlegenderen Objekten komplexe Objekte oder Szenen erstellen möchten.  
  
 Mithilfe des Fensters **Dokumentgliederung** können Sie die Szenenhierarchie auswählen und Szenenknoten anzeigen.  Haben Sie einen Knoten in der Gliederung ausgewählt, können Sie die Eigenschaften mithilfe des Fensters **Eigenschaften** ändern.  
  
 Sie können eine Hierarchie von Objekten entweder erstellen, indem Sie eins davon als übergeordnetes Element festlegen oder indem Sie alle unter einem Platzhalterknoten, der als übergeordnetes Element auftritt, als gleichgeordnete Elemente gruppieren.  
  
##### So erstellen Sie eine Hierarchie mit übergeordnetem Objekt  
  
1.  Wählen Sie im **Auswahl**\-Modus zwei oder mehr Objekte aus.  Das erste Objekt, das Sie auswählen, wird zum übergeordneten Objekt.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Szenenverwaltung**, **Übergeordnetes Element festlegen**.  
  
##### So erstellen Sie eine Hierarchie gleichgeordneter Objekte  
  
1.  Wählen Sie im **Auswahl**\-Modus zwei oder mehr Objekte aus.  Ein Platzhalterobjekt wird erstellt und wird zum übergeordneten Objekt.  
  
2.  Klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Szenenverwaltung**, **Gruppe erstellen**.  
  
 Der Model\-Editor verwendet ein weißes Drahtmodell zur Identifizierung des zuerst ausgewählten Objekts, das zum übergeordneten Element wird.  Andere Objekte in der Auswahl werden mit einem blauen Drahtmodell dargestellt.  Standardmäßig werden Platzhalterknoten nicht angezeigt.  Damit Platzhalterknoten angezeigt werden, klicken Sie auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Szenenverwaltung**, **Platzhalterknoten anzeigen**.  Sie können mit Platzhalterknoten genauso arbeiten, wie mit Objekten ohne Platzhalterknoten.  
  
 Möchten Sie die Zuordnung zwischen zwei übergeordneten und untergeordneten Objekten entfernen, wählen Sie das untergeordnete Objekt und klicken Sie dann auf der Symbolleiste **Model\-Editor** auf **Skripts**, **Szenenverwaltung**, **Übergeordnetes Element entfernen**.  Sobald Sie das übergeordnete Element vom untergeordneten Objekt trennen, wird das untergeordnete Objekt zu einem Stammobjekt in der Szene.  
  
## Tastenkombinationen  
  
|Befehl|Tastenkombinationen|  
|------------|-------------------------|  
|In den **Auswahl**\-Modus umschalten|STRG\+G, STRG\+Q<br /><br /> S|  
|In den **Zoom**\-Modus umschalten|STRG\+G, STRG\+Z<br /><br /> Z|  
|In den **Schwenk**\-Modus umschalten|STRG\+G, STRG\+P<br /><br /> K|  
|Alles auswählen|STRG\+A|  
|Die aktuelle Auswahl löschen|Löschen|  
|Brechen Sie die aktuelle Auswahl ab.|Escape|  
|Vergrößern|Mausrad vorwärts<br /><br /> STRG\+Mausrad vorwärts<br /><br /> UMSCHALT\+Mausrad vorwärts<br /><br /> STRG\+BILD\-AUF<br /><br /> Pluszeichen \(\+\)|  
|Verkleinern|Mausrad rückwärts<br /><br /> STRG\+Mausrad rückwärts<br /><br /> UMSCHALT\+Mausrad rückwärts<br /><br /> STRG\+BILD\-AB<br /><br /> Minuszeichen \(\-\)|  
|Die Kamera nach oben schwenken|BILD\-AB|  
|Die Kamera nach unten schwenken|BILD\-AUF|  
|Die Kamera nach links schwenken|Mausrad links<br /><br /> STRG\+BILD\-AB|  
|Die Kamera nach rechts schwenken|Mausrad rechts<br /><br /> STRG\+BILD\-AB|  
|Oberseite des Modells anzeigen|STRG\+L, STRG\+T<br /><br /> T|  
|Unterseite des Modells anzeigen|STRG\+L, STRG\+U|  
|Linke Seite des Modells anzeigen|STRG\+L, STRG\+L|  
|Rechte Seite des Modells anzeigen|STRG\+L, STRG\+R|  
|Vorderseite des Modells anzeigen|STRG\+L, STRG\+F|  
|Rückseite des Modells anzeigen|STRG\+L, STRG\+B|  
|Objekt im Fenster einrahmen|F|  
|Drahtmodellmodus ein\-\/ausschalten|STRG\+L, STRG\+W|  
|"Am Raster ausrichten" ein\-\/ausschalten|STRG\+G, STRG\+N|  
|Pivotmodus ein\-\/ausschalten|STRG\+G, STRG\+V|  
|x\-Achsen\-Beschränkung ein\-\/ausschalten|STRG\+L, STRG\+X|  
|y\-Achsen\-Beschränkung ein\-\/ausschalten|STRG\+L, STRG\+Y|  
|z\-Achsen\-Beschränkung ein\-\/ausschalten|STRG\+L, STRG\+Z|  
|In den Übersetzungsmodus umschalten|STRG\+G, STRG\+W<br /><br /> W|  
|In den Skaliermodus umschalten|STRG\+G, STRG\+E<br /><br /> E|  
|In den Drehungsmodus umschalten|STRG\+G, STRG\+R<br /><br /> R|  
|In den Punktauswahlmodus umschalten|STRG\+L, STRG\+1|  
|In den Randauswahlmodus umschalten|STRG\+L, STRG\+2|  
|In den Flächenauswahlmodus umschalten|STRG\+L, STRG\+3|  
|In den Objektauswahlmodus umschalten|STRG\+L, STRG\+4|  
|In den Orbitmodus \(Kamera\) umschalten|STRG\+G, STRG\+O|  
|Nächstes Objekt in der Szene auswählen|Registerkarte|  
|Vorhergehendes Objekt in der Szene auswählen|UMSCHALT\+TAB|  
|Ausgewählte Objekt mit dem aktuellen Tool bearbeiten.|Pfeiltasten|  
|Aktuellen Manipulator deaktivieren|Q|  
|Kamera drehen|ALT\+ziehen mit linker Maustaste|  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Arbeiten mit 3D\-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Bietet eine Übersicht über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Tools, die Sie bei der Arbeit mit Grafikressourcen wie Texturen und Bildern, 3D\-Modellen und Shadereffekten verwenden können.|  
|[Grafik\-Editor](../designers/image-editor.md)|Beschreibt, wie der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bild\-Editor für die Arbeit mit Texturen und Bildern verwendet wird.|  
|[Shader\-Designer](../designers/shader-designer.md)|Beschreibt die Verwendung des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shader\-Designers zur Arbeit mit Shadern.|