---
title: Identifizieren und Anpassen von Tastenkombinationen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a2d6420abc9b9d70ce23c1dc8dc1aab5941119f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798986"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identifizieren und Anpassen von Tastenkombinationen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Tastenkombinationen für Visual Studio-Befehle nachschlagen, diese Tastenkombinationen anpassen und sie dann exportieren, damit andere Benutzer sie verwenden können. Viele Tastenkombinationen rufen immer dieselben Befehle auf, aber das Verhalten einer Tastenkombination kann auf der Grundlage von Bedingungen unterschiedlich sein, die von folgenden Fragen abhängen:

- Welche Standardumgebungseinstellungen wurde bei der erstmaligen Ausführung von Visual Studio ausgewählt (beispielsweise "Allgemeine Entwicklungseinstellungen" oder Visual C#)?

- Wurde das Verhalten der Tastenkombination angepasst?

- In welchem Kontext wird die Tastenkombination angewendet? Beispielsweise ruft die Taste F2 den Edit.EditCell-Befehl auf, wenn Sie den Einstellungs-Designer verwenden, aber den File.Rename-Befehl, wenn Sie mit Team Explorer arbeiten.

  Unabhängig von Einstellungen, Anpassungen und Kontext können Sie eine Tastenkombination im Dialogfeld **Optionen** immer nachschlagen und ändern. Sie finden unter [Standardtastenkombinationen für häufig verwendete Befehle](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) die Standardtastenkombinationen für viele Befehle, und unter [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md) die vollständige Liste aller Standardtastenkombinationen für „Allgemeine Entwicklungseinstellungen“.

  **Inhalt**

- [Nachschlagen einer Tastenkombination](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Anpassen einer Tastenkombination](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Freigeben benutzerdefinierter Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Wenn eine Tastenkombinationen einem Befehl im globalen Kontext und in keinem anderen zugewiesen ist, ruft diese Tastenkombination immer diesen Befehl auf. Aber eine Tastenkombination kann einem Befehl im globalen Kontext und einem anderen Befehl in einem speziellen Kontext zugewiesen werden. Wenn Sie eine solche Tastenkombination in dem speziellen Kontext verwenden, ruft sie den Befehl für diesen Kontext auf und nicht den Befehl für den globalen Kontext.

> [!NOTE]
>  Je nach Ihren Einstellungen und der Edition von Visual Studio ändern sich möglicherweise auch die Namen und Positionen von Menübefehlen oder die Optionen in Dialogfeldern. Dieses Thema bezieht sich auf **Allgemeine Entwicklungseinstellungen**.

##  <a name="bkmk_identify"></a> Nachschlagen einer Tastenkombination

1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.

2.  Erweitern Sie **Umgebung**, und klicken Sie dann auf **Tastatur**.

     ![Tastenkombinationen im Dialogfeld „Optionen“ anzeigen](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  Geben Sie in das Feld **Befehle mit folgendem Inhalt anzeigen** den gesamten Befehlsnamen ohne Leerzeichen ein.

     Beispielsweise können Sie Befehle für **solutionexplorer** suchen.

4.  Wählen Sie in der Liste den richtigen Befehl aus.

     Beispielsweise können Sie **View.SolutionExplorer** auswählen.

5.  Wenn dem Befehl eine Tastenkombination zugeordnet ist, wird sie in der Liste **Shortcut(s) for selected command** (Tastenkombination für ausgewählten Befehl) aufgeführt.

     ![Tastenkombination für einen bestimmten Befehl anzeigen](../ide/media/viewshortcut.png "TastenkombinationAnzeigen")

##  <a name="bkmk_assign"></a> Anpassen einer Tastenkombination

1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.

2.  Erweitern Sie den Ordner **Umgebung**, und klicken Sie dann auf **Tastatur**.

     ![Tastenkombinationen im Dialogfeld „Optionen“ anzeigen](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  Geben Sie in das Feld **Befehle mit folgendem Inhalt anzeigen** den gesamten Befehlsnamen ohne Leerzeichen ein.

     Beispielsweise können Sie Befehle für **solutionexplorer** suchen.

4.  Wählen Sie in der Liste den Befehl aus, dem Sie eine Tastenkombination zuweisen möchten.

5.  Wählen Sie in der Liste **Use new shortcut in** (Neue Tastenkombination verwenden in) den Funktionsbereich aus, in dem die Tastenkombination verwendet werden soll.

     Wählen Sie beispielsweise **Global** aus, wenn die Tastenkombination in allen Zusammenhängen funktionieren soll. Sie können jede Tastenkombination verwenden, die in keinem anderen Editor (als Global) zugeordnet ist. Andernfalls wird die Tastenkombination vom Editor überschrieben.

    > [!NOTE]
    >  Die folgenden Tasten können Sie nicht als Teil einer **globalen** Tastenkombination zuweisen: Drucken Sie Bildschirmnavigation/s-ABF, Rollen, Pause/Untbr, Registerkarte, FESTSTELLTASTE, INSERT-, Start, Ende, Bild-auf, Bild-ab, die Windows-Logo-Taste, Schlüssels der Anwendung, die Pfeiltasten oder EINGABETASTE; Num-Lock, löschen oder deaktivieren Sie auf der Zehnertastatur oder Strg + Alt + Entf.

6.  Geben Sie in das Feld **Press shortcut key(s)** (Tastenkombination drücken) die Tastenkombination ein, die Sie verwenden möchten.

    > [!NOTE]
    >  Sie können eine Tastenkombination erstellen, die einen Buchstaben mit der ALT-TASTE, der STRG-TASTE oder mit beiden kombiniert. Sie können auch eine Tastenkombination erstellen, welche die UMSCHALTTASTE und einen Buchstaben mit der ALT-TASTE, der STRG-TASTE oder mit beiden kombiniert.

     Wenn eine Tastenkombination bereits einem anderen Befehl zugeordnet ist, wird sie im Feld **Tastenkombination wird momentan verwendet von** angezeigt. In diesem Fall löschen Sie die Tastenkombination mit der RÜCKTASTE und versuchen es mit einer anderen Tastenkombination.

     ![Eine andere Tastenkombination für einen Befehl angeben](../ide/media/reassignshortcut.png "TastenkombinationNeuZuweisen")

7.  Klicken Sie auf **Zuweisen**.

    > [!NOTE]
    >  Wenn Sie eine andere Tastenkombination für einen Befehl angeben, klicken Sie auf die Schaltfläche **Zuweisen** und dann auf **Abbrechen**. Damit wird das Dialogfeld geschlossen, aber die Änderung bleibt bestehen.

##  <a name="bkmk_transfer"></a> Freigeben benutzerdefinierter Tastenkombinationen
 Sie können Ihre selbstdefinierten Tastenkombinationen freigeben, indem Sie sie in eine Datei exportieren und die Datei dann anderen Benutzern zur Verfügung stellen, sodass diese die Daten importieren können.

#### <a name="to-export-only-keyboard-shortcuts"></a>So exportieren Sie nur Tastenkombinationen

1.  Klicken Sie in der Menüleiste auf die Optionen **Extras** und dann auf **Einstellungen importieren und exportieren**.

2.  Klicken Sie auf **Ausgewählte Umgebungseinstellungen exportieren** und dann auf **Weiter**.

3.  Deaktivieren Sie unter **Welche Einstellungen sollen exportiert werden?** das Kontrollkästchen **Alle Einstellungen**, und erweitern Sie **Optionen** sowie **Umgebung**.

4.  Aktivieren Sie das Kontrollkästchen **Tastatur**, und klicken Sie dann auf **Weiter**.

     ![Nur angepasste Tastenkombinationen exportieren](../ide/media/exportshortcuts.png "TastenkombinationenExportieren")

5.  Übernehmen Sie in den Feldern **Geben Sie den Namen der Einstellungsdatei ein.** und **Einstellungsdatei in folgendem Verzeichnis speichern** entweder die Standardwerte, oder geben Sie andere Werte ein, und klicken Sie dann auf **Fertigstellen**.

     Standardmäßig werden die Tastenkombinationen in einer Datei im Ordner %USERPROFILE%\Dokumente\Visual Studio 2013\Settings gespeichert. Der Name der Datei entspricht dem Datum, an dem Sie die Einstellungen exportiert haben, und die Dateierweiterung ist ".vssettings".

#### <a name="to-import-only-keyboard-shortcuts"></a>So importieren Sie nur Tastenkombinationen

1.  Klicken Sie in der Menüleiste auf die Optionen **Extras** und dann auf **Einstellungen importieren und exportieren**.

2.  Klicken Sie auf das Optionsfeld **Ausgewählte Umgebungseinstellungen importieren** und dann auf **Weiter**.

3.  Klicken Sie auf das Optionsfeld **Nein, neue Einstellungen importieren und aktuelle Einstellungen überschreiben** und dann auf **Weiter**.

4.  Wählen Sie unter **Meine Einstellungen** die Datei mit den Tastenkombinationen aus, die Sie importieren möchten, oder klicken Sie auf **Durchsuchen**, um die gewünschte Datei zu suchen.

5.  Klicken Sie auf **Weiter**.

6.  Deaktivieren Sie unter **Welche Einstellungen sollen importiert werden?** das Kontrollkästchen **Alle Einstellungen**, und erweitern Sie dann **Optionen** sowie **Umgebung**.

7.  Aktivieren Sie das Kontrollkästchen **Tastatur**, und klicken Sie dann auf **Fertigstellen**.

     ![Nur angepasste Tastenkombinationen importieren](../ide/media/importshortcuts.png "TastenkombinationenImportieren")

## <a name="see-also"></a>Siehe auch
 [Barrierefreiheitsfeatures in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
