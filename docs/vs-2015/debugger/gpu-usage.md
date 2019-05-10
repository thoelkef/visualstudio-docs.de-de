---
title: GPU-Nutzung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7dee579f726a1edfc81e1f3e1ec62bf7d8beba4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437956"
---
# <a name="gpu-usage"></a>GPU-Nutzung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie das GPU-Nutzungstool im Visual Studio-Leistungs- und Diagnosehub, um die allgemeine Hardwarenutzung Ihrer Direct3D-App besser zu verstehen. Mit dem Tool können Sie feststellen, ob die Leistung Ihrer App CPU- oder GPU-gebunden ist, und Sie erhalten Einblicke in eine effektivere Nutzung der Plattformhardware. GPU-Nutzung unterstützt Apps, die Direct3D 12, Direct3D 11 und Direct3D 10 verwenden. Andere Grafik-APIs, wie z. B. Direct2D oder OpenGL werden nicht unterstützt.  
  
 Im Folgenden ist das Fenster **GPU-Nutzungsbericht** dargestellt:  
  
 ![Der GPU-Nutzungsbericht mit CPU- und GPU-Zeitplänen](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Anforderungen  
 Im Folgenden werden Anforderungen für die Verwendung des GPU-Nutzungstools aufgeführt, die zusätzlich zu den Anforderungen der Grafikdiagnose gelten.  
  
- Ein Grafikprozessor und Treiber, die die erforderliche zeitliche Timinginstrumentierung unterstützen.  
  
  > [!NOTE]
  > Weitere Informationen zu unterstützter Hardware und unterstützten Treibern finden Sie unter [Unterstützte Hardware und Treiber](#hwsupport) am Ende dieses Dokuments.  
  
  Weitere Informationen zu Anforderungen für die Grafikdiagnose finden Sie unter [Erste Schritte](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Verwenden des GPU-Nutzungstools  
 Wenn Sie Ihre App im GPU-Nutzungstool ausführen, erstellt Visual Studio eine Diagnosesitzung, die allgemeine Informationen zur Renderingleistung und GPU-Auslastung Ihrer App in Echtzeit in Diagrammen darstellt.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>So starten Sie das GPU-Nutzungstool:  
  
1. Wählen Sie im Hauptmenü **Debuggen** und dann **Leistung und Diagnose** (Tastatur: Drücken Sie Alt+F2).  
  
2. Aktivieren Sie im Leistungs- und Diagnosehub das Kontrollkästchen neben **GPU-Nutzung**. Aktivieren Sie optional die Kontrollkästchen neben anderen gewünschten Tools. Sie können mehrere Leistungs- und Diagnosetools gleichzeitig ausführen, um ein umfassenderes Bild der Leistung Ihrer App zu erhalten.  
  
    ![Wählen Sie die Diagnosetools, die Sie verwenden möchten.](../debugger/media/gfx-diag-diagsession-tools.png "gfx_diag_diagsession_tools")  
  
   > [!NOTE]
   > Nicht alle Leistungs- und Diagnosetools können gleichzeitig verwendet werden.  
  
3. Wählen Sie die blaue Schaltfläche **Start** am unteren Rand des Leistungs- und Diagnosehubs, um Ihre App unter den ausgewählten Tools auszuführen.  
  
   Allgemeine Informationen, die in Echtzeit angezeigt werden, umfassen Frametiming, Framerate und GPU-Auslastung. Jedes dieser Datenelemente wird unabhängig voneinander in einem Diagramm dargestellt, es wird jedoch eine gemeinsamen Zeitskala verwendet, sodass Sie diese problemlos in Beziehung zueinander setzen können.  
  
   Die Diagramme **Framedauer (ms)** und **Frames pro Sekunde (FPS)** enthalten zwei rote, horizontale Linien, die Leistungsziele von 60 und 30 Frames pro Sekunde darstellen. Im Diagramm **Framedauer** überschreitet Ihre App das Leistungsziel, wenn sich das Diagramm unterhalb der Linie befindet, und verfehlt es, wenn sich das Diagramm oberhalb der Linie befindet. Im Diagramm „Frames pro Sekunde“ verhält es sich umgekehrt. Wenn sich das Diagramm oberhalb der Linie befindet, überschreitet die App das Leistungsziel, und wenn es sich unterhalb der Linie befindet, verfehlt sie das Leistungsziel. Diese Diagramme werden in erster Linie verwendet, um eine allgemeine Vorstellung der Leistung Ihrer App zu erhalten und ggf. Leistungseinbußen zu ermitteln, u. a. einen plötzlichen Abfall der Framerate oder einen Spitzenwert der GPU-Auslastung.  
  
   Wenn Sie Ihre App im GPU-Nutzungstool ausführen, erfasst die Diagnosesitzung auch detaillierte Informationen zu den auf GPU ausgeführten Grafikereignissen. Diese Informationen werden verwendet, um einen präziseren Bericht zur Hardwarenutzung Ihrer App zu erstellen. Da es einige Zeit dauert, diesen Bericht anhand der erfassten Informationen zu generieren, steht dieser nur zur Verfügung, wenn die Diagnosesitzung das Erfassen von Informationen bereits abgeschlossen hat.  
  
   Wenn Sie sich ein Problem mit der Leistung oder Auslastung näher anschauen möchten, müssen Sie die Erfassung von Leistungsinformationen beenden, damit der Bericht generiert werden kann  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>So generieren Sie einen GPU- Nutzungsbericht und zeigen diesen an:  
  
1. Wählen Sie im unteren Bereich des Fensters „Diagnosesitzung“ den Link **Auflistung beenden**, oder drücken Sie oben links **Beenden**.  
  
    ![Erfassen Sie GPU- und CPU-Zeitsteuerungsinformationen.](../debugger/media/gfx-diag-gpu-usage-collect.png "gfx_diag_gpu_usage_collect")  
  
2. Wählen Sie im oberen Bereich des Berichts einen Abschnitt aus einem der Diagramme, die das Problem anzeigt, das Sie untersuchen möchten. Die Auswahl kann bis zu drei Sekunden umfassen. Längere Abschnitte werden in Richtung Anfang gekürzt.  
  
    ![Nach dem Erfassen, wählen Sie einen Bereich zum Anzeigen von Details](../debugger/media/gfx-diag-gpu-usage-select1.png "gfx_diag_gpu_usage_select1")  
  
3. Wählen Sie im unteren Bereich des Berichts den Link **Details anzeigen** in der Meldung **...Klicken Sie hier, um detaillierte Informationen zur GPU-Nutzung für diesen Bereich anzuzeigen**, um eine detaillierte Zeitachse der Auswahl anzuzeigen.  
  
    ![Nach dem Erfassen, mit ausgewähltem Bereich](../debugger/media/gfx-diag-gpu-usage-select2.png "gfx_diag_gpu_usage_select2")  
  
   Es wird ein neues Dokument im Registerkartenformat mit dem Bericht geöffnet. Mithilfe des GPU-Nutzungsberichts können Sie sehen, wann ein Grafikereignis auf CPU gestartet wurde, wann es GPU erreicht und wie lange die Ausführung auf GPU gedauert hat. Anhand dieser Informationen können Sie Engpässe und Möglichkeiten für eine verbesserte Parallelität in Ihrem Code erkennen.  
  
## <a name="using-the-gpu-usage-report"></a>Verwenden des GPU-Nutzungsberichts  
 Im oberen Teil des GPU-Nutzungsberichts werden Zeitachsen für die CPU-Verarbeitungsvorgänge, GPU-Renderingvorgänge und GPU-Kopiervorgänge. Diese Zeitachsen werden durch hellgraue, vertikale Balken unterteilt, die VSync der Anzeige darstellen; die Häufigkeit der Balken entspricht der Aktualisierungsrate einer der Anzeigen (ausgewählt mithilfe des Dropdownmenüs **Anzeige**), aus der die GPU-Nutzungsdaten erfasst wurden. Da die Anzeige eine höhere Aktualisierungsrate als das Leistungsziel Ihrer App haben kann, besteht ggf. keine 1:1-Beziehung zwischen Vsync und der Framerate, die Ihre App erreichen soll. Damit eine App das Leistungsziel erreichen kann, muss sie alle Verarbeitungsvorgänge abgeschlossen, Renderingvorgänge ausgeführt und einen Present()-Aufruf innerhalb der als Ziel festgelegten Framerate getätigt haben. Das gerenderte Frame wird bis zum nächsten VSync nach Present() nicht angezeigt.  
  
 Im unteren Abschnitt werden Grafikereignisse aufgelistet, die innerhalb des Berichtszeitraums aufgetreten sind.   
  
 Im Folgenden ist das Fenster **GPU-Nutzungsbericht** dargestellt:  
  
 ![Der GPU-Nutzungsbericht mit CPU- und GPU-Zeitplänen](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
 Beim Auswählen eines Ereignisses im unteren Bereich des Berichts wird ein Marker auf den entsprechenden Ereignissen auf den relevanten Zeitachsen platziert, in der Regel ein Ereignis in einem CPU-Thread, der den API-Aufruf darstellt, und ein anderes Ereignis auf einer GPU-Zeitachse, die angibt, wann eine Aufgabe von GPU abgeschlossen wurde. Ebenso wird beim Auswählen eines Ereignisses in einer Zeitachse das entsprechende Ereignis im unteren Bereich des Berichts hervorgehoben. Wenn eine Zeitachse im oberen Bereich des Berichts verkleinert wurde, werden nur die zeitaufwändigsten Ereignisse angezeigt. Zum Anzeigen von Ereignissen mit einer kürzeren Dauer können Sie die Zeitachsen mithilfe von STRG+Mausrad oder des Skalierungssteuerelements in der unteren linken Ecke des oberen Bereichs vergrößern. Sie können auch die Inhalte des Zeitachsenbereichs ziehen, um durch die erfassten Ereignisse zu navigieren.  
  
 Damit Sie leichter das finden, was Sie suchen, können Sie den GPU-Nutzungsbericht nach Prozessnamen, Thread-IDs und Ereignisname filtern. Des Weiteren können Sie die Aktualisierungsrate der Anzeige wählen, die die VSync-Zeilen bestimmt, und Ereignisse hierarchisch sortieren, wenn Ihre App die ID3DUserDefinedAnnotation-Schnittstelle für Gruppenrenderingbefehle verwendet.  
  
 Nachstehend finden Sie weitere Details:  
  
|Filtersteuerelement|Beschreibung|  
|--------------------|-----------------|  
|**Process**|Der Name des Prozesses, der Sie interessiert. Alle Prozesse, die GPU während der Diagnosesitzung verwenden, sind in dieser Dropdownliste enthalten. Die dem Prozess in dieser Dropdownliste zugeordnete Farbe entspricht der Farbe der Threadvorgänge auf den Zeitachsen unten.|  
|**Thread**|Die Thread-ID, die Sie interessiert. In einer Multithread-App können Sie hiermit bestimmte Threads isolieren, die mit dem gewünschten Prozess verknüpft sind. Die im Zusammenhang mit dem ausgewählten Thread stehenden Ereignisse werden auf jeder Zeitachse hervorgehoben.|  
|**Anzeige**|Die Nummer der Anzeige, deren Aktualisierungsrate angezeigt wird. **Hinweis:**  Einige Treiber können so konfiguriert werden, dass mehrere physische Anzeigen als eine einzelne, große virtuelle Anzeige dargestellt werden. Selbst wenn mehrere Monitore an den Computer angeschlossen sind, wird ggf. nur eine Anzeige aufgeführt.|  
|**Filter**|Die Schlüsselwörter, die Sie interessieren. Ereignisse im unteren Bereich des Berichts beinhalten nur diejenigen, die mit einem Schlüsselwort ganz oder teilweise übereinstimmen. Sie können mehrere Schlüsselwörter durch Semikolons (;) getrennt angeben.|  
|**Hierarchische Sortierung**|Ein Kontrollkästchen, das angibt, ob durch Benutzermarkierungen definierte  Ereignishierarchien beibehalten oder ignoriert werden.|  
  
 Die Liste der Ereignisse im unteren Bereich des GPU-Nutzungsberichts enthält detaillierte Informationen zu jedem Ereignis.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Ereignisname**|Der Name des Grafikereignisses. Ein Ereignis entspricht in der Regel einem Ereignis auf einer CPU-Threadzeitachse und einem Ereignis auf einer GPU-Zeitachse.<br /><br /> Ereignisnamen weisen möglicherweise keine Attribute auf, wenn die GPU-Nutzung nicht den Namen eines Ereignisses bestimmen konnte. Weitere Informationen finden Sie unter dieser Tabelle.|  
|**CPU-Start (ns)**|Die Zeit, zu der das Ereignis auf der CPU durch Aufrufen einer Direct3D-API initiiert wurde. Die Zeit wird in Nanosekunden relativ zum Start der Anwendung gemessen.|  
|**GPU-Start (ns)**|Die Zeit, zu der das Ereignis auf der GPU initiiert wurde. Die Zeit wird in Nanosekunden relativ zum Start der App gemessen.|  
|**GPU-Dauer (ns)**|Die Zeit in Nanosekunden, die das Abschließen des Ereignisses in der GPU gedauert hat.|  
|**Prozessname**|Der Name der App, von der das Ereignis stammt.|  
|**Thread-ID**|Die Thread-ID, von der das Ereignis stammt.|  
  
> [!IMPORTANT]
> Windows 8.1 ist für Ereignisattribute erforderlich. Wenn GPU oder Treiber nicht die erforderlichen Instrumentationsfeatures unterstützen, werden darüber hinaus alle Ereignisse mit dem Zusatz „ohne Attribute“ aufgeführt. Stellen Sie sicher, dass Ihr GPU-Treiber aktualisiert ist, und versuchen Sie es erneut, wenn dieses Problem auftritt. Weitere Informationen finden Sie unter [Unterstützte Hardware und Treiber](#hwsupport) weiter unten.  
  
## <a name="gpu-usage-settings"></a>GPU-Nutzungseinstellungen  
 Sie können das GPU-Nutzungstool so konfigurieren, dass die Erfassung von Profilerstellungsinformationen zurückgestellt wird, und nicht bereits beim Appstart beginnt. Da die Größe der Profilerstellungsinformationen beträchtlich sein kann, ist dies hilfreich, dass es erst zu einem späteren Zeitpunkt zur Verlangsamung der Leistung Ihrer App kommt.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>So stellen Sie die Profilerstellung beim Start der App zurück  
  
1. Wählen Sie im Hauptmenü **Debuggen** und dann **Leistung und Diagnose** (Tastatur: Drücken Sie Alt+F2).  
  
2. Klicken Sie im Leistungs- und Diagnosehub auf den Link **Einstellungen** neben **GPU-Nutzung**.  
  
3. Deaktivieren Sie unter **GPU-Profilerstellungskonfiguration** auf der Eigenschaftenseite **Allgemein** das Kontrollkästchen **Profilerstellung beim Appstart beginnen**, um die Profilerstellung zurückzustellen.  
  
     ![Konfigurieren, wenn die GPU-Nutzungserfassung startet](../debugger/media/gfx-diag-gpu-usage-config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
> Das Zurückstellen der Profilerstellung wird derzeit nicht für Direct3D 12-Apps unterstützt.  
  
 Wenn Sie die Erfassung von Profilerstellungsinformationen mit dieser Einstellung zurückstellen, steht im unteren Bereich des GPU-Nutzungstoolfensters ein zusätzlicher Link zur Verfügung, wenn Sie die App im GPU-Nutzungstool ausführen. Wählen Sie zum Starten der Erfassung von Profilinformationen den Link **Starten** in der Meldung **Erfassung detaillierter GPU-Nutzungsdaten starten**.  
  
## <a name="hwsupport"></a> Unterstützte Hardware und Treiber  
 Folgende GPU-Hardware und Treiber werden unterstützt:  
  
|Hersteller|GPU-Beschreibung|Erforderliche Treiberversion|  
|------------|---------------------|-----------------------------|  
|Intel®|Intel® Core Prozessoren der vierten Generation („Haswell“)<br /><br /> -   Intel® HD-Grafik (GT1)<br />-   Intel® HD-Grafik 4200 (GT2)<br />-   Intel® HD-Grafik 4400 (GT2)<br />-   Intel® HD-Grafik 4600 (GT2)<br />-   Intel® HD-Grafik P4600 (GT2)<br />-   Intel® HD-Grafik P4700 (GT2)<br />-   Intel® HD-Grafik 5000 (GT3)<br />-   Intel® Iris™ Grafik 5100 (GT3)<br />-   Intel® Iris™ Pro Grafik 5200 (GT3e)|-- (Verwenden Sie die neuesten Treiber)|  
|AMD®|Die meisten ab der AMD Radeon™ HD 7000-Serie (AMD Radeon™ HD 7350-7670 ausgeschlossen)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ Grafikkarten und GPU-Beschleuniger von AMD FirePro mit Graphics Core Next (GCN)-Architektur.<br /><br /> Accelerated Processing Units (APUs) der AMD® E-Serie und AMD A-Serie mit Graphics Core Next (GCN)-Architektur („Kaveri“, „Kabini“, „Temash“, „Beema“, „Mullins“)|14.7 RC3 oder höher|  
|NVIDIA®|Die meisten ab NVIDIA GeForce®-400-Serie.<br /><br /> NVIDIA® GeForce® GPUs, NVIDIA Quadro® GPUs und NVIDIA® Tesla™ GPU-Beschleuniger mit Fermi™-, Kepler™-, oder Maxwell™-Architektur.|343.37 oder höher|  
  
 Multi-GPU-Konfigurationen, wie z. B. die NVIDIA® SLI™ und AMD Crossfire™ werden derzeit nicht unterstützt. Hybrid-Grafik-Setup, z. B. NVIDIA® Optimus™ und AMD Enduro™ werden unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
  
- [Solve the Tough Graphics Problems with your Game Using DirectX Tools (video) (Lösen Sie die großen Grafikprobleme bei Ihrem Spiel mithilfe von DirectX-Tools (Video))](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
- [GPU Usage Tool in Visual Studio (video) (GPU-Auslastungstool in Visual Studio (Video))](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
- [GPU Usage tool in Visual Studio 2013 Update 4 CTP1 (blog) (GPU-Auslastungstool in Visual Studio 2013 Update 4 CTP1 (Blog))](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
  
- [GPU Usage for DirectX in Visual Studio (blog) (GPU-Auslastung für DirectX in Visual Studio (Blog))](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)
