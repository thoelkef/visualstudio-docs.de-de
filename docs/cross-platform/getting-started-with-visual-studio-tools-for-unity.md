---
title: Erste Schritte mit Visual Studio-Tools für Unity | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: dbe546f43b0a66abc78b94480894b63dc4f5eafa
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283107"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Erste Schritte mit Visual Studio-Tools für Unity

## <a name="install-visual-studio"></a>Installieren von Visual Studio

### <a name="unity-bundled-installation"></a>Gebündelte Installation von Unity

Ab Unity 2018.1 ist Visual Studio der standardmäßige C#-Skript-Editor-IDE für Unity und im Unity-Download-Assistenten sowie im Unity Hub-Installationstool enthalten.

- Laden Sie Unity unter [store.unity.com](https://store.unity.com/) herunter.

Stellen Sie während der Installation sicher, dass Visual Studio in der Liste der Komponenten ausgewählt ist, die mit Unity installiert werden sollen:

#### <a name="unity-hub"></a>Unity Hub

![Installation von Unity Hub](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Unity-Download-Assistent

![Installation mit dem Unity-Download-Assistenten](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Suchen nach Updates für Visual Studio

Die Version von Visual Studio, die in der Installation von Unity enthalten ist, ist möglicherweise nicht aktuell. Es wird empfohlen, nach Updates zu suchen, damit Sie Zugriff auf die aktuellen Tools und Features haben.

- [Visual Studio aktualisieren](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Manuelle Installation

Wenn Sie Visual Studio 2017 bereits installiert haben, oder Sie die manuelle Installation bevorzugen, führen Sie den Visual Studio-Installer aus.

1. [Laden Sie den Visual Studio-Installer herunter](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio), oder öffnen Sie ihn, wenn er bereits installiert ist.

1. Klicken Sie für die gewünschte Version von Visual Studio auf **Ändern** (sofern bereits installiert) oder **Installieren** (für neue Installationen).

1. Scrollen Sie auf der Registerkarte **Workloads** zum Abschnitt **Mobil und Gaming**, und wählen Sie die Workload **Spieleentwicklung mit Unity** aus.

    ![Unity-Workload](media/vstu_unity-workload.png)

1. Klicken Sie in der unteren rechten Ecke des Installer-Fensters auf **Ändern** (sofern bereits installiert) oder **Installieren** (für neue Installationen).

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurieren von Unity für die Verwendung mit Visual Studio

Ab Unity 2018.1 sollte Visual Studio als Standard für den externen Skript-Editor in Unity festgelegt sein. Sie können dies bestätigen oder den externen Skript-Editor in eine spezifische Version von Visual Studio ändern:

1. Wählen Sie im Menü **Bearbeiten** die Option **Einstellungen...** aus.

  ![Auswählen von Einstellungen](media/vstu_unity-preferences.png)

1. Klicken Sie im Dialogfeld "Einstellungen" auf die Registerkarte **Externe Tools**.

1. Wählen Sie in der Dropdownliste **Externer Skript-Editor** Ihre gewünschte Version von Visual Studio aus, falls diese aufgelistet ist, oder andernfalls **Durchsuchen...**

  ![Auswählen von Visual Studio](media/vstu_unity-external-tools.png)

1. Navigieren Sie bei Auswahl von **Durchsuchen...** zum Verzeichnis **Common7/IDE** in Ihrem Visual Studio-Installationsverzeichnis, und wählen Sie **devenv.exe** aus. Klicken Sie dann auf **Öffnen**.

  ![Auswählen von „Öffnen“](media/vstu_browse-for-application.png)

1. Sobald Visual Studio in der Liste **Externer Skript-Editor** ausgewählt ist, überprüfen Sie, ob das Kontrollkästchen **Editoranhängen** aktiviert ist.

1. Schließen Sie das Dialogfeld **Einstellungen**, um die Konfiguration abzuschließen.

## <a name="support-for-older-versions"></a>Unterstützung älterer Versionen

 Laden Sie Visual Studio-Tools für Unity aus dem Visual Studio Marketplace herunter, und installieren Sie sie. Sie müssen das richtige Paket für Ihre Version von Visual Studio installieren.

- Für Visual Studio 2015 Community, Visual Studio 2015 Professional oder Visual Studio 2015 Enterprise:

   [Visual Studio 2015-Tools für Unity herunterladen](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio-Tools für Unity setzt Unity 5.2 und höher voraus sowie eine Version von Visual Studio, die Erweiterungen unterstützt (z.B. Visual Studio Community, Professional, Premium oder Enterprise). Überprüfen Sie, ob Visual Studio-Tools für Unity in Ihrer Installation von Unity aktiviert sind, indem Sie im **Hilfemenü** die Option **Informationen zu Unity** auswählen und unten links im Dialogfeld nach dem Text „Microsoft Visual Studio-Tools für Unity aktiviert“ suchen.
> ![Informationen zu Unity](media/vstu_about-unity.png)

## <a name="next-steps"></a>Nächste Schritte

 Informationen zum Arbeiten mit und Debuggen von Unity-Projekten in Visual Studio finden Sie unter [Verwenden von Visual Studio-Tools für Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
