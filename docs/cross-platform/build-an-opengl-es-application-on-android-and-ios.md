---
title: Entwickeln einer OpenGL ES-Anwendung für Android und iOS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/09/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: a15902278e9a73488b315729a2db6e8fb5d53935
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588924"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Erstellen einer OpenGL ES-Anwendung für Android und iOS

Sie können Visual Studio-Projekte und -Projektmappen für iOS-Apps und Android-Apps erstellen, die gemeinsamen Code nutzen. Dieser Artikel führt Sie durch eine Projektmappenvorlage, die eine einfache iOS-App und eine Android Native Activity-App erstellt. Die Apps verwenden gemeinsamen C++-Code, der OpenGL ES verwendet, um denselben animierten rotierenden Cube auf jeder Plattform anzuzeigen. OpenGL ES (OpenGL for Embedded Systems oder GLES) ist eine 2D- und 3D-Grafik-API, die auf zahlreichen mobilen Geräten unterstützt wird.

## <a name="requirements"></a>Requirements (Anforderungen)

Bevor Sie eine OpenGL ES-App für iOS und Android erstellen, vergewissern Sie sich, dass alle Systemanforderungen erfüllt sind. Installieren Sie die Workload „Mobile-Entwicklung mit C++“ im Visual Studio-Installer, sofern dies nicht bereits erfolgt ist. Zum Abrufen der OpenGL ES-Vorlagen und Entwickeln für iOS binden Sie die optionalen C++-Entwicklungstools für iOS ein. Zur Entwicklung für Android installieren Sie die Tools für die Entwicklung für Android mit C++ sowie die erforderlichen Drittanbietertools: das Android NDK, Apache Ant und der Google Android-Emulator. Für eine bessere Emulatorleistung auf Intel-Plattformen wird empfohlen, dass Sie auch den Hardware Accelerated Execution Manager (HAXM) von Intel installieren. Als Nächstes konfigurieren Sie Intel HAXM und den Android-Emulator für die Ausführung auf Ihrem System. Weitere Informationen und ausführliche Anweisungen finden Sie unter [Installieren der plattformübergreifenden mobilen Entwicklung mit C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).

Zum Entwickeln und Testen der iOS-App benötigen Sie einen Mac-Computer, der gemäß der Installationsanleitung eingerichtet wurde. Weitere Informationen zum Einrichten der iOS-Entwicklung finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="create-a-new-opengles-application-project"></a>Erstellen eines neuen OpenGLES-Anwendungsprojekts

In diesem Tutorial erstellen Sie zunächst ein neues OpenGL ES-Anwendungsprojekt, und dann erstellen Sie die Standard-App und führen sie im Android-Emulator aus. Als Nächstes erstellen Sie die App für iOS und führen sie auf einem iOS-Gerät aus.

::: moniker range="vs-2017"

1. Klicken Sie in Visual Studio auf **Datei**>**Neu**>**Projekt**.

1. Wählen Sie im Dialogfeld **Neues Projekt** unter **Vorlagen** die Option **Visual C++** >**Plattformübergreifend** und dann die Vorlage **OpenGLES-Anwendung (Android, iOS)** aus.

1. Geben Sie der App einen Namen wie *MyOpenGLESApp*, und klicken Sie dann auf **OK**.

   ![Erstellen eines neuen OpenGLES-Anwendungsprojekts](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio erstellt die neue Projektmappe und öffnet den Projektmappen-Explorer.

   ![MyOpenGLESApp im Projektmappen-Explorer](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie in Visual Studio auf **Datei**>**Neu**>**Projekt**.

1. Wählen Sie im Dialogfeld **Neues Projekt erstellen** die Vorlage **OpenGLES-Anwendung (Android, iOS)** aus, und klicken Sie dann auf **Weiter**.

1. Geben Sie im Dialogfeld **Neues Projekt konfigurieren** einen Namen wie *MyOpenGLESApp* in **Projektname** ein, und klicken Sie dann auf **Erstellen**.

   Visual Studio erstellt die neue Projektmappe und öffnet den Projektmappen-Explorer.

   ![MyOpenGLESApp im Projektmappen-Explorer](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

Die neue OpenGL ES-Anwendungsprojektmappe umfasst drei Bibliotheksprojekte und zwei Anwendungsprojekte. Der Bibliotheksordner enthält ein Projekt mit freigegebenem Code und zwei plattformspezifischen Projekte, die auf den gemeinsam verwendeten Code verweisen:

- `MyOpenGLESApp.Android.NativeActivity` enthält die Verweise und den Verbindungscode, mit denen Ihre App als eine systemeigene Aktivität auf Android implementiert werden kann. Die Einstiegspunkte aus dem Verbindungscode sind in der Datei *main.cpp* implementiert, die den gemeinsamen Code in `MyOpenGLESApp.Shared` enthält. Vorkompilierte Header befinden sich in *pch.h*. Das Native Activity-App-Projekt wird in eine gemeinsam genutzte Bibliotheksdatei (*SO*) kompiliert, die durch das `MyOpenGLESApp.Android.Packaging`-Projekt ausgewählt wird.

- `MyOpenGLESApp.iOS.StaticLibrary` erstellt eine statische iOS-Bibliotheksdatei (*A*)-Datei mit dem freigegebenen Code in `MyOpenGLESApp.Shared`. Diese ist mit der vom `MyOpenGLESApp.iOS.Application`-Projekt erstellten App verknüpft.

- `MyOpenGLESApp.Shared` enthält den freigegebenen Code, der plattformübergreifend verwendet werden kann. Die App verwendet Präprozessormakros für die bedingte Kompilierung von plattformspezifischem Code. Der freigegebene Code wird durch den Projektverweis sowohl in `MyOpenGLESApp.Android.NativeActivity` als auch `MyOpenGLESApp.iOS.StaticLibrary` übernommen.

Die Projektmappe enthält zwei Projekte zum Erstellen der Apps für die Android- und iOS-Plattform:

- `MyOpenGLESApp.Android.Packaging` erstellt die *APK*-Datei für die Bereitstellung auf einem Android-Gerät oder -Emulator. Diese Datei enthält die Ressourcen sowie die Datei „AndroidManifest.xml“, in der Sie Manifesteigenschaften festlegen. Es enthält zudem die Datei *build.xml*, die den Ant-Buildprozess steuert. Es ist standardmäßig als Startprojekt festgelegt, sodass es bereitgestellt und direkt in Visual Studio ausgeführt werden kann.

- `MyOpenGLESApp.iOS.Application` enthält die Ressourcen und Objective-C-Verbindungscode zum Erstellen einer iOS-App, die mit dem Code der statischen C++-Bibliothek in `MyOpenGLESApp.iOS.StaticLibrary` verknüpft ist. Dieses Projekt erstellt ein Buildpaket, das von Visual Studio und dem Remote-Agent auf Ihren Mac übertragen wird. Beim Erstellen dieses Projekts sendet Visual Studio die Dateien und Befehle zum Erstellen und Bereitstellen der App auf dem Mac.

## <a name="build-and-run-the-android-app"></a>Erstellen und Ausführen der Android-App

Durch die von der Vorlage erstellte Projektmappe wird die Android-App als Standardprojekt festgelegt.  Sie können die App erstellen und ausführen, um die Installation und Einrichtung zu überprüfen. Führen Sie die App in einem ersten Test in einem der Geräteprofile aus, die vom Emulator für Android installiert werden. Wenn Sie Ihre App auf einem anderen Ziel testen möchten, können Sie den Zielemulator laden oder das Gerät mit Ihrem Computer verbinden.

### <a name="to-build-and-run-the-android-native-activity-app"></a>So erstellen und führen Sie die Android Native Activity-App aus

1. Wählen Sie **x86** aus der Dropdownliste **Projektmappenplattformen** aus (falls diese Plattform nicht bereits ausgewählt ist).

   ![Festlegen der Projektmappenplattform auf x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Wählen Sie "x86" aus, wenn Sie den Emulator als Ziel verwenden möchten. Um ein Gerät als Ziel zu verwenden, wählen Sie je nach Geräteprozessor die entsprechende Projektmappenplattform aus. Wenn die Liste **Projektmappenplattformen** nicht angezeigt wird, wählen Sie **Projektmappenplattformen** aus der Liste **Schaltflächen hinzufügen/entfernen** aus, und wählen Sie dann Ihre Plattform aus.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das `MyOpenGLESApp.Android.Packaging`-Projekt, und wählen Sie dann **Erstellen** aus.

   ![Erstellen eines Android-Paketprojekts](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   Das Ausgabefenster zeigt die Ausgabe des Buildprozesses für die freigegebene Android-Bibliothek und die Android-App an.

   ![Buildausgabe für Android-Objekte](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Wählen Sie eins der emulierten Android-Geräteprofile als Bereitstellungsziel aus.

   ![Auswählen des Bereitstellungsziels](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Wenn Sie andere Emulatoren installiert oder mit einem Android-Gerät verbunden haben, können Sie sie aus der Bereitstellungsziel-Dropdownliste auswählen. Damit die App ausgeführt werden kann, muss die integrierte Projektmappenplattform mit der Plattform des Zielgeräts übereinstimmen.

1. Drücken Sie **F5**, um mit dem Debuggen zu beginnen, oder **UMSCHALT**+**F5**, um ohne Debuggen zu beginnen.

   Visual Studio startet den Emulator, wobei das Laden und Bereitstellen Ihres Codes mehrere Sekunden in Anspruch nimmt. So wird die App im Emulator angezeigt:

   ![Ausführen einer App im Android-Emulator](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Nachdem Ihre App gestartet wurde, können Sie Haltepunkte festlegen und den Debugger verwenden, um den Code schrittweise zu durchlaufen, lokale Variablen zu prüfen und Werte anzuzeigen.

1. Drücken Sie **UMSCHALT**+**F5**, um den Debugvorgang zu beenden.

   Der Emulator ist ein separater Prozess, der weiterhin ausgeführt wird. Sie können Ihren Code mehrfach auf demselben Emulator bearbeiten, kompilieren und bereitstellen. Die App wird in der App-Sammlung für den Emulator angezeigt und kann direkt von dort aus gestartet werden.

   Die generierten Android Native Activity-App- und Bibliotheksprojekte legen den freigegebenen C++-Code in einer dynamischen Bibliothek ab, die "Verbindungscode" für den Anschluss an die Android-Plattform umfasst. Der größte Teil des App-Codes befindet sich in der Bibliothek; Manifest, Ressourcen und Buildanweisungen befinden sich im Paketprojekt. Der freigegebene Code wird von "main.cpp" im NativeActivity-Projekt aufgerufen. Weitere Informationen über das Programmieren einer Android Native Activity-App finden Sie im Android Developer NDK auf der Seite [Konzepte](https://developer.android.com/ndk/guides/concepts.html) .

   Visual Studio erstellt Android Native Activity-Projekte mithilfe des Android-NDKs, das Clang als Plattformtoolset verwendet. Visual Studio ordnet die Eigenschaften des NativeActivity-Projekts den Optionen zu, die zum Kompilieren, Verknüpfen und Debuggen auf der Zielplattform verwendet werden. Um weitere Informationen zu erhalten, öffnen Sie das Dialogfeld **Eigenschaftenseiten** des MyOpenGLESApp.Android.NativeActivity-Projekts. Weitere Informationen zu den Befehlszeilenschaltern finden Sie im [Clang Compiler-Benutzerhandbuch](http://clang.llvm.org/docs/UsersManual.html) (in englischer Sprache).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Erstellen und Ausführen der iOS-App auf einem iOS-Gerät

Das iOS-App-Projekt wird in Visual Studio erstellt und bearbeitet, aufgrund von Lizenzeinschränkungen muss es jedoch auf einem Mac erstellt und von dort aus bereitgestellt werden. Visual Studio kommuniziert mit einem Remote-Agent, der auf dem Mac ausgeführt wird, um Projektdateien zu übertragen und Build-, Bereitstellungs- und Debugbefehle auszuführen. Sie müssen Ihren Mac und Visual Studio für die Kommunikation einrichten und konfigurieren, bevor Sie die iOS-App erstellen können. Ausführliche Anweisungen finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Sobald der Remote-Agent auf Ihrem Mac ausgeführt wird und mit Visual Studio gekoppelt ist, können Sie die iOS-App erstellen und ausführen, um die Installation und Einrichtung zu überprüfen.

Um eine iOS-App auf einem iOS-Gerät bereitzustellen, müssen Sie auf dem Mac auch die automatische Signierung in Xcode einrichten. Durch die automatische Signierung wird die App-Signierung automatisch verwaltet. Zudem wird ein Bereitstellungsprofil erstellt, um den Build einer App zu signieren.

### <a name="to-set-up-automatic-signing-on-xcode"></a>So richten Sie die automatische Signierung in Xcode ein

1. Installieren Sie [Xcode](https://developer.apple.com/xcode/) auf Ihrem Mac, sofern noch nicht geschehen.

1. Öffnen Sie die Xcode-App auf Ihrem Mac.

1. Erstellen Sie ein neues Xcode-Projekt für eine **Einzelansichtanwendung**. Füllen Sie bei der Projekterstellung die Pflichtfelder aus. Die Werte können beliebig sein, da das Projekt nur zum Erstellen eines Bereitstellungsprofils verwendet wird, mit dem später ein Build der App signiert werden soll.

1. Fügen Sie dem Xcode Ihre Apple ID hinzu, die in einem [Apple Developer Program](https://developer.apple.com/programs/)-Konto registriert ist. Ihre Apple ID wird als Signierungsidentität zum Signieren von Apps verwendet. Um die Signierungsidentität zu Xcode hinzuzufügen, öffnen Sie das Menü **Xcode**, und wählen Sie **Einstellungen** aus. Wählen Sie **Konten** aus, und klicken Sie auf die Schaltfläche „Hinzufügen“ (+), um Ihre Apple ID hinzuzufügen. Detaillierte Anweisungen finden Sie unter [Hinzufügen Ihres Apple ID-Kontos](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. Ändern Sie in den allgemeinen Einstellungen Ihres Xcode-Projekts den **Paketbezeichner** zu `com.<NameOfVSProject>`, wobei `<NameOfVSProject>` der Name des von Ihnen erstellten Visual Studio-Projektmappenprojekts ist. Ein Beispiel: Wenn Sie ein Projekt namens `MyOpenGLESApp` in Visual Studio erstellt haben, legen Sie den **Paketbezeichner** auf `com.MyOpenGLESApp` fest.

   ![Xcode-Bündel-ID](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Um das automatische Signieren zu aktivieren, aktivieren Sie das Kontrollkästchen **Signierung automatisch verwalten**.

   ![Automatische Signatur von Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Wählen Sie den Teamnamen der Apple ID aus, die Sie als **Team** für die Entwicklung hinzugefügt haben.

   ![Xcode-Team](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>So erstellen Sie die iOS-App auf einem iOS-Gerät und führen sie aus

1. Führen Sie den Remote-Agent auf Ihrem Mac aus, und stellen Sie sicher, dass Visual Studio mit dem Remote-Agent gekoppelt ist. Wenn Sie den Remote-Agent starten möchten, öffnen Sie ein Terminal-App-Fenster, und geben Sie `vcremote`. Weitere Informationen finden Sie unter [Konfigurieren des Remote-Agents in Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Mac-Terminalfenster bei Ausführung von „vcremote“](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Schließen Sie ein iOS-Gerät an Ihren Mac an. Wenn Sie ein Gerät zum ersten Mal an einen Computer anschließen, werden Sie in einer Warnung gefragt, ob der Computer auf das Gerät zugreifen darf. Teilen Sie dem Gerät mit, dass es dem Mac-Computer vertrauen darf.

1. Wählen Sie in Visual Studio aus der Dropdownliste **Projektmappenplattformen** die Projektmappenplattform aus, die dem Geräteprozessor entspricht (sofern diese nicht bereits ausgewählt ist). In diesem Beispiel handelt es sich um einen **ARM64**-Prozessor.

   ![Festlegen der Projektmappenplattform auf ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü des MyOpenGLESApp.iOS.Application-Projekts, und wählen Sie **Projekt entladen** aus, um das Projekt zu entladen.

1. Öffnen Sie erneut das Kontextmenü für das entladene MyOpenGLESApp.iOS.Application-Projekt, und wählen Sie **„project.pbxproj“ bearbeiten** aus, um die Projektdatei zu bearbeiten. Suchen Sie in der Datei `project.pbxproj` nach dem `buildSettings`-Attribut, und fügen Sie `DEVELOPMENT_TEAM` mit Ihrer Apple Team ID hinzu. Der Screenshot unten zeigt einen Beispielwert von `123456ABC` für die Apple Team ID. Sie finden den Wert Ihrer Apple Team ID in Xcode. Wechseln Sie zu **Buildeinstellungen**, und halten Sie den Mauszeiger auf den Namen Ihres Entwicklungsteams, um eine QuickInfo anzuzeigen. Die QuickInfo zeigt Ihre Team-ID an.

   ![Festlegen des Entwicklungsteams](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Schließen Sie die Datei `project.pbxproj`. Öffnen Sie dann das Kontextmenü für das entladene MyOpenGLESApp.iOS.Application-Projekt, und wählen Sie **Projekt erneut laden** aus, um das Projekt erneut zu laden.

1. Erstellen Sie jetzt das MyOpenGLESApp.iOS.Application-Projekt, indem Sie das Kontextmenü des Projekts öffnen und **Build** auswählen.

   ![Erstellen eines iOS-Anwendungsprojekts](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   Das Ausgabefenster zeigt die Ausgabe des Buildprozesses für die statische iOS-Bibliothek und die iOS-App an. Auf dem Mac zeigt das Terminal-Fenster, in dem der Remote-Agent ausgeführt wird, die Befehls- und Dateiübertragungsaktivitäten an.

   Auf Ihrem Mac-Computer werden Sie möglicherweise aufgefordert, Codesign den Zugriff auf Ihre Keychain zu ermöglichen. Wählen Sie **Zulassen** aus, um den Vorgang fortzusetzen.

1. Wählen Sie auf der Symbolleiste Ihr iOS-Gerät aus, um die App auf dem Gerät auszuführen, das an Ihren Mac angeschlossen ist. Wenn die App nicht gestartet wird, vergewissern Sie sich, dass das Gerät der bereitgestellten Anwendung die Berechtigung für die Ausführung auf dem Gerät erteilt hat. Diese Berechtigung kann auf dem Gerät festgelegt werden: **Einstellungen** > **Allgemein** > **Geräteverwaltung**. Wählen Sie das Konto Ihrer Developer-App aus, legen Sie das Konto als vertrauenswürdig fest, und überprüfen Sie die App. Versuchen Sie erneut, die App in Visual Studio auszuführen.

   ![iOS-App auf iOS-Gerät](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")

   Nachdem Ihre App gestartet wurde, können Sie Haltepunkte festlegen und den Visual Studio-Debugger verwenden, um lokale Variablen zu prüfen, die Aufrufliste anzuzeigen und Werte zu überwachen.

   ![Debugger an Haltepunkt in iOS-App](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Drücken Sie **UMSCHALT**+**F5**, um den Debugvorgang zu beenden.

   Der C++-Code wird von den generierten iOS-App- und -Bibliotheksprojekten in einer statischen Bibliothek abgelegt, die nur den freigegebenen Code implementiert. Der Hauptteil des Anwendungscodes befindet sich im `Application`-Projekt. Die Aufrufe des freigegebenen Bibliothekscodes in diesem Vorlagenprojekt werden in der Datei *GameViewController.m* ausgeführt. Zur Erstellung der iOS-App verwendet Visual Studio das Xcode-Plattformtoolset, das die Kommunikation mit einem Remoteclient erfordert, der auf einem Mac ausgeführt wird.

   Visual Studio überträgt die Projektdateien und sendet Befehle an den Remoteclient, um die App mithilfe von Xcode zu erstellen. Der Remoteclient sendet Buildstatusinformationen zurück an Visual Studio. Nachdem die App erfolgreich erstellt wurde, können Sie Visual Studio verwenden, um Befehle zum Ausführen und Debuggen der App zu senden. Der Debugger in Visual Studio steuert die App, die auf dem an Ihren Mac angeschlossenen iOS-Gerät ausgeführt wird. Visual Studio ordnet die Eigenschaften des StaticLibrary-Projekts den Optionen zu, die zum Kompilieren, Verknüpfen und Debuggen auf der iOS-Zielplattform verwendet werden. Um ausführliche Informationen zur Compiler-Befehlszeilenoption zu erhalten, öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das MyOpenGLESApp.iOS.StaticLibrary-Projekt.

## <a name="customize-your-apps"></a>Anpassen der Apps

Sie können den freigegebenen C++-Code bearbeiten, um allgemeine Funktionen hinzuzufügen oder zu ändern. Sie müssen die Aufrufe des freigegebenen Codes in den `MyOpenGLESApp.Android.NativeActivity`- und `MyOpenGLESApp.iOS.Application`-Projekten ändern, damit sie übereinstimmen. Sie können Präprozessormakros verwenden, um plattformspezifische Abschnitte im gemeinsamen Code anzugeben. Der Präprozessormakro `__ANDROID__` ist bei der Erstellung für Android vordefiniert. Der Präprozessormakro `__APPLE__` ist bei der Erstellung für iOS vordefiniert.

Um IntelliSense für eine bestimmte Projektplattform anzuzeigen, wählen Sie das Projekt aus den Dropdownlistenelementen zum Wechseln des Kontexts in der Navigationsleiste oben im Editor-Fenster aus.

![Dropdownelement zum Wechseln des Projektkontexts im Editor](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

IntelliSense-Probleme im vom aktuellen Projekt verwendeten Code sind durch eine rote Wellenlinie gekennzeichnet. Probleme in anderen Projekten sind durch eine violette Wellenlinie gekennzeichnet. Visual Studio unterstützt weder eine farbliche Kennzeichnung von Code noch IntelliSense für Java- oder Objective-C-Dateien. Sie können jedoch weiterhin die Quelldateien und die Ressourcen ändern, um den Anwendungsnamen, das Symbol und weitere Implementierungsdetails festzulegen.
