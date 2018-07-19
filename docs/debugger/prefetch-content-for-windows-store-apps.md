---
title: Debuggen mithilfe von vorab abgerufenem Inhalt in UWP-apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 458b320b971cbb3c4db74d6f2202455332ca5465
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056321"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debuggen von UWP-apps mithilfe von vorab abgerufenem Inhalt in Visual Studio
  
 Um die UWP-app Reaktionsfähigkeit zu steigern, können Sie anfordern, Windows einige Webinhalte wie Webseiten oder Bilder in der Anwendung vorab geladen [WinINet](/windows/desktop/WinInet/about-wininet) Cache. Diese Funktion wird als Vorabrufen bezeichnet. Es ist besonders effektiv für Inhalte, die beim Start verwendet wird, aber Sie können auch andere häufig genutzten Inhalte Vorabrufen. Die Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) -Klasse können Sie die URIs der gewünschten Inhalte angeben, die vorab geladen werden sollen. Finden Sie im Windows SDK [Beispiel zum Vorabrufen von Inhalt](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) für Beispiele zum Hinzufügen der ContentPrefetcher-Funktionalität zu Ihrer app.  
  
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