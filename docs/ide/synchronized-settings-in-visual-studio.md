---
title: Synchronisieren der Einstellungen
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566786"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronisieren von Visual Studio-Einstellungen auf mehreren Computern

Wenn Sie sich auf mehreren Computern mit demselben Personalisierungskonto bei Visual Studio anmelden, können Ihre Einstellungen auf allen Computern synchronisiert werden.

## <a name="synchronized-settings"></a>Synchronisierte Einstellungen

Standardmäßig werden die folgenden Einstellungen synchronisiert:

- Entwicklungseinstellungen Sie wählen eine Reihe von Einstellungen aus, wenn Sie Visual Studio zum ersten Mal ausführen. Die Auswahl kann jedoch jederzeit geändert werden. Weitere Informationen finden Sie unter [Umgebungseinstellungen](../ide/environment-settings.md).

- Benutzerdefinierte Befehlsaliase. Weitere Informationen zur Definition von Befehlsaliasen finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).

- Benutzerdefinierte Fensterlayouts auf der Seite **Fenster** > **Fensterlayouts verwalten**

- Im Folgenden finden Sie die Optionen auf den Seiten **Extras** > **Optionen**:

  - Design und Einstellungen zur Schreibweise der Menüleiste auf der Optionsseite **Umgebung** > **Allgemein**

  - Alle Einstellungen auf der Optionsseite **Umgebung** > **Schriftarten und Farben**

  - Alle Tastenkombinationen auf der Optionsseite **Umgebung** > **Tastatur**

  - Alle Einstellungen auf der Optionsseite **Umgebung** > **Registerkarten und Fenster**

  - Alle Einstellungen auf der Optionsseite **Umgebung** > **Start**

  - Alle Einstellungen auf den Optionsseiten **Text-Editor**, etwa die [Einstellungen für das Codeformat](code-styles-and-code-cleanup.md).

  - Alle Einstellungen auf den Optionsseiten für den **XAML-Designer**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Deaktivieren der synchronisierten Einstellungen auf einem bestimmten Computer

Die synchronisierten Einstellungen für Visual Studio sind standardmäßig aktiviert. Sie können die synchronisierten Einstellungen auf einem Computer deaktivieren, indem Sie auf der Seite **Extras** > **Optionen** > **Umgebung** > **Konten** das Kontrollkästchen **Einstellungen geräteübergreifend synchronisieren, solange Sie bei Visual Studio angemeldet sind** deaktivieren.

Angenommen, Sie möchten, dass die Einstellungen von Visual Studio auf Computer „A“ nicht synchronisiert werden. So werden alle auf Computer „A“ vorgenommenen Änderungen weder auf Computer „B“ noch auf Computer „C“ angezeigt. Computer „B“ und Computer „C“ werden weiterhin miteinander synchronisiert, jedoch nicht mit Computer „A“.

> [!NOTE]
> Wenn Sie die Einstellungen nicht synchronisieren, indem Sie die Option auf der Seite **Extras** > **Optionen** > **Umgebung** > **Konten** deaktivieren, sind andere Versionen oder Editionen von Visual Studio, die auf dem gleichen Computer installiert sind, nicht betroffen. Diese parallelen Installationen von Visual Studio synchronisieren ihre Einstellungen weiterhin (außer, Sie deaktivieren die Option auch für jede einzelne Version von Visual Studio).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronisieren von Einstellungen mit allen Produkten und Editionen der Visual Studio-Familie

Einstellungen werden zwischen allen *parallel* installierten Versionen und Editionen von Visual Studio synchronisiert. Die Einstellungen werden ebenfalls in der gesamten Visual Studio-Produktfamilie synchronisiert, einschließlich Blend für Visual Studio. Ein einzelnes Produkt kann jedoch auch über eigene Einstellungen verfügen, die nicht mit Visual Studio geteilt werden. Beispielsweise werden für Blend für Visual Studio spezifische Einstellungen auf Computer „A“ nicht mit Visual Studio auf den Computern „A“ oder „B“ geteilt.

## <a name="side-by-side-synchronized-settings"></a>Parallel synchronisierte Einstellungen

::: moniker range="vs-2017"

Bestimmte Einstellungen wie das Layout des Toolfensters werden nicht zwischen verschiedenen parallelen Installationen von Visual Studio freigegeben. Die Datei *CurrentSettings.vssettings* unter *%userprofile%\Documents\Visual Studio 2017\Settings* befindet sich in einem installationsspezifischen Ordner, der *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings* ähnelt.

> [!NOTE]
> Führen Sie eine neue Installation durch, um die neuen installationsspezifischen Einstellungen zu verwenden. Wenn Sie eine vorhandene Visual Studio-Installation aktualisieren, verwendet sie den vorhandenen freigegebenen Speicherort.

Wenn Sie derzeit über Parallelinstallationen von Visual Studio verfügen und den neuen installationsspezifischen Speicherort für die Einstellungsdatei verwenden möchten, führen Sie die folgenden Schritte aus:

1. Upgrade auf Visual Studio 2017 Version 15.3 oder höher

2. Verwenden Sie den **Assistenten zum Importieren und Exportieren von Einstellungen**, um alle vorhandenen Einstellungen in einen Speicherort außerhalb des Ordners *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* zu exportieren.

3. Öffnen Sie die **Developer-Eingabeaufforderung für Visual Studio 2017**, und führen Sie `devenv /resetuserdata` aus.

1. Öffnen Sie Visual Studio, und importieren Sie die gespeicherten Einstellungen aus der exportierten Einstellungsdatei.

::: moniker-end

::: moniker range=">=vs-2019"

Bestimmte Einstellungen wie das Layout des Toolfensters werden nicht zwischen verschiedenen parallelen Installationen von Visual Studio freigegeben. Die Datei *CurrentSettings.vssettings* unter *%userprofile%\Documents\Visual Studio 2019\Settings* befindet sich in einem installationsspezifischen Ordner, der *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings* ähnelt.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Zurücksetzen synchronisierter Einstellungen

Melden Sie sich bei Visual Studio an, und klicken Sie dann auf **Extras** > **Einstellungen importieren/exportieren**, um den **Assistenten zum Importieren und Exportieren von Einstellungen** zu öffnen und alle Einstellungen auf die Standardeinstellung zurückzusetzen. Klicken Sie auf **Alle Einstellungen zurücksetzen**, und führen Sie dann die restlichen Schritte des Assistenten aus.

## <a name="see-also"></a>Weitere Informationen

- [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Umgebungseinstellungen](../ide/environment-settings.md)
- [Umgebung > Dialogfeld „Kontenoptionen“](reference/accounts-environment-options-dialog-box.md)
