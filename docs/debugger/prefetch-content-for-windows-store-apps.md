---
title: "Vorabrufen von Inhalt f&#252;r Windows Store-Apps | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vorabrufen von Inhalt f&#252;r Windows Store-Apps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um die Reaktionsfähigkeit der Windows Store\-App zu steigern, können Sie Windows auffordern, einige Webinhalte wie Webseiten oder Bilder vorab in den [WinINet](http://msdn.microsoft.com/de-de/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)\-Cache der App zu laden. Diese Funktion wird als Vorabrufen bezeichnet. Vorabrufen ist besonders effektiv für Inhalte, die beim Starten verwendet werden, aber Sie können auch andere häufig genutzte Inhalte abrufen. Mit den Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx)\-Klasse können Sie die URIs der Inhalte angeben, die Sie vorab laden. Beispiele zum Hinzufügen der ContentPrefetcher\-Funktionalität zu Apps finden Sie im [Windows SDK\-Beispiel zum Vorabrufen von Inhalt](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309).  
  
 Windows bestimmt heuristisch, wann und ob Vorabrufvorgänge stattfinden und welche Ressourcen heruntergeladen werden. Die Heuristik berücksichtigt Netzwerk\- und Leistungsbedingungen des Systems für das Konto, den Verwendungsverlauf der App für den Benutzer und die Ergebnisse von früheren Vorabrufversuchen. Mit dem Befehl **Vorabrufen von Windows Store\-App auslösen** in Visual Studio zwingen Sie Windows, die ContentPrefetcher\-Heuristik zu ignorieren und sämtliche angegebenen Webinhalte vorab zu laden. Das kann nützlich sein, um das Verhalten oder die Leistung der App zu testen, wenn der Inhalt in einem bekannten Zustand \(entweder geladen oder nicht geladen\) vorabgerufen wird.  
  
## Erzwingen von Vorabladen von Ressourcen, die mit "ContentPrefetcher" angegeben werden  
 Dieses Verfahren setzt voraus, dass Sie die ContentPrefetcher\-Funktionalität bereits im App\-Projekt eingerichtet und die gewünschten Inhalts\-URIs zum Vorabladen angegeben haben. Um das Vorabladen von Inhalt zu erzwingen, wenn die angegebenen Ressourcen neu sind oder geändert wurden, müssen Sie die App starten und beenden, bevor Sie den Befehl **Vorabrufen von Windows Store\-App auslösen** auswählen. Sie führen zuerst die App aus, um die URIs zu registrieren. Anschließend zwingt der Befehl **Vorabrufen von Windows Store\-App auslösen** die ContentPrefetcher\-Funktionalität dazu, den Inhalt herunterzuladen und dem Cache hinzuzufügen. Bei nachfolgenden Ausführungen der App können Sie voraussetzen, dass der Inhalt vorab geladen wurde.  
  
1.  Starten Sie die App, um die Inhalts\-URIs zum Vorabladen in der App zu registrieren. Wählen Sie anschließend im Menü **Debuggen** die Option **Debuggen starten** \(Tastenkombination: F5\) aus.  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden** \(Tastenkombination: UMSCHALT\+F5\) aus.  
  
3.  Wählen Sie im Menü **Debuggen** die Option **Andere Debugziele** und anschließend **Vorabrufen von Windows Store\-App auslösen** aus.  
  
 Sie können die App jetzt mit den vorabgerufenen Webressourcen debuggen, testen oder analysieren.  
  
> [!NOTE]
>  Wiederholen Sie diese Schritte jedes Mal, wenn Sie die angegebenen Webinhalte ändern oder neue hinzufügen.  
  
## Siehe auch  
 [Blogbeitrag: Triggering Prefetch for Windows Store Apps in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)