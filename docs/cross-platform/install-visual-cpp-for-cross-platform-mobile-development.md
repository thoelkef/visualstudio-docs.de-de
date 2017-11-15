---
title: "Installieren von Visual C++ für die plattformübergreifende mobile Entwicklung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b2d86a6025e2ec9c2ba92870939248cf2dffb5b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Installieren von Visual C++ für die plattformübergreifende mobile Entwicklung
[Visual C++ für die plattformübergreifende mobile Entwicklung](http://go.microsoft.com/fwlink/p/?LinkId=536383) ist eine installierbare Komponente in Visual Studio 2015. Sie enthält plattformübergreifende Visual Studio-Vorlagen und installiert die plattformübergreifenden Tools und SDKs für den Schnelleinstieg, ohne dass Sie diese suchen, herunterladen und selbst konfigurieren müssen. Mit diesen Tools in Visual Studio können Sie mühelos plattformübergreifende Projekte erstellen, bearbeiten, debuggen und testen. In diesem Thema wird beschrieben, wie Sie die Tools und Drittanbietersoftware installieren, die zum Entwickeln plattformübergreifender Apps mit Visual Studio benötigt werden. Einen Überblick über die Komponente finden Sie unter [Visual Studio C++ – Plattformübergreifende mobile Entwicklung](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Anforderungen](#Requirements)   
 [Beschaffung der Tools](#GetTheTools)   
 [Installieren der Tools](#InstallTheTools)   
 [Install tools for iOS](#InstallForiOS)   
 [Manuelles Installieren oder Aktualisieren von Abhängigkeiten](#ThirdParty)  
  
##  <a name="Requirements"></a> Anforderungen  
  
-   Die Anforderungen für die Installation finden Sie unter [Visual Studio 2015 – Systemanforderungen](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
    > [!IMPORTANT]
    >  Wenn Sie Windows 7 oder Windows Server 2008 R2 verwenden, können Sie Code für klassische Windows-Anwendungen, Android Native Activity-Apps und -Bibliotheken sowie Apps und Codebibliotheken für iOS, jedoch keine Windows Store- oder universellen Windows-Apps entwickeln.  
  
 Zum Erstellen von Anwendungen für bestimmte Plattformen bestehen einige zusätzliche Anforderungen:  
  
-   Windows Phone-Emulatoren und der Microsoft Visual Studio-Emulator für Android erfordern einen Computer, auf dem Hyper-V ausgeführt werden kann. Die Hyper-V-Funktion unter Windows muss aktiviert sein, muss installiert sein, bevor Sie die Emulatoren installieren und ausführen können. Weitere Informationen finden Sie unter den [Systemanforderungen](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf)des Emulators.  
  
-   Die im Lieferumfang des Android-SDK enthaltenen  x86-Android-Emulatoren funktionieren am besten auf Computern, auf denen der Intel HAXM-Treiber ausgeführt werden kann. Dieser Treiber erfordert einen Intel x64-Prozessor mit VT-x und Execute Disable Bit-Unterstützung. Weitere Informationen finden Sie unter [Installationsanweisungen für Intel® Hardware Accelerated Execution Manager – Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
-   Zum Erstellen von Code für iOS sind eine Apple-ID, ein iOS-Entwicklerprogrammkonto und ein Mac erforderlich, auf dem [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) oder höher unter OS X Mavericks oder höher ausgeführt werden kann. Einfache Installationsschritte finden Sie unter [Install tools for iOS](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Beschaffung der Tools  
 Visual C++ für die plattformübergreifende mobile Entwicklung ist eine installierbare Komponente, die in Visual Studio Community, Professional und Enterprise enthalten ist. Wechseln Sie zur Seite [Visual Studio 2015 Downloads](http://go.microsoft.com/fwlink/p/?linkid=517106), und laden Sie Visual Studio 2015 mit Update 2 oder höher herunter.  
  
##  <a name="InstallTheTools"></a> Installieren der Tools  
 Das Installationsprogramm für Visual Studio 2015 umfasst eine Option zum Installieren von Visual C++ für die plattformübergreifende mobile Entwicklung. Damit werden die erforderlichen C++-Sprachtools, Vorlagen und Komponenten für Visual Studio, die erforderlichen GCC- und Clang-Toolsets für Android-Builds und -Debugging sowie Komponenten für die Kommunikation mit einem Mac für iOS-Entwicklung installiert. Außerdem werden die Drittanbietertools und -Softwareentwicklungskits installiert, die zur Unterstützung der IOS- und Android-App-Entwicklung erforderlich sind. Bei den meisten dieser Drittanbietertools handelt es sich um Open Source-Software für die Android-Plattformunterstützung.  
  
-   Android Native Development Kit (NDK) wird benötigt, um C++-Code für die Android-Plattform zu erstellen.  
  
-   Android SDK, Apache Ant und Java SE Development Kit sind für den Android-Buildprozess erforderlich.  
  
-   Microsoft Visual Studio-Emulator für Android ist ein optionaler High-Performance-Emulator, der für das Testen und Debuggen Ihres Codes nützlich ist.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>So installieren Sie Visual C++ für die plattformübergreifende Mobilgeräteentwicklung und die Drittanbietertools  
  
1.  Führen Sie das Visual Studio 2015-Installationsprogramm aus, das Sie über den Link in [Beschaffung der Tools](#GetTheTools)heruntergeladen haben. Zum Installieren optionaler Komponenten wählen Sie **Benutzerdefiniert** als Installationstyp aus. Klicken Sie auf **Weiter** , um die zu installierenden optionalen Komponenten auszuwählen.  
  
2.  Erweitern Sie unter „Features auswählen“ die Option **Plattformübergreifende, mobile Entwicklung** , und aktivieren Sie **Visual C++ Mobile Development**.  
  
     ![Wählen Sie Visual C&#43;&#43; Mobile Development aus](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Standardmäßig wird bei der Auswahl von **Visual C++ Mobile Development** auch die Option **Programmiersprachen** festgelegt, um **Visual C++** zu installieren; ebenso wird die Option **Häufige Tools und Software Development Kits** zum Installieren der erforderlichen Komponenten von Drittanbietern festgelegt. Wenn benötigt, können sie weitere Komponenten auswählen. Der **Microsoft Visual Studio-Emulator** für Android wird ebenfalls standardmäßig ausgewählt. Die bereits installierten Komponenten werden in der Liste inaktiv angezeigt.  
  
     Um universelle Windows-Apps zu erstellen und Code für diese Apps, Ihr Android-Gerät und Ihre iOS-Projekte freizugeben, erweitern Sie unter **Features auswählen** die Option **Windows- und Webentwicklung** und aktivieren Sie das Kontrollkästchen für **Universal Windows App-Entwicklungstools**. Wenn Sie nicht vorhaben, universelle Windows-Apps zu erstellen, können Sie diese Option überspringen.  
  
     Klicken Sie auf **Weiter** , um fortzufahren.  
  
3.  Die Komponenten von Drittanbietern verfügen über eigene Lizenzbedingungen. Zum Anzeigen der Lizenzbedingungen klicken Sie auf den Link **Lizenzbedingungen** links neben der jeweiligen Komponente. Wählen Sie die Option **Installieren**, um die Komponenten hinzuzufügen und Visual Studio und Visual C++ für die plattformübergreifende mobile Entwicklung zu installieren.  
  
4.  Wenn die Installation abgeschlossen ist, schließen Sie den Installer und starten Sie Ihren Computer neu. Einige Setupaktionen für die Komponenten von Drittanbietern sind erst nach dem Neustart Ihres Computers aktiv.  
  
    > [!IMPORTANT]
    >  Der Neustart ist erforderlich, um sicherzustellen, dass alles korrekt installiert ist.  
  
     Wenn der Microsoft Visual Studio-Emulator für die Android-Komponente nicht installiert werden konnte, ist auf Ihrem Computer möglicherweise Hyper-V nicht aktiviert. Verwenden Sie die Control Panel-Anwendung **Windows-Features aktivieren oder deaktivieren**, um Hyper-V zu aktivieren; führen Sie danach den Visual Studio-Installer erneut aus.  
  
    > [!NOTE]
    >  Wenn Ihr Computer oder die Version Ihres Windows-Betriebssystems Hyper-V nicht unterstützt, können Sie die Komponente „Microsoft Visual Studio-Emulator für Android“ verwenden. Die Home Edition der Windows-Betriebssysteme unterstützt Hyper-V nicht.  
  
5.  Öffnen Sie Visual Studio. Wenn Sie Visual Studio zum ersten Mal ausführen, kann es einige Zeit dauern, bis die Konfiguration abgeschlossen ist und Sie angemeldet werden. Wenn Visual Studio bereit ist, klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**&gt; **Updates**. Wenn Visual Studio-Updates für Visual C++ für die plattformübergreifende mobile Entwicklung oder für den Microsoft Visual Studio-Emulator für Android verfügbar sind, installieren Sie diese.  
  
##  <a name="InstallForiOS"></a> Install tools for iOS  
 Sie können Visual C++ für die plattformübergreifende mobile Entwicklung verwenden, um iOS-Code für den iOS-Simulator oder ein iOS-Gerät zu bearbeiten, zu debuggen und bereitzustellen. Aufgrund von Lizenzeinschränkungen muss der Code jedoch remote auf einem Mac erstellt werden. Zum Erstellen und Ausführen von iOS-Apps mithilfe von Visual Studio müssen Sie den Remote-Agent auf Ihrem Mac einrichten und konfigurieren. Detaillierte Informationen zur Installation, Voraussetzungen und Konfigurationsoptionen finden Sie unter [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Wenn Sie keinen Code für iOS erstellen, können Sie diesen Schritt überspringen.  
  
##  <a name="ThirdParty"></a> Manuelles Installieren oder Aktualisieren von Abhängigkeiten  
 Wenn Sie bei der Installation der Option „Visual C++ Mobile Development“ keine Drittanbieterabhängigkeit mit dem Visual Studio-Installer installieren, können Sie diese später mithilfe der Schritte in [Install the tools](#InstallTheTools)installieren. Sie können die Abhängigkeiten auch unabhängig von Visual Studio installieren oder aktualisieren.  
  
> [!CAUTION]
>  Sie können die Abhängigkeiten mit Ausnahme von Java in beliebiger Reihenfolge installieren. Sie müssen vor der Installation des Android SDK das JDK installieren und konfigurieren.  
  
 Lesen Sie die folgenden Informationen und verwenden Sie die folgenden Links, um Abhängigkeiten manuell zu installieren.  
  
-   [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
     Der Installer legt die Java-Tools standardmäßig unter "C:\Programme (x86)\Java" ab.  
  
-   [Android-SDK](https://developer.android.com/sdk/index.html#Other)  
  
     Aktualisieren Sie während der Installation die APIs wie empfohlen. Stellen Sie sicher, dass mindestens das SDK für Android 5.0 Lollipop (API Level 21) installiert ist. Der Installer legt das Android-SDK standardmäßig unter "C:\Programme (x86)\Android\android-sdk" ab.  
  
     Sie können die SDK Manager-App im Android SDK-Verzeichnis erneut ausführen, um das SDK zu aktualisieren und die optionalen Tools und zusätzliche API-Ebenen zu installieren. Updates können möglicherweise nicht installiert werden, wenn Sie zum Ausführen der SDK-Manager-App nicht die Option **Als Administrator ausführen** verwenden. Wenn Sie Probleme beim Erstellen einer Android-App haben, überprüfen Sie den SDK-Manager auf Updates für Ihre installierten SDKs.  
  
     Wenn Sie einige der im Android-SDK enthaltenen Android-Emulatoren verwenden möchten, müssen Sie die optionalen Intel HAXM-Treiber installieren. Es ist möglicherweise erforderlich, die Hyper-V-Funktion von Windows zu entfernen, um die Intel HAXM-Treiber erfolgreich installieren zu können. Sie müssen die Hyper-V-Funktion wiederherstellen, um die Windows Phone-Emulatoren und den Microsoft Visual Studio-Emulator für Android nutzen zu können.  
  
-   [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
     Standardmäßig legt der Installer das Android NDK in "C:\ProgramData\Microsoft\AndroidNDK" ab. Sie können das Android-NDK erneut herunterladen und installieren, um die NDK-Installation zu aktualisieren.  
  
-   [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
     Der Installer legt Apache Ant standardmäßig in „C:\Programme (x86)\Microsoft Visual Studio 14.0\Apps“ ab.  
  
-   [Microsoft Visual Studio-Emulator für Android](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
     Sie können den Microsoft Visual Studio-Emulator für Android über den Visual Studio-Katalog installieren und aktualisieren.  
  
 In den meisten Fällen kann Visual Studio die Konfigurationen für die von Ihnen installierte Drittanbietersoftware erkennen und verwaltet die Installationspfade in internen Umgebungsvariablen. Sie können die Standardpfade dieser plattformübergreifenden Entwicklungstools in der Visual Studio-IDE außer Kraft setzen.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>So legen Sie die Pfade für Drittanbietertools fest  
  
1.  Wählen Sie in der Menüleiste von Visual Studio **Extras**&gt; **Optionen**aus.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** die Option **Plattformübergreifend**&gt; **C++**und wählen Sie **Android**aus.  
  
     ![Android-Tool-Pfadoptionen](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")  
  
3.  Um den von einem Tool verwendeten Pfad zu ändern, aktivieren Sie das Kontrollkästchen neben dem Pfad, und bearbeiten Sie den Ordnerpfad im Textfeld. Sie können auch über die Schaltfläche zum Durchsuchen (**...**) das Dialogfeld **Speicherort auswählen** öffnen, um den Ordner auszuwählen.  
  
4.  Klicken Sie auf **OK** , um die benutzerdefinierten Toolordnerpfade zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual Studio C++ – Plattformübergreifende mobile Entwicklung](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)