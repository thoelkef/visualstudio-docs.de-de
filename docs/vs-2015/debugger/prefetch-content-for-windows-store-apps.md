---
title: Vorabrufen von Inhalt für Windows Store-apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b01e0cd841c6239a7f2ef76f964482348ee16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513274"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Vorabrufen von Inhalt für Windows Store-Apps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorabrufen von Inhalt für Windows Store-apps](https://docs.microsoft.com/visualstudio/debugger/prefetch-content-for-windows-store-apps).  
  
Bezieht sich nur auf Windows] (.. /Image/windows_only_content.png "Windows_only_content")  
  
 Um Ihre Windows Store-app Reaktionsfähigkeit zu steigern, können Sie anfordern, Windows einige Webinhalte wie Webseiten oder Bilder in der Anwendung vorab geladen [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)Cache. Diese Funktion wird als Vorabrufen bezeichnet. Vorabrufen ist besonders effektiv für Inhalte, die beim Starten verwendet werden, aber Sie können auch andere häufig genutzte Inhalte abrufen. Die Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) -Klasse können Sie die URIs der gewünschten Inhalte angeben, die vorab geladen werden sollen. Finden Sie im Windows SDK [Beispiel zum Vorabrufen von Inhalt](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) für Beispiele zum Hinzufügen der ContentPrefetcher-Funktionalität zu Ihrer app.  
  
 Windows bestimmt heuristisch, wann und ob Vorabrufvorgänge stattfinden und welche Ressourcen heruntergeladen werden. Die Heuristik berücksichtigt Netzwerk- und Leistungsbedingungen des Systems für das Konto, den Verwendungsverlauf der App für den Benutzer und die Ergebnisse von früheren Vorabrufversuchen. In Visual Studio können Sie die **Vorabrufen von Windows Store-App** Befehl aus, um zu erzwingen, dass Windows die ContentPrefetcher-Heuristik zu ignorieren und sämtliche angegebenen Webinhalte vorab zu laden. Das kann nützlich sein, um das Verhalten oder die Leistung der App zu testen, wenn der Inhalt in einem bekannten Zustand (entweder geladen oder nicht geladen) vorabgerufen wird.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Erzwingen von Vorabladen von Ressourcen, die mit "ContentPrefetcher" angegeben werden  
 Dieses Verfahren setzt voraus, dass Sie die ContentPrefetcher-Funktionalität bereits im App-Projekt eingerichtet und die gewünschten Inhalts-URIs zum Vorabladen angegeben haben. Zum Vorabladen von Inhalt zu erzwingen, wenn die angegebenen Ressourcen neu sind oder geändert wurden, müssen Sie starten und beenden die app aus, bevor Sie entscheiden das **Vorabrufen von Windows Store-App** Befehl. Sie führen zuerst die App aus, um die URIs zu registrieren. **Vorabrufen von Windows Store App** Befehl zwingt dann die contentprefetcher-Funktionalität dazu, den Inhalt herunterzuladen und dem Cache hinzuzufügen. Bei nachfolgenden Ausführungen der App können Sie voraussetzen, dass der Inhalt vorab geladen wurde.  
  
1.  Starten Sie die App, um die Inhalts-URIs zum Vorabladen in der App zu registrieren. Auf der **Debuggen** Menü wählen **Debuggen starten** (Tastenkombination: F5).  
  
2.  Auf der **Debuggen** Menü wählen **Debuggen beenden** (Tastenkombination: UMSCHALT + F5).  
  
3.  Auf der **Debuggen** Menü wählen **andere Debugziele** und wählen Sie dann **Vorabrufen von Windows Store-App**.  
  
 Sie können die App jetzt mit den vorabgerufenen Webressourcen debuggen, testen oder analysieren.  
  
> [!NOTE]
>  Wiederholen Sie diese Schritte jedes Mal, wenn Sie die angegebenen Webinhalte ändern oder neue hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Blogbeitrag: Auslösen der Vorabruf für Windows Store-Apps in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)



