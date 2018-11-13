---
title: Synchronisieren von Änderungen zwischen XCode und Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xamarin
ms.openlocfilehash: a32d72869a14e22ba8707036cd4b549ef5228d3b
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379301"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronisieren von Änderungen zwischen XCode und Visual Studio
Die Komponente Microsoft Visual C++ für Mobile-Entwicklung umfasst Remotefunktionen für die Synchronisierung Ihrer Daten zwischen Ihrem PC und Ihrem Mac. Wenn Ihr Visual Studio- und Ihr Mac-Computer gekoppelt sind, sind für iOS-Anwendungsprojekte neue Optionen in Visual Studio verfügbar, mit denen Sie Ihr Projekt in XCode öffnen, den Code zwischen XCode und Visual Studio verschieben und das temporäre XCode-Projektverzeichnis bereinigen können.

 Um die Optionen für Remotecomputer zu verwenden, muss das Projekt ein iOS-Anwendungsprojekt sein, und Visual Studio muss mit Ihrem Mac gekoppelt sein. Voraussetzungen für und Anweisungen zur Kopplung mit einem Mac finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Menü „Remotecomputer“
 Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf ein iOS-Anwendungsprojekt, um das Kontextmenü anzuzeigen. Wählen Sie **Remotecomputer** aus, um die verfügbaren Remoteoptionen anzuzeigen.

 ![Das Menüelement „Remotecomputer“ im Projektmappen-Explorer](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Mit diesen Befehlen können Sie Ihr Projekt in XCode öffnen, lokale Änderungen oder das gesamte Projekt zwischen Visual Studio und XCode verschieben und die temporären Dateien auf dem Remotecomputer bereinigen.

### <a name="open-in-xcode"></a>In XCode öffnen
 Öffnen Sie das Projekt in XCode über Visual Studio, indem Sie im Untermenü **Remotecomputer** die Option **In XCode öffnen** auswählen, um das ausgewählte Projekt auf dem gekoppelten Remotecomputer zu öffnen. Der Vcremote-Server wird verwendet, um XCode auf Ihrem Mac zu öffnen und zu einem temporären Verzeichnis auf Ihrem Mac zu wechseln, das eine Kopie des Projekts enthält. Visual Studio zeigt ein Dialogfeld an, in dem das für das Projekt verwendete temporäre Verzeichnis eingeblendet wird. Die Aktionen, die auf dem Remotecomputer ausgeführt werden, werden auch im Fenster **Ausgabe** in Visual Studio angezeigt. Um diese anzuzeigen, müssen Sie möglicherweise **Visual C++-Remotecomputer** in der Dropdownliste **Ausgabe anzeigen von** am oberen Rand des Fensters **Ausgabe** auswählen.

 ![Das Fenster „Ausgabe“ zeigt die Aktionen des Remotecomputers. ](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")

 Auf Ihrem Mac können Sie alle XCode-Tools verwenden, um Code und Ressourcen, Storyboards und Aktionen zu bearbeiten. In Visual Studio ist das iOS-Anwendungsprojekt mit „In XCode geöffnet“ gekennzeichnet, um anzuzeigen, dass auf dem Remotecomputer Änderungen vorgenommen werden können. Nachdem die Bearbeitung abgeschlossen haben, können mit dem Befehl „Mithilfe von Pull vom Remotecomputer übertragen“ oder „Inkrementeller Pullvorgang vom Remotecomputer“ die Änderungen in Ihr Visual Studio-Projekt zurückkopieren.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>„Mithilfe von Pushvorgang auf den Remotecomputer übertragen“ und „Inkrementeller Pushvorgang auf den Remotecomputer“
 Wenn Sie das iOS-Anwendungsprojekt in Visual Studio geändert haben, können Sie mithilfe der Befehle „Mithilfe von Pushvorgang auf den Remotecomputer übertragen“ und „Inkrementeller Pushvorgang auf den Remotecomputer“ die geänderten Projektdateien auf den gekoppelten Remotecomputer verschieben. Mit dem Befehl „Mithilfe von Pushvorgang auf den Remotecomputer übertragen“ werden alle Projektdateien auf den Remotecomputer kopiert. Mit dem Befehl „Inkrementeller Pushvorgang auf den Remotecomputer“ werden nur geänderte Dateien auf den Remotecomputer kopiert. Bei großen Projekten mit kleinen Änderungen können Sie mit dem Befehl für den inkrementellen Pushvorgang Zeit und Bandbreite sparen.

 Sie können die Projektdateien auf Ihren Mac kopieren, indem Sie in Visual Studio im Fenster **Projektmappen-Explorer** mit der rechten Maustaste auf das iOS-Anwendungsprojekt klicken, um das Kontextmenü zu öffnen. Wählen Sie **Remotecomputer** und danach entweder **Mithilfe von Pushvorgang auf den Remotecomputer übertragen** oder **Inkrementeller Pushvorgang auf den Remotecomputer** aus, um Projektdateien von Visual Studio auf Ihren Mac zu kopieren.

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>„Mithilfe von Pull vom Remotecomputer übertragen“ und „Inkrementeller Pullvorgang vom Remotecomputer“
 Nachdem Sie Ihr Projekt in XCode geändert haben, verschieben Sie die Änderungen zurück zu Visual Studio, damit die Projekte synchronisiert bleiben.

 Sie können die Projektdateien von Ihrem Mac kopieren, indem Sie in Visual Studio im Fenster **Projektmappen-Explorer** mit der rechten Maustaste auf das iOS-Anwendungsprojekt klicken, um das Kontextmenü zu öffnen. Wählen Sie **Remotecomputer** und danach entweder **Mithilfe von Pull vom Remotecomputer übertragen** oder **Inkrementeller Pullvorgang vom Remotecomputer** aus, um Projektdateien von Ihrem Mac zu Visual Studio zu kopieren.

### <a name="clean-remote"></a>Remotecomputer bereinigen
 Mit dem Befehl „Remotecomputer bereinigen“ können Sie die Dateien im temporären Projektverzeichnis auf dem Remotecomputer löschen. Der Inhalt des Verzeichnisses, einschließlich aller Quelldateien oder Build-Produkte, wird auf dem Mac entfernt. Achten Sie darauf, dass Sie alle Änderungen, die Sie beibehalten möchten, mit Visual Studio synchronisiert haben, indem Sie den Befehl mithilfe von „Mithilfe von Pull vom Remotecomputer übertragen“ oder „Inkrementeller Pullvorgang vom Remotecomputer“ vor dem Befehl „Remotecomputer bereinigen“ verwenden.

 Sie können das temporäre Projektverzeichnis auf dem Mac bereinigen, indem Sie in Visual Studio im Fenster **Projektmappen-Explorer** mit der rechten Maustaste auf das iOS-Anwendungsprojekt klicken, um das Kontextmenü zu öffnen. Wählen Sie **Remotecomputer** und danach **Remotecomputer bereinigen** aus, um die Projektverzeichnisdateien von Ihrem Mac entfernen.