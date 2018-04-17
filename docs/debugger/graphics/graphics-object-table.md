---
title: Grafikobjekt-Tabelle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fce78395efff7ec1344d0034c4d18001550798aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="graphics-object-table"></a>Grafikobjekttabelle
Mit der Grafikobjekttabelle in Visual Studio-Grafikanalyse können Sie die Direct3D-Objekte erkennen, die einen Frame Ihres Spiels oder Ihrer App unterstützen.  
  
 Dies ist die Objekttabelle:  
  
 ![Direct3D-Objekte, die durch eine App erstellt wurden](media/gfx_diag_demo_object_table_orientation.png "Gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Die Grafikobjekttabelle verstehen  
 Mit der Objekttabelle können Sie Direct3D-Objekte analysieren, die das Rendern eines bestimmten Frames unterstützen. Sie können ein Renderingproblem auf ein bestimmtes Objekt zurückführen, indem Sie die Eigenschaften und Daten untersuchen (Mit anderen Grafikdiagnosetools können Sie früher in der Diagnose die Liste der Objekte einschränken, die möglicherweise nicht Ihren Erwartungen entsprechen.) Wenn Sie das problemauslösende Objekt gefunden haben, können Sie eine Visualisierung, die in den entsprechenden Typ untersuchen spezifisch ist – z. B. können Sie die Grafik-Editor, um Texturen anzusehen verwenden oder die *Puffer-Schnellansicht* um pufferinhalte anzuzeigen.  
  
 Die Objekttabelle unterstützt das Kopieren und Einfügen, sodass Sie ein anderes Tool, wie etwa Microsoft Excel, zum Überprüfen des Inhalts verwenden können.

 Darüber hinaus können Sie die **Typ** Dropdownliste am oberen linken Ecke zum Umschalten der Anzeige von Objekten des Typs **Puffer**, **Shader** oder **Texturen**, oder alle der folgenden Elemente auf einmal.  Darüber hinaus können Sie das Suchfeld in der oberen rechten Ecke zum Suchen von bestimmter Zeilen über alle Daten, die angezeigt werden.  Sie können z. B. Suchen Sie nach *D32_FLOAT* alle Instanzen von Objekten für dieses Format in der Liste gefunden.
  
### <a name="graphics-object-table-format"></a>Format der Grafikobjekttabelle  
 Die Objekttabelle zeigt die Direct3D-Objekte und die Ressourcen an, die den Frame unterstützen, der mit dem ausgewählten Ereignis verknüpft ist, beispielsweise Zustandsobjekte, Puffer, Shader, Texturen und andere Ressourcen. Nicht in die Objekttabelle aufgenommen werden Objekte, die in einem vorherigen Frame erstellt wurden und während des aufgezeichneten Frames nicht verwendet werden. Objekte, die während des aufgezeichneten Frames durch vorherige Ereignisse zerstört wurden, werden in den folgenden Ereignissen weggelassen. Objekte, die nicht auf D3D10Device oder D3D11DeviceContext festgelegt wurden, werden in grauer Schrift angezeigt. Objekte werden in einem Tabellenformat angezeigt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Bezeichner**|Die Objekt-ID.|  
|**Name**|Anwendungsspezifische Informationen, die für das Objekt mit der Direct3D-Funktion `SetPrivateData` festgelegt wurden (normalerweise zur Bereitstellung zusätzlicher Informationen über das Objekt).|  
|**Type**|Der Objekttyp.|  
|**Aktive**|Zeigt "*" für ein Objekt an, das während des aufgezeichneten Frames auf D3D10Device oder D3D11DeviceContext festgelegt wurde.<br /><br /> Dies entspricht den Objekten, die in grauer Schrift angezeigt werden, stellt aber einen Spalteneintrag bereit, mit dem Sie die Objekttabelle sortieren können.|  
|**Size**|Die Größe des Objekts in Bytes.|  
|**Format**|Das Format des Objekts. Beispielsweise das Format eines Texturobjekts oder das Shadermodell eines Shaderobjekts.|  
|**Breite**|Die Breite eines Texturobjekts. Gilt nicht für andere Objekttypen.|  
|**Höhe**|Die Höhe eines Texturobjekts. Gilt nicht für andere Objekttypen.|  
|**Tiefe**|Die Tiefe eines 3D-Texturobjekts. Wenn eine Textur nicht 3D ist, ist der Wert 0. Gilt nicht für andere Objekttypen.|  
|**MIPS**|Die Anzahl von MIP-Ebenen eines Texturobjekts. Gilt nicht für andere Objekttypen.|  
|**ArraySize**|Die Anzahl von Texturen in einem Texturarray. Der Bereich liegt zwischen 1 und einer von der aktuellen Funktionsebene definierten Obergrenze. Für eine Cubemap beträgt dieser Wert 6 mal die Anzahl der Cubemaps im Array.|  
|**Beispiele**|Die Anzahl der Mehrfachabtastungen pro Pixel.|  
  
## <a name="graphics-object-viewers"></a>Grafikobjekt-Viewer  
 Um Informationen zu einem Objekt anzuzeigen, öffnen Sie es, indem Sie seinen Namen in der Objekttabelle auswählen. Details über das Objekt werden in verschiedenen Formaten angezeigt, je nach Typ des Objekts. Texturen werden beispielsweise unter Verwendung des Textur-Viewers und Gerätestatus angezeigt, z. B. wird Gerätekontext D3D11 als formatierte Liste angezeigt. Unterschiedliche Versionen von Direct3D verwenden unterschiedliche Objekte, und es gibt häufig spezifische Schnellansichten für die wichtigsten Objekte der einzelnen Versionen.  
  
 Hier ist der Textur-Viewer mit dem Inhalt der Pipelinestufe „Ausgabemerge“.  
  
 ![Die texturvorschau mit Anzeige des ausgabemerge](media/gfx_diag_texture_preview.png "Gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>D3D12-Befehlsliste  
 In Direct3D 12 ist eine Befehlsliste ein Objekt, von dem Befehle in einer Befehlszuweisung aufgezeichnet werden, damit sie an die GPU als eine einzelne Anforderung gesendet werden können. Befehlslisten führen in der Regel eine Reihe von Statuseinstellungen aus, zeichnen, deaktivieren und kopieren Befehle. Sie sind besonders wichtig, da sie die bevorzugte Methode für das Rendern in Direct3D 12 sind und zwischen den Frames zur Leistungsoptimierung erneut verwendet werden können. Details zur Befehlsliste werden mit Informationen zu den einzelnen Pipelinestufen auf einer eigenen Registerkarte in einem neuen Dokumentfenster angezeigt.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>D3D12-Pipelinestatusobjekt (PSO)  
 In Direct3D 12 stellt ein Pipelinestatusobjekt einen erheblichen Teil der GPU-Status dar, einschließlich aller derzeit festgelegten Shader und bestimmter Statusobjekte mit festen Funktionen. Nach der Erstellung ist ein Pipelinestatusobjekt unveränderlich – eine Anwendung kann die Konfiguration der Pipeline nur durch die Bindung eines anderen Pipelinestatusobjekts ändern. PSO-Details werden in einem neuen Dokumentfenster angezeigt, wobei die Details der Pipelinekonfiguration hierarchisch angeordnet sind.  
  
### <a name="d3d12-root-signature"></a>D3D12-Stammsignatur  
 In Direct3D 12 definiert die Stammsignatur alle Ressourcen, die an eine Grafik- oder Computepipeline gebunden sind und verknüpft Befehlslisten mit für den Shader erforderlichen Ressourcen. In der Regel gibt es in einer App eine Stammsignatur für Grafiken und eine für Compute. Stammsignaturdetails werden in einem neuen Dokumentfenster angezeigt, wobei die Details der Stammsignatur hierarchisch angeordnet sind.  
  
### <a name="d3d12-resources"></a>D3D12-Ressourcen  
 In Direct3D-12 sind Ressourcen Catchall-Objekte, die Daten für die Renderingpipeline bereitstellen. Dies steht im Gegensatz zu Direct3D11, wo viele spezifische Objekte für verschiedene Arten und Dimensionen von Ressourcen definiert werden. Eine Direct3D 12-Ressource kann Texturdaten, Scheitelpunktdaten, Shaderdaten und mehr enthalten – sie kann sogar Renderziele, z. B. Tiefenpuffer, darstellen. Einzelheiten über eine Direct3D 12-Ressource werden in einem neuen Dokumentfenster angezeigt. Die Grafikanalyse verwendet den entsprechenden Viewer für den Inhalt des Ressourcenobjekts, wenn dessen Typ bestimmt werden kann. Beispielsweise wird ein Ressourcenobjekt mit Texturdaten mit dem Textur-Viewer angezeigt, wie bei einem D3D11 Texture2D-Objekt.  
  
### <a name="device-context-object"></a>Gerätekontextobjekt  
 In Direct3D 11 und Direct3D 10 ist im Gerätekontext (**D3D11-Gerätekontext** oder **D3D10-Gerät**) Objekt ist besonders wichtig, da es die wichtigste Zustandsinformationen enthält, und es enthält zu anderen Links Statusobjekte, die momentan festgelegt sind. Gerätekontextdetails werden in einem neuen Dokumentfenster angezeigt, und jede Kategorie von Informationen wird dort auf einer eigenen Registerkarte angezeigt. Der Gerätekontext ändert sich, wenn ein neues Ereignis ausgewählt wird, um den aktuellen Gerätezustand wiederzugeben.  
  
### <a name="buffer-object"></a>Pufferobjekt  
 Pufferobjektdetails (D3D11-Puffer oder D3D10-Puffer) werden in einem neuen Dokumentfenster angezeigt, das den Pufferinhalt in einer Tabelle darstellt und eine Schnittstelle bereitstellt, um die Art und Weise, wie Pufferinhalt angezeigt wird, zu ändern. Die **Daten zu Puffern** Tabelle unterstützt das Kopieren und einfügen, damit Sie ein anderes Tool verwenden können, z. B. Microsoft Excel – zum Überprüfen des Inhalts. Der Inhalt des Puffers wird gemäß dem Wert des interpretiert die **Format** Kombinationsfeld oben befindet sich die **Puffern von Daten** Tabelle. Im Feld können Sie ein zusammengesetztes Datenformat eingeben, das aus den Datentypen besteht, die in der folgenden Tabelle aufgelistet sind. Beispielsweise zeigt "float int" eine Liste von Strukturen an, die einen 32-Bit-Gleitkommawert enthalten, dem ein 32-Bit-Ganzzahlwert mit Vorzeichen folgt. Zusammengesetzte Datenformate, die Sie angegeben haben, werden dem Kombinationsfeld zur späteren Verwendung hinzugefügt.  
  
 Sie können auch Umschalten der **Offsets anzeigen** Kontrollkästchen, um die Offsets der einzelnen Elemente im Puffer, anzeigen oder ausblenden.  
  
|Typ|Beschreibung|  
|----------|-----------------|  
|**float**|Ein 32-Bit-Gleitkommawert.|  
|**float2**|Ein Vektor, der zwei 32-Bit-Gleitkommawerte enthält.|  
|**float3**|Ein Vektor, der drei 32-Bit-Gleitkommawerte enthält.|  
|**FLOAT4**|Ein Vektor, der vier 32-Bit-Gleitkommawerte enthält.|  
|**byte**|Ein 8-Bit-Ganzzahlwert mit Vorzeichen|  
|**2-byte**|Ein 16-Bit-Ganzzahlwert mit Vorzeichen.|  
|**4-byte**|Ein 32-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **Int**.|  
|**8-byte**|Ein 64-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **int64**.|  
|**xbyte**|Ein 8-Bit-Hexadezimalwert|  
|**x2byte**|Ein 16-Bit-Hexadezimalwert|  
|**x4byte**|Ein 32-Bit-Hexadezimalwert Identisch mit **Xint**.|  
|**x8byte**|Ein 64-Bit-Hexadezimalwert Identisch mit **xint64**.|  
|**ubyte**|Ein 8-Bit-Ganzzahlwert ohne Vorzeichen.|  
|**u2byte**|Ein 16-Bit-Ganzzahlwert ohne Vorzeichen.|  
|**u4byte**|Ein 32-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **"uint"**.|  
|**u8byte**|Ein 64-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **uint64**.|  
|**die Hälfte**|Ein 16-Bit-Gleitkommawert.|  
|**Hälfte2**|Ein Vektor, der zwei 16-Bit-Gleitkommawerte enthält.|  
|**half3**|Ein Vektor, der drei 16-Bit-Gleitkommawerte enthält.|  
|**half4**|Ein Vektor, der vier 16-Bit-Gleitkommawerte enthält.|  
|**double**|Ein 64-Bit-Gleitkommawert.|  
|**int**|Ein 32-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **4-Byte**.|  
|**int64**|Ein 64-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **8byte**.|  
|**xint**|Ein 32-Bit-Hexadezimalwert Identisch mit **x4byte**.|  
|**xint64**|Ein 64-Bit-Hexadezimalwert Identisch mit **x8byte**.|  
|**uint**|Ein 32-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **u4byte**.|  
|**uint64**|Ein 64-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **u8byte**.|  
|**bool**|Ein boolescher Wert (`true` oder `false`) Jeder boolesche Wert wird durch einen 32-Bit-Wert dargestellt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Grafikdiagnose (Debuggen DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)   
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus](walkthrough-missing-objects-due-to-device-state.md)