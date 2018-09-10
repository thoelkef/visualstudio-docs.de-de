---
title: Installieren von Visual C++ für die plattformübergreifende mobile Entwicklung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dffe82511e75889ea588cb23b1f19490f991ab0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251906"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Installieren der plattformübergreifenden Mobile-Entwicklung mit C++

Sie können C++ in Visual Studio verwenden, um Windows-Desktop-Apps, Apps der Universellen Windows-Plattform (UWP), Linux-Apps und jetzt auch Apps für Android und iOS zu erstellen. Die Workload **Mobile-Entwicklung mit C++** ist eine Reihe von Komponenten, die in Visual Studio installiert werden kann und plattformübergreifende Visual Studio-Vorlagen für iOS, Android und UWP enthält. Sie installiert die plattformübergreifenden Tools und SDKs für den Schnelleinstieg, ohne dass Sie diese suchen, herunterladen und selbst konfigurieren müssen. Mit diesen Tools in Visual Studio können Sie mühelos plattformübergreifende Projekte erstellen, bearbeiten, debuggen und testen. In diesem Thema wird beschrieben, wie Sie die Tools und Drittanbietersoftware installieren, die zum Entwickeln plattformübergreifender Apps in C++ mit Visual Studio benötigt werden. Einen Überblick finden Sie unter [Visual C++ – Plattformübergreifende Mobile-Entwicklung](https://go.microsoft.com/fwlink/p/?LinkId=536383).

## <a name="requirements"></a>Anforderungen

- Die Anforderungen für die Installation finden Sie unter [Systemanforderungen der Visual Studio-Produktfamilie](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Wenn Sie Windows 7 oder Windows Server 2008 R2 verwenden, können Sie Code für Windows-Desktopanwendungen, Android Native Activity-Apps und -Bibliotheken sowie Apps und Codebibliotheken für iOS, jedoch keine Windows Phone- oder UWP-Apps entwickeln.

Zum Erstellen von Anwendungen für bestimmte Plattformen bestehen einige zusätzliche Anforderungen:

- Windows Phone-Emulatoren und der Microsoft Visual Studio-Emulator für Android erfordern einen Computer, auf dem Hyper-V ausgeführt werden kann. Die Hyper-V-Funktion unter Windows muss aktiviert sein, muss installiert sein, bevor Sie die Emulatoren installieren und ausführen können. Weitere Informationen finden Sie unter den [Systemanforderungen](system-requirements-for-the-visual-studio-emulator-for-android.md)des Emulators.

- Die im Lieferumfang des Android-SDK enthaltenen  x86-Android-Emulatoren funktionieren am besten auf Computern, auf denen der Intel HAXM-Treiber ausgeführt werden kann. Dieser Treiber erfordert einen Intel x64-Prozessor mit VT-x und Execute Disable Bit-Unterstützung. Weitere Informationen finden Sie unter [Intel® Hardware Accelerated Execution Manager (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- Zum Erstellen von Code für iOS sind eine Apple-ID, ein iOS-Entwicklerprogramm-Konto und ein Mac erforderlich, auf dem [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) Version 6 oder höher unter OS X Mavericks (Version 10.9) oder höher ausgeführt werden kann. Einen Link zu den Installationsschritten finden Sie unter [Install tools for iOS](#install-tools-for-ios) (Installieren der Tools für iOS).

## <a name="get-the-tools"></a>Beschaffung der Tools

Mobile-Entwicklung mit C++ ist in den Editionen Visual Studio Community, Professional und Enterprise verfügbar. Sie können Visual Studio über die Seite [Visual Studio-Downloads](https://go.microsoft.com/fwlink/p/?linkid=517106) herunterladen. Die Tools für die plattformübergreifende Mobile-Entwicklung sind ab Visual Studio 2015 Update 2 oder höher verfügbar.

## <a name="install-the-tools"></a>Installieren der Tools

Der Visual Studio-Installer für Visual Studio 2017 enthält die Workload **Mobile-Entwicklung mit C++**, die die C++-Sprachtools, Vorlagen und Komponenten installiert, die für die Entwicklung für Android und iOS in Visual Studio notwendig sind. Sie installiert die erforderlichen GCC- und Clang-Toolsets für Android-Builds und -Debugging sowie Komponenten für die Kommunikation mit einem Mac für iOS-Entwicklung. Außerdem werden die Drittanbietertools und -Softwareentwicklungskits installiert, die zur Unterstützung der IOS- und Android-App-Entwicklung erforderlich sind. Bei den meisten dieser Drittanbietertools handelt es sich um Open Source-Software für die Android-Plattformunterstützung.

- Android Native Development Kit (NDK) wird benötigt, um C++-Code für die Android-Plattform zu erstellen.

- Android SDK, Apache Ant und Java SE Development Kit sind für den Android-Buildprozess erforderlich.

- Der Google Android-Emulator und Intel Hardware Accelerated Execution Manager sind optionale, aber empfohlene Komponenten. Sie können direkt auf Ihrem Android-Gerät entwickeln und debuggen, es ist jedoch oft einfacher, für das Debuggen einen Emulator auf Ihrem Desktop zu verwenden. Microsoft bietet auch einen Visual Studio-Emulator für Android an, der separat installiert werden kann.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>So installieren Sie die Workload „Mobile-Entwicklung mit C++“ in Visual Studio 2017

1. Führen Sie den **Visual Studio-Installer** über das **Startmenü** aus.

1. Wenn Sie Visual Studio bereits installiert haben, klicken Sie auf die Schaltfläche **Bearbeiten**, um die installierte Version von Visual Studio auszuwählen, die Sie ändern möchten. Wählen Sie andernfalls **Installieren** aus, um Visual Studio zu installieren.

1. Wählen Sie die Registerkarte **Workloads** aus, scrollen Sie nach unten, und wählen Sie im Visual Studio-Installer die Workload **Mobile-Entwicklung mit C++** aus. Wenn diese Workload ausgewählt ist, werden gleichzeitig andere erforderliche Komponenten für die C++-Entwicklung ausgewählt. Sie können auch andere Workloads und einzelne Komponenten auswählen, die zur gleichen Zeit installiert werden. Um plattformübergreifenden Code zu erstellen, der auf UWP ausgerichtet ist, wählen Sie die Workload **Entwicklung für die Universelle Windows-Plattform** aus.

1. Erweitern Sie im Bereich **Details zur Installation** **Mobile-Entwicklung mit C++**. Im Abschnitt **Optional** können Sie zusätzliche Versionen des NDK, des Google Android-Emulators, des Hardware Accelerated Execution Managers und des IncrediBuild-Buildbeschleunigungstools auswählen.

1. Standardmäßig enthält die Workload eine oder mehrere Android SDK-Setupkomponenten. Es sind zusätzliche Versionen von Android SDK verfügbar. Um eine der Versionen zu Ihrer Installation hinzuzufügen, wählen Sie die Registerkarte **Einzelne Komponenten** aus, scrollen Sie zum Bereich **SDKs, Bibliotheken und Frameworks** herunter, und treffen Sie eine Auswahl.

1. Klicken Sie auf die Schaltfläche **Ändern** oder **Installieren**, um die Workload **Mobile-Entwicklung mit C++** und die ausgewählten anderen Workloads und optionalen Komponenten zu installieren.

   Wenn die Installation abgeschlossen ist, schließen Sie den Installer und starten Sie Ihren Computer neu. Einige Setupaktionen für die Komponenten von Drittanbietern sind erst nach dem Neustart Ihres Computers aktiv.

   > [!IMPORTANT]
   > Der Neustart ist erforderlich, um sicherzustellen, dass alles korrekt installiert ist.

1. Öffnen Sie Visual Studio. Wenn Sie Visual Studio zum ersten Mal ausführen, kann es einige Zeit dauern, bis die Konfiguration abgeschlossen ist und Sie angemeldet werden. Wenn Visual Studio bereit ist, suchen Sie nach Updates, und installieren Sie diese.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>So installieren Sie die Komponente für Mobile-Entwicklung und Tools von Drittanbietern in Visual Studio 2015

Der Installer für Visual Studio 2015 enthält eine Option, Visual C++ für plattformübergreifende Mobile-Entwicklung zu installieren, wodurch die erforderlichen C++-Sprachtools, Vorlagen und Komponenten in Visual Studio 2015 installiert werden.

1. Führen Sie den Visual Studio 2015-Installer aus. Zum Installieren optionaler Komponenten wählen Sie **Benutzerdefiniert** als Installationstyp aus. Klicken Sie auf **Weiter** , um die zu installierenden optionalen Komponenten auszuwählen.

1. Erweitern Sie unter **Features auswählen** die Option **Plattformübergreifende Mobile-Entwicklung**, und aktivieren Sie **Mobile Visual C++-Entwicklung**.

   ![Wählen Sie Visual C&#43;&#43; Mobile Development aus](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   Standardmäßig wird bei der Auswahl von **Visual C++ Mobile Development** auch die Option **Programmiersprachen** festgelegt, um **Visual C++** zu installieren; ebenso wird die Option **Häufige Tools und Software Development Kits** zum Installieren der erforderlichen Komponenten von Drittanbietern festgelegt. Wenn benötigt, können sie weitere Komponenten auswählen. Der **Microsoft Visual Studio-Emulator** für Android wird ebenfalls standardmäßig ausgewählt. Die bereits installierten Komponenten werden in der Liste inaktiv angezeigt.

   Um universelle Windows-Apps zu erstellen und Code für diese Apps, Ihr Android-Gerät und Ihre iOS-Projekte freizugeben, erweitern Sie unter **Features auswählen** die Option **Windows- und Webentwicklung** und aktivieren Sie das Kontrollkästchen für **Universal Windows App-Entwicklungstools**. Wenn Sie nicht vorhaben, universelle Windows-Apps zu erstellen, können Sie diese Option überspringen.

   Klicken Sie auf **Weiter** , um fortzufahren.

1. Die Komponenten von Drittanbietern verfügen über eigene Lizenzbedingungen. Zum Anzeigen der Lizenzbedingungen klicken Sie auf den Link **Lizenzbedingungen** links neben der jeweiligen Komponente. Wählen Sie die Option **Installieren**, um die Komponenten hinzuzufügen und Visual Studio und Visual C++ für die plattformübergreifende mobile Entwicklung zu installieren.

1. Wenn die Installation abgeschlossen ist, schließen Sie den Installer und starten Sie Ihren Computer neu. Einige Setupaktionen für die Komponenten von Drittanbietern sind erst nach dem Neustart Ihres Computers aktiv.

   > [!IMPORTANT]
   > Der Neustart ist erforderlich, um sicherzustellen, dass alles korrekt installiert ist.

   Wenn der Microsoft Visual Studio-Emulator für die Android-Komponente nicht installiert werden konnte, ist auf Ihrem Computer möglicherweise Hyper-V nicht aktiviert. Verwenden Sie die Control Panel-Anwendung **Windows-Features aktivieren oder deaktivieren**, um Hyper-V zu aktivieren; führen Sie danach den Visual Studio-Installer erneut aus.

   > [!NOTE]
   > Wenn Ihr Computer oder die Version Ihres Windows-Betriebssystems Hyper-V nicht unterstützt, können Sie die Komponente „Microsoft Visual Studio-Emulator für Android“ verwenden. Die Home Edition der Windows-Betriebssysteme unterstützt Hyper-V nicht.

1. Öffnen Sie Visual Studio. Wenn Sie Visual Studio zum ersten Mal ausführen, kann es einige Zeit dauern, bis die Konfiguration abgeschlossen ist und Sie angemeldet werden. Wenn Visual Studio bereit ist, klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**&gt; **Updates**. Wenn Visual Studio-Updates für Visual C++ für die plattformübergreifende mobile Entwicklung oder für den Microsoft Visual Studio-Emulator für Android verfügbar sind, installieren Sie diese.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Sie können Visual C++ für plattformübergreifende Mobile-Entwicklung verwenden, um iOS-Code für den iOS-Simulator oder ein iOS-Gerät zu bearbeiten, zu debuggen und bereitzustellen. Aufgrund von Lizenzeinschränkungen muss der Code jedoch remote auf einem Mac erstellt werden. Zum Erstellen und Ausführen von iOS-Apps mithilfe von Visual Studio müssen Sie den Remote-Agent auf Ihrem Mac einrichten und konfigurieren. Detaillierte Informationen zur Installation, zu den Voraussetzungen und den Konfigurationsoptionen finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Wenn Sie keinen Code für iOS erstellen, können Sie diesen Schritt überspringen.

## <a name="install-or-update-dependencies-manually"></a>Manuelles Installieren oder Aktualisieren von Abhängigkeiten

Wenn Sie bei der Installation der Workload **Mobile-Entwicklung mit C++** (oder „Visual C++ Mobile Development“ in Visual Studio 2015) keine Drittanbieterabhängigkeit mit dem Visual Studio-Installer installieren, können Sie diese später mithilfe der Schritte in [Install the tools](#install-the-tools) (Installieren der Tools) installieren. Der Visual Studio-Installer wird regelmäßig aktualisiert, um die neuesten Komponenten von Drittanbietern zu installieren. Sie können den Installer verwenden, um aktualisierte SDKs und NDKs zu installieren. Sie können die Abhängigkeiten auch unabhängig von Visual Studio installieren oder aktualisieren.

> [!CAUTION]
> Sie können die Abhängigkeiten mit Ausnahme von Java in beliebiger Reihenfolge installieren. Sie müssen vor der Installation des Android SDK das JDK installieren und konfigurieren.

Lesen Sie die folgenden Informationen und verwenden Sie die folgenden Links, um Abhängigkeiten manuell zu installieren.

- [Java SE Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Der Installer legt die Java-Tools standardmäßig unter *C:\Programme (x86)\Java* ab.

- [Android-SDK](https://developer.android.com/sdk/index.html#command-tools)

   Aktualisieren Sie während der Installation die APIs wie empfohlen. Stellen Sie sicher, dass mindestens das SDK für Android 5.0 Lollipop (API Level 21) installiert ist. Der Installer legt das Android SDK standardmäßig unter *C:\Programme (x86)\Android\android-sdk* ab.

   Sie können die SDK Manager-App im Android SDK-Verzeichnis erneut ausführen, um das SDK zu aktualisieren und die optionalen Tools und zusätzliche API-Ebenen zu installieren. Updates können möglicherweise nicht installiert werden, wenn Sie zum Ausführen der SDK-Manager-App nicht die Option **Als Administrator ausführen** verwenden. Wenn Sie Probleme beim Erstellen einer Android-App haben, überprüfen Sie den SDK-Manager auf Updates für Ihre installierten SDKs.

   Wenn Sie einige der im Android-SDK enthaltenen Android-Emulatoren verwenden möchten, müssen Sie die optionalen Intel HAXM-Treiber installieren. Es ist möglicherweise erforderlich, die Hyper-V-Funktion von Windows zu entfernen, um die Intel HAXM-Treiber erfolgreich installieren zu können. Sie müssen die Hyper-V-Funktion wiederherstellen, um die Windows Phone-Emulatoren und den Microsoft Visual Studio-Emulator für Android nutzen zu können. Weitere Informationen finden Sie unter [Hardwarebeschleunigung für verbesserte Leistung des Android-Emulators](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   Standardmäßig legt der Installer das Android NDK unter *C:\ProgramData\Microsoft\AndroidNDK* ab. Sie können das Android-NDK erneut herunterladen und installieren, um die NDK-Installation zu aktualisieren.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Der Installer legt Apache Ant standardmäßig unter *C:\Programme (x86)\Microsoft Visual Studio 14.0\Apps* ab.

- [Microsoft Visual Studio-Emulator für Android](https://aka.ms/vscomemudownload)

   Microsoft Visual Studio-Emulator für Android ist ein optionaler Emulator, der für das Testen und Debuggen Ihres Code nützlich ist. Nach der Veröffentlichung des Visual Studio-Emulators für Android aktualisierte Google seinen Android-Emulator für die Verwendung der Hardwarebeschleunigung durch HAXM von Intel. Sie sollten wenn möglich den beschleunigten Emulator von Google verwenden, da dieser Zugriff auf die neuesten OS-Images für Android und Google Play-Dienste bietet.

In den meisten Fällen kann Visual Studio die Konfigurationen für die von Ihnen installierte Drittanbietersoftware erkennen und verwaltet die Installationspfade in internen Umgebungsvariablen. Sie können die Standardpfade dieser plattformübergreifenden Entwicklungstools in der Visual Studio-IDE außer Kraft setzen.

#### <a name="to-set-the-paths-for-third-party-tools"></a>So legen Sie die Pfade für Drittanbietertools fest

1. Wählen Sie in der Menüleiste von Visual Studio **Tools** > **Optionen** aus.

1. Wählen Sie im Dialogfeld **Optionen** **Plattformübergreifend** > **C++** > **Android** aus.

   ![Android-Tool-Pfadoptionen](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Um den von einem Tool verwendeten Pfad zu ändern, aktivieren Sie das Kontrollkästchen neben dem Pfad, und bearbeiten Sie den Ordnerpfad im Textfeld. Sie können auch über die Schaltfläche zum Durchsuchen (**...**) das Dialogfeld **Speicherort auswählen** öffnen, um den Ordner auszuwählen.

1. Klicken Sie auf **OK** , um die benutzerdefinierten Toolordnerpfade zu speichern.

## <a name="see-also"></a>Siehe auch

- [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ cross-platform mobile (Visual Studio C++ – Plattformübergreifende Mobile-Entwicklung)](https://go.microsoft.com/fwlink/p/?LinkId=536383)
