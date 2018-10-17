---
title: Entwickeln von Apps für die universelle Windows-Plattform (UWP) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1235416a411935d811f3747fa5127cc395ef0f29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287091"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Entwickeln von Apps für die universelle Windows-Plattform (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Mit der universellen Windows-Plattform und unserem zentralen Windows-Kern können Sie die gleiche App auf jedem Windows 10-Gerät ausführen, von Smartphones bis zu Desktop-PCs. Erstellen Sie diese universellen Windows-Apps mit Visual Studio 2015 und den universellen Windows-App-Entwicklungstools.  
  
 ![Universelle Windows-Plattform](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Führen Sie Ihre App auf einem Windows 10-Phone, Windows 10-Desktop oder einer Xbox aus. Es ist das gleiche App-Paket. Mit der Einführung eines einzelnen, einheitlichen Windows 10-Kerns kann ein App-Paket auf allen Plattformen ausgeführt werden. Mehrere Plattformen verfügen über Erweiterungs-SDKs, die Sie zu Ihrer App hinzufügen können, um die Vorteile bestimmter plattformspezifischer Verhaltensweisen zu nutzen. Mit dem Erweiterungs-SDK für Mobilgeräte wird z. B. die auf einem Windows Phone gedrückte ZURÜCK-Taste behandelt. Wenn Sie in Ihrem Projekt auf ein Erweiterungs-SDK verweisen, fügen Sie einfach Laufzeitüberprüfungen hinzu, um zu prüfen, ob dieses SDK für diese Plattform verfügbar ist. Auf dieses Weise können Sie das gleiche App-Paket für alle Plattformen verwenden.  
  
 **Was ist Windows Core?**  
  
 Zum ersten Mal wurde Windows so umgestaltet, dass ein gemeinsamer Kern für alle Windows 10-Plattformen verwendet wird. Es ist eine gemeinsame Quelle, ein gemeinsamer Windows-Kernel, ein Datei-E/A-Stapel und ein App-Modell vorhanden. Für die Benutzeroberfläche ist nur ein XAML-Benutzeroberlächen-Framework und ein HTML-Benutzeroberflächen-Framework vorhanden. So können Sie sich auf das Entwickeln einer tollen App konzentrieren, weil wir die Bereitstellung Ihrer App auf unterschiedlichen Windows 10-Geräten vereinfacht haben.  
  
 **Was ist die universelle Windows-Plattform?**  
  
 Es ist eine Auflistung von Verträgen und Versionen. Mit diesen können Sie die Ziele auswählen, für die Ihre App ausgeführt werden kann. Es wird nicht länger ein Betriebssystem als Ziel für Ihre App angegeben. Jetzt richten Sie Ihre App auf eine oder mehrere Gerätefamilien aus. Weitere Informationen finden Sie in dieser [Plattform-Anleitung](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
## <a name="requirements"></a>Anforderungen  
 Die Entwicklungstools für universelle Windows-Apps verfügen über Emulatoren, die Sie verwenden können, um zu prüfen, wie Ihre App auf unterschiedlichen Geräten aussieht. Wenn Sie diesen Emulatoren verwenden möchten, müssen Sie diese Software auf einem physischen Computer installieren. Auf dem physischen Computer muss Windows 8.1 (X 64) Professional Edition oder höher installiert sein, und er muss über einen Prozessor verfügen, der Hyper-V für Clients und SLAT (Second Level Address Translation) unterstützt. Die Emulatoren können nicht verwendet werden, wenn Visual Studio auf einem virtuellen Computer installiert ist.  
  
 Hier finden Sie die Liste erforderlicher Softwarekomponenten:  
  
-   [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
-   [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Stellen Sie sicher, dass die Tools für die universelle Windows-App-Entwickung in der Liste der optionalen Features ausgewählt sind. Ohne diese Tools können Sie keine universellen Apps erstellen.  
  
 Nach der Installation der Software müssen Sie Ihr [Windows 10-Gerät](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) für die Entwicklung aktivieren. (Eine Entwicklerlizenz für jedes Windows 10-Gerät wird nicht mehr benötigt.)  
  
 **Windows 8.1- und Windows 7-Unterstützung**  
  
 Wenn Sie universelle Windows-Apps mit Visual Studio 2015 auf einer anderen Plattform als Windows 10 entwickeln möchten, sind dies die Einschränkungen:  
  
-   Windows 8.1: Sie können die App nicht lokal ausführen (Nur auf einem Windows-10-Remotegerät). Sie können die Emulatoren in Visual Studio, jedoch nicht den Simulator verwenden.  
  
-   Windows 8.1: Sie können die App nicht lokal ausführen (Nur auf einem Windows-10-Remotegerät). Sie können weder die Emulatoren noch den Simulator in Visual Studio verwenden.  
  
 Sie können den XAML-Designer nur verwenden, wenn Ihre Entwicklungsplattform Windows 10 ist.  
  
## <a name="universal-windows-apps"></a>Universelle Windows-Apps  
 Wählen Sie Ihre bevorzugte Entwicklungssprache aus C#, Visual Basic, C++ oder JavaScript aus, um [eine universelle Windows-App für Geräte unter Windows 10 zu erstellen](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Oder schauen Sie sich dieses [Video zu den Ersten Schritten](http://channel9.msdn.com/Series/ConnectOn-Demand/229)an.  
  
 Wenn Sie über Windows Store 8.1-Apps, Windows Phone 8.1-Apps oder mit Visual Studio 2015 RC erstellte universelle Windows-Apps verfügen, [portieren Sie diese vorhandenen Apps](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) , um die neueste Version der universellen Windows-Plattform zu verwenden.  
  
 Nachdem Sie die universelle Windows-App erstellt haben, müssen Sie [Ihre App packen](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) , um sie auf einem Windows 10-Gerät zu installieren oder an den Windows Store zu übermitteln.

