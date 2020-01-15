---
title: Installieren der plattformübergreifenden mobilen Entwicklung mit C++ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: c3ea8c91c54586cf54b82566a4803b464e01750c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916482"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Installieren der plattformübergreifenden mobile Entwicklung mit C++

Sie können C++ in Visual Studio verwenden, um Windows-Desktop-Apps, Apps der Universellen Windows-Plattform (UWP), Linux-Apps und jetzt auch Apps für Android und iOS zu erstellen. Die Workload **Mobile-Entwicklung mit C++** ist eine Reihe von Komponenten, die in Visual Studio installiert werden kann und plattformübergreifende Visual Studio-Vorlagen für iOS, Android und UWP enthält. Sie installiert die plattformübergreifenden Tools und SDKs für den Schnelleinstieg, ohne dass Sie diese suchen, herunterladen und selbst konfigurieren müssen. Mit diesen Tools in Visual Studio können Sie mühelos plattformübergreifende Projekte erstellen, bearbeiten, debuggen und testen. In diesem Artikel wird beschrieben, wie Sie die Tools und Drittanbietersoftware installieren, die zum Entwickeln plattformübergreifender Apps in C++ mit Visual Studio benötigt werden. Einen Überblick finden Sie unter [Visual C++ – Plattformübergreifende Mobile-Entwicklung](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/).

## <a name="requirements"></a>Anforderungen

::: moniker range="vs-2017"

- Die Anforderungen für die Installation finden Sie unter [Systemanforderungen der Visual Studio-Produktfamilie](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Wenn Sie Windows 7 oder Windows Server 2008 R2 verwenden, können Sie Code für Windows-Desktopanwendungen, Android-Apps mit nativer Aktivität und -Bibliotheken sowie Apps und Codebibliotheken für iOS, jedoch keine Windows Store- oder UWP-Apps entwickeln.

::: moniker-end
::: moniker range=">=vs-2019"

- Die Anforderungen für die Installation finden Sie unter [Systemanforderungen der Visual Studio-Produktfamilie](/visualstudio/releases/2019/system-requirements).

   > [!IMPORTANT]
   > Wenn Sie Windows 7 oder Windows Server 2008 R2 verwenden, können Sie Code für Windows-Desktopanwendungen, Android Native Activity-Apps und -Bibliotheken sowie Apps und Codebibliotheken für iOS, jedoch keine Windows Phone- oder UWP-Apps entwickeln.

::: moniker-end

Zum Erstellen von Anwendungen für bestimmte Plattformen bestehen einige zusätzliche Anforderungen:

- Die x86-Android-Emulatoren im Android SDK funktionieren am besten auf Computern, die Hardwarebeschleunigung wie beispielsweise Intel Hardware Accelerated Execution Manager (HAXM) unterstützen. Weitere Informationen finden Sie unter [Hardwarebeschleunigung für verbesserte Leistung des Emulators (Hyper-V und HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- Zum Entwickeln von Code für iOS sind eine Apple-ID, ein iOS-Entwicklerprogramm-Konto und ein Mac erforderlich, auf dem [Xcode](https://developer.apple.com/xcode/) Version 10.2 oder höher unter OS X Mavericks (Version 10.9) oder höher ausgeführt werden kann. Einen Link zu den Installationsschritten finden Sie unter [Install tools for iOS](#install-tools-for-ios) (Installieren der Tools für iOS).

- Windows Phone-Emulatoren benötigen einen Computer, auf dem Hyper-V ausgeführt werden kann. Die Hyper-V-Funktion unter Windows muss aktiviert sein, muss installiert sein, bevor Sie die Emulatoren installieren und ausführen können. Weitere Informationen finden Sie unter den [Systemanforderungen](system-requirements-for-the-visual-studio-emulator-for-android.md)des Emulators.

## <a name="get-the-tools"></a>Beschaffung der Tools

Mobile-Entwicklung mit C++ ist in den Editionen Visual Studio Community, Professional und Enterprise verfügbar. Sie können Visual Studio über die Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) herunterladen. Die Tools für die plattformübergreifende Mobile-Entwicklung sind ab Visual Studio 2015 verfügbar.

## <a name="install-the-tools"></a>Installieren der Tools

Der Visual Studio-Installer umfasst die Workload **Mobile Entwicklung mit C++** . Mit dieser Workload werden die C++-Sprachtools, -Vorlagen und -Komponenten installiert, die für die Entwicklung für Android und iOS in Visual Studio notwendig sind. Sie enthält die Toolsets GCC und Clang, die für das Erstellen und Debuggen von Android benötigt werden, das Android SDK und Komponenten zur Kommunikation mit einem Mac für die iOS-Entwicklung. Außerdem werden alle anderen Drittanbietertools und -Softwareentwicklungskits installiert, die zur Unterstützung der Entwicklung von iOS- und Android-Apps erforderlich sind. Bei den meisten dieser Drittanbietertools handelt es sich um Open Source-Software für die Android-Plattformunterstützung.

- Das Android Native Development Kit (NDK), Apache Ant und die C++-Entwicklungstools für Android werden benötigt, um C++-Code für die Android-Plattform zu erstellen.

- Der Google Android-Emulator und Intel Hardware Accelerated Execution Manager (HAXM) sind optionale, aber empfohlene Komponenten. (Die Intel HAXM-Treiber funktionieren nur mit Intel-Prozessoren und sind mit einigen VMs, einschließlich Hyper-V, nicht kompatibel.) Sie können direkt auf Ihrem Android-Gerät entwickeln und debuggen, es ist jedoch oft einfacher, für das Debuggen einen Emulator auf Ihrem Desktop zu verwenden.

- C++-Entwicklungstools für iOS sind erforderlich, um C++-Code für die iOS-Plattform zu entwickeln.

> [!NOTE]
> Wenn Sie Visual Studio 2015 verwenden, lesen Sie [Installieren von Visual C++ für plattformübergreifende Mobile-Entwicklung (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015).

### <a name="install-the-mobile-development-with-c-workload"></a>Installieren der Workload „Mobile-Entwicklung mit C++“

1. Führen Sie den **Visual Studio-Installer** über das **Startmenü** aus.

1. Wenn Sie Visual Studio bereits installiert haben, klicken Sie auf die Schaltfläche **Bearbeiten**, um die installierte Version von Visual Studio auszuwählen, die Sie ändern möchten. Wählen Sie andernfalls **Installieren** aus, um Visual Studio zu installieren.

1. Wählen Sie die Registerkarte **Workloads** aus, scrollen Sie nach unten, und wählen Sie im Visual Studio-Installer die Workload **Mobile-Entwicklung mit C++** aus. Wenn diese Workload ausgewählt ist, werden gleichzeitig andere erforderliche Komponenten für die C++-Entwicklung ausgewählt. Sie können auch andere Workloads und einzelne Komponenten auswählen, die zur gleichen Zeit installiert werden. Um plattformübergreifenden Code zu erstellen, der auf UWP ausgerichtet ist, wählen Sie die Workload **Entwicklung für die Universelle Windows-Plattform** aus.

1. Erweitern Sie im Bereich **Details zur Installation** **Mobile-Entwicklung mit C++** . Im Abschnitt **Optional** können Sie zusätzliche Versionen des NDK, des Google Android-Emulators, des Hardware Accelerated Execution Managers und des IncrediBuild-Buildbeschleunigungstools auswählen.

1. Standardmäßig enthält die Workload eine oder mehrere Android SDK-Setupkomponenten. Es sind zusätzliche Versionen von Android SDK verfügbar. Um eine der Versionen zu Ihrer Installation hinzuzufügen, wählen Sie die Registerkarte **Einzelne Komponenten** aus, scrollen Sie zum Bereich **SDKs, Bibliotheken und Frameworks** herunter, und treffen Sie eine Auswahl.

1. Klicken Sie auf die Schaltfläche **Ändern** oder **Installieren**, um die Workload **Mobile-Entwicklung mit C++** und die ausgewählten anderen Workloads und optionalen Komponenten zu installieren.

   Wenn die Installation abgeschlossen ist, schließen Sie den Installer und starten Sie Ihren Computer neu. Einige Setupaktionen für die Komponenten von Drittanbietern sind erst nach dem Neustart Ihres Computers aktiv.

   > [!IMPORTANT]
   > Der Neustart ist erforderlich, um sicherzustellen, dass alles korrekt installiert ist.

1. Öffnen Sie Visual Studio.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Sie können Visual Studio verwenden, um iOS-Code im iOS-Simulator oder auf einem iOS-Gerät zu bearbeiten, zu debuggen und bereitzustellen. Aufgrund von Lizenzierungseinschränkungen muss der Code jedoch remote auf einem Mac erstellt werden. Zum Erstellen und Ausführen von iOS-Apps mithilfe von Visual Studio müssen Sie den Remote-Agent auf Ihrem Mac einrichten und konfigurieren. Detaillierte Informationen zur Installation, zu den Voraussetzungen und den Konfigurationsoptionen finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Wenn Sie keinen Code für iOS erstellen, können Sie diesen Schritt überspringen.

## <a name="install-or-update-dependencies-manually"></a>Manuelles Installieren oder Aktualisieren von Abhängigkeiten

Wenn Sie bei der Installation der Workload **Mobile-Entwicklung mit C++** (oder „Visual C++ Mobile Development“ in Visual Studio 2015) keine Drittanbieterabhängigkeit mit dem Visual Studio-Installer installieren, können Sie diese später mithilfe der Schritte in [Install the tools](#install-the-tools) (Installieren der Tools) installieren. Der Visual Studio-Installer wird regelmäßig aktualisiert, um die neuesten Komponenten von Drittanbietern zu installieren. Sie können den Installer verwenden, um aktualisierte SDKs und NDKs zu installieren. Sie können die Abhängigkeiten auch unabhängig von Visual Studio installieren oder aktualisieren.

Sie können die SDK Manager-App im Android SDK-Verzeichnis erneut ausführen, um das SDK zu aktualisieren und die optionalen Tools und zusätzliche API-Ebenen zu installieren. Updates können möglicherweise nicht installiert werden, wenn Sie zum Ausführen der SDK-Manager-App nicht die Option **Als Administrator ausführen** verwenden. Wenn Sie Probleme beim Erstellen einer Android-App haben, überprüfen Sie den SDK-Manager auf Updates für Ihre installierten SDKs.

Um einige der Android-Emulatoren im Android SDK verwenden zu können, müssen Sie möglicherweise die Hardwarebeschleunigung einrichten. Weitere Informationen finden Sie unter [Hardwarebeschleunigung für verbesserte Leistung des Emulators (Hyper-V und HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

In den meisten Fällen kann Visual Studio die Konfigurationen für die von Ihnen installierte Drittanbietersoftware erkennen und verwaltet die Installationspfade in internen Umgebungsvariablen. Sie können die Standardpfade dieser plattformübergreifenden Entwicklungstools in der Visual Studio-IDE außer Kraft setzen.

#### <a name="to-set-the-paths-for-third-party-tools"></a>So legen Sie die Pfade für Drittanbietertools fest

1. Wählen Sie in der Menüleiste von Visual Studio **Tools** > **Optionen** aus.

1. Wählen Sie im Dialogfeld **Optionen** **Plattformübergreifend** > **C++**  > **Android** aus.

   ![Pfadoptionen für Android-Tools](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Um den von einem Tool verwendeten Pfad zu ändern, aktivieren Sie das Kontrollkästchen neben dem Pfad, und bearbeiten Sie den Ordnerpfad im Textfeld. Sie können auch über die Schaltfläche zum Durchsuchen ( **...** ) das Dialogfeld **Speicherort auswählen** öffnen, um den Ordner auszuwählen.

1. Klicken Sie auf **OK** , um die benutzerdefinierten Toolordnerpfade zu speichern.

## <a name="see-also"></a>Siehe auch

- [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ cross-platform mobile (Visual Studio C++ – Plattformübergreifende Mobile-Entwicklung)](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
