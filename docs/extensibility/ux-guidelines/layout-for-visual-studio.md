---
title: Layout für Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698396"
---
# <a name="layout-for-visual-studio"></a>Layout für Visual Studio
Die meisten Visual Studio-Dialogfelder sind [Dienstprogrammdialoglayout](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), d. h. die nicht themed-Dialogfelder, die den standardmäßigen [Windows Desktop-Dialoglayoutprinzipien](/windows/desktop/uxguide/win-dialog-box)folgen. Während Visual Studio seine Benutzeroberfläche aktualisieren wird, verfügen einige der prominenteren Dialogfelder über einen neuen Entwurf, der sie als produktdefinierende Benutzeroberflächen festlegt. Diese [Themendialoglayout haben](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) eine thematische Darstellung.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Utility-Dialoglayout

- Alle Steuerelemente innerhalb eines Dienstprogrammdialogs sollten oben/links beginnen und nach unten fließen.

- Konzentrieren Sie sich niemals auf Steuerelemente in einem Dialogfeld, um einen großen Bereich auszufüllen.

- Verwenden Sie die Umgebungsschriftart für den gesamten Dialogtext. Geben Sie beim Schreiben einer visuellen Spezifikation die Umgebungsschriftart an, anstatt eine bestimmte Schriftart und Größe auszuwählen. Siehe [Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Verwenden Sie konsistente Regelabstände und Platzierungen, um das Ziel der Qualität in der Handwerkskunst zu unterstützen.

- Dialoge können durch eine größere Anzahl von Steuerelementen, eine eindeutige Gegenüberstellung von Steuerelementen oder beides komplexer werden. Lassen Sie für diese komplexen Situationen ausreichend Platz zwischen Steuerelementgruppierungen zu, um dem Benutzer einen logischen Ablauf zum Analysieren zu geben.

### <a name="utility-dialog-layout-examples"></a>Beispiel für Das Dienstprogramm-Dialoglayout
 Alle Dimensionen werden als Pixel ausgedrückt.

 ![Dialogfeldabstände für Beschriftungen über Steuerelementen](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Abbildung 08.01-a: Abstandsrichtlinien für Dienstprogrammdialogfelder mit Beschriftungen über Steuerelementen**

 ![Dialogfeldabstände für Beschriftungen links neben Steuerelementen](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Abbildung 08.01-b: Abstandsrichtlinien für Dienstprogrammdialoge mit Beschriftungen links von Steuerelementen**

### <a name="layout-details"></a>Layoutdetails

#### <a name="margins"></a>Ränder

- Alle Dialoge sollten einen 12-Pixel-Rahmen um alle Kanten haben.

- Ränder innerhalb eines Gruppenrahmens sollten 9 Pixel vom Rand des Rahmens entfernt sein.

- Die Ränder innerhalb eines Registerkartensteuerelements sollten 6 Pixel vom Rand des Registerkartensteuerelements entfernt sein.

#### <a name="command-buttons"></a>Befehlsschaltflächen

- Befehlsschaltflächen funktionieren auf dem Dialograhmen, nicht auf dem Inhalt. Sie sollten unten rechts platziert werden und über genügend variablen Platz verfügen, um die Tasten deutlich voneinander zu trennen.

- Wenn horizontale Schaltflächen innerhalb des Dialogfelds ausgeführt werden, ist die alternative Befehlsschaltflächenkonfiguration ein vertikaler Stapel oben rechts. Siehe [Innenbefehlsschaltflächen](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) unten.

- Der Abstand links neben den Befehlsschaltflächen (unten links/Mitte des Dialogs) wird als Teil des "Band" der Dialogbetriebssteuerungen betrachtet. Das einzige, was in diesen Bereich eindringen sollte, ist ein Hilfelink, der für die gesamte Aufgabe oder das Dialogfeld relevant ist.

- Befehlsschaltflächen sollten 75x23 Pixel groß sein.

- Befehlsschaltflächen sollten 6 Pixel voneinander entfernt sein.

  ![Grundlegende Ausrichtung von Steuerelementen](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Abbildung 08.01-c: Grundlegende Tastenausrichtung**

#### <a name="labels"></a>Bezeichnungen

- Alle Beschriftungen links ausrichten.

- Bei Beschriftungen, die sich über einem Steuerelement befinden, sollten sie genau mit dem Steuerelement darunter links ausgerichtet sein, und der Boden der Beschriftung sollte 5 Pixel über dem oberen Rand des anderen Steuerelements liegen (z. B. ein Kombinationsfeld).

- Bei Beschriftungen, die sich links neben Steuerelementen erarbeiten, beträgt die Mindestbreite zwischen der Beschriftung und dem Eingabesteuerelement 10 Pixel. Eine implizite zweite Spalte sollte zum Ausrichten der Textfelder, Kombinationsfelder oder anderer Steuerelemente eingerichtet werden.

- Beschriftungen sind Satzfall und werden von einem Doppelpunkt gefolgt. Siehe [Textstil](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Abstand zwischen Steuerelementen
 Stack-Steuerelemente vernünftig. Es gibt keine absolute Richtlinie für den Abstand zwischen gestapelten Steuerelementen. Die Dichtheit zwischen den Steuerelementen kann zwischen den Dialogen leicht variieren. Der empfohlene Abstand beträgt 20 Pixel für vertikale Steuerelement-/Beschriftungspaare und 9 Pixel für horizontale Steuerelement-/Beschriftungspaare. Der minimale Steuerabstand für horizontale Paare beträgt 6 Pixel.

 ![Empfohlener Abstand zwischen Steuerelementen](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Abbildung 08.01-d: Empfehlungen für den Abstand zwischen den Kontrollen**

#### <a name="control-indentation"></a>Kontrolleinzug
 Wenn Steuerelemente verschachtelt sind, richten Sie innere Steuerelemente horizontal am linken Rand des Steuerelements oben aus, in der Regel die Beschriftung.

 ![Ausrichtung von verschachtelten Steuerelementen](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Abbildung 08.01-e: Verschachtelte Steuerungsausrichtung**

#### <a name="control-width"></a>Steuerbreite
 Die Breite eines Textfelds oder anderer ähnlicher Steuerelemente sollte nicht länger als die durchschnittliche Eingabe für das Feld sein. Das durchschnittliche englische Wort besteht aus fünf Zeichen. Beispielsweise sollte ein Textfeld, das einen langen Pfadnamen erfordert, so lang sein, wie es das horizontale Layout zulässt, während eine Dropdown-Liste für Plattformnamen nur eine Länge haben sollte, die den längsten Eintrag zulässt.

#### <a name="helper-text"></a>Hilfstext

- Ein Dialogfeld kann Hilfstext anzeigen, der weitere Informationen zum Zweck des Dialogfelds enthält. Dies sitzt in der Regel an der Spitze und kann 1-2 Sätze sein.

- Die Zeilenlänge sollte eine komfortable Breite für einen Benutzer zum Analysieren und Lesen sein. Ein mittlerer Dialog sollte nicht mehr als 550 Pixel breit sein.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Innenbefehlstasten
 In komplexeren Dialogfeldern verfügt ein internes Steuerelement möglicherweise über eigene zugehörige Schaltflächen, die sich auf die Schaltflächen der Commit-Schaltflächen des Dialogfelds auswirken können.

- Verwenden Sie eine vertikale Ausrichtung (Spalte) von Innenschaltflächen, wenn **OK**/**Abbrechen** in der unteren rechten Ecke horizontal ausgerichtet ist.

- Verwenden Sie eine horizontale Ausrichtung (Zeile) von Innentasten, wenn **OK**/**Abbrechen** in der oberen rechten Ecke vertikal ausgerichtet ist. Diese Situation ist seltener.

- Die Innentastengröße sollte auf die Standard-Tastengröße von 75x23 Pixeln abzielen und nach Möglichkeit der Größe der **SCHALTFLÄCHEn OK**/**Abbrechen** entsprechen. Wenn eine Schaltflächenbeschriftung dazu führt, dass die Schaltfläche die Standard-Schaltflächengröße überschreitet, sollten die anderen Schaltflächen in diesem Satz an dieser größeren Größe ausgerichtet werden.

  ![Horizontale Schaltflächen "OK" und "Abbrechen"](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Abbildung 08.01-f: Vertikale Innentasten mit horizontalem OK/Abbrechen**

  ![Vertikale Schaltflächen "OK" und "Abbrechen"](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Abbildung 08.01-g: Horizontale Innentasten mit vertikalen OK/Cancel**

#### <a name="browse-button"></a>[Durchsuchen...] Schaltfläche
 **[Durchsuchen...]** Schaltflächen, die einem Textfeld folgen, sollten "Durchsuchen..." einschließlich der Ellipsen. Wenn der Platz knapp ist oder mehrere **[Browse...]-Schaltflächen** auf dem Bildschirm vorhanden sind, kann die Schaltfläche auf nur die Auslassungspunkte reduziert werden.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Thematisches Dialoglayout
 Thematische Dialoge in Visual Studio haben ein helleres Erscheinungsbild und bieten mehr Leerraum. Typografie bietet mehr Betonung und Interesse, bietet mehr offene Zeilenabstände und eine Variation der Schriftgrößen und -gewichte. Nach Möglichkeit wurden Chrom- und Titelleisten reduziert oder entfernt. Das Layout dieser Dialogfelder sollte diesem grundgrundlegenden Muster folgen:

1. Der Hintergrund des Dialogs ist weiß.

2. Es gibt einen 1-Pixel-Regelrahmen in einem Grau mit mittlerem Wert.

3. Der Dialogtitel befindet sich nicht mehr in einer Titelleiste, sondern bietet visuelles Interesse und Betonung in einer größeren Punktgröße. (Siehe Abschnitt Schriftgröße im [Textformat](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Beschriftungen, die mit zusätzlichem Text gekoppelt sind, z. B. eine Beschreibung, sollten **Umgebungsschriftart + Fett**sein.

5. Innenspalten werden durch eine 1-Pixel-Regel in hellgrau getrennt.

6. Standardlinks haben keinen Unterstrich. Hover und gedrückte Zustände haben eine Farbänderung plus Unterstrich.

7. Commit-Schaltflächen (wie **OK**/**Abbrechen**) sitzen in der unteren rechten Ecke.

### <a name="themed-dialog-layout-examples"></a>Themendialoglayoutbeispiele
 ![Dialogfeldlayout mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Abbildung 08.01-h: Themendialog**

 ![Dialogfeldabmessungen mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Abbildung 08.01-i: Themendialog - Dimensionen**

 ![Dialogfeldschriftarten mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Abbildung 08.01-j: Themendialog - Schriftarten**

 ![Dialogfeldfarben mit angewendetem Design](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Abbildung 08.01-k: Themendialog - Farben**

## <a name="see-also"></a>Weitere Informationen
- [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Steuerelemente (Windows)](/windows/desktop/uxguide/controls)
- [Dialogfelder (Windows)](/windows/desktop/uxguide/win-dialog-box)
