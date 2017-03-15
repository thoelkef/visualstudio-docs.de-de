---
title: "Visual C++ für die plattformübergreifende Mobile-Entwicklung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 9
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 591fc488e2a2801fd6acb6e065038d11aaa13b67
ms.lasthandoff: 02/22/2017

---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ für plattformübergreifende Mobile-Entwicklung
Mithilfe von Visual C++ für plattformübergreifende Mobile-Entwicklung können Sie native C++-Apps für iOS-, Android- und Windows-Geräte erstellen sowie für iOS, Android und Windows erstellten allgemeinen Code in Bibliotheken freigeben. Mit dieser in Visual Studio 2015 optional verfügbaren Komponente werden die SDKs und Tools installiert, die Sie für die plattformübergreifende Entwicklung von freigegebenen Bibliotheken und systemeigenen Apps benötigen. Bei Installation können Sie mithilfe von Visual C++ Code erstellen, der außer auf Windows-, Windows Phone- und Xbox- auch auf iOS- und Android-Geräten und -Plattformen ausgeführt werden kann.  
  
 Das Schreiben von Code für mehrere Plattformen kann recht mühsam sein. Die primären Entwicklungssprachen und Tools für iOS, Android und Windows sind auf jeder Plattform unterschiedlich. Alle Plattformen unterstützen jedoch das Schreiben von Code in C++. Dies ist der gemeinsame Nenner, der es Ihnen ermöglicht, Kerncode plattformübergreifend zu wiederzuverwenden. In C++ geschriebener systemeigener Code kann sowohl leistungsfähiger als auch beständiger gegen Reverse Engineering sein. Die Wiederverwendung von Code spart Zeit und Mühe beim Erstellen von Apps für mehrere Plattformen.  
  
 Die Entwicklung mit Visual C++ für plattformübergreifende Mobile-Entwicklung hat mehrere Vorteile:  
  
1.  **Einfache Installation.** Der Visual Studio-Installer ruft die erforderlichen Tools von Drittanbietern und SDKs ab, die Sie zum Erstellen von Apps oder Bibliotheken für Android und iOS benötigen, und installiert diese. Konfiguration und Installation sind einfach und erfolgen größtenteils automatisch.  
  
2.  **Eine leistungsstarke und vertraute Buildumgebung.** Erstellen Sie freigebbare plattformübergreifende Projektmappen und Projekte einfach mit Visual Studio-Vorlagen. Verwalten Sie die Eigenschaften für alle Projekte mit einer gemeinsamen Oberfläche. Bearbeiten Sie den gesamten Code im Visual Studio-Editor, und nutzen Sie die integrierte plattformübergreifende IntelliSense-Funktion für die Codevervollständigung und Fehlerhervorhebung.  
  
3.  **Einheitliche Funktionen für das Debuggen.** Verwenden Sie die erstklassigen Debugtools in Visual Studio, um den C++-Code auf allen Plattformen, einschließlich Android-Geräten und -Emulatoren, iOS-Simulatoren und -Geräten sowie Windows- oder Windows Phone-Geräten und -Emulatoren, zu überwachen und zu durchlaufen.  
  
## <a name="get-the-tools"></a>Beschaffung der Tools  
 Visual C++ für plattformübergreifende Mobile-Entwicklung ist eine optionale Komponente, die in Visual Studio 2015 enthalten ist. Erforderliche Komponenten und Installationsanweisungen finden Sie unter [Install Visual C++ for Cross-Platform Mobile Development (Installieren von Visual C++ für die plattformübergreifende Mobile-Entwicklung)](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Um Code für iOS zu erstellen, benötigen Sie auch einen Macintosh-Computer und ein Apple iOS-Entwicklerkonto. Weitere Informationen finden Sie unter [Install And Configure Tools to Build using iOS (Installieren und Konfigurieren von Tools zu Erstellen mit iOS)](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Optimales Leistungsniveau  
 Für alle, die bislang in der Android- oder iOS- Entwicklung zu Hause waren, steht hilfreiches Material für die ersten Schritte zur Verfügung. Visual Studio ist eine ausdrucksvolle und leistungsfähige Entwicklungsumgebung. Informationen dazu, wie Sie das Programm nutzen können, finden Sie unter [Erste Schritte für Android-Entwickler](https://msdn.microsoft.com/en-us/library/windows/apps/dn275875.aspx) bzw. [Erste Schritte für iOS-Entwickler](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj657966.aspx). Diese Themen machen Sie mit Visual Studio und den Konzepten vertraut, die Sie benötigen, um plattformübergreifende Apps für Windows und Windows Phone zu entwickeln. Informationen zu den ersten Schritten beim Schreiben Ihrer ersten plattformübergreifenden App für iOS und Android finden Sie unter [Build an OpenGL ES Application on Android and iOS (Erstellen einer OpenGL ES-Anwendung für Android und iOS)](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ für plattformübergreifende Mobile-Entwicklung umfasst mehrere Vorlagen, die Ihnen bei Ihren Apps helfen sollen:  
  
-   OpenGLES 2-Anwendung (Android, iOS, Windows Universal)  
  
     Erstellt eine Projektmappe, die Projekte zum Erstellen einer Android Native Activity-, iOS- und Universal Windows-App sowie eine freigegebene C++-Codebibliothek enthält. Diese Apps verwenden plattformspezifische Bibliotheken mit gemeinsamem C++ OpenGL ES-Code zum Zeichnen des gleichen sich drehenden Würfels in jeder App. Wenn Sie diese Vorlage verwenden möchten, müssen Sie bei der Installation von Visual Studio die Option „Entwicklungstools für universelle Windows-Apps“ aktivieren.  
  
-   Anwendung mit systemeigener Aktivität (Android)  
  
     Erstellt eine vollständige C++ OpenGL-App in Form eines Android-Projekts mit systemeigener Aktivität.  
  
-   OpenGLES-Anwendung (Android, iOS)  
  
     Erstellt eine Projektmappe mit einem Satz von Projekten zum Erstellen einer Android-App mit systemeigener Aktivität und einer iOS-Apps. Diese Apps verwenden plattformspezifische Bibliotheken mit gemeinsamem C++ OpenGL ES-Code zum Zeichnen des gleichen sich drehenden Würfels in jeder App.  
  
-   Freigegebene Bibliothek (Android, iOS)  
  
     Erstellt eine Projektmappe mit Projekten zum Erstellen einer Datei für eine dynamische Bibliothek für Android (.so) und einer Datei für eine statische Bibliothek für iOS (.a) mithilfe von gemeinsamem C++-Code in einem freigegebenen Projekt.  
  
-   Basisanwendung (Android, Ant)  
  
     Erstellt ein „Hello World“-App-Projekt für Android, das nur Java-Quellcode und das Ant-Buildsystem verwendet.  
  
-   Basisanwendung (Android, Gradle)  
  
     Erstellt ein „Hello World“-App-Projekt für Android, das nur Java-Quellcode und das Gradle-Buildsystem verwendet.  
  
-   Basisbibliothek (Android, Ant)  
  
     Erstellt ein „Hello World“-Bibliotheksprojekt für Android, das nur Java-Quellcode und das Ant-Buildsystem verwendet.  
  
-   Basisbibliothek (Android, Gradle)  
  
     Erstellt ein „Hello World“-Bibliotheksprojekt für Android, das nur Java-Quellcode und das Gradle-Buildsystem verwendet.  
  
-   Dynamische freigegebene Bibliothek (Android)  
  
     Erstellt eine Datei für eine dynamische Bibliothek für Android (.so) mithilfe von C++-Code.  
  
-   OpenGLES 2-Anwendung (iOS)  
  
     Erstellt eine Projektmappe mit Projekten zum Erstellen einer OpenGL ES 2 iOS-App. Die App verwendet zum Zeichnen eines sich drehenden Würfels in einer iOS-App eine Bibliothek mit C++ OpenGL ES-Code. Diese App ist ein guter Ausgangspunkt für den Import von C++-Bibliotheken in die iOS-App.  
  
-   Statische Bibliothek (Android)  
  
     Erstellt ein Projekt zum Erstellen einer statischen Bibliothek für Android. Sie können nur eine dynamische Bibliothek in einer Android-App verknüpfen, aber Sie können eine beliebige Anzahl von statischen Bibliotheken verknüpfen.  
  
-   Statische Bibliothek (iOS)  
  
     Erstellt ein Projekt zum Erstellen einer statischen Bibliothek für iOS.  
  
-   Makefile-Projekt (Android)  
  
     Erstellt einen Projektwrapper für Android Makefile-Projekte.  
  
## <a name="try-out-sample-code"></a>Testen des Beispielcodes  
 Laden Sie die Beispiele herunter, die zeigen, wie Sie freigegebene Codebibliotheken, die Sie in Windows-, Android- und iOS-Apps verwenden können, und vollständige Apps mit systemeigener Aktivität für Android erstellen können. Informationen zu den ersten Schritten finden Sie unter [Cross-Platform Mobile Development Examples (Beispiele für die plattformübergreifende Mobile-Entwicklung)](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
1.  [Install Visual C++ for Cross-Platform Mobile Development (Installieren von Visual C++ für die plattformübergreifende Mobile-Entwicklung)](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Install and Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Erstellen einer Android Native Activity-App](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Build an OpenGL ES Application on Android and iOS (Erstellen einer OpenGL ES-Anwendung für Android und iOS)](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Cross-Platform Mobile Development Examples (Beispiele für die plattformübergreifende Mobile-Entwicklung)](../cross-platform/cross-platform-mobile-development-examples.md)
