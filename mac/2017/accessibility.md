---
title: Zugriff
description: In diesem Artikel werden die Barrierefreiheitsfunktionen in Visual Studio für Mac eingeführt, und es wird erklärt, wie sie aktiviert werden können.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.topic: overview
ms.openlocfilehash: a2f151cbf593d2b8e26be7ac60eaf8ff3c687499
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938924"
---
# <a name="accessibility"></a>Zugriff

Neben den Barrierefreiheitsfunktionen und Hilfsprogrammen in macOS bietet Visual Studio für Mac folgende Features, um Personen mit Behinderungen den Zugang zu erleichtern:

- Vergrößern des Texts in Lösungspads und Editor-Pads
- Textgrößenoptionen in den Editoren
- Anpassen der Farbe in den Editoren
- Anpassen von Tastenkombinationen
- Codevervollständigung für Methoden und Parameter

Weitere Informationen zu Barrierefreiheitsfunktionen in macOS finden Sie auf der [Website von Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Verwenden von Barrierefreiheitsfunktionen in Visual Studio für Mac

Die Barrierefreiheitsfunktionen in Visual Studio für Mac sind standardmäßig deaktiviert. Führen Sie folgende Schritte aus, um sie zu aktivieren:

1. Wechseln Sie zu **Visual Studio > Einstellungen > Weiter > Barrierefreiheit**.

2. Aktivieren Sie das Kontrollkästchen **Barrierefreiheit aktivieren**, wie im folgenden Diagramm gezeigt:

    ![Kontrollkästchen „Barrierefreiheit aktivieren“](media/accessibility-image1.png)

3. Klicken Sie auf die Schaltfläche **Visual Studio neu starten**, um die Barrierefreiheitsfunktionen zu aktivieren.

Alternativ dazu können Sie die Barrierefreiheitsfunktionen über die Befehlszeile aktivieren. Geben Sie im Terminal folgenden Befehl ein:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Nach dem Aktivieren der Barrierefreiheit müssen Sie Visual Studio neu starten.

## <a name="how-to-use-keyboard-navigation"></a>Vorgehensweise: Verwenden der Tastaturnavigation

Die Tastaturnavigation kann aktiviert werden, indem unter **Systemeinstellungen > Tastatur > Kurzbefehle** die Tastatursteuerung auf die Option **Alle Steuerungen** festgelegt wird:

![Systemeinstellungen in macOS](media/accessibility-image2.png)

Durch Festlegen der Tastatursteuerung wird das Fokusrechteck aktiviert. Sie können Steuerelemente folgendermaßen auswählen:

- Drücken der TABULATORTASTE, um vorwärts durch Steuerelemente zu navigieren
- Drücken der UMSCHALTTASTE + TABULATORTASTE, um rückwärts durch Steuerelemente zu navigieren
- Drücken der Pfeiltasten, um in Richtung der Pfeile zwischen Steuerelementen zu navigieren

Durch Drücken der Leertaste wird das Steuerelement mit dem Fokus aktiviert.

## <a name="how-to-enable-and-use-voice-over"></a>Vorgehensweise: Aktivieren und Verwenden von VoiceOver

Aktivieren oder deaktivieren Sie VoiceOver, indem Sie **BEFEHLSTASTE + F5** drücken.

Um zwischen VoiceOver-Befehlen der Benutzeroberfläche zu navigieren, verwenden Sie folgende Befehle:

- Bewegen des VoiceOver-Cursors zwischen Steuerelementen: **STRG + ALT + NACH-LINKS-TASTE/NACH-RECHTS-TASTE**

   VoiceOver liest die Namen der Steuerelemente sowie einige Informationen und mögliche Aktionen vor.

- Geben Sie Gruppen und Steuerelemente ein (z. B. Lösungspad, Toolbox und andere Pads): **STRG + ALT + UMSCHALT + NACH-UNTEN-TASTE**

   Wenn Sie sich innerhalb eines Steuerelements befinden, können Sie **STRG + ALT + Pfeiltasten** verwenden, um darin zu navigieren.

Allgemeine Informationen zur Verwendung von VoiceOver in macOS finden Sie in folgenden Leitfäden:

- [VoiceOver-Einführungshandbuch](https://help.apple.com/voiceover/info/guide/10.12/)
- [VoiceOver Commands in macOS](https://lab.dotjay.com/notes/voiceover-commands/) (VoiceOver-Befehle in macOS)

## <a name="see-also"></a>Siehe auch

- [Barrierefreiheitsfunktionen in Visual Studio (unter Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)