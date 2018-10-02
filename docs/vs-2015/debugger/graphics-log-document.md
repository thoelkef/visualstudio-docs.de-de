---
title: Grafikprotokolldokument | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385744b280bbd8069acef4da0a36ae9bd9716fcb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512628"
---
# <a name="graphics-log-document"></a>Grafikprotokolldokument
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Grafikprotokolldokument](https://docs.microsoft.com/visualstudio/debugger/graphics/graphics-log-document).  
  
Das Grafikprotokolldokument enthält die beim Ausführen Ihrer App in einer Grafikdiagnosesitzung aufgetretenen Grafikereignisse. Wenn das Prokotoll erstellt wurde, können Sie es in der Visual Studio-Grafikanalyse auf Renderings- und Leistungsprobleme durchsuchen.  
  
 So sieht ein Grafikprotokolldokument in der Grafikanalyse aus:  
  
 ![Diagrammprotokoll mit zwei erfasste Rahmen. ](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "Gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Grundlegendes zu Grafikprotokolldokumenten  
 Wenn Sie das Grafikprotokolldokument mithilfe der Grafikanalyse überprüfen, können Sie die erfassten Auswirkungen von Direct3D-Ereignissen auf das Renderziel visuell darstellen. Sie können Bereiche des Renderziels festlegen, die unerwartete Ausgabe enthalten. Wenn Sie ein Pixel im betroffenen Bereich auswählen, können Sie dieses, seine Shader, die Direct3D-Ereignisse, die Auswirkungen auf das Pixel hatten, die Anwendungsaufrufliste, die zu diesen Ereignissen führte, sowie die DirectX-Objekte, die diese Ereignisse unterstützen, mit der Grafikdiagnose überprüfen. Sie können diese Informationen verwenden, um Renderingprobleme im Spiel oder in der App zu bestimmen.  
  
 Der obere Bereich des Fensters (**Graphics Experiment.vsglog**) zeigt die aktuelle renderzielausgabe der ausgewählten Frames und im unteren Teil wird ein **Frameliste** , die Miniaturbilder der enthält die erfasste Frames.  
  
#### <a name="to-inspect-a-frame"></a>So überprüfen einen Frame  
  
-   In der **Frameliste**, wählen Sie den Rahmen, die Sie untersuchen möchten. Die Renderzielausgabe im obersten Abschnitt des Grafikprotokolldokuments wird aktualisiert und zeigt den ausgewählten Frame an.  
  
#### <a name="to-inspect-a-pixel"></a>So überprüfen Sie ein Pixel  
  
-   Wählen Sie das gewünschte Pixel im obersten Abschnitt des Grafikprotokolldokuments aus der Renderzielausgabe aus. Wenn Sie ein Pixel ausgewählt wurde, können Sie mithilfe der **Grafikpixelverlauf** Fenster aus, um ausführliche Informationen über das ausgewählte Pixel anzeigen. Weitere Informationen finden Sie unter [Pixelverlauf](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Wiedergabecomputer  
 Auch angezeigt, in der oberen rechten Ecke des der **Frameliste** ist die **Wiedergabecomputer**. Der Wiedergabecomputer ist ein Computer oder ein Gerät, das Grafikereignisse aus einer Grafikprotokolldatei während einer späteren Grafikdiagnosesitzung wiedergibt. Wenn Sie ein anderes Gerät als Ihren Entwicklungscomputer zur Wiedergabe der aufgezeichneten Ereignisse verwenden, können Sie die Ausführungsumgebung genauer reproduzieren, in der das Problem aufgetreten ist – Sie können beispielsweise einen Computer mit anderer Grafikhardware oder anderen Treibern als Ihr Entwicklungscomputer oder andere Arten von Geräten verwenden, z. B. ein ARM-basiertes Windows RT-Tablet oder ein Gerät mit Windows Phone.  
  
 Weitere Informationen zur Vorgehensweise beim Angeben eines wiedergabecomputers finden Sie unter [Vorgehensweise: Ändern Sie die Grafikdiagnose-Wiedergabecomputers](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Kurzinformationen zum Grafikprotokoll  
 Wenn eine grafikprotokolldatei das aktive Dokument ist die **Eigenschaften** Fenster zeigt Informationen über die Umgebung, die die Grafikdiagnose-erfassungssitzung gehostet. Es werden verschiedene Kategorien von Informationen angezeigt.  
  
 **Direct3D-Informationen**  
 Führt Informationen über die Hardwarekonfiguration und Treiberfunktionen der Grafikkarte auf, die während der Erfassungssitzung verwendet wurde.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**10-Bit XR-Format mit hoher Farbtiefe**|**"True"** ist 10-Bit XR-Format mit hoher Farbtiefe unterstützt wird; anderenfalls **"false"**.|  
|**DirectCompute CS 4.x**|**"True"** Wenn Compute-Shader 4.0 unterstützt; andernfalls wird **"false"**.|  
|**Shader mit doppelter Genauigkeit**|**"True"** , wenn die Grafikkarte Gleitkommazahl mit doppelter Genauigkeit (64-Bit)-Werte; unterstützt, andernfalls **"false"**.|  
|**Treiber-Befehlslisten**|**"True"** , wenn der Treiber befehlslisten unterstützt; andernfalls **"false"**.|  
|**Treiber-Simultanerstellungen**|**"True"** Wenn der Treiber die gleichzeitige (asynchrone) Erstellung unterstützt, andernfalls **"false"**.|  
|**Erweiterte Formate (BGRA usw.)**|**"True"** Wenn erweiterte Formate wie BGRA unterstützt; andernfalls werden **"false"**.|  
|**Maximale Hardwarefunktionsebene**|Zeigt die höchste Funktionsebene an, die über die Grafikkarte unterstützt wird.|  
  
 **Anzeigen von Informationen**  
 Führt Informationen über die Grafikkarte auf, die während der Erfassungssitzung verwendet wurde.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Beschreibung**|Die Zeichenfolge für die Grafikkartenbeschreibung.|  
|**Anzeigespeicher**|Der Speicherplatz, der auf der Grafikkarte installiert ist.|  
|**Treibername**|Der Name des Grafikkartentreibers.|  
|**Treiberversion**|Die Version des Grafikkartentreibers.|  
|**Name**|Der Name der Grafikkarte.|  
  
 **Experimentedatei**  
 Listet Informationen über die Experimentedatei auf, die mit dieser Erfassungssitzung verknüpft ist.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Pfad**|Der Pfad der .vsglog-Datei. **Hinweis:** in früheren Erfassungen wird diese Eigenschaft nicht verwendet.|  
  
 **Modulinformationen**  
 Führt den Namen und die Version der Dynamic Link Librarys (DLL) auf, die während der Erfassungssitzung durch die App geladen wurden.  
  
 **Systeminformationen**  
 Führt Informationen über die Hardware und das Betriebssystem auf, die die App während der Erfassungssitzung gehostet haben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Arbeitsspeicher**|Der Speicher, der auf dem Computer installiert ist.|  
|**BS-Architektur**|Die CPU-Architektur des Betriebssystems des Zielcomputers.|  
|**Betriebssystemversion**|Die Version des Betriebssystems.|  
|**Prozessor**|Der Prozessor, der auf dem Computer installiert ist.|  
|**Architektur der Zielanwendung**|Die CPU-Architektur der App auf dem Zielcomputer. Dies kann sein, anders als die **Betriebssystemarchitektur**.|  
  
 **Zielanwendung**  
 Führt Informationen über die App auf, die von der Erfassungssitzung erfasst wird.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Datum/Uhrzeit der letzten Änderung**|Datum und Uhrzeit der Erstellung der App.|  
|**Pfad**|Der Pfad der App.|  
|**Prozess-ID**|Die Prozess-ID, die zur App angegeben wurde.|  
|**Version**|Die App-Version.|  
  
 **VSG-Protokolldatei**  
 Führt Informationen über das Grafikprotokolldokument auf.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Erstellt von**|Der Name der App, die das Grafikprotokolldokument erstellt hat. Wenn die Erfassungssitzung z. B. von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] initiiert wurde (manuelle Erfassung) ist der Wert dieser Eigenschaft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|**Startzeit der Sitzung**|Das Datum und die Uhrzeit, zu der die Erfassungssitzung begann.|  
|**Size**|Die Größe des Grafikprotokolldokuments.|  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Vertex-Shading](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



