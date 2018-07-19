---
title: Überprüfen Ihrer Xamarin-Umgebung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 7d53a668014ba8f08b0715a0f0a02c351756435e
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924472"
---
# <a name="verify-your-xamarin-environment"></a>Überprüfen Ihrer Xamarin-Umgebung

Nachdem die Installationsprogramme abgeschlossen wurden (siehe dazu [Setup and install](../cross-platform/setup-and-install.md)) sollten Sie ein paar Minuten investieren, um zu überprüfen, ob alles für den Einstieg in die Xamarin-Entwicklung bereit ist.

 Nach Abschluss dieser Überprüfung können Sie eine oder beide der folgenden exemplarischen Vorgehensweisen verwenden:

-   [Erlernen von Grundlagen der App-Erstellung mit Xamarin.Forms in Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md), um eine Xamarin.Forms-Anwendung zu erstellen.

-   [Erstellen von Apps mit nativer Benutzeroberfläche über Xamarin in Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md), um die nativen Benutzeroberflächen jeder Plattform zu verwenden, wobei Sie jedoch Code in einer .NET Standard-Bibliothek freigeben.

## <a name="all-platforms"></a>Alle Plattformen

Wählen Sie in Visual Studio zunächst **Extras > Erweiterungen und Updates**, und prüfen Sie, ob eine der Xamarin-Komponenten Updates erfordert.

Dann erstellen Sie in Visual Studio eine neue Xamarin.Forms-Projektmappe, indem Sie **Datei > Neues Projekt** auswählen. Erweitern Sie im Dialogfeld **Visual C# > Plattformübergreifend**, wählen Sie die Option **Mobile App (Xamarin.Forms)** aus, und klicken Sie auf „OK“. Wählen Sie im dann angezeigten Dialogfeld **Leere App** aus. Wählen Sie unter **Codefreigabestrategie** die Option **.NET Standard** aus. Klicken Sie auf OK.

Dadurch wird eine Projektmappe mit vier Projekten erstellt: ein freigegebenes Projekt für die .NET Standard 2.0-Bibliothek sowie Anwendungsprojekte für Android, iOS und die universelle Windows-Plattform (UWP):

![Ergebnisse der Erstellung eines neuen Projekts aus der Xamarin.Forms-Vorlage „Leere App“](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")

## <a name="android"></a>Android

1. Überprüfen Sie, ob Sie die aktuellen Android SDK Tools installiert haben. Wechseln Sie hierzu zu **Tools > Android > Android SDK-Manager**. Installieren Sie die neueste Version der Android SDK Tools, der Android SDK Platform-Tools und der Android SDK Build-Tools. Es ist nicht erforderlich, immer die neueste Android-API-Ebene zu installieren. Welche API erforderlich ist, hängt von der Plattformebene ab, die Sie als Ziel auswählen. Im Allgemeinen wird bei der Installation der Xamarin-Plattform die erforderliche Android-Plattformebene installiert.

2.  Überprüfen Sie das Erstellen und Debuggen auf einem Gerät oder im Emulator:

    -   Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das Android-Projekt, und wählen Sie **Als Startprojekt festlegen**aus.

    -   In der Symbolleiste sollte ein Dropdownmenü mit einer Liste der verfügbaren Android-Geräte und -Emulatoren angezeigt werden.

    Android-Geräte müssen für das USB-Debugging in den Entwickleroptionen auf der Seite mit den Geräteeinstellungen aktiviert sein. Das Gerät wird dann mit dem Computer über ein USB-Kabel verbunden.

    Emulatoren werden ebenfalls aufgeführt. Wählen Sie ein Gerät oder einen Visual Studio-Emulator aus:

  ![Auswählen des Visual Studio-Emulators für Android als Debugziel](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")

  Weitere Informationen finden Sie unter [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (Einführen der Emulatoren von Visual Studio für Android) (Visual Studio ALM-Blog). Wenn bei der Inbetriebnahme des Emulators Probleme auftreten, finden Sie Hilfe unter [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Sie können auch neue Geräteprofile für den Emulator erstellen, indem Sie **Extras > Android > Android-Emulator-Manager** auswählen.

3. Drücken Sie F5, um das Programm zu kompilieren und auf dem Android-Gerät oder -Emulator bereitzustellen.

## <a name="windows"></a>Windows

1.  Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das universelle Windows-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.

2.  Wählen Sie im Dropdownmenü **Projektmappenplattformen** entweder **x86** oder **x64**. Wählen Sie **Lokaler Computer**.

3.  Drücken Sie F5, um das Programm auf dem Desktop bereitzustellen.

## <a name="ios"></a>iOS

1.  Überprüfen Sie, ob der Mac im Netzwerk verfügbar und mit Visual Studio gepaart ist, wie unter [Herstellen einer Verbindung mit dem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) beschrieben.

2.  Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das iOS-Projekt, und wählen Sie **Als Startprojekt festlegen**aus.

3.  Wählen Sie in der Erstellen-Dropdownliste von Visual Studio das Ziel **iPhoneSimulator** (siehe unten) oder das Ziel **iPhone** aus, wenn Sie ein mit dem Mac verbundenes Gerät haben.

 ![Auswählen von iPhoneSimulator als Buildziel](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")

 Wenn keine Simulatoren aufgelistet sind, starten Sie Xcode auf dem Mac, wählen Sie **Xcode > Einstellungen** aus, und klicken Sie auf **Laden**. Unter der Überschrift **Komponenten** sollten die für den Download verfügbaren Simulatorversionen zu sehen sein. Weitere Debuganweisungen finden Sie auf der Seite [Debuggen für iOS](/xamarin/ios/deploy-test/debugging-in-xamarin-ios/?tabs=vsmac#Debugging_on_the_Simulator).

4.  Wählen Sie ein Emulatorgeräteziel aus dem Dropdownmenü von Visual Studio aus:

 ![Auswählen eines iPhones als Debugziel](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")

5. Starten Sie den Debugger, indem Sie F5 drücken. Dadurch wird der Simulator auf dem Mac gestartet, auf dem Sie mit der App interagieren, während das Debuggen in Visual Studio erfolgt. Wenn Sie mit einem physischen iPhone oder iPad arbeiten, das mit dem Mac verbunden ist, wird es in der Liste angezeigt, und Sie können es stattdessen auswählen. Wenn keine Geräte oder Simulatoren aufgelistet sind, überprüfen Sie die Verbindung zum Mac. Lesen Sie den in Schritt 1 verknüpften Artikel, oder wechseln Sie zu **Extras > iOS > Mit Mac koppeln**.

6.  Gibt es Probleme beim Herstellen einer Verbindung mit dem Mac, lesen Sie [Problembehandlung bei der Verbindung](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/).

7.  Wird die Fehlermeldung „No installed provisioning profiles match the installed iOS signing keys“ (Zu den installierten iOS-Anmeldeschlüsseln passt keines der installierten Bereitstellungsprofile) angezeigt, probieren Sie einen der folgenden Ansätze:

  - Vergewissern Sie sich, dass Ihr Apple ID-Konto in Xcode auf dem Mac hinzugefügt wurde, wie dies unter [Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) beschrieben ist.  Nachdem Ihr Konto hinzugefügt wurde, müssen Sie sowohl Visual Studio als auch Xcode neu starten.

  - Stellen Sie sicher, dass in den iOS-Projekteigenschaften auf der Registerkarte „iOS-Bundle-Signierung“ das Feld „Benutzerdefinierte Berechtigungen“ für die aktive Debugkonfiguration leer ist.  Hinweis: Sie sollten nur dann versuchen, diese Einstellung zu löschen, wenn die oben genannte Fehlermeldung angezeigt wurde.

  ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")
