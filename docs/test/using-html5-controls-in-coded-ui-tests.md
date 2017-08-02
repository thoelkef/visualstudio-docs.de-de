---
title: Verwenden von HTML5-Steuerelementen in Tests der programmierten UI | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 17
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 834f53c8d75a06de69f1afe682a0a0b1863dfde0
ms.lasthandoff: 04/04/2017

---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Verwenden von HTML5-Steuerelementen in Tests der programmierten UI
Bei Tests der programmierten UI werden einige HTML5-Steuerelemente unterstützt, die in Internet Explorer 9 und in Internet Explorer 10 enthalten sind.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  In Versionen vor Internet Explorer 10 konnten Tests der programmierten UI im Vergleich zum Internet Explorer-Prozess mit einer höheren Berechtigungsstufe ausgeführt werden. Beim Ausführen von Tests der programmierten UI in Internet Explorer 10 müssen sowohl der Prozess für Tests der programmierten UI als auch der Internet Explorer-Prozess dieselbe Berechtigungsstufe aufweisen. Dies liegt an sichereren AppContainer-Features in Internet Explorer 10.  
  
> [!WARNING]
>  Wenn Sie einen Test der programmierten UI in Internet Explorer 10 erstellen, wird dieser mit Internet Explorer 9 oder Internet Explorer 8 möglicherweise nicht ausgeführt. Der Grund hierfür ist, dass Internet Explorer 10 HTML5-Steuerelemente wie Audio, Video, ProgressBar und Schieberegler enthält. Diese HTML5-Steuerelemente werden von Internet Explorer 9 oder Internet Explorer 8 nicht erkannt. Entsprechend kann der Test der codierten UI unter Verwendung von Internet Explorer 9 einige HTML5-Steuerelemente enthalten, die auch nicht von Internet Explorer 8 erkannt werden.  
  
## <a name="supported-html5-controls"></a>Unterstützte HTML5-Steuerelemente  
 Tests der programmierten UI umfassen die Unterstützung für die Aufzeichnung, Wiedergabe und Validierung der folgenden HTML5-Steuerelemente:  
  
-   [Audio-Steuerelement](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Videosteuerelement](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Schieberegler](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Audio-Steuerelement  
 **Audiosteuerelement:** Aktionen im HTML5-Audiosteuerelement werden ordnungsgemäß aufgezeichnet und wiedergegeben.  
  
 ![HTML5-Audiosteuerelement](~/docs/test/media/codedui_html5_audio.png "CodedUI_HTML5_Audio")  
  
|Aktion|Aufzeichnung|Generierter Code|  
|------------|---------------|--------------------|  
|**Audiowiedergabe**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audiodatei mit dem Namen \<name> ab 00:00:00 wiedergeben|HtmlAudio.Play(TimeSpan)|  
|**Einen bestimmten Zeitpunkt in der Audiodatei auswählen**|Audiodatei mit dem Namen \<name> ab 00:01:48 auswählen|HtmlAudio.Seek(TimeSpan)|  
|**Audiodatei anhalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audiodatei mit dem Namen \<name> bei 00:01:53 anhalten|HtmlAudio.Pause(TimeSpan)|  
|**Ton ausschalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audiodatei mit dem Namen \<name> stummschalten|HtmlAudio.Mute()|  
|**Stummschaltung der Audiodatei aufheben**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Stummschaltung der Audiodatei mit dem Namen \<name> aufheben|HtmlAudio.Unmute()|  
|**Ändern der Lautstärke der Audiodatei**|Lautstärke der Audiodatei mit dem Namen \<name> auf 79 % festlegen|HtmlAudio.SetVolume(float)|  
  
 Die folgenden Eigenschaften stehen für „HtmlAudio“ zur Verfügung, und Sie können eine Assertion für alle davon hinzufügen:  
  
```  
string AutoPlay  
string Controls  
string CurrentSrc  
string CurrentTime  
string CurrentTimeAsString  
string Duration  
string DurationAsString  
string Ended  
string Loop  
string Muted  
string Paused  
string PlaybackRate  
string ReadyState  
string Seeking  
string Src  
string Volume  
  
```  
  
 **Sucheigenschaften:** Die Sucheigenschaften für `HtmlAudio` sind `Id`, `Name` und `Title`.  
  
 **Filtereigenschaften:** Die Filtereigenschaften für `HtmlAudio` sind `Src`, `Class`, `ControlDefinition` und `TagInstance`.  
  
> [!NOTE]
>  Die Zeitdauer für das Suchen und Anhalten kann erheblich sein. Während der Wiedergabe wartet der Test der programmierten UI bis zur in `(TimeSpan)` angegebenen Zeit, bevor die Audiodatei angehalten wird. Wenn die angegebene Zeit unter bestimmten Ausnahmefällen verstrichen ist, bevor der Befehl „Pause“ aktiviert wurde, wird eine Ausnahme zurückgegeben.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Videosteuerelement  
 **Videosteuerelement:** Aktionen im HTML5-Videosteuerelement werden ordnungsgemäß aufgezeichnet und wiedergegeben.  
  
 ![HTML5-Videosteuerelement](~/docs/test/media/codedui_html5_video.png "CodedUI_HTML5_Video")  
  
|Aktion|Aufzeichnung|Generierter Code|  
|------------|---------------|--------------------|  
|**Videowiedergabe**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video mit dem Namen \<name> ab 00:00:00 wiedergeben|HtmlVideo.Play(TimeSpan)|  
|**Einen bestimmten Zeitpunkt im Video auswählen**|Video mit dem Namen \<name> ab 00:01:48 auswählen|HtmlVideo.Seek(TimeSpan)|  
|**Video anhalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video mit dem Namen \<name> bei 00:01:53 anhalten|HtmlVideo.Pause(TimeSpan)|  
|**Video stummschalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video mit dem Namen \<name> stummschalten|HtmlVideo.Mute()|  
|**Stummschaltung des Videos aufheben**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Stummschaltung des Videos mit dem Namen \<name> aufheben|HtmlVideo.Unmute()|  
|**Ändern der Lautstärke des Videos**|Lautstärke des Videos mit dem Namen \<name> auf 79 % festlegen||  
  
 Alle Eigenschaften von „HtmlAudio“ sind auch für „HtmlVideo“ verfügbar. Darüber hinaus sind die folgenden drei Eigenschaften auch verfügbar. Die Assertion können Sie für alle davon hinzufügen.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Sucheigenschaften:** Die Sucheigenschaften für `HtmlVideo` sind `Id`, `Name` und `Title`.  
  
 **Filtereigenschaften:** Die Filtereigenschaften für `HtmlVideo` sind `Src`, `Poster`, `Class`, `ControlDefinition` und `TagInstance`.  
  
> [!NOTE]
>  Wenn Sie das Video mithilfe der Bezeichnung „-30s“ oder „+30s“ zurück- bzw. vorspulen, wird dies aggregiert, um nach der entsprechenden Zeit zu suchen.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Schieberegler  
 **Schiebereglersteuerung:** Aktionen in der HTML5-Schiebereglersteuerung werden ordnungsgemäß aufgezeichnet und wiedergegeben.  
  
 ![HTML5-Schiebereglersteuerung](~/docs/test/media/codedui_html5_slider.png "CodedUI_HTML5_Slider")  
  
|Aktion|Aufzeichnung|Generierter Code|  
|------------|---------------|--------------------|  
|**Eine Position im Schieberegler festlegen**|Legen Sie die Position im Schieberegler \<name> auf \<x> fest|HtmlSlider.ValueAsNumber=\<x>|  
  
 Die folgenden Eigenschaften sind für „HtmlSlider“ und die Assertion verfügbar und können für alle davon hinzugefügt werden:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> ProgressBar  
 **ProgreesBar-Steuerelement:** Bei der „ProgressBar“ handelt es sich um ein Steuerelement ohne Interaktionen. Sie können Assertionen für die `Value`- und `Max`-Eigenschaften dieses Steuerelements hinzufügen.  
  
 ![HTML5-ProgressBar-Steuerelement](~/docs/test/media/codedui_html5_progressbar.png "CodedUI_HTML5_ProgressBar")  
  
## <a name="see-also"></a>Siehe auch  
 [HTML-Elemente](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anpassen des Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

