---
title: Visual Studio und Xamarin | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: c16898fa94bcdb051b215f3ff89cf4d42cbe7fe7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio und Xamarin

Xamarin ist eine Entwicklungsplattform für mobile Apps zum Erstellen nativer iOS-, Android- und Windows-Apps auf einer gemeinsamen C#/.NET-Codebasis. Für in Xamarin geschriebene Apps kann eine Wiederverwendung des Codes über die Plattformgrenzen hinweg zwischen 75 % und nahezu 100 % erzielt werden. Diese Apps haben vollen Zugriff auf die zugrundeliegenden Plattform-APIs und können native Benutzeroberflächen integrieren. Sie werden zu plattformspezifischen Paketen mit geringem Einfluss auf die Laufzeitleistung kompiliert. (Hinweis: Xamarin unterstützt auch F#. In dieser Dokumentation wird jedoch nur C# behandelt. Visual Basic wird derzeit nicht unterstützt.)  
  
Entwickler, die mit C#, .NET und Visual Studio vertraut sind, werden die gleiche Leistung und Produktivität bei der Arbeit mit Xamarin für mobile Apps genießen. Diese Vorteile schließen das Remotedebuggen auf Android-, iOS- und Windows-Geräten ein, ohne dass Sie native Programmiersprachen wie Objective-C oder Java erlernen müssen. So überrascht es kaum, dass viele sehr leistungsstarke Apps mit überzeugender Benutzeroberfläche – wie etwa NASCAR, Aviva und MixRadio – mithilfe von Xamarin erstellt wurden.  
  
Diese Dokumentation unterstützt Sie bei der Bewertung der Leistung von **Visual Studio mit Xamarin** beim Erstellen dieser Oberflächen.  
  
-   Beginnen Sie mit [Setup and install](../cross-platform/setup-and-install.md). Dieser Vorgang wird einige Zeit in Anspruch nehmen (normalerweise 2–4 Stunden, abhängig von der Geschwindigkeit Ihrer Internetverbindung, der bereits installieren Software und den ausgewählten Optionen).  
  
-   Während die Installationsprogramme ausgeführt werden, können Sie [Learn about mobile development with Xamarin (Informationen zur Mobile-Entwicklung mit Xamarin)](learn-about-mobile-development-with-xamarin.md) lesen. Hier lernen Sie Xamarin kennen, können Xamarin.Forms und native UI miteinander vergleichen und vieles mehr.  
  
-   Lesen Sie nach Abschluss der Installation [Verify your Xamarin environment (Überprüfen der Xamarin-Umgebung)](../cross-platform/verify-your-xamarin-environment.md).  
  
-   Schließen Sie den Vorgang mit dem Tutorial [Learn app-building basics with Xamarin.Forms in Visual Studio (Grundlegendes zur Erstellung von Apps mit Xamarin.Forms in Visual Studio)](/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
Die Xamarin-Funktionen können in [allen Editionen von Visual Studio 2017](https://www.visualstudio.com/vs) (Community, Professional und Enterprise) verwendet werden. Es ist keine separate Lizenz erforderlich.  
  
> [!NOTE]
>  In diesen Anweisungen ist die einfachste und geradlinigste Computerkonfiguration für Entwickler mit Windows- und Visual Studio-Hintergrund beschrieben. Bei dieser Konfiguration vereinfacht sich die Entwicklung durchgängig, da Sie mit dem Mac nur für die Verwendung des iOS-Simulators und der verbundenen Geräte interagieren müssen. Wenn Sie jedoch aus dem Mac-Umfeld stammen, empfehlen wir, entweder Visual Studio innerhalb von Parallels oder VMware auszuführen oder Visual Studio für Mac zu verwenden. Eine Anleitung finden Sie unter [Setup, install, and verifications for Mac users (Setup, Installation und Überprüfungen für Mac-Benutzer)](../cross-platform/setup-install-and-verifications-for-mac-users.md).  
  
> [!NOTE]
>  Wenn Sie nach einer plattformübergreifenden Entwicklungslösung auf der Basis von HTML und CSS suchen, prüfen Sie die Visual Studio-Tools für Apache Cordova. Eine Beschreibung hierzu finden Sie unter [Cross-Platform Development in Visual Studio (Plattformübergreifende Entwicklung in Visual Studio)](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).