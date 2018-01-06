---
title: Debuggen Sie Prefetch Inhalt in uwp-apps mit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: f98867a5420755ca2eb4e2fb5e75070759a1a91b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debuggen von uwp-apps mit Prefetch Inhalt in Visual Studio
![Gilt nur für Windows](../debugger/media/windows_only_content.png "Windows_only_content")  
  
 Um die uwp-app Reaktionsfähigkeit vorzunehmen, können Sie Windows einige Webinhalte wie Webseiten oder Bilder in der app vorab anfordern [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)Cache. Diese Funktion wird als Vorabrufen bezeichnet. Sie können andere häufig genutzte Inhalte Vorabrufen, aber es ist besonders effektiv für Inhalte, die beim Start verwendet wird. Die Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) -Klasse können Sie die URIs des Inhalts angeben, die Sie laden möchten. Finden Sie im Windows SDK [Beispiel zum Vorabrufen von Inhalt](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) Beispiele zum Hinzufügen der ContentPrefetcher-Funktionalität zu Ihrer app.  
  
 Windows bestimmt heuristisch, wann und ob Vorabrufvorgänge stattfinden und welche Ressourcen heruntergeladen werden. Die Heuristik berücksichtigt Netzwerk- und Leistungsbedingungen des Systems für das Konto, den Verwendungsverlauf der App für den Benutzer und die Ergebnisse von früheren Vorabrufversuchen. In Visual Studio können Sie die **Vorabrufen von Windows Store-App** Befehl zum Erzwingen von Windows die ContentPrefetcher-Heuristik zu ignorieren und sämtliche angegebenen Webinhalte vorab zu laden. Das kann nützlich sein, um das Verhalten oder die Leistung der App zu testen, wenn der Inhalt in einem bekannten Zustand (entweder geladen oder nicht geladen) vorabgerufen wird.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Erzwingen von Vorabladen von Ressourcen, die mit "ContentPrefetcher" angegeben werden  
 Dieses Verfahren setzt voraus, dass Sie die ContentPrefetcher-Funktionalität bereits im App-Projekt eingerichtet und die gewünschten Inhalts-URIs zum Vorabladen angegeben haben. Um das Vorabladen von Inhalt zu erzwingen, wenn die angegebenen Ressourcen neu sind oder geändert wurden, starten und beenden die app aus, bevor Sie auswählen, stehen Ihnen die **Vorabrufen von Windows Store-App** Befehl. Sie führen zuerst die App aus, um die URIs zu registrieren. **Vorabrufen von Windows Store-App** Befehl anschließend zwingt der contentprefetcher-Funktionalität dazu, den Inhalt herunterzuladen und dem Cache hinzuzufügen. Bei nachfolgenden Ausführungen der App können Sie voraussetzen, dass der Inhalt vorab geladen wurde.  
  
1.  Starten Sie die App, um die Inhalts-URIs zum Vorabladen in der App zu registrieren. Auf der **Debuggen** Menü wählen **Debuggen** (Tastenkombination: F5).  
  
2.  Auf der **Debuggen** Menü wählen **Beenden des Debuggens** (Tastenkombination: UMSCHALT + F5).  
  
3.  Auf der **Debuggen** Menü wählen **andere Debugziele** und wählen Sie dann **Vorabrufen von Windows Store-App**.  
  
 Sie können die App jetzt mit den vorabgerufenen Webressourcen debuggen, testen oder analysieren.  
  
> [!NOTE]
>  Wiederholen Sie diese Schritte jedes Mal, wenn Sie die angegebenen Webinhalte ändern oder neue hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Blogbeitrag: Auslösen des Vorabrufens für Windows Store-Apps in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)