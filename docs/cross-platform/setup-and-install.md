---
title: Installieren von Xamarin für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 045b7745d8d9d171560546e893e89ea6cebe1b6f
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495894"
---
# <a name="setup-and-install"></a>Setup und Installation

Zum Erstellen von nativen iOS- Android- und Windows-Apps aus einer gemeinsamen C#/.NET-Codebasis mithilfe von Xamarin benötigen Sie die folgenden Hardware- und Softwarekomponenten:

-   Für das Arbeiten mit Windows- und Android-Apps: einen Windows-Entwicklungscomputer (keine VM) mit installiertem Visual Studio 2017 (einschließlich Xamarin-Entwicklungsfunktionen).

-   Für das Arbeiten mit iOS-Apps: einen Mac mit installiertem macOS Sierra 10.12 oder höher, Xcode und Visual Studio für Mac.

Für die Verwendung der Xamarin-Plattform sind keine separaten Lizenzen erforderlich.

Sie können die Windows- und Mac-Computer gleichzeitig einrichten, und während die Installationsprogramme ausgeführt werden, können Sie in [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) das erforderliche Hintergrundmaterial durchlesen und ansehen.

Wenn Sie nach dem Setup und der Installation Probleme mit der Verwendung der Xamarin-Plattform haben, posten Sie Ihre Frage auf [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" />

## <a name="pre-requisites"></a>Voraussetzungen

###  <a name="for-targeting-windows-and-android"></a>Für Windows und Android

Weitere Informationen zu den Installationsanforderungen für Visual Studio 2017 finden Sie unter [Systemanforderungen der Visual Studio-Produktfamilie 2017](/visualstudio/productinfo/vs2017-system-requirements-vs).

Installieren Sie Visual Studio 2017 auf einem physischen Windows-Computer (nicht auf einem virtuellen Computer), auf dem Windows 10 mit allen installierten Updates ausgeführt wird.

### <a name="for-targeting-ios"></a>Für iOS

Zur Nutzung von iOS-Emulatoren und -Geräten von Ihrem Windows-Computer benötigen Sie einen vernetzten Mac oder Mac mini mit macOS Sierra 10.12 oder höher und Xcode 8.3. Weitere Informationen zu den Anforderungen finden Sie unter [Einrichten und Installieren von Visual Studio für Mac](/visualstudio/mac/installation).

<a name="windows" />

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Windows-Setup (Visual Studio und Xamarin)

Wenn Visual Studio 2017 noch nicht installiert ist, gehen Sie wie folgt vor:

1.  [Laden Sie das Installationsprogramm für eine beliebige Edition von Visual Studio 2017 herunter, und führen Sie es aus](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community, Professional oder Enterprise). Visual Studio 2017 Community ist die kostenlose Edition. Die Professional- und Enterprise-Editionen sind 30 Tage lang als Testversion erhältlich, danach ist eine Lizenz erforderlich.

2.  Wenn das Dialogfeld **Installieren** angezeigt wird, aktivieren Sie die folgenden Kontrollkästchen:

    - **Mobil und Gaming > Mobile Entwicklung mit .NET**. Durch diese Option werden auch automatisch verschiedene Android-Tools und Software Development Kits ausgewählt.

        ![Aktivieren der Option „Mobile Entwicklung“ unter „Spiele und mobile Entwicklung“](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Plattformübergreifendes Xamarin-Setup 2")

    - (Optional) **Windows > Entwicklung für die universelle Windows-Plattform**.

Wenn Visual Studio 2017 bereits installiert ist, die Xamarin-Plattform jedoch noch nicht, gehen Sie wie folgt vor:

1. Führen Sie den **Visual Studio-Installer** über das **Startmenü** aus.

2.  Klicken Sie im Installer auf die Schaltfläche **Mehr** und dann auf **Ändern**:

    ![Auswählen der Option „Ändern“ bei Visual Studio-Installation](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Plattformübergreifendes Xamarin-Setup 1")

3.  Wenn das Dialogfeld **Installation** erscheint, wählen Sie **Mobil und Gaming > Mobile Entwicklung mit .NET** und (optional) **Windows > Entwicklung auf der universellen Windows-Plattform**. Die Option **Mobile Entwicklung mit .NET** sollte auch alle vorhandenen Xamarin-Installationen aktualisieren.

Während der Installation können Sie mit den Anweisungen zum Mac-Setup fortfahren oder [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) durcharbeiten.

5.  Starten Sie Visual Studio nach dem Abschluss der Installation, und melden Sie sich mit Ihrem Microsoft-Konto an, wenn Sie dazu aufgefordert werden. Es handelt sich um das gleiche Konto, das Sie für Windows verwenden.

6.  Verwenden Sie zum Testen von Android-Apps den [Android SDK-Emulator](/xamarin/android/get-started/installation/android-emulator/), sofern Sie keine physischen Android-Geräte haben.

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Mac-Setup (Apple ID, Xcode und Xamarin)

1.  Erstellen Sie eine kostenlose Apple-ID unter [https://appleid.apple.com](https://appleid.apple.com/), wenn Sie noch keine besitzen. Diese Apple-ID ist für die Installation von und die Anmeldung bei Xcode erforderlich.

2.  Laden Sie Xcode über [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) herunter, installieren Sie Xcode, und fügen Sie Ihre Apple-ID so hinzu, wie es unter [Adding Your Account to Xcode (Hinzufügen Ihres Kontos zu Xcode)](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) beschrieben wird.

3.  Laden Sie Visual Studio für Mac herunter, und führen Sie eine Installation durch, indem Sie den Anweisungen unter [Einrichten und Installieren von Visual Studio für Mac](/visualstudio/mac/installation) folgen.

4.  Sobald Sie die Installation von Xamarin auf dem Windows- und dem Mac-Computer abgeschlossen haben, folgen Sie den Anweisungen unter [Herstellen einer Verbindung mit dem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/), sodass Sie mit iOS und dem Mac in Visual Studio auf dem Windows-Computer arbeiten können.

Beide Computer müssen sich im selben lokalen Netzwerk befinden.
