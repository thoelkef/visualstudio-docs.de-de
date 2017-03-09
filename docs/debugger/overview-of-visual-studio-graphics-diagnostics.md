---
title: "&#220;bersicht &#252;ber Visual Studio-Grafikdiagnose | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# &#220;bersicht &#252;ber Visual Studio-Grafikdiagnose
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die *Grafikdiagnose* von Visual Studio umfasst eine Reihe von Tools zum Aufzeichnen und anschließenden Analysieren von Rendering\- und Leistungsproblemen in Direct3D\-Apps.  Die Grafikdiagnose kann für Apps verwendet werden, die lokal auf Ihrem Windows\-PC, in einem Windows\-Geräteemulator oder auf einem Remotecomputer oder\-gerät ausgeführt werden.  
  
## Verwenden der Grafikdiagnose zum Debuggen von Renderingproblemen  
 Das Debuggen von Renderingproblemen in einer grafisch aufwendigen App ist kein einfaches Starten des Debuggers und die schrittweise Untersuchung des Codes.  In jeden Frame werden Hunderttausende eindeutige Pixel erzeugt, wobei jedes einen komplexen Satz aus Zustand, Daten, Parameter und Code enthält – und von diesen Pixeln liefern möglicherweise nur wenige Hinweise auf das Problem, das Sie zu diagnostizieren versuchen.  Darüber hinaus wird der Code, der die einzelnen Pixel generiert, auf spezialisierter Hardware ausgeführt, die Hunderte Pixel parallel verarbeitet.  Herkömmliche Debugtools und \-techniken, für die bereits Code mit wenigen Threads ein Problem darstellt, sind bei so großen Datenmengen wirkungslos.  
  
 Die Grafikdiagnose\-Tools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurden für die Suche nach den Ursprüngen von Renderingproblemen entwickelt. Sie beginnen mit den visuellen Artefakten, die auf das Problem hinweisen, und verfolgen dann das Problem zurück zu seinem Ursprung, wobei der Fokus auf den zugehörigen Shader\-Code, die Grafikpipelinestufen, die Zeichnen\-Aufrufe, die Ressourcen, den Gerätezustand und sogar auf den Quellcode der App gelegt wird.  
  
## DirectX\-Versionskompatibilität  
 Die Grafikdiagnose unterstützt Apps, die Direct3D 12, Direct3D 11 und Direct3D 10 verwenden, und bietet eingeschränkte Unterstützung für Apps, die Direct2D verwenden.  Sie unterstützt keine Apps, die frühere Versionen von Direct3D und DirectDraw verwenden oder andere Grafik\-APIs.  
  
### Windows 10 und Direct3D 12  
 Mit Windows 10 wird die nächste Version von Direct3D eingeführt: *Direct3D 12*. Diese unterscheidet sich deutlich von Direct3D 10 und Direct3D 11.  Diese Unterschiede bringen DirectX wieder in Einklang mit moderner Grafikhardware und ermöglichen die Nutzung des gesamten Potenzials der Software. Sie bringen jedoch auch umfangreiche API\-Änderungen mit sich und übertragen mehr Verantwortung auf den Programmierer, wenn es um die Verwaltung der Lebensdauer von Ressourcen sowie die Behandlung von Konflikten geht.  Damit Programmierern der Übergang leichter fällt, stehen ihnen hervorragende Tools zum Debuggen zur Verfügung. Die Grafikdiagnose in Visual Studio 2015 unterstützt Direct3D12 von Anfang an.  Trotz aller Unterschiede hat die Grafikdiagnose für Direct3D 12 die gleichen Features wie die Grafikdiagnose für Direct3D 11.2, wobei die Frame\-Analyse derzeit eine Ausnahme darstellt.  Die Frame\-Analyse wird bald auch in Direct3D 12 unterstützt, gefolgt von neuen Diagnosetools, die Sie dabei unterstützen, möglicherweise in Direct3D 12 erstmals auftretende Fehler zu beheben.  
  
 Windows 10 bietet außerdem weiterhin Unterstützung für ältere Versionen von Direct3D sowie für die Spiele und Anwendungen, die davon abhängig sind.  Die Grafikdiagnose in Visual Studio 2015 unterstützt weiterhin Direct3D 10 und Direct3D 11 unter Windows 10 sowie unter Windows 8.1.  
  
### Windows 8.1 und Direct3D 11.2  
 In [!INCLUDE[win81](../debugger/includes/win81_md.md)] führt DirectX 11.2 neue Funktionen ein, u. a. die Unterstützung von Grafikinformationen während der Laufzeit.  [!INCLUDE[win81](../debugger/includes/win81_md.md)] verwendet die neue laufzeitbasierte Erfassung – die als *stabile Erfassung* bekannt ist—exklusiv für alle Versionen von DirectX, die [!INCLUDE[win81](../debugger/includes/win81_md.md)] unterstützt.  Die stabile Erfassung unterstützt auch neue Funktionen von Direct3D 11.2.  
  
### Begrenzte Direct2D\-Unterstützung  
 Da Direct2D eine Benutzermodus\-API ist, die auf Grundlage von Direct3D erstellt wurde, können Sie mithilfe der Grafikdiagnose Renderingprobleme in Apps debuggen, die Direct2D verwenden.  Es werden jedoch nur die zugrunde liegenden Direct3D\-Ereignisse und keine Direct2D\-Ereignisse auf höherer Ebene erfasst, sodass Direct2D\-Ereignisse nicht in der Grafikereignisliste angezeigt werden.  Außerdem ist die Beziehung zwischen Direct2D\-Ereignissen und den resultierenden Direct3D\-Ereignissen nicht immer nachvollziehbar, daher ist die Verwendung der Grafikdiagnose zum Debuggen von Renderingproblemen in Apps, die Direct2D verwenden, nicht ganz einfach.  Sie können die Grafik\-Diagnose aber verwenden, um Informationen zu Problemen abzurufen, die in Direct2D\-Apps beim Rendern auf unterster Ebene auftreten.  
  
## Features der Grafikdiagnose in Visual Studio  
 Die Grafikdiagnose verfügt über eine eigene Benutzeroberfläche zum Diagnostizieren von Renderingproblemen: das Fenster „Grafikanalyse“. Die Grafikdiagnose fügt jedoch auch einige Tools zur Visual Studio\-Benutzeroberfläche hinzu.  
  
### Die Grafiksymbolleiste \(Visual Studio\)  
 Die Grafiksymbolleiste bietet schnellen Zugriff auf Grafikdiagnosebefehle.  
  
 Die Schaltfläche **Diagnose starten** führt die App unter der Grafikdiagnose aus.  Wenn eine App unter der Grafikdiagnose ausgeführt, ist die Schaltfläche **Das nächste gerenderte Bild aufzeichnen** aktiviert.  
  
### Die Benutzeroberfläche für die Diagnoseerfassung  
 Wenn Sie Ihre App unter der Grafikdiagnose ausführen, zeigt Visual Studio eine Benutzeroberfläche für die Diagnosesitzung an, mit der Sie Frames erfassen können. Sie zeigt außerdem die aktuelle CPU\- und GPU\-Auslastung an.  Die CPU\- und GPU\-Auslastung wird angezeigt, um Sie beim Erfassen von Frames zu unterstützen, die Sie möglicherweise aufgrund ihrer Leistungsmerkmale statt der Renderingfehler erfassen möchten.  
  
 Dies ist jedoch nicht die einzige Möglichkeit zum Erfassen von Frames.  Sie können Frames auch über die programmgesteuerte Erfassungsschnittstelle oder mithilfe eines Befehlszeilenerfassungsprogramms wie „dxcap.exe“ erfassen.  
  
 Weitere Informationen erhalten Sie unter [Erfassen von Grafikinformationen](../debugger/capturing-graphics-information.md).  
  
### GPU\-Nutzung  
 Die Grafikdiagnose kann auch ein Profil der Leistung Ihrer Direct3D\-App erstellen.  Da Profilerstellungsdaten durch das Aufzeichnen von Details zu Grafikereignissen verfälscht würden, unterscheidet sich dies vom Erfassen von Frames, die mit der Grafikanalyse untersucht werden sollen.  
  
 Weitere Informationen erhalten Sie unter [GPU\-Nutzung](../debugger/gpu-usage.md).  
  
### DirectX\-Systemsteuerung  
 Die DirectX\-Systemsteuerung ist eine Komponente von DirectX, die Sie verwenden können, um das Verhalten von DirectX zu ändern. Sie können z. B. die Debugversion der DirectX\-Laufzeitkomponenten aktivieren, die Art der Debugmeldungen festlegen, oder bestimmte Funktionen der Grafikhardware deaktivieren, um weniger leistungsfähige Hardware zu emulieren.  Diese Einflussmöglichkeiten auf DirectX können Ihnen helfen, DirectX\-Apps zu debuggen und zu testen.  Sie können über Visual Studio auf die DirectX\-Systemsteuerung zugreifen.  
  
##### So öffnen Sie die DirectX\-Systemsteuerung  
  
-   Wählen Sie in der Menüleiste **Debuggen**, dann **Grafiken** und **DirectX\-Systemsteuerung**.  
  
## Grafikanalyse  
 Die Visual Studio\-Grafikanalyse ist eine eigene Benutzeroberfläche zum Untersuchen von Rendering\- und Leistungsproblemen mit bereits erfassten Frames.  Die Grafikanalyse umfasst mehrere Tools, mit denen Sie das Renderingverhalten Ihrer App untersuchen und besser verstehen können.  Jedes Tool stellt andere Informationen über den untersuchten Frame bereit. Die Tools sind so aufeinander abgestimmt, dass sie die Ursache des Renderingproblems intuitiv eingrenzen, beginnend beim Auftreten des Fehlers im Frame\-Puffer.  
  
 Diese Abbildung zeigt ein typisches Layout der Tools in der Grafikanalyse.  
  
 ![Alle Grafikdebuggerfenster](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### Die Grafiksymbolleiste \(Grafikanalyse\)  
 Die Grafiksymbolleiste bietet schnellen Zugriff die Toolfenster der Grafikanalyse.  
  
 ![Die Grafik&#45;Symbolleiste im Grafikdiagnosemodus](../debugger/media/vsg_toolbar.png "vsg\_toolbar")  
  
### Grafikprotokolldokument  
 In der Grafikanalyse ist das Grafikprotokolldokument das auffälligste Toolfenster.  In diesem Fenster werden alle Frames dargestellt, die Sie beim Ausführen der App unter der Grafikdiagnose erfasst haben.  Hier können Sie einen anderen Frame zum Überprüfen oder ein bestimmtes Pixel auswählen, das Sie mit dem Pixelverlauftool genauer untersuchen möchten.  Das in diesem Dokument angezeigte Frame\-Pufferbild ändert sich so, dass es das derzeit ausgewählte Ereignis darstellt. Auf diese Weise können Sie sehen, wie sich der Frame\-Puffer im Zeitverlauf ändert.  
  
 Das [Grafikprotokolldokument](../debugger/graphics-log-document.md) ist auch der Einstiegspunkt für das Frame\-Analysetool. Dieses Tool unterstützt Sie dabei, die Leistung eines Frames besser einschätzen zu können, indem bestimmte Aspekte der Renderingkonfiguration geändert und Ergebnisse von Vergleichstests für den Vergleich mit dem Original bereitgestellt werden.  
  
### Ereignisliste  
 Grafikereignisse markieren jeden Direct3D\-API\-Aufruf und jedes benutzerdefinierte Ereignis.  
  
 Die [Ereignisliste](../debugger/graphics-event-list.md) zeigt alle Grafikereignisse an, die während des untersuchten Frames aufgezeichnet wurden.  Damit Sie die wichtigen Informationen einfacher ermitteln können, kann die Ereignisliste hierarchisch angezeigt werden, wobei aktuelle Statusänderungen unter dem nachfolgenden Zeichnen\-Befehl aufgeführt werden, oder sie kann als Zeitachse angezeigt werden.  Darüber hinaus sind die Ereignisse entsprechend der Warteschlange, zu der sie gehören, farblich gekennzeichnet. Sie können die Liste auch filtern, sodass nur die für Sie interessanten Ereignisse eingeschlossen werden.  
  
 Wenn Sie ein Ereignis in der Liste auswählen, spiegelt der Rest des Grafikanalysetools den Status des Frames zum Zeitpunkt dieses Ereignisses wider.  Auf diese Weise können Sie die Auswirkungen eines Ereignisses auf die GPU sehen.  Sie können zum Beispiel sofort sehen, welche Auswirkungen ein Zeichnen\-Befehl auf den Frame\-Puffer hat, selbst wenn er durch nachfolgende Zeichnen\-Befehle verdeckt wird.  Einige Ereignisse verfügen darüber hinaus über Hyperlinks, denen Sie folgen können, um weitere Details über die Parameter oder die zugehörigen Ressourcenobjekte anzuzeigen.  
  
### Pipelinestufen  
 Jeder Zeichnen\-Befehl in Ihrer App durchläuft die von Direct3D bereitgestellte Grafikpipeline.  In jeder Stufe der Pipeline wird die Ausgabe der vorherigen Stufe durch ein kleines Programm transformiert, das als „Shader“ bezeichnet wird. Anschließend wird sie an die nächste Stufe übergeben, bis sie schließlich auf dem Bildschirm gerendert wird.  Viele Renderingfehler treten bei den Übergängen der Pipelinestufen auf, wenn das Ausgabeformat anders ist, als die nächste Stufe es erwartet, oder wenn in einer der Stufen einfach ein falsches Ergebnis erzeugt wird.  Normalerweise erhalten Sie nur die Endergebnisse, so wie sie auf dem Bildschirm angezeigt werden, und Sie können nicht einfach feststellen, wo in der Pipeline der Fehler aufgetreten ist.  
  
 Im Fenster [Pipelinestufen](../debugger/graphics-pipeline-stages.md) wird das Ergebnis der einzelnen Stufen unabhängig dargestellt, sodass Sie einfacher ermitteln können, in welcher Stufe ein Renderingproblem erstmals auftritt.  Sobald Sie die Stufe ermittelt haben, können Sie mit dem Debuggen des Shaders direkt im Fenster „Pipelinestufen“ beginnen.  
  
### Grafikzustand  
 Renderingvorgänge hängen sehr viel vom Status ab, der in der Regel über mehrere Objekte verteilt ist.  Zahlreiche Renderingproblemen werden durch die Fehlkonfiguration des Status verursacht.  
  
 Das Fenster [Zustand](../debugger/graphics-state.md) sammelt Informationen über den Status der einzelnen Zeichnen\-Befehle an einem zentralen Ort, sodass sie einfacher zu finden sind. Darüber hinaus werden die Statusänderungen seit dem letzten Zeichnen\-Befehl hervorgehoben.  
  
### Pixelverlauf  
 Bei komplexen Szenen ist es nicht ungewöhnlich, dass ein Pixel in einem einzelnen Frame mehrmals schattiert wird.  In einigen Fällen wird die frühere Farbe einfach überschrieben, in anderen Fällen werden die Farben jedoch auch kombiniert, um beispielsweise einen Effekte wie Transparenz zu erzielen.  Wenn das Ergebnis der Farbkombination nicht die gewünschte Darstellung erzielt, ist es nicht einfach zu ermitteln, ob dies an einer falschen Farbe oder an der Kombination der Farben liegt.  In einigen Fällen scheint ein Objekt zu fehlen, da sein Beitrag zum Pixel aus einem bestimmten Grund abgelehnt wurde.  
  
 Im Fenster [Pixelverlauf](../debugger/graphics-pixel-history.md) wird der gesamte Shaderverlauf jedes einzelnen Pixels im Frame visuell dargestellt, einschließlich der abgelehnten Beiträge.  Für Beiträge, die nicht abgelehnt wurden, zeigt der Grafikpixelverlauf die unformatierten Shaderergebnisse sowie Informationen darüber an, wie jede neue Farbe mit der vorherigen kombiniert wurde.  Mit diesen Informationen ist es viel einfacher, die Fehlerursache in Pixeln zu ermitteln, die Shaderergebnisse kombinieren, oder wenn ein gerendertes Objekt fehlt, da sein Beitrag zum Pixel fälschlicherweise abgelehnt wurde.  
  
### Ereignisaufrufliste  
 Der Shadercode ist nicht die einzige Ursache für Renderingprobleme in einer Direct3D\-App. Manchmal übergibt der Quellcode Ihrer App einen falschen Parameter oder konfiguriert Direct3D nicht richtig.  Eine Art von Fehler, die Sie mit dem bereits vorgestellten Feature „Pixelverlauf“ ermitteln können, ist ein fehlendes gerendertes Objekt, das deshalb fehlt, weil alle seine Pixel abgelehnt wurden.  Diese Art von Fehler tritt normalerweise auf, wenn Sie eine Einstellung falsch konfiguriert haben. Dies kann beispielsweise die Einstellung sein, die die Ausführung des Tiefentests steuert. In der Regel finden Sie den Fehler an einer Stelle in der Aufrufliste des Zeichnen\-Befehls des fehlenden Objekts.  
  
 Das Fenster [Ereignisaufrufliste](../debugger/graphics-event-call-stack.md) zeigt die vollständige Aufrufliste für jedes Grafikereignis in der Ereignisliste an, und Sie können sogar zum Quellcode Ihrer App wechseln, falls Debuginformationen verfügbar sind.  Dies ist ein leistungsfähiges Tool, um einen Fehler bei seinem ersten Auftreten in der GPU bis zurück zu seinem Ursprung im Quellcode Ihrer App zu verfolgen.  
  
### Objekttabelle  
 Jeder Frame, den Ihre App rendert, wird wahrscheinlich von Hunderten oder sogar Tausenden von Ressourcenobjekten gestützt.  Diese umfassen Hintergrundpuffer und Renderziele, Texturen, Vertexpuffer, Indexpuffer, allgemeine Puffer: Fast alles, was Direct3D speichert, ist ein Objekt.  
  
 Die [Objekttabelle](../debugger/graphics-object-table.md) zeigt alle Objekte an, die zum Zeitpunkt des in der Ereignisliste ausgewählten Ereignisses vorhanden waren.  Da die meisten Objekte in einer typischen App Texturen sind, ist die Ereignisliste so optimiert, dass Sie die für Bilder relevanten Details auf einen Blick erkennen können.  Die Spalte „Typ“ gibt an, welche Art von Objekt in jeder Zeile aufgeführt ist, und die Spalte „Format“ zeigt darüber hinaus den Untertyp oder die Version des Objekts an.  Weitere Details werden ebenfalls angezeigt.  Einige Objekte verfügen außerdem über Hyperlinks, denen Sie folgen können, um das Objekt mit einem speziellen Viewer anzuzeigen. So können Sie zum Beispiel Texturen als Bilder anzeigen, oder für Puffer können Sie durch Definition des Pufferformats festlegen, wie der Pufferviewer die umformatierten Pufferbytes analysieren und anzeigen soll.  
  
### Frame\-Analyse  
 Die Grafiken für Ihre App müssen nicht nur korrekt zu sein, sondern sie müssen auch schnell sein.  Sie müssen auch auf weniger leistungsfähigen Geräten wie Laptops mit integrierter Grafikkarte oder auf Mobiltelefonen eine schnell sein.  Außerdem müssen sie auch noch hervorragend aussehen.  
  
 Das Tool [Frameanalyse](../debugger/graphics-frame-analysis.md) ermittelt, ob ein Potenzial zur Leistungsoptimierung vorhanden ist, indem es automatisch die Art und Weise ändert, in der die App Direct3D verwendet, und anschließend Ergebnisse von Vergleichstests zum Vergleich bereitstellt.  Die Frame\-Analyse kann beispielsweise die MIP\-Zuordnung für alle Texturen aktivieren, sodass möglicherweise Texturen ermittelt werden, die von der MIP\-Zuordnung profitieren, für die sie jedoch derzeit nicht aktiviert ist.  Für Hardware, die dies unterstützt, stellt die Frame\-Analyse auch Informationen bereit, die von den GPU\-Leistungsindikatoren erfasst wurden. Mit dieser Art von Informationen können Leistungsprobleme in Bezug auf die Hardware ermittelt werden, wie z. B. eine hohe Anzahl von Verzögerungen beim Abrufen von Texturen oder Cachefehlern.  
  
 Bei der Frame\-Analyse geht es jedoch nicht nur um Schnelligkeit. Es geht darum, die bestmögliche Leistung zu erzielen, ohne dabei zu viel visuelle Qualität einzubüßen.  Manchmal hinterlässt ein ressourcenintensiver Effekt, der auf einem großen Bildschirm toll aussieht, gar keinen besonderen Eindruck auf dem kleinen Bildschirm eines Mobiltelefons, wo ein einfacher Effekt vielleicht genauso gut wirkt, jedoch das Akku schont.  Die von der Grafikanalyse bereitgestellten automatischen Änderungen und Benchmarks können Sie dabei unterstützen, Ihre App so ausgewogen zu gestalten, dass sie auf einer Vielzahl von Geräten optimal verwendet werden kann.  
  
## Siehe auch  
 [Befehlszeilen\-Erfassungs\-Tool](../debugger/command-line-capture-tool.md)   
 [HLSL\-Debugger](../debugger/hlsl-shader-debugger.md)