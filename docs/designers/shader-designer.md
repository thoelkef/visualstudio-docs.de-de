---
title: Shader-Designer | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
caps.latest.revision: 32
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: af7472d5152babe2088ae3cc49caaf718a539878
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="shader-designer"></a>Shader-Designer
In diesem Dokument wird beschrieben, wie mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shader-Designer benutzerdefinierte visuelle Effekte, auch als *Shader* bekannt, erstellt, bearbeitet und exportiert werden können.  
  
 Sie können Shader-Designer dazu verwenden, benutzerdefinierte visuelle Effekte für Ihr Spiel oder Ihre App zu erstellen, selbst wenn Sie sich nicht mit der HLSL-Programmierung auskennen. Um einen Shader im Shader-Designer zu erstellen, ordnen Sie ihn als Diagramm an. Das heißt, Sie fügen der Entwurfsoberfläche *Knoten* hinzu, die Daten und Vorgänge darstellen, und stellen dann Verbindungen zwischen ihnen her, um zu definieren, wie die Vorgänge die Daten verarbeiten. An jedem Vorgangsknoten wird eine Vorschau des Effekts bis zu diesem Zeitpunkt bereitgestellt, sodass Sie das Ergebnis visuell darstellen können. Daten fließen über die Knoten in Richtung eines letzten Knotens, der die Ausgabe des Shaders darstellt.  
  
## <a name="supported-formats"></a>Unterstützte Formate  
 Der Shader-Designer unterstützt die folgenden Shader-Formate:  
  
|Formatname|Dateierweiterung|Unterstützte Vorgänge (Anzeigen, Bearbeiten, Exportieren)|  
|-----------------|--------------------|-------------------------------------------------|  
|Directed Graph Shader Language|.dgsl|Anzeigen, Bearbeiten|  
|HLSL-Shader (Quellcode)|.hlsl|Exportieren|  
|HLSL-Shader (Bytecode)|.cso|Exportieren|  
|C++-Header (HLSL-Bytecode-Array)|H|Exportieren|  
  
## <a name="getting-started"></a>Erste Schritte  
 In diesem Abschnitt wird beschrieben, wie Sie Ihrem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekt einen DGSL-Shader hinzufügen. Außerdem erhalten Sie grundlegende Informationen über die ersten Schritte.  
  
#### <a name="to-add-a-dgsl-shader-to-your-project"></a>So fügen Sie einen DGSL-Shader zu Ihrem Projekt hinzu  
  
1.  Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü des Projekts, zu dem Sie den Shader hinzufügen möchten, und wählen Sie dann **Hinzufügen** und **Neues Element** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Installiert** die Option **Grafiken** und anschließend **Visual Shader-Diagramm (.dgsl)** aus.  
  
3.  Geben Sie den **Namen** der Shader-Datei und den **Speicherort** an, an dem sie erstellt werden soll.  
  
4.  Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
### <a name="the-default-shader"></a>Der Standard-Shader  
 Jedes Mal, wenn Sie einen DGSL-Shader erstellen, startet er als minimaler Shader, der nur über einen Knoten **Punktfarbe** verfügt, der mit dem Knoten **Endgültige Farbe** verbunden ist. Obwohl dieser Shader vollständig und funktional ist, tut er nicht viel. Der erste Schritt beim Erstellen eines funktionierenden Shaders ist daher oft, den Knoten **Punktfarbe** zu löschen oder dessen Verbindung mit dem Knoten **Endgültige Farbe** zu trennen, um Platz für andere Knoten zu schaffen.  
  
## <a name="working-with-the-shader-designer"></a>Arbeiten mit dem Shader-Designer  
 In den folgenden Abschnitten wird beschrieben, wie Sie den Shader-Designer für die Arbeit mit benutzerdefinierten Shadern verwenden können.  
  
### <a name="shader-designer-toolbars"></a>Symbolleisten des Shader-Designers  
 Die Symbolleisten des Shader-Designers enthalten Befehle, die Sie bei der Arbeit mit DGSL-Shader-Diagrammen unterstützen.  
  
 Befehle, die den Zustand des Shader-Designers beeinflussen, finden Sie auf der **Shader-Designer-Modus**-Symbolleiste im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Hauptfenster. Designtools und -befehle befinden sich auf der **Shader-Designer**-Symbolleiste auf der Shader-Designer-Entwurfsoberfläche.  
  
 So sieht die **Shader-Designer-Modus**-Symbolleiste aus:  
  
 ![Die Shader-Designer-Modus-Symbolleiste](~/docs/designers/media/digit-dsd-modal-toolbar.png "Ziffer-DSD-Modale-Symbolleiste")  
  
 In dieser Tabelle werden die Elemente der **Shader-Designer-Modus**-Symbolleiste beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von links nach rechts angezeigt werden:  
  
|Element der Symbolleiste|Beschreibung|  
|------------------|-----------------|  
|**Auswählen**|Ermöglicht die Interaktion mit Knoten und Kanten im Diagramm. In diesem Modus können Sie Knoten auswählen und verschieben oder löschen. Zudem können Sie Kanten einrichten oder unterbrechen.|  
|**Schwenken**|Ermöglicht das Bewegen eines Shader-Diagramms relativ zum Fensterrahmen. Wählen Sie zum Schwenken einen Punkt auf der Entwurfsoberfläche aus, und verschieben Sie ihn.<br /><br /> Im **Auswahl**-Modus können Sie den **Schwenken**-Modus durch Gedrückthalten der STRG-TASTE vorübergehend aktivieren.|  
|**Zoom**|Ermöglicht das Anzeigen von mehr oder weniger Details des Shader-Diagramms relativ zum Fensterrahmen. Wählen Sie im **Zoom**-Modus einen Punkt auf dem Bild aus, und verschieben Sie ihn zum Vergrößern nach rechts oder nach unten und zum Verkleinern nach links oder nach oben.<br /><br /> Im **Auswählen**-Modus können Sie zum Vergrößern oder Verkleinern das Mausrad verwenden. Halten Sie dazu STRG gedrückt.|  
|**Mit Zoom anpassen**|Zeigt das gesamte Shader-Diagramm im Fensterrahmen an.|  
|**Real-Time Rendering Mode** (Echtzeit-Renderingmodus)|Bei aktiviertem Real-Time Rendering, zeichnet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Entwurfsoberfläche auch dann neu, wenn keine Benutzeraktion ausgeführt wird. Ein hilfreicher Modus, bei der Arbeit mit Shadern, die sich im Laufe der Zeit ändern.|  
|**Vorschau mit Kugel**|Wenn diese aktiviert ist, wird ein Modell einer Kugel für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|  
|**Vorschau mit Würfel**|Wenn diese aktiviert ist, wird ein Modell eines Würfels für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|  
|**Vorschau mit Zylinder**|Wenn diese aktiviert ist, wird ein Modell eines Zylinders für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|  
|**Vorschau mit Kegel**|Wenn diese aktiviert ist, wird ein Modell eines Kegels für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|  
|**Vorschau mit Teekanne**|Wenn diese aktiviert ist, wird ein Modell einer Teekanne für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|  
|**Vorschau mit Ebene**|Wenn diese aktiviert ist, wird ein Modell einer Ebene für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|  
|**Werkzeugkasten**|Zeigt die **Toolbox** entweder an oder blendet sie aus.|  
|**Eigenschaften**|Zeigt das Fenster **Eigenschaften** entweder an oder blendet es aus.|  
|**Erweitert**|Enthält erweiterte Befehle und Optionen.<br /><br /> **Exportieren**: Ermöglicht das Exportieren eines Shaders in verschiedene Formate.<br /><br /> **Exportieren als**: Exportiert den Shader entweder als HLSL-Quellcode oder als kompilierten Shader-Bytecode. Weitere Informationen zum Exportieren von Shadern finden Sie unter [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md).<br /><br /> **Grafikmodule**: Ermöglicht die Auswahl des Renderers, der für die Anzeige der Entwurfsoberfläche verwendet wird<br /><br /> **Rendern mit D3D11**: Verwendet Direct3D 11 zum Rendern der Entwurfsoberfläche des Shader-Designers<br /><br /> **Rendern mit D3D11WARP**: Verwendet Direct3D 11 Windows Advanced Rasterization Platform (WARP) zum Rendern der Entwurfsoberfläche des Shader-Designers.<br /><br /> **Ansicht**: Ermöglicht die Auswahl zusätzlicher Informationen über den Shader-Designer.<br /><br /> **Bildfrequenz**: Wenn diese aktiviert ist, wird in der rechten oberen Ecke der Entwurfsoberfläche die Bildfrequenz angezeigt. Die Einzelbildrate ist die Anzahl von Bildern, die pro Sekunde gezeichnet werden.  Diese Option ist hilfreich, wenn Sie die Option **Real-Time Rendering Mode** (Echtzeit-Renderingmodus) aktivieren.|  
  
> [!TIP]
>  Klicken Sie zum erneuten Ausführen des letzten Befehls auf die Schaltfläche **Erweitert**.  
  
### <a name="working-with-nodes-and-connections"></a>Arbeiten mit Knoten und Verbindungen  
 Verwenden Sie den Modus **Auswählen**, um Knoten hinzuzufügen, zu entfernen, neu anzuordnen, zu verbinden und zu konfigurieren. So werden diese grundlegenden Vorgänge ausgeführt:  
  
##### <a name="to-perform-basic-operations-in-select-mode"></a>Ausführen von grundlegenden Vorgängen im Modus „Auswählen“  
  
-   Gehen Sie dabei folgendermaßen vor:  
  
    -   Um einen Knoten zum Diagramm hinzuzufügen, wählen Sie diesen in der **Toolbox** aus, und verschieben Sie ihn anschließend auf die Entwurfsoberfläche.  
  
    -   Um einen Knoten aus dem Diagramm zu entfernen, wählen Sie ihn aus, und drücken Sie dann die ENTF-TASTE.  
  
    -   Um einen Knoten neu anzuordnen, wählen Sie diesen aus, und verschieben Sie ihn dann an einen neuen Speicherort.  
  
    -   Um zwei Knoten zu verbinden, verschieben Sie ein Ausgabeterminal eines Knotens in ein Eingabeterminal des anderen Knotens. Es können nur Terminals mit kompatiblen Typen verbunden werden. Eine Linie zwischen den Terminals zeigt die Verbindung.  
  
    -   Um eine Verbindung zu entfernen, wählen Sie im Kontextmenü eines der verbundenen Terminals **Zeilen umbrechen** aus.  
  
    -   Um die Eigenschaften eines Knotens zu konfigurieren, wählen Sie den Knoten aus, und geben Sie dann im Fenster **Eigenschaften** neue Werte für die Eigenschaften an.  
  
### <a name="previewing-shaders"></a>Anzeigen der Vorschau von Shadern  
 Damit Sie verstehen, wie ein Shader in Ihrer App angezeigt wird, können Sie konfigurieren, wie der Effekt in der Vorschau angezeigt wird. Um Ihre App anzupassen, können Sie eine aus mehreren Formen zum Rendern auswählen, Texturen und andere Materialparameter konfigurieren, die Animation von zeitbasierten Effekten aktivieren und die Vorschau aus verschiedenen Perspektiven untersuchen.  
  
#### <a name="shapes"></a>Formen  
 Der Shader-Designer umfasst sechs Formen (eine Kugel, einen Würfel, einen Zylinder, einen Kegel, eine Teekanne und eine Ebene), die Sie für die Vorschau Ihrer Shader verwenden können. Je nach Shader bieten Ihnen bestimmte Formen möglicherweise eine bessere Vorschau.  
  
###### <a name="to-choose-a-preview-shape"></a>So wählen Sie eine Vorschauform aus  
  
-   Auf der **Shader-Designer-Modi**-Symbolleiste wählen Sie die gewünschte Form aus.  
  
####  <a name="WWS_MaterialParameters"></a> Texturen und Materialparameter  
 Viele Shader greifen auf Texturen und Materialeigenschaften zurück, um ein einheitliches Aussehen für jede Art von Objekt in Ihrer App zu erstellen. Um anzuzeigen, wie der Shader in Ihrer App aussieht, können Sie die Texturen und Materialeigenschaften, die zum Rendern der Vorschau verwendet werden, so einstellen, dass sie mit den Texturen und Parametern übereinstimmen, die Sie möglicherweise in Ihrer App verwenden.  
  
###### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>So binden Sie eine andere Textur an ein Texturregister oder bearbeiten andere Materialparameter  
  
1.  Wählen Sie im Modus **Auswählen** einen leeren Bereich auf der Entwurfsoberfläche aus. Dadurch werden im Fenster **Eigenschaften** die globalen Shader-Eigenschaften angezeigt.  
  
2.  Geben Sie im Fenster **Eigenschaften** neue Werte für die Textur- und Parametereigenschaften an, die Sie ändern möchten.  
  
 Die folgenden Shader-Parameter können Sie ändern:  
  
|Parameter|Eigenschaften|  
|---------------|----------------|  
|**Textur 1** - **Textur 8**|**Zugriff**: **Öffentlich**, sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Dateiname**: Der vollständige Pfad der Texturdatei, die diesem Texturregister zugeordnet ist.|  
|**Material (Umgebung)**|**Zugriff**: **Öffentlich**, sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**: Die diffuse Farbe des aktuellen Pixels aufgrund indirekter oder Umgebungsbeleuchtung.|  
|**Material (Diffus)**|**Zugriff**: **Öffentlich**, sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**: Eine Farbe, die beschreibt, wie das aktuelle Pixel die direkte Beleuchtung streut.|  
|**Material (Selbstleuchtend)**|**Zugriff**: **Öffentlich**, sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**: Die Farbeinwirkung des aktuellen Pixels aufgrund der selbsterzeugten Beleuchtung.|  
|**Material (Glanz)**|**Zugriff**: **Öffentlich**, sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**: Eine Farbe, die beschreibt, wie das aktuelle Pixel die direkte Beleuchtung reflektiert.|  
|**Material (Glanzkraft)**|**Zugriff**: **Öffentlich**, sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**: Der Exponent, mit dem die Intensität von Glanzlichtern auf dem aktuellen Pixel definiert wird.|  
  
#### <a name="time-based-effects"></a>Zeitbasierte Effekte  
 Einige Shader verfügen über eine zeitbasierte Komponente, die den Effekt animiert. Um anzuzeigen, wie der Effekt in Aktion aussieht, muss die Vorschau mehrmals pro Sekunde aktualisiert werden. Standardmäßig wird die Vorschau nur aktualisiert, wenn der Shader geändert wird. Um dieses Verhalten zu ändern, sodass Sie zeitbasierte Effekte anzeigen können, müssen Sie das Echtzeit-Rendering aktivieren.  
  
###### <a name="to-enable-real-time-rendering"></a>So aktivieren Sie das Echtzeit-Rendering  
  
-   Wählen Sie auf der Shader-Designer-Symbolleiste **Real time Rendering** (Echtzeit-Rendering) aus.  
  
#### <a name="examining-the-effect"></a>Untersuchen des Effekts  
 Viele Shader werden von Variablen wie dem Anzeigewinkel oder der direktionalen Beleuchtung beeinflusst. Um zu untersuchen, wie der Effekt reagiert, wenn sich diese Variablen ändern, können Sie die Vorschauform frei drehen und beobachten, wie sich der Shader verhält.  
  
###### <a name="to-rotate-the-shape"></a>So drehen Sie die Form  
  
-   Halten Sie die ALT-TASTE gedrückt, wählen Sie einen beliebigen Punkt auf der Entwurfsoberfläche aus, und verschieben Sie diesen.  
  
### <a name="exporting-shaders"></a>Exportieren von Shadern  
 Bevor Sie einen Shader in Ihrer App verwenden können, müssen Sie ihn in ein Format exportieren, das DirectX versteht.  
  
 Sie können Shader als HLSL-Quellcode oder als kompilierten Shader-Bytecode exportieren. HLSL-Quellcode wird in eine Textdatei exportiert, die über die Dateierweiterung „.hlsl“ verfügt. Shader-Bytecode kann entweder in eine unformatierte Binärdatei exportiert werden, die über die Dateierweiterung „.cso“ verfügt, oder in eine C++-Headerdatei (.h), die den Shader-Bytecode in ein Array codiert.  
  
 Weitere Informationen zum Exportieren von Shadern finden Sie unter [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md).  
  
## <a name="keyboard-shortcuts"></a>Tastenkombinationen  
  
|Befehl|Tastenkombinationen|  
|-------------|------------------------|  
|In den Modus **Auswählen** wechseln|STRG+G, STRG+Q<br /><br /> S|  
|In den Modus **Zoom** wechseln|STRG+G, STRG+Z<br /><br /> Z|  
|In den Modus **Schwenken** wechseln|STRG+G, STRG+P<br /><br /> K|  
|Alles auswählen|STRG + A|  
|Die aktuelle Auswahl löschen|Löschen|  
|Brechen Sie die aktuelle Auswahl ab.|Escape|  
|Vergrößern|STRG+Mausrad vorwärts<br /><br /> Pluszeichen (+)|  
|Verkleinern|STRG+Mausrad rückwärts<br /><br /> Minuszeichen (-)|  
|Die Entwurfsoberfläche nach oben schwenken|Mausrad rückwärts<br /><br /> BILD-AB|  
|Die Entwurfsoberfläche nach unten schwenken|Mausrad vorwärts<br /><br /> BILD-AUF|  
|Die Entwurfsoberfläche nach links schwenken|UMSCHALT+Mausrad rückwärts<br /><br /> Mausrad links<br /><br /> UMSCHALT+BILD-AB|  
|Die Entwurfsoberfläche nach rechts schwenken|UMSCHALT+Mausrad vorwärts<br /><br /> Mausrad rechts<br /><br /> UMSCHALT+BILD-AUF|  
|Den Tastaturfokus auf einen anderen Knoten verschieben|Pfeiltasten|  
|Wählen Sie den Knoten aus, der über den Tastaturfokus verfügt (fügt den Knoten der Auswahlgruppe hinzu)|UMSCHALT+LEERTASTE|  
|Die Auswahl des Knotens wechseln, der über den Tastaturfokus verfügt|STRG+LEERTASTE|  
|Die aktuelle Auswahl wechseln (wenn keine Knoten ausgewählt sind, wählen Sie den Knoten aus, der über den Tastaturfokus verfügt)|LEERTASTE|  
|Die aktuelle Auswahl nach oben verschieben|UMSCHALT+NACH-OBEN|  
|Die aktuelle Auswahl nach unten verschieben|UMSCHALT+NACH-UNTEN|  
|Die aktuelle Auswahl nach links verschieben|STRG+NACH-LINKS|  
|Die aktuelle Auswahl nach rechts verschieben|UMSCHALT+NACH-RECHTS-TASTE|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Arbeiten mit 3D-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Bietet eine Übersicht über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Tools, die Sie bei der Arbeit mit Texturen und Bildern, 3D-Modellen und Shadereffekten verwenden können.|  
|[Bildbearbeitung](../designers/image-editor.md)|Beschreibt, wie der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bild-Editor für die Arbeit mit Texturen und Bildern verwendet wird.|  
|[Modell-Editor](../designers/model-editor.md)|Beschreibt, wie der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Modell-Editor für die Arbeit mit 3D-Modellen verwendet wird.|
