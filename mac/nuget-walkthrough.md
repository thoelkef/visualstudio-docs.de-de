---
title: Einschließen eines NuGet-Pakets in Ihr Projekt
description: In diesem Dokument wird erläutert, wie Sie ein NuGet-Paket mithilfe von Visual Studio für Mac in ein Projekt einfügen. Es veranschaulicht das Suchen und Herunterladen von Paketen und bietet eine Einführung in die IDE-Integrationsfunktionen.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127242"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installieren und Verwalten von NuGet-Paketen in Visual Studio für Mac

Über die Benutzeroberfläche des NuGet-Paket-Managers in Visual Studio für Mac können Sie auf einfache Weise NuGet-Pakete in Projekten und Projektmappen installieren, deinstallieren und aktualisieren. Sie können nach Paketen suchen und diese zu Ihren .NET Core-, ASP.NET Core- und Xamarin-Projekten hinzufügen.

Dieser Artikel befasst sich mit dem Einschließen eines NuGet-Pakets in ein Projekt und veranschaulicht die Toolkette, durch die der Prozess nahtlos abläuft.

Eine Einführung in die Verwendung von NuGet in Visual Studio für Mac finden Sie im [Schnellstart: Installieren und Verwenden eines Pakets in Visual Studio für Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac).

## <a name="find-and-install-a-package"></a>Suchen und Installieren eines Pakets

1. Klicken Sie bei einem in Visual Studio für Mac geöffneten Projekt im **Lösungspad** mit der rechten Maustaste auf den Ordner **Abhängigkeiten** (**Pakete**, wenn Sie ein Xamarin-Projekt verwenden), und wählen Sie dann **NuGet-Pakete verwalten...** aus.

    ![Kontextaktion für das Hinzufügen eines neuen NuGet-Pakets](media/nuget-walkthrough-packages-menu.png)

2. Daraufhin wird das Fenster **NuGet-Pakete verwalten** geöffnet. Stellen Sie sicher, dass das Dropdownmenü „Quelle“ in der oberen linken Ecke des Dialogfelds auf `nuget.org` festgelegt ist, sodass das zentrale Repository des NuGet-Pakets durchsucht wird.

    ![Liste von NuGet-Paketen](media/nuget-walkthrough-add-packages1.png)

3. Verwenden Sie das Suchfeld in der oberen rechten Ecke, um ein bestimmtes Paket, zum Beispiel `EntityFramework`, zu finden. Wenn Sie ein Paket gefunden haben, das Sie verwenden möchten, wählen Sie es aus, und klicken Sie auf die Schaltfläche **Paket hinzufügen**, um die Installation zu starten.

    ![Hinzufügen des EntityFramework-NuGet-Pakets](media/nuget-walkthrough-add-packages2.png)

4. Sobald das Paket heruntergeladen wurde, wird es Ihrem Projekt hinzugefügt. Die Projektmappe ändert sich, je nachdem, welche Art von Projekt Sie bearbeiten:

    **Xamarin-Projekte**
    * Der Knoten **Referenzen** wird eine Liste aller Assemblys enthalten, die Teil eines NuGet-Pakets sind.
    * Der Knoten **Pakete** zeigt alle NuGet-Pakete an, die Sie heruntergeladen haben. Sie können Pakete aus dieser Liste aktualisieren oder entfernen.
    
    **.NET Core-Projekte**

    * Der Knoten **Abhängigkeiten > NuGet** zeigt alle NuGet-Pakete an, die Sie heruntergeladen haben. Sie können Pakete aus dieser Liste aktualisieren oder entfernen.

## <a name="using-nuget-packages"></a>Verwenden von NuGet-Paketen

Sobald das NuGet-Paket hinzugefügt und die Projektverweise aktualisiert wurden, können Sie so mit der API programmieren, wie Sie es mit jedem anderen Projektverweis tun würden.

Versichern Sie sich, dass sie alle erforderlichen `using`-Anweisungen zum Anfang Ihrer Datei hinzufügen:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aktualisieren von Paketen

Paketupdates können entweder alle auf einmal durchgeführt werden, indem Sie mit der rechten Maustaste auf den Knoten **Abhängigkeiten** (**Pakete** bei Xamarin-Projekten) klicken, oder einzeln, indem Sie auf jedes Paket klicken. Wenn eine neue Version eines NuGet-Pakets verfügbar ist, wird ein Symbol für die Aktualisierung ![NACH-OBEN-TASTE mit Kreis](media/nuget-walkthrough-update-icon.png) angezeigt.

Klicken Sie mit der rechten Maustaste auf **Abhängigkeiten**, um das Kontextmenü anzuzeigen, und wählen Sie **Aktualisieren** aus, um alle Pakete zu aktualisieren:

![Paketmenü](media/nuget-walkthrough-packages-menu-update.png)

* **NuGet-Pakete verwalten:** Öffnet das Fenster, um dem Projekt weitere Pakete hinzuzufügen.
* **Aktualisieren**: Überprüft den Quellserver auf jedes Paket und lädt neuere Versionen herunter.
* **Wiederherstellen**: Lädt fehlende Pakete herunter (ohne bestehende Pakete auf neuere Versionen zu aktualisieren).

Die Optionen „Aktualisieren“ und „Wiederherstellen“ sind auch auf Projektmappenebene verfügbar und wirken sich auf alle Projekte in der Projektmappe aus.

### <a name="locating-outdated-packages"></a>Suchen veralteter Pakete
Im Lösungspad wird angezeigt, welche Version eines Pakets derzeit installiert ist, und Sie können per Rechtsklick ein Update für das Paket durchführen.

![Paketmenü mit den Optionen „Update“, „Entfernen“ und „Aktualisieren“](media/nuget-walkthrough-PackageMenu.png)

Außerdem wird neben dem Paketnamen eine Benachrichtigung angezeigt, wenn eine neue Version für ein Paket zur Verfügung steht, damit Sie entscheiden können, ob Sie ein Update durchführen möchten.

![Benachrichtigung bei verfügbarer neuen Paketversion](media/nuget-walkthrough-package-update-available.png)

Im angezeigten Menü stehen die folgenden zwei Optionen zur Auswahl:

* **Aktualisieren**: Überprüft den Quellserver und lädt eine neuere Version herunter (falls vorhanden).
* **Entfernen**: Entfernt das Paket aus diesem Projekt und die relevanten Assemblys aus den Projektverweisen.

## <a name="manage-packages-for-the-solution"></a>Verwalten von Paketen für die Projektmappe

Die Verwaltung von Paketen für eine Projektmappe ist eine praktische Möglichkeit, mit mehreren Projekten gleichzeitig zu arbeiten.

1. Klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete verwalten...** aus.

    ![Verwalten von NuGet-Paketen für die Projektmappe](media/nuget-walkthrough-manage-packages-solution.png)

1. Bei der Verwaltung von Paketen für die Projektmappe können Sie über die Benutzeroberfläche die Projekte auswählen, die von den Vorgängen beeinflusst werden:

    ![Projektselektor beim Verwalten von Paketen für die Projektmappe](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Registerkarte „Konsolidieren“

Wenn Sie in einer Projektmappe mit mehreren Projekten arbeiten, wird empfohlen, dass Sie in allen Projekten, für die dasselbe NuGet-Paket verwendet wird, auch dieselbe Version dieses Pakets verwenden. In Visual Studio für Mac können Sie dies einfach über die Registerkarte **Konsolidieren** auf der Benutzeroberfläche des Paket-Managers feststellen, wenn Sie die Pakete für eine Projektmappe verwalten. Über diese Registerkarte sehen Sie, wo Pakete mit unterschiedlichen Versionsnummern von unterschiedlichen Projekten in der Projektmappe verwendet werden:

![Registerkarte „Konsolidieren“ in der Benutzeroberfläche des Paket-Managers](media/nuget-walkthrough-consolidate-tab.png)

In diesem Beispiel verwendet das Projekt NuGetDemo das Paket Microsoft.EntityFrameworkCore 2.20, während NuGetDemo.Shared das Paket Microsoft.EntityFrameworkCore 2.2.6 verwendet. Gehen Sie zum Konsolidieren von Paketversionen folgendermaßen vor:

- Wählen Sie die zu aktualisierenden Projekte in der Projektliste aus.
- Wählen Sie die zu verwendende Version, z. B. Microsoft.EntityFrameworkCore 3.0.0, für diese Projekte über die Liste **Neue Version** aus.
- Klicken Sie auf **Paket konsolidieren**.

Der Paket-Manager installiert die ausgewählte Paketversion in allen ausgewählten Projekten. Danach erscheint das Paket nicht mehr auf der Registerkarte **Konsolidieren**.

## <a name="adding-package-sources"></a>Hinzufügen von Paketquellen

Pakete, die für die Installation verfügbar sind, werden ursprünglich von nuget.org abgerufen. Sie können jedoch andere Paketspeicherorte zu Visual Studio für Mac hinzufügen. Das kann hilfreich sein, um Ihre NuGet-Pakete in der Entwicklung zu testen oder um einen privaten NuGet-Server innerhalb Ihres Unternehmens oder Ihrer Organisation zu verwenden.

Navigieren Sie in Visual Studio für Mac zu **Visual Studio > Einstellungen > NuGet > Quellen**, um die Liste der Paketquellen anzuzeigen und zu bearbeiten. Beachten Sie, dass es sich bei den Quellen um einen Remoteserver (angegeben durch eine URL) oder ein lokales Verzeichnis handeln kann.

![Paketquellen](media/nuget-walkthrough-PackageSource.png)

Klicken Sie auf **Hinzufügen**, um eine neue Quelle festzulegen. Geben Sie einen Anzeigenamen und die URL (oder den Dateipfad) zur Paketquelle an. Wenn es sich bei der Quelle um einen sicheren Webserver handelt, geben Sie auch einen Benutzernamen und ein Kennwort an, andernfalls lassen Sie diese Einträge leer:

![Hinzufügen von Paketquellen](media/nuget-walkthrough-PackageSource2.png)

Verschiedene Quellen können bei der Suche nach Paketen angegeben werden:

![Hinzufügen von Paketquellen](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Quellcodeverwaltung

Die NuGet-Dokumentation erläutert [das Verwenden von NuGet ohne das Übernehmen von Paketen in die Quellcodeverwaltung](/nuget/consume-packages/packages-and-source-control). Wenn Sie keine Binärdateien und nicht verwendeten Informationen in der Quellcodeverwaltung speichern möchten, können Sie Visual Studio für Mac für das automatische Wiederherstellen vom Server konfigurieren. Wenn ein Entwickler das Projekt zum ersten Mal aus der Quellcodeverwaltung abruft, lädt Visual Studio für Mac dadurch die erforderlichen Pakete automatisch herunter und installiert diese.

![Automatisches Wiederherstellen von Paketen](media/nuget-walkthrough-AutoRestore.png)

Weitere Informationen zum Ausschließen der Verfolgung des Verzeichnisses `packages` finden Sie in der Dokumentation zu Ihrer speziellen Quellcodeverwaltung.

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Siehe auch

* [Installieren und Verwenden eines Pakets in Visual Studio (unter Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
