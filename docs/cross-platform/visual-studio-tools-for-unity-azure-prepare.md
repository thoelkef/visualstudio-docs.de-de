---
title: "Visual Studio-Tools für Unity: Vorbereiten – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7554380435c77750eb48a5ce261cc0a2b3885ccd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="prepare-the-development-environment"></a>Vorbereiten der Entwicklungsumgebung

Einige Voraussetzungen müssen erfüllt sein, bevor das Azure Mobile Client SDK in Unity verwendet werden kann.

## <a name="download-and-install-unity-2017"></a>Herunterladen und Installieren von Unity 2017

Unity 2017.1 oder höher ist erforderlich. Für diese exemplarische Vorgehensweise ist es egal, welchen Unity-Abonnementplan Sie besitzen; auch der kostenlose Personal-Abonnementplan reicht aus. Laden Sie Unity unter https://store.unity.com/ herunter.

## <a name="download-and-install-visual-studio-2017"></a>Herunterladen und Installieren von Visual Studio 2017

Die exemplarische Vorgehensweise erfordert Visual Studio 2017 15.3 und höher, zusammen mit der Workload „Spieleentwicklung mit Unity“. Die exemplarische Vorgehensweise ist mit allen Editionen von Visual Studio 2017 möglich, einschließlich der kostenlosen Community Edition.

1. Laden Sie Visual Studio 2017 auf https://www.visualstudio.com/ herunter.

2. Installieren Sie Visual Studio 2017, und stellen Sie sicher, dass die Workload **Spieleentwicklung mit Unity** aktiviert ist.

 ![Auswählen der Unity-Workload](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Wenn Visual Studio 2017 bereits installiert ist, können Sie Workloads durch Ausführen des Visual Studio-Installers anzeigen und ändern.

## <a name="create-a-new-3d-unity-project"></a>Erstellen eines neuen 3D-Projekts mit Unity

Starten Sie Unity, und erstellen Sie ein neues 3D-Projekt.

![Erstellen eines neuen Unity-Projekts](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Festlegen von Visual Studio Preview 2017 als Skript-Editor

Möglicherweise ist Visual Studio 2017 bereits als externer Skript-Editor für Unity festgelegt, aber stellen Sie dennoch sicher, dass die Vorschauversion 15.3 ausgewählt ist.

1. Wählen Sie in Unity im Menü **Bearbeiten** **Bearbeiten > Einstellungen...** aus.

  ![Öffnen des Menüs „Einstellungen“](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Wenn in Unity das Fenster „Einstellungen“ angezeigt wird, wählen Sie auf der linken Seite die Registerkarte **Externe Tools** aus.

3. Wählen Sie im Dropdownmenü **External Script Editor** (Externer Skript-Editor) **Visual Studio 2017** aus.

  ![Externen Skript-Editor festlegen](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Ändern der Unity-Skriptlaufzeit auf .NET 4.6
Für die exemplarische Vorgehensweise ist .NET 4.6 erforderlich, damit das Azure Mobile Client SDK und seine Abhängigkeiten verwendet werden können.

1. Wählen Sie in Unity im Menü **Datei** **Datei > Buildeinstellungen...** aus.

  ![Öffnen der Buildeinstellungen](media/vstu_azure-prepare-dev-environment-image4.png)

2. Klicken Sie auf die Schaltfläche **Playereinstellungen...**.

  ![Öffnen der Playereinstellungen](media/vstu_azure-prepare-dev-environment-image5.png)

3. Die Playereinstellungen werden in Unity im Inspector-Fenster geöffnet. Klicken Sie unter der Überschrift **Konfiguration** auf die Dropdownliste **Scripting Runtime Version** (Version der Skriptlaufzeit), und wählen Sie **Experimental (.NET 4.6 Equivalent)** (Experimentell (entspricht .NET 4.6)) aus. Daraufhin werden Sie in einem Dialogfeld aufgefordert, Unity neu zu starten. Wählen Sie **Restart** (Neustart).

  ![Auswählen von .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Fügen Sie einen Verweis auf „System.Net.Http.dll“ hinzu.

In Unity kann dank der mit .NET 4.6 identischen Skriptlaufzeit das Paket „System.Net.Http“ verwendet werden, welches auch für das Azure Mobile Client SDK benötigt wird. Die DLL-Datei ist in Unity enthalten, jedoch muss ein Verweis hinzugefügt werden, damit sie verwendet werden kann.

1. Klicken Sie im Unity-Editor im Fenster „Projekt“ **mit der rechten Maustaste** den Ordner **Objekte** an, und wählen Sie **Im Explorer anzeigen**.

  ![Ordner „Objekte“ im Explorer anzeigen](media/vstu_azure-prepare-dev-environment-image7.png)

2. Klicken Sie im Fenster „Explorer“, das jetzt eingeblendet wird, doppelt auf das Verzeichnis **Objekte**, um es zu öffnen.

3. Klicken Sie im Verzeichnis „Objekte“ **mit der rechten Maustaste**, und wählen Sie **Neu > Textdokument** aus.

4. Öffnen Sie das neue Textdokument in einem Text-Editor, und fügen Sie die Zeile `-r:System.Net.Http.dll` hinzu.

5. Speichern Sie das Dokument, und schließen Sie es.

4. Benennen Sie das neue Textdokument in „**mcs.rsp**“ um, und achten Sie darauf, dass Sie die Dateierweiterung „.txt“ löschen.

  * Wenn bei Ihnen die Dateierweiterungen ausgeblendet sind, müssen Sie die Optionen der Ordneransicht ändern, damit diese angezeigt werden.
  * Öffnen Sie das Startmenü, und geben Sie „Ordneroptionen“ ein, um danach zu suchen. Wählen Sie „**File Explorer Options**“ (Datei-Explorer-Optionen).
  * Wählen Sie die Registerkarte **Ansicht** aus, und stellen Sie sicher, dass in den erweiterten Einstellungen „**Hide extensions for known file types**“ (Erweiterungen bekannter Dateitypen ausblenden) deaktiviert ist.

    ![Ordner „Objekte“ im Explorer anzeigen](media/vstu_azure-prepare-dev-environment-image8.png)

Nachdem Sie diese Schritte durchgeführt haben, sollten Sie im **Objekte**-Stammverzeichnis Ihres Unity-Projekts eine Datei namens **mcs.rsp** besitzen, die die Zeile `r:System.Net.Http.dll` enthält.

>[!NOTE]
> Die Funktionalität „Verweis“ erfordert Visual Studio-Tools für Unity 3.3 und höher. Dies ist in der Unity-Workload von Visual Studio 15.3 und höher enthalten. Wenn dieser Schritt nicht funktioniert, stellen Sie sicher, dass Sie die richtige Version von VSTU installiert haben.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Hinzufügen des NuGet-Pakets „Newtonsoft.Json“ zu Ihrem Projekt

Das Azure Mobile Client SDK erfordert das Newtonsoft.Json-Paket. Unity unterstützt NuGet leider nicht. Wenn Sie in Visual Studio ein Unity-Projekt öffnen und mit NuGet ein Paket hinzufügen, löscht Unity das Paket das nächste Mal, wenn Sie das Projekt im Unity-Editor öffnen. NuGet-Pakete können jedoch manuell zu einem Unity-Projekt hinzugefügt werden.

1. Erstellen Sie im Verzeichnis „Objekte“ Ihres Unity-Projekts einen neuen Ordner mit dem Namen „**NuGet-Pakete**“. Dieser dient nur zur Organisation.

2. Wechseln Sie zu https://www.nuget.org/packages/Newtonsoft.Json/, und klicken Sie auf die Schaltfläche **Manual Download** (Manuell herunterladen). Laden Sie die NUPKG-Datei herunter.

  ![Ordner „Objekte“ im Explorer anzeigen](media/vstu_azure-prepare-dev-environment-image9.png)

3. Suchen Sie die neu heruntergeladene Datei, und ändern Sie deren Erweiterung (.nupkg) in **.zip** um. Jetzt sollten Sie die darin enthaltenen Dateien anzeigen und extrahieren können, so wie das bei gewöhnlichen ZIP-Dateien der Fall ist.

4. Öffnen oder extrahieren Sie das ZIP-Verzeichnis, und navigieren Sie zu **\lib\net45**.

5. Kopieren Sie die Datei **Newtonsoft.Json.dll** in das Verzeichnis **Assets\NuGet Packages** (Objekte\NuGet-Pakete) Ihres Unity-Projekts.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Hinzufügen des NuGet-Pakets für das Azure Mobile Client SDK zu Ihrem Projekt

Das Azure Mobile Client SDK enthält Funktionen, die es erleichtern, „Einfache Tabellen“ (Azure) zu lesen und mit Inhalt zu füllen.

1. Wechseln Sie zu https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/, und klicken Sie auf die Schaltfläche **Manual Download** (Manuell herunterladen). Laden Sie die NUPKG-Datei herunter.

2. Suchen Sie die neu heruntergeladene Datei, und ändern Sie deren Erweiterung (.nupkg) in **.zip** um. Jetzt sollten Sie die darin enthaltenen Dateien anzeigen und extrahieren können, so wie das bei gewöhnlichen ZIP-Dateien der Fall ist.

3. Öffnen oder extrahieren Sie das ZIP-Verzeichnis, und navigieren Sie zu **\lib\net45**.

4. Kopieren Sie die Datei **Microsoft.Azure.Mobile.Client.dll** in das **Assets\NuGet Packages**-Verzeichnis (Objekte\NuGet-Pakete) Ihres Unity-Projekts.

>[!WARNING]
> Nach Durchführen dieser Schritte müssen Sie Unity und Visual Studio neu starten, da IntelliSense die neu hinzugefügten Pakete andernfalls möglicherweise nicht erkennt.

## <a name="conclusion"></a>Schlussbemerkung

Nach Durchführen dieser Schritte sollte Ihr Unity-Projekt zum Verwenden des Azure Mobile Client SDK bereit sein. Sie können Ihre Entwicklungsumgebung testen, indem Sie in Ihrem Unity-Projekt ein neues C#-Skript erstellen, dies in Visual Studio öffnen und die folgenden Using-Anweisungen oben eingeben:
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Wenn IntelliSense diese Using-Anweisungen erkennt, wurde die Einrichtung ordnungsgemäß abgeschlossen. Wenn Fehler auftreten oder IntelliSense diese Pakete nicht erkennt, starten Sie Unity und Visual Studio neu. Wenn es dann immer noch nicht funktioniert, wiederholen Sie die oben beschriebenen Schritte.

## <a name="next-step"></a>Nächster Schritt

* [Erstellen von Datenmodellklassen](visual-studio-tools-for-unity-azure-data.md)
