---
title: "Gewusst wie: Installieren eines bestimmten Releases von Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Installieren eines bestimmten Releases, Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Gewusst wie: Installieren eines bestimmten Releases von Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wir aktualisieren Visual Studio\-Setup häufig, damit Sie die aktuellste, optimierte Version der optionalen Funktionen erhalten.  Wenn Sie aber ein früheres Release von Visual Studio 2015 installieren möchten, – beispielsweise ein Release von Visual Studio 2015 mit iOS\-Unterstützung vor Update 1 – müssen Sie Visual Studio\-Setup zwingen, eine frühere Version der Funktionsmanifestdateien zu verwenden. Dieser Artikel beschreibt, wie das geht.  
  
## Installieren des aktuellen Releases  
 Seit der Erstveröffentlichung von Visual Studio 2015 haben wir das Setupmodul ein Mal aktualisiert, die Manifestdateien jedoch mehr als fünf Mal.  Das bedeutet, wenn Sie [Visual Studio\-Setup heute herunterladen und ausführen](https://www.visualstudio.com/downloads/download-visual-studio-vs) und dazu einen sauberen Computer mit Internetverbindung verwenden, installiert Setup Visual Studio 2015 Update 1, das die neuesten Produktverbesserungen sowie neuere, aktuelle Versionen der optionalen Funktionen und Tools enthält.  
  
## Installieren früherer Releases  
 Sie können entweder ein ISO\-Image erstellen und einbinden oder das Webinstallationsprogramm direkt herunterladen und starten, wenn Sie anschließend die EXE\-Datei mit zusätzlichen Befehlszeilenparametern \(wie etwa „\/CustomInstallPath“, „\/Full“, „\/InstallSelectableItems“, „\/NoRestart“ usw.\) anfügen, um zu steuern, wie Visual Studio installiert wird.  
  
 In der folgenden Tabelle sind einige spezifische Szenarien für bestimmte Entwicklungsstände und die erforderlichen Befehlszeilenparameter verzeichnet, die an das Enterprise Edition\-Webinstallationsprogramm übergeben werden müssen. \(Die gleichen Parameter funktionieren auch mit den Webinstallationsprogrammen der Community oder Professional Edition.\)  
  
|Visual Studio 2015\-Edition|Auszuführendes Programm|Zu übergebende Befehlszeile|Aktionen von Setup|  
|---------------------------------|-----------------------------|---------------------------------|------------------------|  
|Visual Studio Enterprise \(die neueste veröffentlichte Version\)|Visual Studio Enterprise mit Update 1 \(verfügbar über [VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx)\)|`vs_enterprise.exe` **Note:**  Mit dem Standardverhalten dieser Installation werden die aktuellsten optionalen Funktionen installiert, daher sind dafür keine Befehlszeilenparameter erforderlich.|Visual Studio\-Setup verwendet die aktuellste „feed.xml“ und installiert die aktuellsten Dateien|  
|Visual Studio Enterprise \(ursprüngliche RTM\-Version, jedoch mit Updates vor Update 1\)|Visual Studio Enterprise RTM \(verfügbar über die [Downloadseite für MSDN\-Abonnements](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio\-Setup verwendet die „feed.xml“, die vor der Veröffentlichung von Update 1 aktuell war|  
|Visual Studio Enterprise Update 1 \(das ursprüngliche Update 1 ohne weitere Updates aus der Zeit der allgemeinen Verfügbarkeit von Update 1\)|Visual Studio Enterprise mit Update 1 \(verfügbar über die [Downloadseite für MSDN\-Abonnements](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio\-Setup verwendet die „feed.xml“, die zum Zeitpunkt von Update 1 verfügbar war|  
|Visual Studio Enterprise \(die ursprüngliche RTM\-Version ohne Update\)|Visual Studio Enterprise RTM \(verfügbar über die [Downloadseite für MSDN\-Abonnements](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio\-Setup verwendet die „feed.xml“, die zur Veröffentlichung der RTM\-Version verfügbar war|  
  
> [!IMPORTANT]
>  Ersetzen Sie je nach Sprache, die Sie verwenden möchten, "enu" \(für Englisch\) durch einen der folgenden Werte:  
>   
>  -   chs \(für Chinesisch \(vereinfacht\)\)  
> -   cht \(für Chinesisch \(traditionell\)\)  
> -   csy \(für Tschechisch\)  
> -   deu \(für Deutsch\)  
> -   esn \(für Spanisch\)  
> -   fra \(für Französisch\)  
> -   ita \(für Italienisch\)  
> -   jpa \(für Japanisch\)  
> -   kor \(für Koreanisch\)  
> -   plk \(für Polnisch\)  
> -   ptb \(für Portugiesisch\)  
> -   rus \(für Russisch\)  
> -   trk \(für Türkisch\)  
  
## Siehe auch  
 [Installieren von Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)