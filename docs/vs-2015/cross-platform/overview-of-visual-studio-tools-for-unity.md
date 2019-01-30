---
title: Übersicht über Visual Studio-Tools für Unity | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: 69b9fb9bd21ad19199e5ba268c8f0a87fb546d57
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776510"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Übersicht über Visual Studio-Tools für Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In diesem Abschnitt erfahren Sie mehr über die Funktionen von Visual Studio-Tools für Unity und wie Sie sie nutzen können, um mit Unity produktiver zu arbeiten.  
  
 Mithilfe von Visual Studio-Tools für Unity (*VSTU*) können Sie Visual Studio zum Schreiben von Spiel- und Editorskripts in C# verwenden und dann den leistungsfähigen Debugger zum Suchen und Beheben von Fehlern nutzen. Das neueste Release von VSTU umfasst Syntaxfarben für die Shadersprache ShaderLab von Unity, bessere Debugger-Visualisierungen und verbesserte Codegenerierung für den MonoBehavior-Assistenten. Mit VSTU werden außerdem die Unity-Projektdateien, Konsolenmeldungen und die Möglichkeit zum Starten des Spiels in Visual Studio eingebunden, sodass beim Schreiben von Code weniger Zeit zum Umschalten in und aus dem Unity-Editor benötigt wird.  
  
 Lesen Sie weiter, um mehr über diese Features zu erfahren.  
  
## <a name="integration-with-unity"></a>Integration in Unity  
 Mit Visual Studio-Tools für Unity wäre keine Produktivitätssteigerung möglich, wenn Sie ständig zwischen dem Unity-Editor und Visual Studio hin- und herwechseln müssten. Dank Visual Studio-Tools für Unity können Sie die Arbeit fortsetzen, ohne Visual Studio verlassen zu müssen.  
  
-   Im **Unity-Projektexplorer** wird Ihr gesamtes Unity-Projekt innerhalb von Visual Studio mithilfe der gleichen Hierarchie wie im Unity-Editor angezeigt.  
  
-   Die Integration der Unity-Konsole ermöglicht das Anzeigen der Ausgabe der Unity-Konsole direkt im Fehlerfenster von Visual Studio.  
  
-   Debuggen Sie Ihr Spiel in Visual Studio, ohne zurück zu Unity wechseln zu müssen. Drücken Sie einfach F5.  
  
## <a name="superior-debugging"></a>Überlegenes Debugging  
 Verbinden Sie den leistungsfähigen Debugger von Visual Studio mit Ihrem Unity-Spiel zum Debuggen Ihrer C#-Skripts und DLLs unabhängig davon, ob es eigenständig oder im Unity-Editor ausgeführt wird. Sie können alle Debuggingfeatures nutzen, die Sie von Visual Studio erwarten:  
  
- Haltepunkte einschließlich bedingter Haltepunkte.  
  
- Auswertung komplexer Ausdrücke im Überwachungsfenster.  
  
- Überprüfen und Ändern des Werts von Variablen und Argumenten.  
  
- Detailsuchen in komplexen Objekten und Datenstrukturen.  
  
  Sie können auch Ihr Unity-Spiel auch dann debuggen, wenn es auf einem anderen Computer in Ihrem Netzwerk ausgeführt wird.  
  
## <a name="productivity"></a>Produktivität  
 Zusätzlich zur gewohnten Produktivität von Visual Studio beim Schreiben und Umgestalten von Code in C# bietet Visual Studio-Tools für Unity zusätzliche Produktivitätsfeatures für Unity-Entwickler.  
  
-   Mithilfe von Farben für die Syntax der ShaderLab-Sprache von Unity können Sie Fehler in Ihren Shadern frühzeitig erkennen. Öffnen Sie einfach Ihre ShaderLab-Dateien in Visual Studio.  
  
-   Der MonoBehavior-Assistent ermöglicht Ihnen, eine Liste von Unity-Verhalten zu durchsuchen und Codebausteine für Verhalten zu erstellen, mit denen Sie möglicherweise nicht vertraut sind. Drücken Sie STRG+UMSCHALT+M.  
  
-   Sobald Sie mit den Unity-Verhalten vertraut sind, die Sie am häufigsten verwenden, stellt der Quick MonoBehavior-Assistent sie Ihnen per Tastenkombination zur Verfügung. Drücken Sie STRG+UMSCHALT+Q.  
  
-   Greifen Sie in Visual Studio auf Unity-Dokumentation zu. Markieren Sie einfach den API-Aufruf, zu dem Sie Informationen möchten, und drücken Sie dann STRG+ALT+M, STRG+H.  
  
-   Greifen Sie über Tastenkombinationen auf alle diese und noch weitere Funktionen zu.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Visual Studio Tools für Unity-API  
 Sie können das Verhalten von Visual Studio-Tools für Unity unter Verwendung der bereitgestellten APIs anpassen und erweitern.  
  
-   Visual Studio-Tools für Unity registriert einen Protokollrückruf, damit die Unity-Konsole nach Visual Studio gestreamt werden kann. Wenn Sie Editorskripts haben, die Informationen protokollieren, können Sie diese mit demselben Rückruf verbinden, um Ihre Nachrichten an Visual Studio zu senden. Weitere Informationen finden Sie im Beispiel zum Protokollrückruf.  
  
-   Sie können ändern, wie Visual Studio-Tools für Unity Projektdateien mithilfe des Rückrufs von "ProjectFileGeneration" im Unity-Stil erstellt. Weitere Informationen finden Sie im Beispiel "Erstellung der Projektdatei".  
  
## <a name="see-also"></a>Siehe auch  
 [Unity-Homepage](http://unity3d.com)
