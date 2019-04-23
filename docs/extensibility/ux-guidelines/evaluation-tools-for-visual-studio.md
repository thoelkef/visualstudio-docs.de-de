---
title: Analysetools für Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11856141a6c3f5ca186428d67edf10fdbd35787b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086351"
---
# <a name="evaluation-tools-for-visual-studio"></a>Analysetools für Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Checkliste für handwerkliches können für Visual Studio
 Verwenden Sie diese Prüfliste, um Qualität der benutzerfreundlichkeit Visual und Interaktion ausführliche auszuwerten.

### <a name="overview"></a>Übersicht

- Stellen Sie sicher, dass alle Befehle Feedback erhalten, der Benutzer darüber informiert, dass ihre Befehle ausgeführt haben.

- Stellen Sie sicher, dass alle Elemente der Benutzeroberfläche und Steuerelemente in allen Designs übernimmt und im Modus für hohe Kontraste sichtbar sind.

- Stellen Sie sicher, dass inaktive und aktive Auswahl immer unterscheiden, sowohl in der Standard- und der Modus für hohe Kontraste.

- Stellen Sie sicher, dass der Fokus immer sichtbar und offensichtlich ist.

### <a name="performance"></a>Leistung

- Stellen Sie sicher, dass eine Art von "beschäftigt" Indikator angezeigt wird, wenn ein Befehl mehr als eine Sekunde dauert.

- Überprüfen Sie, ob ein Befehl mehr als 10 Sekunden, eine explizite Statusanzeige, entweder akzeptiert bestimmte (bevorzugt) oder unbestimmt ist, wird angezeigt.

### <a name="ui-text"></a>Benutzeroberflächentext

- Stellen Sie sicher, dass alle Bezeichnungen Satz oder Buchstabe groß sind und kein Text ausschließlich Kleinbuchstaben ist.

    ||Richtig|Falsche|
    |-|-------------|---------------|
    |**Befehlstext (alle)**|Satz-Fall:<br /><br /> **Verzeichnisname:**|Verzeichnisname:|
    |**Text der Schaltfläche (Client)**|Große Anfangsbuchstaben:<br /><br /> **[Als Standard festlegen]**|SET AS DEFAULT|
    |**Text der Schaltfläche (online)**|Satz-Fall:<br /><br /> **[Als Standard festgelegt]**||

- Stellen Sie sicher, dass alle Bezeichnungen, mit Ausnahme von Kopfzeilen von Gruppen und Schaltflächen mit einem Doppelpunkt enden, und stellen Sie das Steuerelement, mit dem sie miteinander kombiniert sind, voran.

- Stellen Sie sicher, dass für Schaltflächen, Befehle und Befehlslinks, die die Benutzeroberfläche zum Erfassen von Benutzereingaben starten ein Auslassungszeichen aufgetreten **[...]** .

     Beispiele:

    - Ein **[Erweitert]**  Schaltfläche in einem Dialogfeld.

    - Die Befehlsoptionen an, unter dem Menü "Extras" (**Tools > Optionen**) Auslassungspunkte sollte nicht abgerufen werden, da starten das Dialogfeld selbst die Absicht des Befehls ist.

- Stellen Sie sicher, dass die Benutzeroberfläche keine Abkürzungen, mit Ausnahme der Branche zum Standard-Begriffe enthält. Z. B. müssen weder die HTML-als auch die TCP/IP, geschrieben werden, obwohl OOM-Bedingungen (nicht genügend Arbeitsspeicher) und personenbezogene Informationen (persönlich identifizierbare Informationen) sollten.

### <a name="keyboard-access"></a>Tastaturzugriff

- Stellen Sie sicher, dass es eine Möglichkeit zum Ausführen der jeweiligen Aufgabe mit der Tastatur. In der Regel erfolgt dies über den Zugriff für jedes Steuerelement, aber für einige Bereiche visuell eine problemumgehung, z. B. zur Codeansicht hier akzeptabel ist.

- Stellen Sie sicher, dass Sie über Steuerelemente in einer logischen Reihenfolge (links-nach-rechts und oben-nach-unten) TAB-Taste. Obwohl dies eine bewährte Methode für die meisten Steuerelemente ist, müssen nicht alle Steuerelemente dieser Ansatz. Beispielsweise stellen Sie sicher, Optionsfeld, die in einer Gruppe mit einer einzelnen Tabstopp-Steuerelemente sind.

- Stellen Sie sicher, dass alle Steuerelemente über Bezeichnungen verfügen und dass jede Bezeichnung mnemonisches Zeichen (Ausnahmen enthalten einige nicht beschrifteten-Steuerelemente, die ein mit Bezeichnung-Steuerelement auf der Registerkarte ausführen können).

- Stellen Sie sicher, dass keine mnemonische Konflikte vorhanden sind.

### <a name="fonts"></a>Schriftarten

- Stellen Sie sicher, dass alle Schriftarten (Face, Größe, Farbe) konsistent verwendet werden, und Warten der Hierarchie.

- Stellen Sie sicher, dass alle Elemente der Benutzeroberfläche den Umgebung Schriftart-Dienst verwenden. (Finden Sie unter [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Um festzustellen, ob der Dienst verwendet wird, wechseln Sie zu **Tools > Optionen > Schriftarten und Farben**. Wählen Sie in der Dropdownliste "Einstellungen" Umgebungsschriftart aus ändern Sie Schriftart, einen stilistisch fehlerhaften anderen (z. B. Harrington oder Comic-Sans), und legen Sie die Größe auf 12 pt. Klicken Sie dann auf OK. Sie müssen möglicherweise die IDE neu zu starten, aber die meisten UI wird sofort geändert. Bereiche, die die Schriftart Änderung auch auf Neustart übernimmt nicht verwenden die Umgebungsschriftart nicht.

- Stellen Sie sicher, dass die Schriftarten, die Ableitung des Diensts (z. B. fett oder vergrößerte Text) sind, behalten ihre Größe und in Bezug auf "normal" Text formatieren, wenn der Schriftgrad der Umgebung geändert wird.

- Stellen Sie sicher, dass keine Clipping Fehler aufgrund von vergrößerte Schriftarten vorhanden sind. Schriftarten, die abgeschnitten wird, erhalten, sind wahrscheinlich das Ergebnis der feste Höhe Steuerelemente oder feste Höhe-Container.

### <a name="dialogs"></a>Dialogfelder

- Stellen Sie sicher, dass der Dialogfeldtitel ist identisch mit dem Befehl, der sie gestartet.

- Stellen Sie sicher, dass alle Standardsteuerelemente konsistent mit dem Betriebssystem sind: Hintergrundfarbe standard ist und keine Steuerelemente müssen einen speziellen Re auf Vorlagen basierenden Stil, mit der sie sich von standardmäßigen Steuerelementen angezeigt werden.

- Stellen Sie sicher, dass Ränder, innerhalb des Formulars sollte 12 Pixel und einheitliches und konsistentes sollte angezeigt werden.

- Stellen Sie sicher, dass Dialoge steht in der Mitte in der IDE-Shell oder das Fenster, das sie erzeugt.

- Wenn nützlich ist, sollte die Dialogfelder mit veränderbarer Größe sein. Für Dialoge, die in der Größe veränderbar sind, stellen Sie sicher, dass beim Ändern der Größe, die entsprechenden Steuerelemente ändern müssen, während andere Teile des Dialogfelds konstant bleibt.

- Stellen Sie sicher, dass Dialoge mit änderbarer Größe jeder Benutzer angepasst Größe (Größe, Position, Erweiterung der Dialogfeld-Steuerelemente, usw.) beibehalten werden.

- Stellen Sie sicher, dass es in der Titelleiste kein Symbol wird.

- Stellen Sie sicher, dass es keine minimieren und Maximieren-Schaltflächen in der Titelleiste angezeigt stehen.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Dialogfeld vorgangsschaltflächen (gilt nur für Visual Studio-Client)

- Stellen Sie sicher, dass die Operation Schaltflächen in der folgenden Reihenfolge: **OK**, **Abbrechen**, **anwenden**.

- Überprüfen Sie, ob **OK** und **Abbrechen** Schaltflächen sind die Standardgröße: 75 x 23 Pixel.

- Überprüfen Sie, ob **OK** und **Abbrechen** Schaltflächen sind gleicher Größe unabhängig von der Länge der Zeichenfolge.

- Wenn die Bezeichnung auf eine Schaltfläche "Vorgang" Schaltfläche auf breiter als Standard erforderlich ist, sicherstellen, dass die entsprechenden **Abbrechen** Schaltfläche gleicher Größe ist.

- Stellen Sie sicher, dass ein 6-Pixel-Abstand zwischen Schaltflächen und dem zugeordneten Steuerelement vorhanden ist.

- Überprüfen Sie, ob die **OK** und **Abbrechen** Schaltflächen müssen keine mnemonischen Zeichen (Zugriffstasten, die durch einen unterstrichenen Buchstaben definiert).

- Eine Schaltfläche "Überprüfen" (in der Regel **OK**) den Fokus besitzt, wird standardmäßig.

- Überprüfen Sie, ob **Esc** das Dialogfeld wird abgebrochen

- Überprüfen Sie, ob **EINGABETASTE** die Schaltfläche "Standard" ausgeführt wird, wenn der Fokus nicht in einem Steuerelement befindet, die Eingabe verarbeitet.

- Überprüfen Sie, ob die **OK** und **Abbrechen** Schaltflächen werden in der unteren rechten Ecke des Dialogfelds positioniert. In wenigen Ausnahmen abgesehen ist es akzeptabel ist, damit sie in der oberen rechten Ecke vertikal gestapelt werden.

- Stellen Sie sicher, dass die vertikale Konfiguration nur, wenn andere Schaltflächen in eine horizontale Ausrichtung im Dialogfeld verwendet wird.

### <a name="control-standards"></a>Steuerelement-standards

#### <a name="general"></a>Allgemein

- Stellen Sie sicher, dass wenn möglich, es gute Standardwerte sind, um die Benutzerinteraktion und leiten Sie Benutzer in Richtung eines Ergebnisses sicher oder allgemeine zu beschleunigen.

- Stellen Sie sicher, dass die Standardsteuerelemente dasselbe Verhalten auf, damit Benutzer wissen, was geschieht basierend auf frühere Erfahrung.

#### <a name="label-controls"></a>Label-Steuerelemente

- Stellen Sie sicher, dass für jedes Steuerelement eine Bezeichnung und jede Bezeichnung visuell das Steuerelement (in der Regel in einem 4 bis 6-Pixel-Bereich) zugeordnet ist, und näher an das entsprechende Steuerelement als für andere Steuerelemente ist.

- Stellen Sie sicher, dass Bezeichnungen leeren positioniert sind Links, mit dem Steuerelement linken Fensterrands, wenn oben positioniert und horizontal zentriert werden, damit, dass die Baseline für die Beschriftung der Grundlinie des Eingabetexts ausgerichtet ist, wenn auf der linken Seite befindet.

- Stellen Sie sicher, dass wenn mehrere gestapelte Bezeichnung und Benutzereingabe-Steuerelemente auf der linken Seite eines Steuerelements positioniert ist, die Bezeichnungen linksbündig sind und jeweils denselben Abstand vom Rand des Dialogfelds nicht leeren, Recht und die jeweils denselben Abstand von den Steuerelementen. Paare sollten gleichmäßig verteilt werden, es sei denn, der benötigten zusätzlichen Abstand soll Grouping.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Benutzereingabe-Steuerelemente (Textfelder und Kombinationsfelder)

- Stellen Sie sicher, dass wenn Sie die Standardschriftart für die Umgebung verwenden zu können, sind die Anzeigehöhe für Textfelder, Kombinationsfelder und Schaltflächen alle 23 Pixel.

- Wenn Hinweistext verwendet wird, stellen Sie sicher, dass die Farbe, um festgelegt wird `Environment.ControlEditHintText` mithilfe des Color-Diensts.

- Wenn das Feld ein Pflichtfeld, die als solche gekennzeichnet werden müssen ist, stellen Sie Folgendes sicher:

    - das der Hintergrund nastaven NA hodnotu `Environment.ControlEditRequiredBackground` und auf der Vordergrund festgelegt ist `Environment.ControlEditRequiredHintText`

    - es der Hinweistext im Steuerelement, das wird als angezeigt wird **"\<erforderlichen >"**

#### <a name="button-controls"></a>Schaltflächen-Steuerelemente

- Stellen Sie sicher, dass die Schaltflächen mit einer Mindestgröße von 75 x 23 Pixel sind, es sei denn, sodass mehr Text.

- Stellen Sie sicher, dass die Schaltflächen verlassen haben und rechten Rand von 3 bis 5 Pixel als auch die Auffüllung für den Inhalt.

- Es ist akzeptabel, verwenden Sie eine kleine quadratische Schaltfläche mit nur einer Ellipse **[...]**  darauf statt einer **[durchsuchen...]**  Schaltfläche (oder ähnliche Funktionalität). Wenn verwendet, stellen Sie sicher, dass die Schaltfläche mit der 23 x 23 groß ist.

- Wenn es mehr als eine **[durchsuchen...]**  in einem Dialogfeld, und klicken Sie dann überprüfen Sie, ob die verkürzte Version (nur Auslassungszeichen **[...]** ) wird für alle verwendet.

- Stellen Sie sicher, mit den Auslassungspunkten **[...]**  Schaltflächen müssen sich nicht auf ein mnemonisches Zeichen. Wenn der Fokus auf das Eingabesteuerelement daneben befindet, sollten eine Registerkarte den Fokus auf die Schaltfläche mit den Auslassungspunkten verschieben.

- Stellen Sie sicher, dass die Schaltflächen, Befehle und Befehlslinks, die sekundäre Benutzeroberfläche zu starten, die weitere Eingabe des Benutzers erfasst ein Auslassungszeichen enden müssen **[...]** .

#### <a name="hyperlinks"></a>Hyperlinks

- Stellen Sie sicher, dass ein Linksteuerelement nie Rot, wenn aktive blinkt. Dies ist ein Indikator, dass der Color-Dienst nicht verwendet wird

- Stellen Sie sicher, dass die VS-Farben, die verwendet werden:

    - `Environment.ControlLinkText`

    - `Environment.ControlLinkTextHover`

    - `Environment.ControlLinkTextPressed`

- Stellen Sie sicher, dass die Hyperlinks werden blau nicht zu unterstreichen, es sei denn, die in einem Absatz eingebettet angezeigt.

#### <a name="check-boxes"></a>Kontrollkästchen

- Wenn das Kontrollkästchen für ein mehrzeiligen Text verfügt, stellen Sie sicher, dass das Feld mit der ersten Zeile des Texts, die nicht in allen Geschäftsbereichen vertikal zentriert ausgerichtet ist.

- Stellen Sie sicher, dass Sie die Kontrollkästchen immer eine binäre Wahl kennzeichnen und nicht den Benutzer oder neuen Fenstern oder Seiten zu öffnen.

- Wenn das Kontrollkästchen eine Option, die im Zusammenhang mit der eines Eingabesteuerelements vorweisen, stellen Sie sicher, dass sie unveränderliche links und sehr eng unter das Steuerelement an dessen Beziehung positioniert ist.

- Stellen Sie sicher, dass das Kontrollkästchen ist **nie** als Mittel verwendet werden, um den gesamten Inhalt eines Dialog- oder die Seite zu aktivieren.

#### <a name="group-boxes"></a>Gruppenfelder

- Stellen Sie sicher, dass ein Dialogfeld kein einzelnes Gruppenfeld darin enthält, das den gesamten Inhalt des Dialogfelds enthält.

- Stellen Sie sicher, dass mindestens zwei Steuerelemente in jeder Gruppenfeld vorhanden sind.

- Nur selten sollte mehr als zwei Gruppenfelder in einem Dialogfeld angezeigt werden.

- Stellen Sie sicher, dass keine geschachtelte Gruppenfelder vorhanden sind.

### <a name="icons"></a>Symbole

- Stellen Sie sicher, dass Symbole in das Design "dunkel" ordnungsgemäß invertierten angezeigt werden.

- Stellen Sie sicher, dass alle Symbole für die grundlegenden Konzepte basieren.

- Stellen Sie sicher, dass jedes Symbol distinct, einfach zu erkennen, und nicht mehr als zwei Konzepte (ohne Status Modifizierer/Sprache enthält).

- Stellen Sie sicher, dass das Symbol "Basis" zentriert innerhalb des Bereichs angezeigt wird.

- Stellen Sie sicher, dass alle Symbole im Modus für hohe Kontraste lesbar angezeigt werden.

- Sicherstellen Sie, dass eine beliebige Farbe verwendet Farbe Nutzung Standards entspricht.

- Stellen Sie sicher, dass keine Halos (Rahmen) vorhanden sind, um Symbole. (Falls vorhanden, sollte des Halo-Effekts die Hintergrundfarbe der angrenzenden Benutzeroberfläche übereinstimmen).

### <a name="touch-enabled-ui"></a>Touchscreen-Benutzeroberfläche

- Stellen Sie sicher, dass interaktive Steuerelemente werden einfach touchable: minimale groß genug sind **23 x 23 Pixel** Größe

- Stellen Sie sicher, dass die am häufigsten verwendeten Steuerelemente mindestens **40 x 40 Pixel** Größe.

- Überprüfen Sie, ob interaktive Steuerelemente mindestens **5 Pixel Abstand** dazwischen