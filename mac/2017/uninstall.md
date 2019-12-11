---
title: Deinstallieren von Visual Studio für Mac
description: Anleitung zum Deinstallieren von Visual Studio für Mac und dazugehörigen Tools
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 78bf7fce98f2a77e05a3fbbd31afcf3f20d97a9f
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985135"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Deinstallieren von Visual Studio für Mac

Es gibt eine Reihe von Xamarin-Produkten einschließlich eigenständiger Apps wie Visual Studio für Mac, die die plattformübergreifende Anwendungsentwicklung ermöglichen.

Sie können diesen Leitfaden verwenden, um jedes Produkt einzeln zu deinstallieren, indem Sie zum entsprechenden Abschnitt navigieren, oder die Skripts im Abschnitt [Deinstallationsskript](#uninstall-script) bereitgestellten Skripts verwenden, um das gesamte Produkt zu deinstallieren.

Wenn Sie zuvor bereits Xamarin Studio auf Ihrem Computer installiert hatten, müssen Sie außer den nachfolgenden Schritten möglicherweise auch die Anleitung im [Deinstallationshandbuch für Xamarin](/xamarin/cross-platform/get-started/installation/uninstalling-xamarin#uninstall-xamarin-studio-on-mac) ausführen.

## <a name="uninstall-script"></a>Deinstallieren des Skripts

Es gibt zwei Skripts, die für die Deinstallation von Visual Studio für Mac und sämtliche Komponenten von Ihrem Computer verwendet werden können:

- [Visual Studio- und Xamarin-Skript](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core-Skript](#net-core-script)

In folgenden Abschnitten werden Informationen zum Herunterladen und Verwenden der Skripts bereitgestellt.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Visual Studio für Mac- und Xamarin-Skript

Sie können Visual Studio- und Xamarin-Komponenten mithilfe des [Deinstallationsskripts](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh) gleichzeitig deinstallieren.

Dieses Deinstallationsskript enthält die meisten Befehle, die Sie im Artikel finden. Es gibt drei wichtige Auslassungen gegenüber dem Skript, die aufgrund von möglichen externen Abhängigkeiten nicht enthalten sind. Um diese zu entfernen, wechseln Sie zum entsprechenden Abschnitt unten, und entfernen Sie sie manuell:

- **[Deinstallieren von Mono](#uninstall-mono-sdk-mdk)**
- **[Deinstallieren von Android-AVDs](#uninstall-android-avd)**
- **[Deinstallieren des Android SDK und des Java SDK](#uninstall-android-sdk-and-java-sdk)**

Führen Sie die folgenden Schritte durch, um das Skript auszuführen:

1. Klicken Sie mit der rechten Maustaste auf das Skript, und wählen Sie **Speichern unter** aus, um die Datei auf Ihrem Mac zu speichern.
2. Öffnen Sie das Terminal, und ändern Sie das Arbeitsverzeichnis, in das das Skript heruntergeladen wurde:

    ```bash
    cd /location/of/file
    ```

3. Machen Sie das Skript ausführbar, und führen Sie es mit **sudo** aus:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Löschen Sie schließlich das Deinstallationsskript.

### <a name="net-core-script"></a>.NET Core-Skript

Das Deinstallationsskript für .NET Core befindet sich in diesem [dotnet-CLI-Repository](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh).

Führen Sie die folgenden Schritte durch, um das Skript auszuführen:

1. Klicken Sie mit der rechten Maustaste auf das Skript, und wählen Sie **Speichern unter** aus, um die Datei auf Ihrem Mac zu speichern.
2. Öffnen Sie das Terminal, und ändern Sie das Arbeitsverzeichnis, in das das Skript heruntergeladen wurde:

    ```bash
    cd /location/of/file
    ```

3. Machen Sie das Skript ausführbar, und führen Sie es mit **sudo** aus:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Löschen Sie schließlich das .NET Core-Deinstallationsskript.

## <a name="uninstall-visual-studio-for-mac"></a>Deinstallieren von Visual Studio für Mac

Der erste Schritt bei der Deinstallation von Visual Studio für Mac besteht darin, die **Visual Studio.app** im Verzeichnis **/Anwendungen** zu suchen und in den **Papierkorb** zu legen. Alternativ können Sie mit der rechten Maustaste darauf klicken und wie hier dargestellt auf **In den Papierkorb legen** klicken:

![Visual Studio-Anwendung in den Papierkorb verschieben](media/uninstall-image1.png)

Durch das Löschen dieses App Bundles wird Visual Studio für Mac entfernt, obwohl es im Dateisystem möglicherweise noch andere Dateien im Zusammenhang mit Xamarin gibt.

Um alle Spuren von Visual Studio für Mac zu entfernen, führen Sie die folgenden Befehle im Terminal aus:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

Sie können auch das folgende Verzeichnis entfernen, das verschiedene Xamarin-Dateien und -Ordner enthält. Sie sollten sich dabei aber bewusst sein, dass dieses Verzeichnis die Android-Signaturschlüssel enthält. Weitere Informationen finden Sie im Abschnitt **[Deinstallieren des Android SDK und des Java SDK](#uninstall-android-sdk-and-java-sdk)** .

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Deinstallieren des Mono SDK (MDK)

Mono ist eine Open Source-Implementierung von Microsofts .NET Framework und wird von allen Xamarin-Produkten (Xamarin.iOS, Xamarin.Android und Xamarin.Mac) verwendet, damit diese Plattformen in C# entwickelt werden können.

> [!WARNING]
> Außerhalb von Visual Studio für Mac gibt es weitere Anwendungen, die ebenfalls Mono verwenden, z.B. Unity.
> Achten Sie darauf, dass es keine weiteren Abhängigkeiten mit Mono bestehen, bevor Sie es deinstallieren.

Um das Mono-Framework von einem Computer zu entfernen, führen Sie die folgenden Befehle im Terminal aus:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Deinstallieren von Xamarin.Android

Es gibt eine Anzahl von Elementen, die für die Installation und Verwendung von Xamarin.Android erforderlich sind, z.B. das Android SDK und das Java SDK.

Verwenden Sie die folgenden Befehle, um Xamarin.Android zu entfernen:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Deinstallieren des Android SDK und des Java SDK

Das Android SDK ist für die Entwicklung von Android-Anwendungen erforderlich. Um alle Bestandteile des Android SDK vollständig zu entfernen, suchen Sie die Datei unter **~/Library/Developer/Xamarin/** , und verschieben Sie sie in den **Papierkorb**.

> [!WARNING]
> Sie sollten dabei beachten, dass sich Android Signaturschlüssel, die von Visual Studio für Mac generiert werden, in `~/Library/Developer/Xamarin/Keystore` befinden. Stellen Sie sicher, dass diese entsprechend gesichert werden, oder vermeiden Sie es, dieses Verzeichnis zu entfernen, wenn Sie Ihren Keystore beibehalten möchten.

Java SDK (JDK) muss nicht deinstalliert werden, da es unter Mac OS X/macOS bereits vorab installiert ist.

### <a name="uninstall-android-avd"></a>Deinstallieren von Android-AVDs

> [!WARNING]
> Es gibt weitere Anwendungen außerhalb von Visual Studio für Mac, die ebenfalls Android-AVDs und diese zusätzlichen Android-Komponenten wie z.B. Android Studio verwenden. Durch Entfernen dieses Verzeichnisses werden Projekte in Android Studio möglicherweise unterbrochen.

Verwenden Sie zum Entfernen aller Android-AVDs und weiteren Android Komponenten den folgenden Befehl:

```bash
rm -rf ~/.android
```

Um nur Android-AVDs zu entfernen, verwenden Sie den folgenden Befehl:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Deinstallieren von Xamarin.iOS

Xamarin.iOS ermöglicht die Entwicklung von iOS-Anwendungen mit C# oder F# in Visual Studio für Mac.

Führen Sie die folgenden Befehle im Terminal aus, um alle Xamarin.iOS-Dateien aus einem Dateisystem zu entfernen:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Deinstallieren von Xamarin.Mac

Sie können Xamarin.Mac und die zugehörige Lizenz mithilfe der folgenden beiden Befehle vom Computer entfernen:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Deinstallieren von Workbooks und Inspector

Ab 1.2.2 kann Xamarin Workbooks & Inspektor im Terminal deinstalliert werden, indem Sie Folgendes ausführen:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Für frühere Versionen müssen Sie folgende Artefakte manuell entfernen:

* Löschen Sie die Workbooks-App unter `"/Applications/Xamarin Workbooks.app"`.
* Löschen Sie die Inspector-App unter `"Applications/Xamarin Inspector.app"`.
* Löschen Sie die Add-ins `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` und `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`.
* Löschen Sie Inspector und die unterstützenden Dateien hier: `/Library/Frameworks/Xamarin.Interactive.framework` und `/Library/Frameworks/Xamarin.Inspector.framework`.

## <a name="uninstall-the-xamarin-profiler"></a>Deinstallieren von Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Deinstallieren Sie den Visual Studio-Installer.

Verwenden Sie die folgenden Befehle, um alle Spuren des Xamarin-Universal-Installer zu entfernen:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Siehe auch

- [Deinstallieren von Visual Studio (unter Windows)](/visualstudio/install/uninstall-visual-studio)