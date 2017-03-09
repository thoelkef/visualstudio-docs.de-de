---
title: "Shader-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.designer.effectdesigner"
  - "vs.graphics.shaderdesigner"
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
caps.latest.revision: 32
caps.handback.revision: 32
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Shader-Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dokument beschreibt die Arbeit mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shader-Designer zum Erstellen, ändern und benutzerdefinierte visuelle Effekte, die als bekanntermaßen exportieren *Shader*.  
  
 Shader-Designer können Sie um benutzerdefinierte visuelle Effekte für Ihr Spiel oder Ihrer app zu erstellen, auch wenn Sie nicht, dass die HLSL-Programmierung wissen. Um einen Shader im Shader-Designer zu erstellen, legen Sie nur es als Diagramm; d. h. Sie der Entwurfsoberfläche hinzufügen *Knoten* die Daten und Vorgänge darstellen, und stellen Sie Verbindungen zwischen ihnen zu definieren, wie die Vorgänge der Daten zu verarbeiten. An jedem Vorgangsknoten wird eine Vorschau des Effekts bis zu diesem Zeitpunkt bereitgestellt, sodass Sie das Ergebnis visuell darstellen können. Datenfluss über die Knoten in Richtung einer letzten Knoten, der die Ausgabe des Shaders darstellt.  
  
## <a name="supported-formats"></a>Unterstützte Formate  
 Shader-Designer unterstützt diese Shader-Formate:  
  
|Formatname|Dateierweiterung|Unterstützte Vorgänge (anzeigen, bearbeiten, exportieren)|  
|-----------------|--------------------|-------------------------------------------------|  
|Gerichtetes Diagramm Shader Language|.dgsl|Ansicht bearbeiten|  
|HLSL-Shader (Quellcode)|.HLSL|Exportieren|  
|HLSL-Shader (Bytecode)|.CSO|Exportieren|  
|C++-Header (HLSL-Bytecode Array)|H|Exportieren|  
  
## <a name="getting-started"></a>Erste Schritte  
 In diesem Abschnitt wird beschrieben, wie einen DGSL-Shader zum Hinzufügen Ihrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt, und bietet grundlegende Informationen, um Ihnen beim Einstieg helfen.  
  
#### <a name="to-add-a-dgsl-shader-to-your-project"></a>Einen DGSL-Shader zu Ihrem Projekt hinzufügen  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, das Sie verwenden möchten, fügen den Shader, und wählen Sie dann **Hinzufügen**, **Neues Element**.  
  
2.  In der **Neues Element hinzufügen** Dialogfeld **installierte**, Option **Grafiken**, und wählen Sie dann **Visual Shader-Diagramm (.dgsl)**.  
  
3.  Geben Sie den **Namen** der Shader-Datei und die **Speicherort** in dem Sie erstellt werden soll.  
  
4.  Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
### <a name="the-default-shader"></a>Der Standard-shader  
 Jedes Mal, Sie einen DGSL-Shader erstellen, als Shader, die nur minimale beginnt eine **Farbe** Knoten, die mit verbunden ist die **endgültige Farbe** Knoten. Obwohl dieser Shader vollständig und funktionsbereit ist, nicht viel möglich ist. Der erste Schritt beim Erstellen eines Shaders arbeiten also häufig So löschen Sie die **Farbe** Knoten, oder trennen Sie ihn von der **endgültige Farbe** Knoten, um Platz für andere Knoten.  
  
## <a name="working-with-the-shader-designer"></a>Arbeiten mit der Shader-Designer  
 In den folgenden Abschnitten wird beschrieben, wie Shader-Designer mit der Arbeit mit benutzerdefinierten Shadern.  
  
### <a name="shader-designer-toolbars"></a>Shader-Designer-Symbolleisten  
 Shader-Designer, den Symbolleisten enthalten Befehle, die Arbeit mit DGSL-Shader-Diagramme.  
  
 Befehle, mit denen der Zustand des Shader-Designers befinden sich auf den **-Shader-Designer im Modus** Symbolleiste im Hauptfenster [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fenster. Tools zum Entwerfen und Befehle befinden sich auf der **Shader-Designer** Symbolleiste auf der Shader-Designer-Entwurfsoberfläche.  
  
 Hier wird die **Shader-Designer im Modus** Symbolleiste:  
  
 ![Modale Shader-Designer-Symbolleiste](../designers/media/digit-dsd-modal-toolbar.png "Digit-DSD-Modal-Toolbar")  
  
 Diese Tabelle beschreibt die Elemente auf der **Shader-Designer im Modus** Symbolleiste, die Reihenfolge von links nach rechts in der Reihenfolge aufgeführt werden:  
  
|Element der Symbolleiste|Beschreibung|  
|------------------|-----------------|  
|**Wählen Sie**|Ermöglicht die Interaktion mit Knoten und Kanten im Diagramm. In diesem Modus können Sie Knoten auswählen und verschieben oder löschen, und Sie können Ränder einrichten oder aufzuteilen.|  
|**Schwenken**|Ermöglicht die Verschiebung der Shader-Diagramm relativ zum Fensterrahmen. Um zu verschieben, wählen Sie einen Punkt auf der Entwurfsoberfläche, und verschieben Sie ihn.<br /><br /> Im **Wählen Sie** -Modus, die Sie drücken und halten Sie die STRG-Taste aktivieren können **Schwenken** Modus vorübergehend.|  
|**Zoom**|Ermöglicht die Anzeige von mehr oder weniger Shader-Diagramm Detail relativ zum Fensterrahmen. In **Zoom** Modus wählen Sie einen Punkt auf der Entwurfsoberfläche und ihn nach rechts verschieben oder nach unten, um zu vergrößern bzw. nach links oder nach oben.<br /><br /> Im **wählen** Modus drücken Sie und halten Sie STRG gedrückt, vergrößern oder verkleinern das Mausrad verwenden.|  
|**Zoom anpassen**|Zeigt die vollständige Shader-Diagramm im Fensterrahmen an.|  
|**Echtzeit Renderingmodus**|Bei aktiviertem Real-Time Rendering, zeichnet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Entwurfsoberfläche auch dann neu, wenn keine Benutzeraktion ausgeführt wird. Ein hilfreicher Modus, bei der Arbeit mit Shadern, die sich im Laufe der Zeit ändern.|  
|**Vorschau mit Kugel**|Wenn aktiviert, wird ein Modell einer Kugel verwendet, um eine Shader-Vorschau. Nur eine Vorschau Formen gleichzeitig kann aktiviert werden.|  
|**Vorschau mit cube**|Wenn aktiviert, wird ein Modell eines Cubes verwendet, um eine Shader-Vorschau. Nur eine Vorschau Formen gleichzeitig kann aktiviert werden.|  
|**Vorschau mit Zylinder**|Wenn aktiviert, wird ein Modell eines Zylinders verwendet, um eine Shader-Vorschau. Nur eine Vorschau Formen gleichzeitig kann aktiviert werden.|  
|**Vorschau mit Kegel**|Wenn aktiviert, wird ein Modell eines Kegels verwendet, um eine Shader-Vorschau. Nur eine Vorschau Formen gleichzeitig kann aktiviert werden.|  
|**Vorschau mit Teekanne**|Wenn aktiviert, wird ein Modell aus einer Teekanne Shader-Vorschau. Nur eine Vorschau Formen gleichzeitig kann aktiviert werden.|  
|**Mit Vorschau**|Wenn aktiviert, wird ein Modell einer Ebene verwendet, um eine Shader-Vorschau. Nur eine Vorschau Formen gleichzeitig kann aktiviert werden.|  
|**Toolbox**|Alternativ Blendet die **Toolbox**.|  
|**Eigenschaften**|Sie können auch anzeigen oder Ausblenden der **Eigenschaften** Fenster.|  
|**Erweiterte**|Enthält erweiterte Befehle und Optionen.<br /><br /> **Exportieren Sie**: ermöglicht das Exportieren eines Shaders in verschiedenen Formaten.<br /><br /> **Exportieren als**: exportiert die Shader als entweder HLSL-Quellcode oder als kompilierte Shader-Bytecode. Weitere Informationen zum Exportieren von Shadern finden Sie unter [Gewusst wie: Exportieren eines Shaders](../designers/how-to-export-a-shader.md).<br /><br /> **Grafik-Engine**: ermöglicht die Auswahl der Renderer, der verwendet wird, um der Entwurfsoberfläche anzuzeigen.<br /><br /> **Mit D3D11 Rendern**: verwendet Direct3D 11 zum Rendern der Shader-Designer-Entwurfsoberfläche.<br /><br /> **Mit D3D11WARP Rendern**: verwendet Direct3D 11 Windows Advanced Rasterization Platform (WARP) zum Rendern der Shader-Designer-Entwurfsoberfläche.<br /><br /> **Ansicht**: ermöglicht die Auswahl zusätzlicher Informationen über den Shader-Designer.<br /><br /> **Einzelbildrate**: Wenn aktiviert, wird die aktuelle Framerate in der oberen rechten Ecke der Entwurfsoberfläche angezeigt. Die Einzelbildrate ist die Anzahl von Bildern, die pro Sekunde gezeichnet werden.  Diese Option ist nützlich, wenn Sie aktivieren die **Real-Time Rendering Mode** Option.|  
  
> [!TIP]
>  Sie können die **Erweitert** Schaltfläche mit dem letzten Befehl erneut ausführen.  
  
### <a name="working-with-nodes-and-connections"></a>Arbeiten mit Knoten und Verbindungen  
 Verwendung **wählen** Modus zum Hinzufügen, entfernen, neu anordnen, verbinden und Knoten konfigurieren. So wird diese grundlegenden Operationen ausführen:  
  
##### <a name="to-perform-basic-operations-in-select-mode"></a>Grundlegende Operationen im Auswahlmodus  
  
-   Gehen Sie dabei folgendermaßen vor:  
  
    -   Um einen Knoten im Diagramm hinzuzufügen, wählen sie in der **Toolbox** und verschieben Sie es auf die Entwurfsoberfläche.  
  
    -   Um einen Knoten aus dem Diagramm zu entfernen, wählen Sie ihn, und drücken Sie dann ENTF.  
  
    -   Um einen Knoten verschieben möchten, wählen sie aus, und dann an einen neuen Speicherort verschieben.  
  
    -   Um zwei Knoten verbinden möchten, verschieben Sie ein Terminal-Ausgabe eines Knotens in ein Eingabe-Terminal des anderen Knotens. Nur Terminals, die kompatible Typen aufweisen können verbunden werden. Eine Linie zwischen den Terminals wird die Verbindung.  
  
    -   Wählen Sie zum Entfernen einer Verbindung, auf das Kontextmenü für eines der verbundenen-Terminals **unterbrechen Links**.  
  
    -   Konfigurieren Sie die Eigenschaften eines Knotens, wählen Sie den Knoten, und klicken Sie dann auf die **Eigenschaften** Fenster, geben Sie neue Werte für die Eigenschaften.  
  
### <a name="previewing-shaders"></a>Vorschau von Shadern  
 Damit Sie verstehen, wie ein Shader in Ihrer app angezeigt wird, können Sie konfigurieren, wie der Effekt in der Vorschau angezeigt wird. Um Ihre app anzugleichen, können Sie einer von mehreren Formen zu rendern, Texturen und andere wesentliche Parameter konfigurieren, aktivieren Sie die Animation zeitbasierten Effekte und untersuchen Sie die Vorschau aus verschiedenen Blickwinkeln dar.  
  
#### <a name="shapes"></a>Formen  
 Shader-Designer enthält sechs Shapes – einer Kugel, einen Cube, einen Zylinder, Kegel, eine Teekanne und eine Ebene –, dass Sie den Shader-Vorschau verwenden können. Je nach den Shader bestimmte Formen eine bessere Vorschau Ihnen möglicherweise.  
  
###### <a name="to-choose-a-preview-shape"></a>Wählen Sie eine Form "Vorschau"  
  
-   Auf der **Shader-Designer Modi** Symbolleiste, wählen Sie die gewünschte Form aus.  
  
####  <a name="a-namewwsmaterialparametersa-textures-and-material-parameters"></a><a name="WWS_MaterialParameters"></a> Texturen und Material-Parameter  
 Viele Shader basieren auf Texturen und Material-Eigenschaften, um ein einheitliches Aussehen für jede Art von Objekt in Ihrer app zu erstellen. Um zu sehen, wie der Shader in Ihrer app aussieht, können Sie festlegen, die Strukturen und Material-Eigenschaften, die verwendet werden, um das Rendern der Vorschau entsprechend der Texturen und Parametern, die Sie in Ihrer Anwendung verwenden können.  
  
###### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>Eine andere Textur auf ein Register Textur gebunden oder andere Material Parameter zu ändern.  
  
1.  In **wählen** Modus wählen Sie einen leeren Bereich der Entwurfsoberfläche. Dies bewirkt, dass die **Eigenschaften** Fenster, um die globale Shader-Eigenschaften anzuzeigen.  
  
2.  In der **Eigenschaften** Fenster, geben Sie neue Werte für die Struktur und Parameter-Eigenschaften, die Sie ändern möchten.  
  
 Hier sind die Shader-Parameter, die Sie ändern können:  
  
|Parameter|Eigenschaften|  
|---------------|----------------|  
|**Texture-1** – **Texture-8**|**Zugriff**:                             **öffentlichen** zu der Eigenschaft im Modell-Editor, andernfalls **Private**.<br /><br /> **Dateiname**: der vollständige Pfad der Texturdatei, die diesem Register Struktur zugeordnet ist.|  
|**Ambient Material**|**Zugriff**:                             **öffentlichen** zu der Eigenschaft im Modell-Editor, andernfalls **Private**.<br /><br /> **Wert**: die Diffus Farbe des aktuellen Pixels aufgrund indirekte – oder ambient-Beleuchtung.|  
|**Diffuses Material**|**Zugriff**: **öffentlichen** zu der Eigenschaft im Modell-Editor, andernfalls **Private**.<br /><br /> **Wert**: eine Farbe, die beschreibt, wie das aktuelle Pixel direkten Beleuchtung zerstreut.|  
|**Selbstleuchtendes Material**|**Zugriff**:                              **öffentlichen** zu der Eigenschaft im Modell-Editor, andernfalls **Private**.<br /><br /> **Wert**: der Anteil von Farbe für das aktuelle Pixel aufgrund von Ihnen selbst bereitgestellten Beleuchtung.|  
|**Glänzendes Material**|**Zugriff**:                              **öffentlichen** zu der Eigenschaft im Modell-Editor, andernfalls **Private**.<br /><br /> **Wert**: eine Farbe, die beschreibt, wie das aktuelle Pixel direkten Beleuchtung wiedergibt.|  
|**Material Glanzkraft**|**Zugriff**:                             **öffentlichen** zu der Eigenschaft im Modell-Editor, andernfalls **Private**.<br /><br /> **Wert**: der Exponent, der die Intensität von Glanzlichtern auf das aktuelle Pixel definiert.|  
  
#### <a name="time-based-effects"></a>Zeitbasierte Effekte  
 Einige Shader haben eine zeitbasierte-Komponente, die den Effekt animiert. Um anzuzeigen, wie der Effekt in Aktion dargestellt, muss die Vorschau mehrmals pro Sekunde aktualisiert werden. Standardmäßig wird die Vorschau nur aktualisiert, wenn der Shader geändert wird; Um dieses Verhalten ändern, sodass Sie Effekte zeitbasierten anzeigen können, müssen Sie in Echtzeit-Rendering aktivieren.  
  
###### <a name="to-enable-real-time-rendering"></a>So aktivieren Sie Echtzeit-rendering  
  
-   Wählen Sie auf der Symbolleiste des Shader-Designers **Real-Time Rendering**.  
  
#### <a name="examining-the-effect"></a>Untersuchen den Effekt  
 Viele Shader werden von Variablen wie z. B. das Anzeigen von Winkel oder eine direktionale Beleuchtung beeinflusst. Untersuchen, wie der Effekt reagiert, da diese Variablen ändern, können Sie die Vorschauform frei drehen und beobachten Sie das Verhalten des Shaders.  
  
###### <a name="to-rotate-the-shape"></a>Um die Form zu rotieren  
  
-   Drücken Sie und halten Sie ALT gedrückt, wählen Sie einen beliebigen Punkt auf der Entwurfsoberfläche, und verschieben Sie sie.  
  
### <a name="exporting-shaders"></a>Exportieren von Shadern  
 Bevor Sie einen Shader in Ihrer app verwenden können, müssen Sie es in ein Format zu exportieren, die DirectX versteht.  
  
 Sie können den Shader als HLSL-Quellcodes oder als kompilierte Shader-Bytecode exportieren. HLSL-Quellcode wird in eine Textdatei exportiert, die Erweiterung .hlsl verfügt. Shader-Bytecode kann exportiert werden, um eine unformatierte binäre Datei, die Erweiterung .cso oder an eine C++-Headerdatei (.h)-Datei, die den Shader-Bytecode in ein Array codiert.  
  
 Weitere Informationen zum Exportieren von Shadern finden Sie unter [Gewusst wie: Exportieren eines Shaders](../designers/how-to-export-a-shader.md).  
  
## <a name="keyboard-shortcuts"></a>Tastenkombinationen  
  
|Befehl|Tastenkombinationen|  
|-------------|------------------------|  
|Wechseln Sie zu **wählen** Modus|STRG+G, STRG+Q<br /><br /> S|  
|Wechseln Sie zu **Zoom** Modus|STRG+G, STRG+Z<br /><br /> Z|  
|Wechseln Sie zu **Schwenken** Modus|STRG+G, STRG+P<br /><br /> K|  
|Alles auswählen|STRG + A|  
|Die aktuelle Auswahl löschen|Löschen|  
|Brechen Sie die aktuelle Auswahl ab.|Escape|  
|Vergrößern|STRG+Mausrad vorwärts<br /><br /> Pluszeichen (+)|  
|Verkleinern|STRG+Mausrad rückwärts<br /><br /> Minuszeichen (-)|  
|Die Entwurfsoberfläche nach oben schwenken|Mausrad rückwärts<br /><br /> BILD-AB|  
|Die Entwurfsoberfläche nach unten schwenken|Mausrad vorwärts<br /><br /> BILD-AUF|  
|Die Entwurfsoberfläche nach links schwenken|UMSCHALT+Mausrad rückwärts<br /><br /> Mausrad links<br /><br /> UMSCHALT+BILD-AB|  
|Die Entwurfsoberfläche nach rechts schwenken|UMSCHALT+Mausrad vorwärts<br /><br /> Mausrad rechts<br /><br /> UMSCHALT+BILD-AUF|  
|Den Tastaturfokus auf einen anderen Knoten verschieben|Die Pfeiltasten|  
|Wählen Sie den Knoten, der über den Tastaturfokus verfügt (fügt den Knoten der Auswahlgruppe)|UMSCHALT + LEERTASTE|  
|Wechseln der Auswahl des Knotens, der den Tastaturfokus|STRG+LEERTASTE|  
|Wechseln der aktuellen Auswahl (wenn keine Knoten ausgewählt werden, wählen Sie den Knoten, der über den Tastaturfokus verfügt)|LEERTASTE|  
|Die aktuelle Auswahl nach oben verschieben|UMSCHALT+NACH-OBEN|  
|Die aktuelle Auswahl nach unten verschieben|UMSCHALT+NACH-UNTEN|  
|Die aktuelle Auswahl nach links verschieben|STRG+NACH-LINKS|  
|Aktuelle Auswahl nach rechts verschieben|UMSCHALT + nach-rechts-Pfeil.|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Arbeiten mit 3D-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Bietet eine Übersicht über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tools, die Sie zum Arbeiten mit Texturen und Bildern, 3D-Modellen und shadereffekten verwenden können.|  
|[Grafik-Editor](../designers/image-editor.md)|Beschreibt, wie der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bild-Editor für die Arbeit mit Texturen und Bildern verwendet wird.|  
|[Modell-Editor](../designers/model-editor.md)|Beschreibt, wie der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Modell-Editor für die Arbeit mit 3D-Modellen verwendet wird.|