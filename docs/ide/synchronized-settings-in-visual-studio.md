---
title: Synchronisieren der Einstellungen
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 633767e66a4b3d976999574c885a3e6f7a06ddcf
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766128"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronisieren von Visual Studio-Einstellungen auf mehreren Computern

Wenn Sie sich auf mehreren Computern mit demselben Personalisierungskonto bei Visual Studio anmelden, können Ihre Einstellungen auf allen Computern synchronisiert werden.

## <a name="synchronized-settings"></a>Synchronisierte Einstellungen

Standardmäßig werden die folgenden Einstellungen synchronisiert:

- Entwicklungseinstellungen Sie müssen eine Reihe von Einstellungen auswählen, wenn Sie Visual Studio zum ersten Mal ausführen. Die Auswahl kann jedoch jederzeit geändert werden. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

- Benutzerdefinierte Befehlsaliase. Weitere Informationen zur Definition von Befehlsaliasen finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).

- Benutzerdefinierte Fensterlayouts auf der Seite **Fenster** > **Fensterlayouts verwalten**

- Im Folgenden finden Sie die Optionen auf den Seiten **Extras** > **Optionen**:

   - Design und Einstellungen zur Schreibweise der Menüleiste auf der Optionsseite **Umgebung** > **Allgemein**

   - Alle Einstellungen auf der Optionsseite **Umgebung** > **Schriftarten und Farben**

   - Alle Tastenkombinationen auf der Optionsseite **Umgebung** > **Tastatur**

   - Alle Einstellungen auf der Optionsseite **Umgebung** > **Registerkarten und Fenster**

   - Alle Einstellungen auf der Optionsseite **Umgebung** > **Start**

   - Alle Einstellungen auf den Optionsseiten des **Text-Editors**

   - Alle Einstellungen auf den Optionsseiten für den **XAML-Designer**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Deaktivieren der synchronisierten Einstellungen auf einem bestimmten Computer

Die synchronisierten Einstellungen für Visual Studio sind standardmäßig aktiviert. Sie können die synchronisierten Einstellungen auf einem Computer deaktivieren, indem Sie auf der Seite **Extras** > **Optionen** > **Umgebung** > **Konten** das Kontrollkästchen **Einstellungen geräteübergreifend synchronisieren, solange Sie bei Visual Studio angemeldet sind** deaktivieren. Angenommen, Sie möchten, dass die Einstellungen von Visual Studio auf Computer „A“ nicht synchronisiert werden. So werden alle auf Computer „A“ vorgenommenen Änderungen weder auf Computer „B“ noch auf Computer „C“ angezeigt. Computer „B“ und Computer „C“ werden weiterhin miteinander synchronisiert, jedoch nicht mit Computer „A“.

## <a name="reset-settings"></a>Zurücksetzen von Einstellungen

Sie können alle Einstellungen für eine Sammlung von Standardeinstellungen zurücksetzen, indem Sie die folgenden Schritte ausführen:

1. Klicken Sie in Visual Studio auf **Extras** > **Einstellungen importieren/exportieren**, um den **Assistenten zum Importieren und Exportieren von Einstellungen** zu öffnen.

1. Klicken Sie im **Assistenten zum Importieren und Exportieren von Einstellungen** auf **Alle Einstellungen zurücksetzen** und dann auf **Weiter**.

   ![Assistent zum Importieren und Exportieren von Einstellungen in Visual Studio](media/reset-all-settings.png)

1. Klicken Sie auf der Seite **Aktuelle Einstellungen speichern** entweder auf **Ja** oder **Nein**, und klicken Sie dann auf **Weiter**.

1. Wählen Sie auf der Seite **Standardsammlung von Eigenschaften auswählen** eine Sammlung aus, und klicken Sie dann auf **Fertig stellen**.

   ![Sammlungen von Einstellungen in Visual Studio](media/settings-collections.png)

1. Klicken Sie auf der Seite **Zurücksetzungsvorgang abgeschlossen** auf **Schließen**.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronisieren von Einstellungen mit allen Produkten und Editionen der Visual Studio-Familie

Einstellungen können mit allen Editionen von Visual Studio synchronisiert werden, einschließlich der Community Edition. Einstellungen werden auch mit allen Produkten der Visual Studio-Familie synchronisiert. Jedes dieser Familienprodukte weist jedoch möglicherweise eigene Einstellungen auf, die nicht für Visual Studio freigegeben werden. Beispielsweise werden für ein Produkt spezifische Einstellungen auf Computer „A“ für ein anderes Produkt auf Computer „B“ freigegeben, jedoch nicht für Visual Studio auf Computer „A“ oder „B“.

## <a name="side-by-side-synchronized-settings"></a>Parallel synchronisierte Einstellungen

In Visual Studio 2017 Version 15.3 und höher werden bestimmte Einstellungen wie das Toolfensterlayout zwischen parallelen Installationen von Visual Studio 2017 nicht freigegeben. Die Datei *CurrentSettings.vssettings* unter *%userprofile%\Documents\Visual Studio 2017\Settings* befindet sich in einem installationsspezifischen Ordner, der *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings* ähnelt.

> [!NOTE]
> Führen Sie eine neue Installation durch, um die neuen installationsspezifischen Einstellungen zu verwenden. Wenn ein Upgrade einer vorhandenen Installation von Visual Studio 2017 auf das aktuellste Update durchgeführt wird, verwendet es den vorhandenen freigegebenen Speicherort.

Wenn Sie derzeit über Parallelinstallationen von Visual Studio 2017 verfügen und den neuen installationsspezifischen Speicherort für die Einstellungsdatei verwenden möchten, führen Sie die folgenden Schritte aus:

1. Upgrade auf Visual Studio 2017 Version 15.3 oder höher

1. Verwenden Sie den **Assistenten zum Importieren/Exportieren von Einstellungen**, um alle Ihre vorhandenen Einstellungen in einen Speicherort außerhalb des Ordners *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* zu exportieren.

1. Öffnen Sie die **Developer-Eingabeaufforderung für Visual Studio 2017** der aktualisierten Visual Studio-Installation, und führen Sie `devenv /resetuserdata` aus.

1. Starten Sie Visual Studio, und importieren Sie die gespeicherten Einstellungen aus der exportierten Einstellungsdatei.

## <a name="see-also"></a>Siehe auch

[Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
