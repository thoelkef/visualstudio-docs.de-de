---
title: Vorabrufen von Inhalt für Windows Store-apps | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04842202e8534c551212d7322ab74e9b0ace5848
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446181"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Vorabrufen von Inhalt für Windows Store-Apps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bezieht sich nur auf Windows] (.. /Image/windows_only_content.png "Windows_only_content")  
  
 Um Ihre Windows Store-app Reaktionsfähigkeit zu steigern, können Sie anfordern, Windows einige Webinhalte wie Webseiten oder Bilder in der Anwendung vorab geladen [WinINet](http://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)Cache. Diese Funktion wird als Vorabrufen bezeichnet. Vorabrufen ist besonders effektiv für Inhalte, die beim Starten verwendet werden, aber Sie können auch andere häufig genutzte Inhalte abrufen. Mit den Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx)-Klasse können Sie die URIs der gewünschten Inhalte angeben. Beispiele zum Hinzufügen der ContentPrefetcher-Funktionalität zu Apps finden Sie im [Windows SDK-Beispiel zum Vorabrufen von Inhalt](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309).  
  
 Windows bestimmt heuristisch, wann und ob Vorabrufvorgänge stattfinden und welche Ressourcen heruntergeladen werden. Die Heuristik berücksichtigt Netzwerk- und Leistungsbedingungen des Systems für das Konto, den Verwendungsverlauf der App für den Benutzer und die Ergebnisse von früheren Vorabrufversuchen. Mit dem Befehl **Vorabrufen von Windows Store-App auslösen** in Visual Studio zwingen Sie Windows, die ContentPrefetcher-Heuristik zu ignorieren und sämtliche angegebenen Webinhalte vorab zu laden. Das kann nützlich sein, um das Verhalten oder die Leistung der App zu testen, wenn der Inhalt in einem bekannten Zustand (entweder geladen oder nicht geladen) vorabgerufen wird.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Erzwingen von Vorabladen von Ressourcen, die mit "ContentPrefetcher" angegeben werden  
 Dieses Verfahren setzt voraus, dass Sie die ContentPrefetcher-Funktionalität bereits im App-Projekt eingerichtet und die gewünschten Inhalts-URIs zum Vorabladen angegeben haben. Um das Vorabladen von Inhalt zu erzwingen, wenn die angegebenen Ressourcen neu sind oder geändert wurden, müssen Sie die App starten und beenden, bevor Sie den Befehl **Vorabrufen von Windows Store-App auslösen** auswählen. Sie führen zuerst die App aus, um die URIs zu registrieren. Anschließend zwingt der Befehl **Vorabrufen von Windows Store-App auslösen** die ContentPrefetcher-Funktionalität dazu, den Inhalt herunterzuladen und dem Cache hinzuzufügen. Bei nachfolgenden Ausführungen der App können Sie voraussetzen, dass der Inhalt vorab geladen wurde.  
  
1. Starten Sie die App, um die Inhalts-URIs zum Vorabladen in der App zu registrieren. Wählen Sie anschließend im Menü **Debuggen** die Option **Debuggen starten** (Tastenkombination: F5) aus.  
  
2. Auf der **Debuggen** Menü wählen **Debuggen beenden** (Tastenkombination: UMSCHALT + F5).  
  
3. Wählen Sie im Menü **Debuggen** die Option **Andere Debugziele** und anschließend **Vorabrufen von Windows Store-App auslösen** aus.  
  
   Sie können die App jetzt mit den vorabgerufenen Webressourcen debuggen, testen oder analysieren.  
  
> [!NOTE]
> Wiederholen Sie diese Schritte jedes Mal, wenn Sie die angegebenen Webinhalte ändern oder neue hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Blogbeitrag: Vorabrufen auslösen, für Windows Store-Apps in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)
