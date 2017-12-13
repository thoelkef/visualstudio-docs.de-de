---
title: "Installieren von Visual Studio für Mac | Microsoft-Dokumentation"
description: "Anweisungen zum Installieren von Visual Studio für Mac und zusätzlicher erforderlichen Komponenten für die plattformübergreifende Entwicklung"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 25d3227bcf8a18a2fc6ba68c194e9cac75b2e919
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Einrichten und Installieren von Visual Studio für Mac

## <a name="setup"></a>Setup

Um mit der Entwicklung nativer, plattformübergreifender Apps zu beginnen, wenn Sie Visual Studio für Mac heruntergeladen haben, müssen Sie vorher verschiedene Installationen und Setups durchführen.

Damit Visual Studio unter iOS funktioniert, benötigen Sie Folgendes:

* einen Mac mit macOS Sierra 10.12 oder höher
* Xcode 8.3
* eine Apple-ID Erstellen Sie eine kostenlose Apple-ID unter https://appleid.apple.com, wenn Sie noch keine besitzen. Dies ist für die Installation von und die Anmeldung bei Xcode erforderlich.

## <a name="install"></a>Installieren

1. Laden Sie Visual Studio für Mac unter [https://www.visualstudio.com/](https://www.visualstudio.com/) herunter.

2. Wenn das Installer-Paket heruntergeladen wurde, klicken Sie auf die Datei **VisualStudioInstaller.dmg**, um den Installer einzubinden, und führen Sie in dann aus, indem Sie das Logo doppelklicken, wie in der folgenden Abbildung veranschaulicht:

  ![Dialogfeld „Installer“](media/installer-image1.png)

3. Möglicherweise wird ein Warnungsdialogfeld wie das folgende angezeigt. Klicken Sie in einem solchen Fall auf **Öffnen**:

  ![Warnungsdialogfeld](media/installer-image2.png)

4. Der Installer prüft Ihr System, um zu bestimmen, welche Komponenten installiert oder aktualisiert werden müssen:

  ![Bewerten Ihres Systems](media/installer-image3.png)

5. Dann wird ein Warnungsdialogfeld angezeigt, über das Sie aufgefordert werden, die Datenschutz- und Lizenzbedingungen zu akzeptieren. Klicken Sie auf die Schaltfläche **Weiter**, um die Bedingungen zu akzeptieren.

  ![Dialogfeld „Lizenz“](media/installer-image4.png)

6. Der Installer zeigt eine Liste der erforderlichen Komponenten an, die fehlen und die heruntergeladen und installiert werden müssen. Wählen Sie hier die Produkte aus, die Sie herunterladen möchten:

  ![Auswählen von Elementen](media/installer-image5.png)

  Auf dieser Installationsseite wird die Version und Größe jeder einzelnen Komponente angezeigt. Sie können auf jede Komponente klicken, um eine Liste mit deren Abhängigkeiten (für Android), zusätzliche heruntergeladenen Pakete (für .NET Core) oder zusätzliche erforderliche Anwendungen (für iOS und macOS) anzuzeigen.

  ![Zusätzliche Abhängigkeiten von Android](media/installer-image6.png)

7. Sobald Sie mit Ihrer Auswahl zufrieden sind, klicken Sie auf die Schaltfläche **Installieren und aktualisieren**, um mit dem Installationsprozess zu beginnen.

8. Der Installer startet mit dem Download- und Installationsprozess der ausgewählten Elemente:

  ![Starten der Installation](media/installer-image7.png)

  ![Herunterladen von Xamarin.Mac](media/installer-image8.png)

  ![Fertigstellen der Installation](media/installer-image9.png)

9. Möglicherweise werden Sie dazu aufgefordert, die erforderlichen Berechtigungen für einzelne Komponenten zu erhöhen, die zum Abschluss der Installation erforderlich sind. Geben Sie hier Ihre Administratoranmeldeinformationen ein, um mit dem Installationsprozess fortzufahren:

  ![Eingeben der Berechtigungen zum Fortfahren des Installers](media/installer-image10.png)

10. Sobald die Installation erfolgreich abgeschlossen wurde, können Sie mit der Entwicklung von Apps in Visual Studio beginnen, indem Sie auf **Start** drücken.

  ![Öffnen Sie Visual Studio.](media/installer-image11.png)

> [!NOTE]
Wenn Sie sich gegen die Installation einer Plattform oder eines Tools während der ursprünglichen Installation entschieden haben (indem Sie die Auswahl in Schritt 6 gelöscht haben), müssen Sie den [Installer](https://www.visualstudio.com/vs/) erneut ausführen, wenn Sie die Komponenten später hinzufügen möchten.

## <a name="manual-installation"></a>Manuelle Installation

Wenn die gesamte Installation oder auch nur eine Komponente der Installation fehlschlägt, können Sie das Problem möglicherweise über eine manuelle Installation lösen. Führen Sie die folgenden Schritte aus, um die erforderlichen Komponenten abzurufen und sie herunterzuladen:

1. Wechseln Sie in der zweiten Anzeige des Visual Studio-Installers auf die Menüleiste, und klicken Sie auf **View Manual Installation Instructions** („Anweisungen für die manuelle Installation anzeigen“):

    ![Option „Menüelement für die manuelle Installation anzeigen“](media/installer-image12.png)

2. Befolgen Sie die Anweisungen zum manuellen Herunterladen und Installieren der Komponenten:

  ![Dialogfeld „Manuelle Installation“](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installieren von Visual Studio für Mac hinter einer Firewall oder einem Proxyserver

Für die Installation von Visual Studio für Mac hinter einer Firewall müssen bestimmte Endpunkte zugänglich gemacht werden, um die Downloads der erforderlichen Tools und Updates für Ihre Software zuzulassen.

Konfigurieren Sie Ihr Netzwerk, damit der Zugriff auf die folgenden Speicherorte gewährt wird:

* [Visual Studio-Endpunkte](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)