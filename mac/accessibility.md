---
title: Zugriff
description: In diesem Artikel werden die Barrierefreiheitsfunktionen in Visual Studio für Mac eingeführt, und es wird erklärt, wie sie aktiviert werden können.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 0ee6ffc7bd1567a86bc361f55e00c52ccecddd61
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824445"
---
# <a name="accessibility"></a>Zugriff

Visual Studio für Mac bietet die folgenden Barrierefreiheitsfunktionen, um Personen mit Behinderungen den Zugang zu erleichtern:

- Vergrößern des Texts in Lösungspads und Editor-Pads
- Textgrößenoptionen in den Editoren
- Anpassen der Farbe in den Editoren
- Tastaturnavigation
- Anpassen von Tastenkombinationen
- Codevervollständigung für Methoden und Parameter

Zusätzlich zu diesen Features bietet Apple eine Reihe von Tools, die Benutzer mit besonderen Anforderungen unterstützen, wie VoiceOver und Diktat.

Weitere Informationen zu Barrierefreiheitsfunktionen in macOS finden Sie auf der [Website von Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Aktivieren von macOS-Hilfstechnologien in Visual Studio für Mac

Die Unterstützung von Visual Studio für Mac für macOS-Hilfstechnologien ist standardmäßig deaktiviert. Um sie zu aktivieren, gehen Sie folgendermaßen vor:

1. Wechseln Sie zu **Visual Studio (Menü) > Einstellungen > Weiter > Barrierefreiheit**.

2. Aktivieren Sie das Kontrollkästchen **Barrierefreiheit aktivieren**:

   ![Einstellungen „Barrierefreiheit aktivieren“](media/accessibility-preferences.png)

3. Wählen Sie die Schaltfläche **Visual Studio neu starten**, um Visual Studio neu zu starten und die Unterstützung für Apple-Hilfstechnologien zu aktivieren.

## <a name="how-to-use-keyboard-navigation"></a>Vorgehensweise: Verwenden der Tastaturnavigation

Die Unterstützung der Tastaturnavigation ist direkt in macOS integriert, aber um die umfassendste Erfahrung zu haben, sollten Sie macOS so einstellen, dass es durch **Alle Steuerelemente** navigiert:

![Systemeinstellungen – Tastatur – Alle Steuerelemente](media/accessibility-preferences-keyboard.png)

Wenn Sie **Vollständiger Tastaturzugriff** auf **Alle Steuerelemente** festlegen, können Sie durch alle Steuerelemente in einem Fenster oder Dialogfenster navigieren. Sie können Steuerelemente folgendermaßen auswählen:

- Drücken der TABULATORTASTE, um vorwärts durch Steuerelemente zu navigieren
- Drücken der UMSCHALTTASTE + TABULATORTASTE, um rückwärts durch Steuerelemente zu navigieren
- Drücken der Pfeiltasten, um in Richtung der Pfeile zwischen Steuerelementen zu navigieren
- Registerkarte „Steuerelement“ aus den Textbereichsfeldern
- Durch Drücken der Leertaste wird das Steuerelement aktiviert, auf dem momentan der Fokus liegt.

## <a name="how-to-enable-and-use-voiceover"></a>Vorgehensweise: Aktivieren und Verwenden von VoiceOver

Zu Aktivieren oder Deaktivieren von VoiceOver, drücken Sie auf **&#8984; + F5**.

VoiceOver-Befehle werden in diesem Handbuch als **VO+*Taste*** angezeigt, wobei **VO** sich auf den Modifizierer bezieht, der im **VoiceOver -Hilfsprogramm** eingestellt ist. Standardmäßig wird **Strg + Alt** als Modifizierer verwendet. Abhängig von Ihrem VoiceOver-Modifizierer bedeutet **VO + M** beispielsweise **Strg + Alt + M**. Aus Gründen der Übersichtlichkeit werden Pfeiltasten als **Links** und **Rechts** usw. bezeichnet.

Verwenden Sie die folgenden Tastenkombinationen, um durch die Benutzeroberfläche von Visual Studio für Mac zu navigieren:

- **VO + Rechts/Links**: Navigieren zwischen den Elementen der Benutzeroberfläche
  - VoiceOver sagt die Bezeichnung und die Art des Steuerelements an und erklärt die Interaktion mit ihm.
- **VO + UMSCHALT + Nach unten / Nach oben**: Schritt in Element/aus Element
  - Sobald Sie sich in einem Element befinden, können Sie mit **VO + Links/Rechts** durch die Elemente innerhalb dieses Elements navigieren.
- **VO + Leertaste**: Auswählen/Interagieren mit einem Steuerelement
- **VO + M**: Interagieren mit der Visual Studio für Mac-Menüleiste

Weitere Informationen zur Verwendung von VoiceOver und eine umfassende Liste von Befehlen finden Sie in den folgenden Anleitungen:

- [Apple VoiceOver – Erste Schritte](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [VoiceOver Commands in macOS](http://lab.dotjay.com/notes/voiceover-commands/) (VoiceOver-Befehle in macOS)

## <a name="see-also"></a>Siehe auch

- [Barrierefreiheitsfunktionen in Visual Studio (unter Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
