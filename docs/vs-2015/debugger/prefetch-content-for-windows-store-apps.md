---
title: Vorab rufen von Inhalt für Windows Store-Apps | Microsoft-Dokumentation
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
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300524"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Vorabrufen von Inhalt für Windows Store-Apps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt nur für Windows] (.. /Image/windows_only_content. png "windows_only_content")  
  
 Damit Ihre Windows Store-App reaktionsfähiger wird, können Sie anfordern, dass Windows einige Webinhalte wie Webseiten oder Bilder vorab in den [WinInet](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)-[WinInet](https://msdn.microsoft.com/library/aa383630.aspx)-Cache der APP lädt. Diese Funktion wird als Vorabrufen bezeichnet. Vorabrufen ist besonders effektiv für Inhalte, die beim Starten verwendet werden, aber Sie können auch andere häufig genutzte Inhalte abrufen. Mit den Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx)-Klasse können Sie die URIs der gewünschten Inhalte angeben.  
  
 Windows bestimmt heuristisch, wann und ob Vorabrufvorgänge stattfinden und welche Ressourcen heruntergeladen werden. Die Heuristik berücksichtigt Netzwerk- und Leistungsbedingungen des Systems für das Konto, den Verwendungsverlauf der App für den Benutzer und die Ergebnisse von früheren Vorabrufversuchen. Mit dem Befehl **Vorabrufen von Windows Store-App auslösen** in Visual Studio zwingen Sie Windows, die ContentPrefetcher-Heuristik zu ignorieren und sämtliche angegebenen Webinhalte vorab zu laden. Das kann nützlich sein, um das Verhalten oder die Leistung der App zu testen, wenn der Inhalt in einem bekannten Zustand (entweder geladen oder nicht geladen) vorabgerufen wird.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Erzwingen von Vorabladen von Ressourcen, die mit "ContentPrefetcher" angegeben werden  
 Dieses Verfahren setzt voraus, dass Sie die ContentPrefetcher-Funktionalität bereits im App-Projekt eingerichtet und die gewünschten Inhalts-URIs zum Vorabladen angegeben haben. Um das Vorabladen von Inhalt zu erzwingen, wenn die angegebenen Ressourcen neu sind oder geändert wurden, müssen Sie die App starten und beenden, bevor Sie den Befehl **Vorabrufen von Windows Store-App auslösen** auswählen. Sie führen zuerst die App aus, um die URIs zu registrieren. Anschließend zwingt der Befehl **Vorabrufen von Windows Store-App auslösen** die ContentPrefetcher-Funktionalität dazu, den Inhalt herunterzuladen und dem Cache hinzuzufügen. Bei nachfolgenden Ausführungen der App können Sie voraussetzen, dass der Inhalt vorab geladen wurde.  
  
1. Starten Sie die App, um die Inhalts-URIs zum Vorabladen in der App zu registrieren. Wählen Sie anschließend im Menü **Debuggen** die Option **Debuggen starten** (Tastenkombination: F5) aus.  
  
2. Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden** (Tastenkombination: UMSCHALT+F5) aus.  
  
3. Wählen Sie im Menü **Debuggen** die Option **Andere Debugziele** und anschließend **Vorabrufen von Windows Store-App auslösen** aus.  
  
   Sie können die App jetzt mit den vorabgerufenen Webressourcen debuggen, testen oder analysieren.  
  
> [!NOTE]
> Wiederholen Sie diese Schritte jedes Mal, wenn Sie die angegebenen Webinhalte ändern oder neue hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Blog Beitrag: Auslösen von Vorabruf für Windows Store-Apps in Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
