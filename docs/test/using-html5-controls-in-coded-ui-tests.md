---
title: Verwenden von HTML5-Steuerelementen in Tests der programmierten UI in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 418c0aa6660b01896252d04a711d4069da389f00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914488"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Verwenden von HTML5-Steuerelementen in Tests der programmierten UI

Bei Tests der programmierten UI werden einige HTML5-Steuerelemente unterstützt, die in Internet Explorer 9 und in Internet Explorer 10 enthalten sind.

 **Anforderungen**

-   Visual Studio Enterprise

> [!WARNING]
> In Versionen vor Internet Explorer 10 konnten Tests der programmierten UI im Vergleich zum Internet Explorer-Prozess mit einer höheren Berechtigungsstufe ausgeführt werden. Beim Ausführen von Tests der programmierten UI in Internet Explorer 10 müssen sowohl der Prozess für Tests der programmierten UI als auch der Internet Explorer-Prozess dieselbe Berechtigungsstufe aufweisen. Dies liegt an sichereren AppContainer-Features in Internet Explorer 10.


> [!WARNING]
> Wenn Sie einen Test der programmierten UI in Internet Explorer 10 erstellen, wird dieser mit Internet Explorer 9 oder Internet Explorer 8 möglicherweise nicht ausgeführt. Der Grund hierfür ist, dass Internet Explorer 10 HTML5-Steuerelemente wie Audio, Video, ProgressBar und Schieberegler enthält. Diese HTML5-Steuerelemente werden von Internet Explorer 9 oder Internet Explorer 8 nicht erkannt. Entsprechend kann der Test der codierten UI unter Verwendung von Internet Explorer 9 einige HTML5-Steuerelemente enthalten, die auch nicht von Internet Explorer 8 erkannt werden.


## <a name="audio-control"></a>Audio-Steuerelement
 **Audiosteuerelement:** Aktionen im HTML5-Audiosteuerelement werden ordnungsgemäß aufgezeichnet und wiedergegeben.

 ![HTML5-Audiosteuerelement](../test/media/codedui_html5_audio.png)

|Aktion|Aufzeichnung|Generierter Code|
|-|---------------|-|
|**Audiowiedergabe**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audiodatei mit dem Namen \<name> ab 00:00:00 wiedergeben|HtmlAudio.Play(TimeSpan)|
|**Einen bestimmten Zeitpunkt in der Audiodatei auswählen**|Audiodatei mit dem Namen \<name> ab 00:01:48 auswählen|HtmlAudio.Seek(TimeSpan)|
|**Audiodatei anhalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audiodatei mit dem Namen \<name> bei 00:01:53 anhalten|HtmlAudio.Pause(TimeSpan)|
|**Ton ausschalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audiodatei mit dem Namen \<name> stummschalten|HtmlAudio.Mute()|
|**Stummschaltung der Audiodatei aufheben**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Stummschaltung der Audiodatei mit dem Namen \<name> aufheben|HtmlAudio.Unmute()|
|**Ändern der Lautstärke der Audiodatei**|Lautstärke der Audiodatei mit dem Namen \<name> auf 79 % festlegen|HtmlAudio.SetVolume(float)|

Unter [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) finden Sie eine Liste der Eigenschaften, zu denen Sie eine Assertion hinzufügen können.

 **Sucheigenschaften:** Die Sucheigenschaften für `HtmlAudio` sind `Id`, `Name` und `Title`.

 **Filtereigenschaften:** Die Filtereigenschaften für `HtmlAudio` sind `Src`, `Class`, `ControlDefinition` und `TagInstance`.

> [!NOTE]
> Die Zeitdauer für das Suchen und Anhalten kann erheblich sein. Während der Wiedergabe wartet der Test der programmierten UI bis zur in `(TimeSpan)` angegebenen Zeit, bevor die Audiodatei angehalten wird. Wenn die angegebene Zeit unter bestimmten Ausnahmefällen verstrichen ist, bevor der Befehl „Pause“ aktiviert wurde, wird eine Ausnahme zurückgegeben.


## <a name="video-control"></a>Videosteuerelement
 **Videosteuerelement:** Aktionen im HTML5-Videosteuerelement werden ordnungsgemäß aufgezeichnet und wiedergegeben.

 ![HTML5-Videosteuerelement](../test/media/codedui_html5_video.png)

|Aktion|Aufzeichnung|Generierter Code|
|-|---------------|-|
|**Videowiedergabe**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video mit dem Namen \<name> ab 00:00:00 wiedergeben|HtmlVideo.Play(TimeSpan)|
|**Einen bestimmten Zeitpunkt im Video auswählen**|Video mit dem Namen \<name> ab 00:01:48 auswählen|HtmlVideo.Seek(TimeSpan)|
|**Video anhalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video mit dem Namen \<name> bei 00:01:53 anhalten|HtmlVideo.Pause(TimeSpan)|
|**Video stummschalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video mit dem Namen \<name> stummschalten|HtmlVideo.Mute()|
|**Stummschaltung des Videos aufheben**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Stummschaltung des Videos mit dem Namen \<name> aufheben|HtmlVideo.Unmute()|
|**Ändern der Lautstärke des Videos**|Lautstärke des Videos mit dem Namen \<name> auf 79 % festlegen||

Unter [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) finden Sie eine Liste der Eigenschaften, zu denen Sie eine Assertion hinzufügen können.

 **Sucheigenschaften:** Die Sucheigenschaften für `HtmlVideo` sind `Id`, `Name` und `Title`.

 **Filtereigenschaften:** Die Filtereigenschaften für `HtmlVideo` sind `Src`, `Poster`, `Class`, `ControlDefinition` und `TagInstance`.

> [!NOTE]
> Wenn Sie das Video mithilfe der Bezeichnung „-30s“ oder „+30s“ zurück- bzw. vorspulen, wird dies aggregiert, um nach der entsprechenden Zeit zu suchen.

## <a name="progressbar"></a>ProgressBar
 **ProgressBar-Steuerelement:** ProgressBar ist ein Steuerelement ohne Interaktionen. Sie können Assertionen für die `Value`- und `Max`-Eigenschaften dieses Steuerelements hinzufügen. Weitere Informationen finden Sie unter [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

 ![HTML5 ProgressBar-Steuerelement](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Siehe auch

- [HTML-Elemente](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md)
- [Supported Configurations and Platforms for Coded UI Tests and Action Recordings (Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen)](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
