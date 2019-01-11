---
title: 'Vorgehensweise: Installieren eines bestimmten Releases | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 42776c20cd6634903344569f9ce1f35a776c5f86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959894"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Vorgehensweise: Installieren eines bestimmten Releases von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wir aktualisieren Visual Studio-Setup häufig, damit Sie die aktuellste, optimierte Version der optionalen Funktionen erhalten.  Wenn Sie aber ein früheres Release von Visual Studio 2015 installieren möchten, – beispielsweise ein Release von Visual Studio 2015 mit iOS-Unterstützung vor Update 1 – müssen Sie Visual Studio-Setup zwingen, eine frühere Version der Funktionsmanifestdateien zu verwenden. Dieser Artikel beschreibt, wie das geht.

## <a name="installing-the-current-release"></a>Installieren des aktuellen Releases
 Seit der ersten Version von Visual Studio 2015 haben wir das Setupmodul und die Manifestdateien mehrmals aktualisiert.  Dies bedeutet, dass, wenn Sie den Installer von Herunterladen der [Visual Studio-Downloads](https://www.visualstudio.com/downloads/download-visual-studio-vs) -Website auf einem sauberen, Internet verbundenen Computer wird die neueste Visual Studio 2015 zu aktualisieren, darunter die neuesten produktverbesserungen sowie neuere, aktuelle Versionen der optionalen Funktionen und Tools.

## <a name="installing-earlier-releases"></a>Installieren früherer Releases
 Sie können entweder erstellen und Bereitstellen eines ISO-Abbilds oder können Sie herunterladen und starten Sie das Installationsprogramm direkt aus [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) und fügen Sie dann die .exe-Datei mit zusätzlichen Befehlszeilenparametern (wie z. B. custominstallpath, / voll ist, / InstallSelectableItems "," / norestart usw..) Steuern Sie, wie Visual Studio installiert wird.

 Die folgende Tabelle enthält einige spezifischen Szenarien für Point-in-Time- und die erforderlichen Befehlszeilenparameter verzeichnet, die an dem Enterprise-Edition-webinstallationsprogramm übergeben werden müssen. (Die gleichen Parameter funktionieren auch mit den Installationsprogrammen der Community oder Professional Edition.)

|Visual Studio 2015-Edition|Auszuführendes Programm|Zu übergebende Befehlszeile|Aktionen von Setup|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (die neueste veröffentlichte Version)|Visual Studio Enterprise mit Updates (verfügbar über [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Hinweis:**  Mit dem Standardverhalten dieser Installation werden die aktuellsten optionalen Funktionen installiert, daher sind dafür keine Befehlszeilenparameter erforderlich.|Visual Studio-Setup verwendet die aktuellste „feed.xml“ und installiert die aktuellsten Dateien|
|Visual Studio Enterprise Update 3 (das ursprüngliche Update 3 ohne weitere Updates aus der Zeit der allgemeinen Verfügbarkeit von Update 3)|Visual Studio Enterprise RTM (verfügbar über die [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Visual Studio-Setup verwendet die "Feed.xml", die verfügbar waren, bei der Veröffentlichung von Update 3|
|Visual Studio Enterprise Update 2 (die ursprüngliche Update 2, jedoch mit updates, dass vor Update 3)|Visual Studio Enterprise RTM (verfügbar über die [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Visual Studio-Setup verwendet die „feed.xml“, die vor der Veröffentlichung von Update 3 aktuell war|
|Visual Studio Enterprise (die ursprüngliche Update 2 ohne weitere Update 2-Ära Updates)|Visual Studio Enterprise RTM (verfügbar über die [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Visual Studio-Setup verwendet die "Feed.xml", die verfügbar waren, bei der Veröffentlichung von Update 2|
|Visual Studio Enterprise Update 1 (das ursprüngliche Update 1, aber mit updates, vor Update 2)|Visual Studio Enterprise RTM (verfügbar über die [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Visual Studio-Setup verwendet die „feed.xml“, die vor der Veröffentlichung von Update 2 aktuell war|
|Visual Studio Enterprise Update 1 (das ursprüngliche Update 1 ohne weitere Updates aus der Zeit der allgemeinen Verfügbarkeit von Update 1)|Visual Studio Enterprise RTM (verfügbar über die [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio-Setup verwendet die "Feed.xml", die verfügbar waren, bei der Veröffentlichung von Update 1|
|Visual Studio Enterprise (ursprüngliche RTM-Version, jedoch mit Updates vor Update 1)|Visual Studio Enterprise RTM (verfügbar über die  [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/en-us/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio-Setup verwendet die „feed.xml“, die vor der Veröffentlichung von Update 1 aktuell war|
|Visual Studio Enterprise (die ursprüngliche RTM-Version ohne Update)|Visual Studio Enterprise RTM (verfügbar über die [Downloadseite für MSDN-Abonnements](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio-Setup verwendet die "Feed.xml", die bei der Veröffentlichung der RTM-Version verfügbar war|

> [!IMPORTANT]
>  Ersetzen Sie je nach Sprache, die Sie verwenden möchten, "enu" (für Englisch) durch einen der folgenden Werte:
>
> - chs (für Chinesisch (vereinfacht))
>   -   cht (für Chinesisch (traditionell))
>   -   csy (für Tschechisch)
>   -   deu (für Deutsch)
>   -   esn (für Spanisch)
>   -   fra (für Französisch)
>   -   ita (für Italienisch)
>   -   jpa (für Japanisch)
>   -   kor (für Koreanisch)
>   -   plk (für Polnisch)
>   -   ptb (für Portugiesisch)
>   -   rus (für Russisch)
>   -   trk (für Türkisch)

## <a name="see-also"></a>Siehe auch
 [Administratorhandbuch für Visual Studio](../install/visual-studio-administrator-guide.md)