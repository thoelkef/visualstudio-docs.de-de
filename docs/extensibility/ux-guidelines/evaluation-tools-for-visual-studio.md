---
title: Evaluierungstools für Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698431"
---
# <a name="evaluation-tools-for-visual-studio"></a>Auswertungstools für Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Handwerks-Checkliste für Visual Studio
 Verwenden Sie diese Checkliste, um die Qualität der Benutzerfreundlichkeit für visuelle und Interaktionsdetails zu bewerten.

### <a name="overview"></a>Übersicht

- Stellen Sie sicher, dass alle Befehle zu Feedback führen, das Benutzern mitteilt, dass ihre Befehle ausgeführt wurden.

- Stellen Sie sicher, dass alle UI-Elemente und Steuerelemente in allen Designs und im Modus mit hohem Kontrast sichtbar sind.

- Stellen Sie sicher, dass die inaktive und aktive Auswahl sowohl im Standardmodus als auch im Modus mit hohem Kontrast immer differenziert ist.

- Stellen Sie sicher, dass der Fokus immer sichtbar und sichtbar ist.

### <a name="performance"></a>Leistung

- Stellen Sie sicher, dass eine Art "beschäftigter" Indikator angezeigt wird, wenn ein Befehl mehr als eine Sekunde dauert.

- Stellen Sie sicher, dass, wenn ein Befehl mehr als 10 Sekunden benötigt, eine explizite Fortschrittsleiste angezeigt wird, entweder determiniert (bevorzugt) oder unbestimmt.

### <a name="ui-text"></a>UI-Text

- Stellen Sie sicher, dass alle Beschriftungen satz- oder titelgroß sind und dass kein Text vollständig klein geschrieben ist.

    ||Richtig|Falsch|
    |-|-------------|---------------|
    |**Befehlstext (alle)**|Satzfall:<br /><br /> **Verzeichnisname:**|Verzeichnisname:|
    |**Schaltflächentext (Client)**|Titelfall:<br /><br /> **[ Als Standard festlegen ]**|ALS STANDARD FESTLEGEN|
    |**Button-Text (online)**|Satzfall:<br /><br /> **[ Als Standard festlegen ]**||

- Stellen Sie sicher, dass alle Beschriftungen, mit Ausnahme von Gruppenüberschriften und Schaltflächen, mit einem Doppelpunkt enden und dem Steuerelement, mit dem sie gekoppelt sind, voranstellen.

- Überprüfen Sie, ob Schaltflächen, Befehle und Befehlslinks, die die Benutzeroberfläche starten, um Benutzereingabezugaben zu erfassen, in einer Auslassungsrolle **enden [...]**.

  Beispiele:

  - Eine **[Erweiterte...]** Schaltfläche in einem Dialogfeld.

  - Die Befehlsoptionen im Menü Extras (**Tools > Options**) sollten keine Auslassung erhalten, da das Starten des Dialogfelds selbst die Absicht des Befehls ist.

- Stellen Sie sicher, dass die Benutzeroberfläche keine Abkürzungen enthält, mit Ausnahme von Branchenstandardbegriffen. Zum Beispiel müssen weder HTML noch TCP/IP buchstabiert werden, obwohl OOM (nicht im Speicher) und PII (persönlich identifizierbare Informationen) festgelegt werden sollten.

### <a name="keyboard-access"></a>Tastaturzugriff

- Stellen Sie sicher, dass es eine Möglichkeit gibt, jede Aufgabe mit der Tastatur auszuführen. Im Allgemeinen wird dies durch den Tastaturzugriff für jedes Steuerelement erreicht, aber für einige sehr visuelle Bereiche ist eine Problemumgehung, z. B. das Durchlaufen der Codeansicht, akzeptabel.

- Stellen Sie sicher, dass Sie Steuerelemente in logischer Reihenfolge (von links nach rechts und von oben nach unten) durchkreuzen können. Obwohl dies für die meisten Steuerelemente eine bewährte Methode ist, erfordern nicht alle Steuerelemente diesen Ansatz. Stellen Sie beispielsweise sicher, dass sich die Optionsfeldsteuerelemente in einer Gruppe mit einem einzelnen Tabstopp befinden.

- Stellen Sie sicher, dass alle Steuerelemente über Beschriftungen verfügen und dass jede Beschriftung über eine mnemonic verfügt (Ausnahmen umfassen einige nicht beschriftete Steuerelemente, die einem beschrifteten Steuerelement auf der Registerkarte folgen können).

- Stellen Sie sicher, dass keine mnmonischen Konflikte vorhanden sind.

### <a name="fonts"></a>Schriftarten

- Stellen Sie sicher, dass alle Schriftarten (Gesicht, Größe, Farbe) konsistent verwendet werden, und behalten Sie die Hierarchie bei.

- Stellen Sie sicher, dass alle UI-Elemente den Umgebungsschriftartdienst verwenden. (Siehe [Schriftarten und Formatierung enerther für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Um zu überprüfen, ob der Dienst verwendet wird, gehen Sie zu **Tools > Optionen > Schriftarten und Farben**. Wählen Sie in der Dropdown-Liste Einstellungen Umgebungsschrift aus und ändern Sie die Schriftart in etwas stilistisch anderes (z. B. Harrington oder Comic Sans) und legen Sie die Größe auf 12 Pkt fest. Klicken Sie dann auf „OK“. Möglicherweise müssen Sie die IDE neu starten, aber die meisten Benutzeroberfläche enden sofort. Bereiche, die die Schriftartänderung auch beim Neustart nicht übernehmen, verwenden die Umgebungsschriftart nicht.

- Stellen Sie sicher, dass Schriftarten, die vom Dienst abgeleitet sind (z. B. fett formatierter oder vergrößerter Text), ihre Größe und Formatierung in Bezug auf "normalen" Text beibehalten, wenn die Größe der Umgebungsschriftart geändert wird.

- Stellen Sie sicher, dass aufgrund vergrößerter Schriftarten keine Clipping-Fehler vorliegen. Schriftarten, die abgeschnitten werden, sind wahrscheinlich das Ergebnis von Steuerelementen für feste Höhen oder Container mit fester Höhe.

### <a name="dialogs"></a>Dialogfelder

- Stellen Sie sicher, dass der Dialogfeldtitel mit dem Befehl identisch ist, der ihn gestartet hat.

- Stellen Sie sicher, dass alle Standardsteuerelemente mit dem Betriebssystem konsistent sind: Die Hintergrundfarbe ist Standard, und keine Steuerelemente sollten einen speziellen neu formatierten Stil haben, der sie von Standardsteuerelementen unterscheiden lässt.

- Stellen Sie sicher, dass die Ränder innerhalb des Formulars 12 Pixel groß sein und einheitlich und konsistent erscheinen sollten.

- Stellen Sie sicher, dass Die Dialoge zentriert in der IDE-Shell oder im Fenster angezeigt werden, das sie erstellt hat.

- Wenn dies nützlich ist, sollten Dialoge in der Geänderten Semittierbarkeit sein. Stellen Sie bei Dialogen, die die Größe ändern können, sicher, dass bei der Größenänderung die Größe der entsprechenden Steuerelemente geändert werden muss, während andere Teile des Dialogfelds konstant bleiben.

- Stellen Sie sicher, dass in der Größe der Größe geänderte Dialogfelder jede vom Benutzer angepasste Größe beibehalten (Größe, Speicherort, Erweiterung von Dialogsteuerelementen usw.).

- Stellen Sie sicher, dass in der Titelleiste kein Symbol vorhanden ist.

- Stellen Sie sicher, dass in der Titelleiste keine Schaltflächen minimieren und maximieren vorhanden sind.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Dialog-Bedienungsschaltflächen (nur VS Client)

- Stellen Sie sicher, dass die Vorgangsschaltflächen in dieser Reihenfolge sind: **OK**, **Abbrechen**, **Anwenden**.

- Stellen Sie sicher, dass die **Schaltflächen OK** und **Abbrechen** die Standardgröße von 75x23 Pixeln haben.

- Stellen Sie sicher, dass die **Schaltflächen OK** und **Abbrechen** unabhängig von der Zeichenfolgenlänge gleich groß sind.

- Wenn die Beschriftung auf einer Bedienschaltfläche erfordert, dass die Schaltfläche breiter als der Standard ist, stellen Sie sicher, dass die entsprechende **Schaltfläche Abbrechen** gleich groß ist.

- Stellen Sie sicher, dass zwischen Schaltflächen und zugehörigen Steuerelementen ein 6-Pixel-Aufabstand vorhanden ist.

- Stellen Sie sicher, dass die Schaltflächen **OK** und **Abbrechen** nicht über mnemonics verfügen (Zugriffsschlüssel, die durch einen unterstrichenen Buchstaben definiert sind).

- Stellen Sie sicher, dass eine Schaltfläche (in der Regel **OK**) standardmäßig den Fokus hat.

- Stellen Sie sicher, dass **Esc** das Dialogfeld abbricht

- Stellen Sie sicher, dass **Enter** die Standardschaltfläche ausführt, wenn sich der Fokus nicht in einem Steuerelement befindet, das Enter verarbeitet.

- Stellen Sie sicher, dass die Schaltflächen **OK** und **Abbrechen** in der unteren rechten Ecke des Dialogfelds positioniert sind. In seltenen Ausnahmen ist es akzeptabel, dass sie vertikal in der oberen rechten Seite gestapelt werden.

- Stellen Sie sicher, dass die vertikale Konfiguration nur verwendet wird, wenn sich andere Schaltflächen in einer horizontalen Ausrichtung innerhalb des Dialogfelds befinden.

### <a name="control-standards"></a>Kontrollnormen

#### <a name="general"></a>Allgemein

- Stellen Sie sicher, dass es nach Möglichkeit gute Standardwerte gibt, um die Benutzerinteraktion zu beschleunigen und Benutzer zu einem sicheren oder allgemeinen Ergebnis zu bewegen.

- Stellen Sie sicher, dass Standardsteuerelemente auf die gleiche Weise verhalten, damit Benutzer basierend auf früheren Erfahrungen wissen, was passieren wird.

#### <a name="label-controls"></a>Beschriftungssteuerelemente

- Stellen Sie sicher, dass jedes Steuerelement über eine Beschriftung verfügt und dass jedes Steuerelement visuell mit seinem Steuerelement (in der Regel innerhalb eines 4-6-Pixel-Bereichs) gekoppelt ist und näher an der entsprechenden Steuerung als an anderen Steuerelementen liegt.

- Stellen Sie sicher, dass Beschriftungen bündig mit der linken Kante des Steuerelements positioniert sind, wenn sie über und horizontal zentriert sind, sodass die Basislinie der Beschriftung an der Basislinie des Eingabetextes ausgerichtet ist, wenn sie nach links positioniert ist.

- Stellen Sie sicher, dass, wenn mehrere gestapelte Beschriftungs- und Eingabesteuerelemente links neben einem Steuerelement positioniert sind, die Beschriftungen bündig links und einen gleichen Abstand vom Rand des Dialogfelds sind, niemals nach rechts und einen gleichen Abstand von den Steuerelementen bündigen. Paare sollten gleichmäßig verteilt werden, es sei denn, sie benötigen zusätzliche Abstände, um die Gruppierung anzuzeigen.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Eingabesteuerelemente (Textfelder und Kombinationsfelder)

- Stellen Sie sicher, dass bei Verwendung der Standardumgebungsschriftart die Anzeigehöhe für Textfelder, Kombinationsfelder und Schaltflächen alle 23 Pixel beträgt.

- Wenn Hinweistext verwendet wird, stellen Sie `Environment.ControlEditHintText` sicher, dass die Farbe auf verwendungsbasiert erlegen ist.

- Wenn es sich bei dem Feld um ein erforderliches Feld handelt, das als solches identifiziert werden muss, überprüfen Sie Folgendes:

  - dass der Hintergrund `Environment.ControlEditRequiredBackground` und der Vordergrund auf`Environment.ControlEditRequiredHintText`

  - dass es Hinweistext innerhalb des Steuerelements gibt, der als **"Erforderlicher\<>"** angezeigt wird

#### <a name="button-controls"></a>Schaltflächen-Steuerelemente

- Stellen Sie sicher, dass Schaltflächen eine Mindestgröße von 75x23 Pixeln haben, es sei denn, sie können längeren Text aufnehmen.

- Stellen Sie sicher, dass Schaltflächen links und rechts mit 3-5 Pixeln sowie eine Auffüllung für den Inhalt aufweisen.

- Es ist akzeptabel, einen kleinen quadratischen Knopf mit nur einer **Auslassungsfunktion zu** verwenden [...] darauf anstelle eines **[Browse...]-Buttons** (oder ähnlicher Funktionen). Wenn sie verwendet wird, stellen Sie sicher, dass die Schaltfläche 23x23 groß ist.

- Wenn es mehr als eine **[Browse...]** Schaltfläche in einem Dialoggibt gibt, überprüfen Sie, ob die gekürzte Version (nur Ellipsen **[...]**) für alle verwendet wird.

- Stellen Sie sicher, dass die Tasten der Ellipse **[...]** keine mnemonic haben. Wenn der Fokus auf dem Eingabesteuerelement daneben liegt, sollte eine Registerkarte den Fokus auf die Auslassungsschaltfläche verschieben.

- Stellen Sie sicher, dass Schaltflächen, Befehle und Befehlslinks, die die sekundäre Benutzeroberfläche starten, die mehr Benutzereingaben erfasst, in einer Auslassungsrolle enden müssen **[...]**.

#### <a name="hyperlinks"></a>Links

- Stellen Sie sicher, dass ein Hyperlinksteuerelement nie rot blinkt, wenn es aktiv ist. Dies ist ein Indikator dafür, dass der Farbdienst nicht verwendet wird.

- Stellen Sie sicher, dass die verwendeten VS-Farben wie:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Stellen Sie sicher, dass Hyperlinks blau ohne Unterstreichung angezeigt werden, es sei denn, sie sind in einen Absatz eingebettet.

#### <a name="check-boxes"></a>Kontrollkästchen

- Wenn ein Kontrollkästchen mehrzeiligen Text enthält, stellen Sie sicher, dass das Kontrollkästchen an der ersten Textzeile ausgerichtet ist und nicht vertikal über alle Zeilen zentriert ist.

- Stellen Sie sicher, dass Kontrollkästchen immer eine binäre Auswahl anzeigen und nicht durch den Benutzer navigieren oder neue Fenster oder Seiten öffnen.

- Wenn ein Kontrollkästchen eine Option für ein Eingabesteuerelement darstellt, stellen Sie sicher, dass es bündig links und sehr nah unter diesem Steuerelement positioniert ist, um seine Beziehung anzugeben.

- Stellen Sie sicher, dass ein Kontrollkästchen **nie** als Mittel verwendet wird, um den gesamten Inhalt eines Dialogfelds oder einer Seite zu aktivieren.

#### <a name="group-boxes"></a>Gruppenboxen

- Stellen Sie sicher, dass ein Dialogfeld kein einzelnes Gruppenfeld enthält, das den gesamten Inhalt des Dialogfelds enthält.

- Stellen Sie sicher, dass in jedem Gruppenfeld mindestens zwei Steuerelemente vorhanden sind.

- Selten sollten mehr als zwei Gruppenfelder in einem Dialogfeld vorhanden sein.

- Stellen Sie sicher, dass keine verschachtelten Gruppenfelder vorhanden sind.

### <a name="icons"></a>Symbole

- Stellen Sie sicher, dass Symbole korrekt invertiert angezeigt werden, wenn sie sich im dunklen Design befinden.

- Stellen Sie sicher, dass alle Symbole auf Kernkonzepten basieren.

- Stellen Sie sicher, dass jedes Symbol unterschiedlich, leicht zu erkennen ist und nicht mehr als zwei Konzepte enthält (ohne Statusmodifizierer/Sprache).

- Stellen Sie sicher, dass das Basissymbol zentriert im Raum angezeigt wird.

- Stellen Sie sicher, dass alle Symbole im Modus "Hoher Kontrast" lesbar angezeigt werden.

- Stellen Sie sicher, dass die verwendete Farbe den Farbverwendungsstandards entspricht.

- Stellen Sie sicher, dass keine Halos (Rahmen) um Symbole herum vorhanden sind. (Falls vorhanden, sollte der Halo mit der Hintergrundfarbe der benachbarten Benutzeroberfläche übereinstimmen).

### <a name="touch-enabled-ui"></a>Touch-fähige Benutzeroberfläche

- Stellen Sie sicher, dass interaktive Steuerelemente groß genug sind, um leicht ansetzbar zu sein - mindestens **23x23 Pixel** in der Größe

- Stellen Sie sicher, dass die am häufigsten verwendeten Steuerelemente mindestens **40 x 40 Pixel** groß sind.

- Stellen Sie sicher, dass interaktive **Steuerelemente** mindestens 5 Pixel Abstand zwischen ihnen haben
