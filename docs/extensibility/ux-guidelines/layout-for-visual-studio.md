---
title: Layout für Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dc9c53055c31e8cfbedb089b48eda4274fe8b9a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683401"
---
# <a name="layout-for-visual-studio"></a>Layout für Visual Studio
Die meisten Visual Studio-Dialogfelder sind [Hilfsprogramm Dialogfeldlayout](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), die der Unthemed sind, führen Sie Standard-Dialogfelder [Windows Desktop Dialogfeld Layout Prinzipien](/windows/desktop/uxguide/win-dialog-box). Wie Visual Studio verschoben wird, um die Benutzeroberfläche zu aktualisieren, müssen einige der bekannteren Dialoge ein neues Design, das sie als Produkt – beim Definieren von Umgebungen herstellt. Diese [Dialogfeldlayout](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) Design Darstellung aufweisen.

##  <a name="BKMK_UtilityDialogLayout"></a> Hilfsprogramm Dialogfeldlayout

-   Alle Steuerelemente in einem Dialogfeld Hilfsprogramm sollten beginnen am oben links und nach unten übertragen.

-   Nie Zentrieren von Steuerelementen in einem Dialogfeld, um eine große Fläche auszufüllen.

-   Verwenden Sie die Umgebungsschriftart verwendet für alle den Text des Dialogfelds an. Wenn Sie eine visual-Spezifikation zu schreiben, geben Sie die Umgebungsschriftart verwendet anstelle einer bestimmten Schriftart und Größe. Finden Sie unter [die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

-   Verwenden Sie konsistente Steuerung Abstand und die Platzierung, um das Ziel für die Qualität in handwerkliches können zu unterstützen.

-   Dialoge können aus einer größeren Anzahl von Steuerelementen, einem eindeutigen Juxtaposition Steuerelemente oder beides komplexer. Können Sie für diese komplexen Situationen ausreichend Abstand zwischen Steuerelement Gruppierungen, Benutzern einen logischen Ablauf zu analysieren.

### <a name="utility-dialog-layout-examples"></a>Beispiele für die Utility-Dialogfeld-layout
 Alle Dimensionen werden als Pixel ausgedrückt.

 ![Dialogfeldabstände für Beschriftungen über Steuerelementen](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-A_UtilitySpacingAbove")

 **Abbildung 08.01-a: Abstand von Richtlinien für das Hilfsprogramm-Dialogfelder mit Beschriftungen über Steuerelementen**

 ![Dialogfeldabstände für Beschriftungen links neben Steuerelementen](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-B_UtilitySpacingLeft")

 **Abbildung 08.01-b: Abstand von Richtlinien für das Hilfsprogramm Dialogfelder mit Bezeichnungen auf der linken Seite von Steuerelementen**

### <a name="layout-details"></a>Layoutdetails

#### <a name="margins"></a>Seitenränder

-   Alle Dialogfelder müssen einen 12-Pixel-Rahmen um alle Ränder.

-   Ränder, innerhalb einer Gruppe sollte 9 Pixel vom Rand des Frames.

-   Ränder, innerhalb eines Registerkarten-Steuerelements sollte 6 Pixel von der Kante des Registersteuerelements sein.

#### <a name="command-buttons"></a>Befehlsschaltflächen

- Befehlsschaltflächen, die für die Dialogfeldrahmen, nicht auf den Inhalt verwendet werden. Sie sollte sollten unten rechts angeordnet werden und genügend Leerzeichen-Variable aus, um die Schaltflächen klar getrennt festgelegt.

- Wenn es horizontale Schaltflächen, die im Dialogfeld ausgeführt werden, ist die Konfiguration der alternativen Befehl Schaltfläche einem vertikalen Stapel auf der oberen rechten Ecke. Finden Sie unter [inneren Befehlsschaltflächen](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) unten.

- Der Speicherplatz auf der linken Seite der Befehlsschaltflächen (unteren linken/Mitte des Dialogfelds), wird als Teil vom Band "-" der Vorgang Dialogfeldsteuerelemente betrachtet. Das einzige, das in diesen Speicherplatz den Eindringen sollte, ist eine Hilfe-Link, der auf die gesamte Aufgabe oder Dialogfeld relevant ist.

- Befehlsschaltflächen müssen es sich um 75 x 23 Pixel sein.

- Befehlsschaltflächen sollte 6 Pixel auseinander liegen.

  ![Grundlegende Ausrichtung](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-C_ButtonAlign")

  **Abbildung 08.01 c: Grundlegende Ausrichtung**

#### <a name="labels"></a>Bezeichnungen

-   Linksbündig alle Bezeichnungen.

-   Für Bezeichnungen, die über ein Steuerelement befinden, sollten sie linksbündig genau mit dem Steuerelement darunter und am Ende die Bezeichnung muss 5 Pixel oberhalb des oberen anderer Steuerelemente (z. B. ein Kombinationsfeld).

-   Für Bezeichnungen, die sich auf der linken Seite der Steuerelemente befinden, ist die minimale Breite zwischen dem Bezeichnungsfeld und das Eingabesteuerelement 10 Pixel. Zum Ausrichten von den Inhalt der Textfelder, Kombinationsfelder oder andere Steuerelemente, sollte eine implizite Spalte für die zweite hergestellt werden.

-   Bezeichnungen großgeschrieben werden, gefolgt von einem Doppelpunkt. Finden Sie unter [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Abstand zwischen Steuerelementen
 Stapeln Sie Steuerelemente relativ. Es gibt keine absolute Richtlinie für den Abstand zwischen Steuerelementen der gestapelt. Die Dichtigkeit zwischen den Steuerelementen kann leicht zwischen Dialogfelder variieren. Der empfohlene Abstand wird 20 Pixel für vertikale Steuerelement bezeichnungs-Paaren und 9 Pixel für die horizontale Steuerelement bezeichnungs-Paaren. Die minimale Steuerelement Abstand für horizontale Paare ist 6 Pixel.

 ![Abstand zwischen Steuerelementen empfohlen](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-D_ControlDistance")

 **Abbildung 08.01-d: Empfehlungen für den Abstand zwischen Steuerelementen**

#### <a name="control-indentation"></a>Einzug des Steuerelements
 Bei Steuerelementen geschachtelten richten Sie innere Steuerelemente horizontal mit dem linken Rand des Steuerelements oben in der Regel die Bezeichnung aus.

 ![Ausrichtung des Steuerelements verschachtelt](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-E_ControlAlign")

 **Abbildung 08.01-e: Ausrichtung von verschachtelten Steuerelementen**

#### <a name="control-width"></a>Breite des Steuerelements
 Die Breite eines Textfelds oder andere Steuerelemente mit ähnlichen sollte nicht länger als die durchschnittliche Eingabe für das Feld sein. Die durchschnittliche englischen wörtertrennung ist fünf Zeichen. Beispielsweise muss ein Textfeld, das einen lange Pfadnamen erfordert, solange die horizontalen Layout ermöglicht, während Sie eine Dropdownliste aus, for Plattformnamen nur eine Länge sein sollte, die für den längsten Eintrag ermöglicht.

#### <a name="helper-text"></a>Hilfstext

-   Ein Dialogfeld kann Hilfetext anzeigen, die Weitere Informationen zu den Zweck des Dialogfelds enthält. Diese kann in der Regel befindet sich am oberen Rand und 1 bis 2 Sätze.

-   Die Länge der Zeile muss eine vertraut Breite für einen Benutzer zu analysieren und zu lesen. Ein Mittel Dialogfeld sollte nicht mehr als 550 Pixel breit sein.

####  <a name="BKMK_InteriorCommandButtons"></a> Innere Befehlsschaltflächen
 In komplexeren Dialogfeldern möglicherweise ein internes Steuerelement einen eigenen zugehörigen Schaltflächen, beeinflussen können, wo sich das Dialogfeld "Commit-Schaltflächen befinden.

- Verwenden, die eine vertikale Ausrichtung (Spalte) des inneren beim Schaltflächen **OK**/**Abbrechen** horizontal in der unteren rechten Ecke ausgerichtet sind.

- Verwenden, die eine horizontale Ausrichtung (Zeile) des inneren beim Schaltflächen **OK**/**Abbrechen** sind in der oberen rechten Ecke, vertikal ausgerichtet. Dies ist weniger häufig.

- Größe der Schaltfläche "inneren" sollten als Ziel die Standardschaltfläche Größe von 75 x 23 Pixel, die Größe des übereinstimmenden **OK**/**Abbrechen** Schaltflächen, wenn möglich. Wenn eine Beschriftung der Schaltfläche auf die Schaltfläche die Standardschaltfläche überschreiten vornimmt, sollten die anderen Schaltflächen in diesem Satz mit größeren Größe ausgerichtet sein.

  ![Horizontale OK und Abbrechen Schaltflächen](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-F_HorizOKCan")

  **Abbildung 08.01-f: Vertikale inneren Schaltflächen mit horizontalen OK/Abbrechen**

  ![Vertikale OK und Abbrechen Schaltflächen](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-G_VertOKCan")

  **Abbildung 08.01-g: Horizontale inneren Schaltflächen mit vertikalen OK/Abbrechen**

#### <a name="browse-button"></a>[Durchsuchen...] Schaltfläche "
 **[Durchsuchen...]**  Schaltflächen, die ein Textfeld zu folgen sollten schreiben Sie "Durchsuchen..." vollständig einschließlich der mit den Auslassungspunkten. Wenn der Speicherplatz ist eng gesteckt, oder es sind mehrere **[durchsuchen...]**  Schaltflächen auf dem Bildschirm die Schaltfläche mit den können reduziert werden, um nur mit den Auslassungspunkten.

##  <a name="BKMK_ThemedDialogLayout"></a> Dialogfeldlayout
 Design Dialogfelder in Visual Studio haben die Darstellung ein heller und bieten mehr Leerzeichen. Typografie bietet mehr Bedeutung und Interesse sind, bietet weitere open Zeilenabstand und eine Variante der Schriftgrade und Gewichtungen. Wo möglich, Chrome und Titelleisten verringert oder entfernt wurden. Das Layout dieser Dialogfelder sollten dieses grundlegende Muster befolgen:

1.  Der Hintergrund des Dialogfelds ist weiß.

2.  In einem mittleren Wert grau ist ein 1-Pixel-Regel-Rahmen vorhanden.

3.  Der Dialogfeldtitel nicht mehr befindet sich in der Titelleiste, bietet jedoch interessanter und geht es in eine größere Größe. (Finden Sie im Abschnitt Größe Schriftart [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4.  Bezeichnungen, die zusammen mit zusätzlichen Text, z. B. eine Beschreibung, sollte **Umgebungsschriftart + Fettformatierung**.

5.  Innere Spalten sind durch eine Regel 1 Pixel hellgrau getrennt.

6.  Standardmäßig Links haben keinen Unterstrich. Haben eine Textfarbe ändern und den Unterstrich, Hover- und den gedrückten Zustand.

7.  Übernehmen Sie die Schaltflächen (z. B. **OK**/**Abbrechen**) befinden sich in der unteren rechten Ecke.

### <a name="themed-dialog-layout-examples"></a>Beispiele für die Design-Dialogfeld-layout
 ![Dialogfeldlayout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-H_ThemedDialog")

 **Abbildung 08.01-h: Design-Dialogfeld**

 ![Dialogfeldabmessungen](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-I_ThemedDialogDimensions")

 **Abbildung 08.01-i: Dialogfeld "Design" - Dimensionen**

 ![Dialogfeldschriftarten](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-J_ThemedDialogFonts")

 **Abbildung 08.01-j: Dialogfeld "Design" - Schriftarten**

 ![Dialogfeldfarben](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-K_ThemedDialogColors")

 **Abbildung 08.01-k: Dialogfeld "Design" - Farben**

## <a name="see-also"></a>Siehe auch
- [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Steuerelemente (Windows)](/windows/desktop/uxguide/controls)
- [Dialogfelder (Windows)](/windows/desktop/uxguide/win-dialog-box)