---
title: "So funktioniert die Grafikdiagnose | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ae14497-c77c-4399-bc0c-595caba23656
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# So funktioniert die Grafikdiagnose
Fügen Sie hier eine Einleitung ein.  
  
## So funktioniert die Grafikdiagnose  
 Zeichnen Sie zur Verwendung der Grafikdiagnose zuerst Informationen darüber auf, wie eine App die Direct3D\-API während der Ausführung verwendet, und untersuchen Sie später das aufgezeichnete Verhalten.  Die aufgezeichneten Informationen enthalten API\-Aufrufe für festgelegte Frames, zum Beispiel Aufrufe zum Löschen des Bildschirminhalts, Zeichnen von Geometrien, Verteilen von Compute\-Shadern oder Ändern des Grafikgerätzustands, sowie deren Argumente und Kopien von Puffern und Objekten, auf die indirekt verwiesen wird.  Außerdem werden API\-Aufrufe, die mit der Einrichtung und Initialisierung in Verbindung stehen, vor dem Rendern jeglicher Frames aufgezeichnet.  Die aufgezeichneten Informationen werden in eine Datei des *Grafikprotokolls* \(.vsglog\) geschrieben.  
  
 Sie können das in den Grafikprotokollen erfasste Renderingverhalten neu erstellen, indem Sie die Grafikereignisse auf dem Entwicklungscomputer oder einem Remotecomputer bzw. \-gerät wiedergeben.  Als Wiedergabecomputer können derselbe Computer oder dasselbe Gerät verwendet werden, auf dem das Grafikprotokoll ursprünglich aufgezeichnet wurde, oder ein anderes Gerät.  In den meisten Wiedergabefunktionen wird die Grafikhardware des Wiedergabecomputers zur Wiedergabe von Grafikereignissen verwendet. Bei Verwendung des HLSL\-Debuggers wird jedoch der Shader\-Code immer mithilfe eines emulierten GPUs auf der CPU wiedergegeben.  Die Verwendung eines emulierten GPUs ermöglicht die schrittweise Ausführung des Shader\-Codes, die Überprüfung von Variablen und die Verwendung anderer gängiger Debugfunktionen, und zwar unabhängig davon, ob die Grafikhardware im Wiedergabecomputer das Debugging von Hardware unterstützt.  
  
> [!NOTE]
>  Obwohl ein Grafikprotokoll die meisten relevanten Informationen intern erfasst, sind zusätzliche Informationen erforderlich, damit einige Grafikdiagnosefunktionen vollständig verwendet werden können.  Um beispielsweise die Grafikaufrufliste in vollem Umfang nutzen zu können, müssen Sie über die Programmdatenbankdatei \(.pdb\) und den Quellcode der App verfügen.  Um HLSL\-Shader\-Quellcode zu debuggen, müssen Sie über den Shader\-Quellcode verfügen.  \(Wenn der Shader mit dem Shadercompiler D3D11.1 kompiliert wird und die Debuginformationen aktiviert sind, wird der Shaderquellcode während der Erfassung in die Grafikprotokolle eingebettet.\)  
  
> [!NOTE]
>  Da bestimmte APIs in vorherigen Versionen von Windows oder DirectX eventuell nicht verfügbar sind, können Sie Grafikprotokolle, in denen diese API\-Aufrufe erfasst wurden, auf einem Wiedergabecomputer wiedergeben, der sie nicht unterstützt.  
  
### Grafikprotokolle  
 Ein Grafikprotokoll enthält einen oder mehrere Frames, die von einer ausgeführten DirectX\-Grafikanwendung aufgezeichnet wurden.  Da ein Grafikprotokoll in sich abgeschlossen ist, können diese Frames später schrittweise und ohne externe Informationen oder Verweise neu erstellt werden.  Sie können Grafikprotokolle daher für andere Entwickler freigeben, Probleme auf unterschiedlichen Computern untersuchen und und alte Grafikprotokolle überprüfen, auch wenn die Modelle und die Texturen in der Entwicklung geändert wurden.  Sie können ebenfalls mehrere Dateien des Grafikprotokolls \(.vsglog\) gleichzeitig laden, um Daten und Renderingergebnisse zu vergleichen.  
  
##### So öffnen Sie eine Datei \(VSGLOG\) des Grafikprotokolls  
  
1.  Wählen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der Befehlsleiste **Datei**, **Öffnen** und **Datei**.  Das Dialogfeld **Datei öffnen** wird angezeigt.  
  
2.  Geben Sie eine Datei \(VSGLOG\) des Grafikprotokolls an, die geöffnet werden soll, und wählen Sie dann die Schaltfläche **Öffnen**.  
  
> [!NOTE]
>  Sie können Kopien von Netzen und Texturen aus einem Grafikprotokoll extrahieren, ändern und speichern, indem Sie die Grafiktools verwenden, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthalten sind.  Allerdings wird der Inhalt des Grafikprotokolls nicht von diesen Änderungen betroffen.  Informationen zu diesen Grafiktools finden Sie unter [Arbeiten mit 3D\-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md).