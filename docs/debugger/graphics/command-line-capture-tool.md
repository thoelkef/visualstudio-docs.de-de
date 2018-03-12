---
title: Befehlszeilen-Erfassungstool | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4290ccb1184f658d04d6903520f709384e58e837
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2018
---
# <a name="command-line-capture-tool"></a>Befehlszeilen-Erfassungs-Tool
DXCap.exe ist ein Befehlszeilenprogramm für die Aufzeichnung und Wiedergabe der Grafikdiagnose. Es unterstützt Direct3D 10 bis Direct3D 12 auf allen Funktionsebenen.  
  
## <a name="syntax"></a>Syntax  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe -p [filename] -screenshot [-frame frames]  
DXCap.exe -p [filename] -toXML [xml_filename]  
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe -info  
```  
  
#### <a name="parameters"></a>Parameter  
 `-file` `filename`  
 Unter dem Erfassungsmodus (`-c`), `filename` gibt den Namen der grafikprotokolldatei an, die Grafikinformationen aufgezeichnet werden. Wenn `filename` nicht angegeben ist, werden Grafikinformationen in eine Datei mit dem Namen aufgezeichnet wird `<appname>-<date>-<time>.vsglog` standardmäßig.  
  
 Unter Gültigkeitsprüfung (-V)-Modus `filename` wird der Namen der zu prüfenden Grafikprotokolldatei angezeigt. Wenn `filename` nicht angegeben ist, wird das Graphics-Protokoll, das zuletzt geprüft wurde, erneut verwendet.  
  
 `-frame` `frames`  
 Unter dem Erfassungsmodus gibt `frames` die Frames an, die Sie erfassen möchten. Der erste Frame ist 1. Sie können mehrere Frames mithilfe von Kommas und Bereichen angeben. Z. B. wenn `frames` ist `2, 5, 7-9, 15`, dann werden die frames `2`, `5`, `7`, `8`, `9`, und `15` erfasst werden.  

> [!TIP]
> Verwendung `-frame` `manual` um anzugeben, dass Bilder manuell durch Drücken der Taste "Druck" erfasst werden sollen. Frames können erfasst werden, wenn die Anwendung gestartet wird; Um das Erfassen von Frames zu beenden, kehren Sie zur Befehlszeilen-Schnittstelle zurück und drücken Sie die EINGABETASTE.  
  
 `-period` `periods`  
 Unter dem Erfassungsmodus legt `periods` die Bereiche für die Zeit in Sekunden fest, in denen Sie Frames erfassen möchten. Sie können mehrere Perioden mithilfe von Kommas und Bereichen angeben. Zum Beispiel wenn `periods` ist `2.1-5, 7.0-9.3`, dann werden Frames, die zwischen `2.1` und `5` Sekunden und zwischen`7` und `9.3` Sekunden liegen, erfasst.  
  
 `-c` `app` [`args...`]  
 Aufnahme-Modus. Unter dem Aufnahmemodus gibt `app` den Namen der Anwendung an, aus der Sie Grafikinformationen aufzeichnen möchten; `args...` gibt zusätzliche Befehlszeilenparameter für diese Anwendung an.  
  
 `-p` [`filename`]  
 Wiedergabemodus (`-p`). Unter dem Wiedergabemodus gibt `filename` den Namen der Grafikprotokolldatei an, die wiedergegeben werden soll. Wenn `filename` nicht angegeben ist, wird das Grafikprotokoll, das zuletzt wiedergegeben wurde, erneut verwendet.  
  
 `-debug`  
 Unter dem Wiedergabemodus `-debug` angegeben, dass die Wiedergabe mit der Direct3D-Debug-Ebene aktiviert ausgeführt werden soll.  
  
 `-warp`  
 Unter dem Wiedergabemodus `-warp` gibt an, dass die Wiedergabe mit dem warpsoftwarerenderer durchgeführt werden soll.  
  
 `-hw`  
 Unter dem Wiedergabemodus `-hw` gibt an, dass die Wiedergabe mit GPU-Hardware ausgeführt werden soll.  
  
 `-config`  
 Unter dem Wiedergabemodus `-config` zeigt Informationen über den Computer, der verwendet wurde, um die grafikprotokolldatei zu erfassen, wenn diese Informationen im Protokoll aufgezeichnet wurde.  
  
 `-rawmode`  
 Unter dem Wiedergabemodus `-rawmode` angegeben, dass die Wiedergabe ohne Änderung der aufgezeichneten Ereignisse ausgeführt werden soll. Unter normalen Bedingungen werden unter dem Wiedergabemodus möglicherweise geringfügige Änderungen an der Wiedergabe vorgenommen, um das Debuggen zu vereinfachen und die Wiedergabe zu beschleunigen. z. B. kann eine Swap-Ketten-Ausgabe anstelle der Ausführung von Swap-Kette Befehlen simuliert werden. Dies ist normalerweise kein Problem, aber möglicherweise muss die Wiedergabe auf eine Weise erfolgen, die für die aufgezeichneten Ereignisse zuverlässiger ist; Sie können mithilfe dieser Option das Full-Screen-Rendering-Verhalten auf einer Anwendung wiederherstellen, die während der Ausführung im Vollbildmodus erfasst wurde.  
  
 `-toXML` [`xml_filename`]  
 Unter dem Wiedergabemodus gibt `xml_filename` den Namen der Datei an, in die eine XML-Darstellung der Wiedergabe geschrieben wird. Wenn `xml_filename` nicht angegeben ist, wird die XML-Darstellung in eine Datei mit demselben Namen der widergegebenen Datei geschrieben, erhält aber eine `.xml` Erweiterung.  
  
 `-v`  
 Validierungsmodus Unter dem Validierungsmodus erfasste Frames werden sowohl auf Hardware als auch auf WARP wiedergegeben, und ihre Ergebnisse werden mithilfe einer Bildvergleichsfunktion verglichen. Diese Funktion können Sie verwenden, um Treiberprobleme schnell zu identifizieren, die sich auf das Rendering auswirken.  
  
 `-examine` `events`  
 Unter dem Validierungsmodus gibt `events` den Grafikereignissatz an, dessen sofortige Ergebnisse verglichen werden. Beispielsweise `-examine present,draw,copy,clear` schränkt den Vergleich nur die Ereignisse, die zu diesen Kategorien gehören.  
  
> [!TIP]
>  Es wird empfohlen, beginnend mit `-examine present,draw,copy,clear` , da dies die meisten Probleme offengelegt jedoch deutlich weniger Zeit als einer umfangreicheren Reihe von Ereignissen benötigt wird. Bei Bedarf können Sie eine größere oder andere Ereignismenge angeben, um diese Ereignisse zu prüfen und andere Arten von Problemen offenzulegen.  
  
 `-haltonfail`  
 Unter dem Validierungsmodus `-haltonfail` Validierung angehalten, wenn Unterschiede zwischen der Hardware und dem WARP-Renderer erkannt werden. Die Validierung wird fortgesetzt, wenn eine Taste gedrückt wird.  
  
 `-exitonfail`  
 Unter dem Validierungsmodus `-exitonfail` Validierung sofort beendet Wenn Unterschiede zwischen der Hardware und dem WARP-Renderer erkannt werden. Zurückgibt, wenn das Programm auf diese Weise beendet, `0` mit der Umgebung; Anderfalls wird `1`.  
  
 `-showprogress`  
 Unter dem Validierungsmodus `-showprogress` zeigt Statusinformationen zur Validierung-Sitzung. Der WARP-Fortschritt wird auf der linken Seite angezeigt; der Hardware-Status wird auf der rechten Seite angezeigt.  
  
 `-e` `search_string`  
 Listet die uwp-apps, die installiert werden. Sie können diese Informationen zum Ausführen von Befehlszeilen-Snapshots mit uwp-apps verwenden.  
  
 `-info`  
 Zeigt Informationen über den Computer und Erfassung von DLLs an.  
  
## <a name="remarks"></a>Hinweise  
 DXCap.exe kann in drei verschiedenen Modi betrieben werden:  
  
 Aufnahme-Modus (-c)  
 Erfassung von Grafikinformationen aus einer ausgeführten Anwendung und Aufzeichnung dieser Informationen in einer Grafikprotokolldatei. Die Erfassungsfunktionen und das Dateiformat sind identisch mit denen in Visual Studio.  
  
 Wiedergabemodus (-p).  
 Wiedergabe von Grafiken zuvor aufgezeichneter Ereignisse aus einer vorhandenen Grafikprotokolldatei. Standardgemäß erfolgt die Wiedergabe in einem Fenster, auch wenn die Grafikprotokolldatei aus einer Vollbild-Anwendung erfasst wurde. Erfolgt die Wiedergabe im Vollbildmodus nur-Datei von einer Vollbild-Anwendung erfasst wurde, wenn die grafikprotokolldatei und `-rawmode` angegeben ist.  
  
 Validierungsmodus (`-v`)  
 Überprüfen des Renderingverhaltens durch die Wiedergabe erfasster Frames sowohl auf Hardware und als auch auf WARP und Vergleich ihrer Ergebnisse mithilfe einer Bildvergleichsfunktion. Dieses Feature können Sie verwenden, um Treiberprobleme schnell zu identifizieren, die sich auf das Rendering auswirken.  
  
 Zusätzlich zu diesen Modi führt dxcap.exe zwei weitere Funktionen aus, die keine Aufnahme oder Wiedergabe von Grafikinformationen durchführen.  
  
 Enumerationsfunktion (`-e`)  
 Zeigt Details zu den uwp-apps, die auf dem Computer installiert sind. Diese Details zählen der Paketname und "Appid", die die ausführbare Datei in einer uwp-app zu identifizieren. Verwenden Sie zum Erfassen von Grafikinformationen aus einer Windows Store-Anwendung mit DXCap.exe den Paketnamen und die Anwendungs-ID anstelle der ausführbaren Datei, die verwendet wird, wenn Sie eine Desktop-Anwendung aufnehmen.  
  
 Info-Funktion (`-info)`  
 Zeigt Details über den Computer und Erfassung von DLLs an.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Erfassung von Grafikinformationen aus einer Desktopanwendung  
 Verwendung `-c` zur Angabe der app aus der Sie Grafikinformationen erfassen möchten.  
  
```ms-dos  
DXCap.exe -c BasicHLSL11.exe  
```  
  
 Standardmäßig Grafikinformationen aufgezeichnet, um eine Datei namens `<appname>-<date>-<time>.vsglog`. Verwendung `-file` an eine andere Datei zum Aufzeichnen.  
  
```ms-dos  
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe  
```  
  
 Geben Sie zusätzliche Befehlszeilenparameter für die Anwendung, aus der Sie aufzeichnen an, indem sie sie nach dem Dateinamen der Anwendung einbeziehen.  
  
```ms-dos  
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Der Befehl im obigen Beispiel erfasst Grafikinformationen aus der Desktopversion von Internet Explorer beim Anzeigen der Webseite am www.fishgl.com die die WebGL-API verwendet, um 3D-Inhalt zu rendern.  
  
> [!NOTE]
>  Da die Befehlszeilenargumente, die nach der Anwendung angezeigt werden, die an ihn übergeben werden, müssen Sie die Argumente, die für die DXCap.exe vor der Verwendung vorgesehen angeben der `-c` Option.  
  
### <a name="capture-graphics-information-from-a-uwp-app"></a>Erfassen von Grafikinformationen aus einer uwp-app.  
 Sie können Grafikinformationen aus einer uwp-app erfassen.  
  
```ms-dos  
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Verwendung der DXCap.exe zum Erfassen von einer uwp-app ähnelt der verwenden, um aus einer Windows-desktop-app erfassen jedoch stattdessen eine desktop-app nach Dateinamen identifizieren Sie identifizieren einer uwp-app nach ihrem Paketnamen und dem Namen oder ID der ausführbaren Datei in, das Paket möchten  Erfassen Sie aus. Damit sie einfacher zu erfahren, wie die uwp-apps zu identifizieren, die auf dem Computer installiert sind, verwenden die `-e` -Option mit DXCap.exe, um sie aufzulisten:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Sie können eine optionale Suchzeichenfolge angeben, um die Anwendung zu finden, die Sie suchen. Wenn die zu suchende Zeichenfolge angegeben wird, listet DXCap.exe die uwp-apps, deren Paketname, Anwendungsname oder app-IDs der Suchzeichenfolge entsprechen. Die Groß- und Kleinschreibung wird bei der Suche nicht berücksichtigt.  
  
```ms-dos  
DXCap.exe -e map  
```  
  
 Der obige Befehl listet uwp-apps, die mit "Map"; übereinstimmen. die Ausgabe ist wiefolgt:  
  
 **Package "Microsoft.BingMaps":**  
 **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **Vollständiger Name: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Name: Microsoft.BingMaps**  
 **Herausgeber: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Version          : 2.1.2914.1734**  
 **Ausführbare Anwendungen:**  
 **ID: AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: Nein**  
 **AppSpec (to launch): **DXCap.exe -c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps**** The last line of output for each enumerated app displays the command you can use to capture graphics information from it.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Erfassen Sie bestimmte Bilder oder Bilder zwischen bestimmten Zeiten.  
 Verwendung `-frame` um die Frames anzugeben, die Sie mithilfe von Kommas und Bereichen erfassen möchten:  
  
```ms-dos  
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe  
```  
  
 Oder verwenden Sie `-period` an einen Satz von Zeiträume aus, um die Frames zu erfassen. Zeiträume werden in Sekunden angegeben, und mehrere Bereiche können angegeben werden:  
  
```ms-dos  
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Erfassen Sie Frames interaktiv.  
 Verwendung `-manual` Frames interaktiv erfassen. Drücken Sie die EINGABETASTE, um die Aufnahme zu starten, und drücken Sie die EINGABETASTE, um zu stoppen.  
  
```ms-dos  
DXCap.exe -manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Wiedergeben einer Grafikprotokolldatei  
 Verwendung `-p` eine zuvor aufgezeichnete grafikprotokolldatei wiedergeben.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog  
```  
  
 Lassen Sie den Dateinamen aus, um das Grafikprotokoll wiederzugeben, das zuletzt aufgezeichnet wurde.  
  
```ms-dos  
DXCap.exe -p  
```  
  
### <a name="play-back-in-raw-mode"></a>Wiedergabe im raw-Modus  
 Verwendung `-rawmode` wiedergeben aufgezeichnete Befehle genau so, wie sie aufgetreten sind. Unter einer normalen Wiedergabe werden bestimmte Befehle emuliert, z. B. wird eine Grafikprotokolldatei, die aus einer Vollbild-Anwendung erfasst wurde, in einem Fenster wiedergegeben; bei aktiviertem raw-Modus versucht die gleiche Datei diese im Vollbildmodus wiederzugeben.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Wiedergabe mit WARP oder einem Hardwaregerät  
 Vielleicht möchten Sie die Wiedergabe einer Grafikprotokolldatei erzwingen, die auf einem Hardwaregerät mit WARP aufgezeichnet wurde, oder Sie erzwingen die Wiedergabe eines Protokolls auf einem Hardwaregerät, das WARP verwendet. Verwendung `-warp` für die Wiedergabe mit WARP.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -warp  
```  
  
 Verwendung `-hw` für die Wiedergabe mit Hardware.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Überprüfen einer Grafikprotokolldatei anhand von WARP  
 Unter dem Validierungsmodus wird die Grafikprotokolldatei sowohl auf Hardware als auch WARP wiedergegeben und ihre Ergebnisse werden verglichen. Dadurch können Sie die Rendering-Fehler identifizieren, die vom Treiber verursacht werden. Verwenden Sie so überprüfen Sie die richtige Verhaltens der Grafikhardware gegenüber WARP - V.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Um das Vergleichsmaß zu verringern, können Sie eine Teilmenge der Befehle für die Validierung des Vergleichs angeben, und andere Befehle werden ignoriert. Verwenden Sie - examine, um die Befehle anzugeben, deren Ergebnisse Sie vergleichen möchten.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Konvertieren einer Grafikprotokolldatei in PNG-Dateien  
 Um Frames aus einer Grafikprotokolldatei anzuzeigen oder zu analysieren, können mit DXCap.exe erfasste Frames als PNG (Portable Network Graphics)-Bilddateien gespeichert werden. Verwendung `-screenshot` , unter dem Wiedergabemodus zur Ausgabe aufgezeichneten Frames als PNG-Dateien.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Verwendung `-frame` mit `-screenshot` um die Frames anzugeben, die Sie ausgeben möchten.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Konvertieren einer Grafikprotokolldatei in XML-Dateien  
 Um Grafikprotokolldateien mit vertrauten Tools wie FindStr oder XSLT zu verarbeiten und zu analysieren, kann DXCap.exe eine Grafikprotokolldatei in XML konvertiert werden. Verwendung `-toXML` unter dem Wiedergabemodus, das Protokoll in XML zu konvertieren, anstatt es zu sichern.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -toXML  
```  
  
 Standardmäßig wird die XML-Ausgabe in eine Datei mit demselben Namen wie das Grafikprotokoll geschrieben, aber die Erweiterung .xml wurde zugewiesen. Im obigen Beispiel wird die XML-Datei mit dem Namen werden **regression_test_12.xml**. Um der XML-Datei einen anderen Namen geben, geben Sie ihn nach dem `-toXML`.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml  
```  
  
 Die resultierende Datei enthält XML, die etwa so aussieht:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Anforderungen