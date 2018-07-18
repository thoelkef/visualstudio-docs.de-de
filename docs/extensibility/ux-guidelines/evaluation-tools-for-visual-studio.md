---
title: Analysetools für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a149d9163e61dd49105f123b373ecd9c7c1c278
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147332"
---
# <a name="evaluation-tools-for-visual-studio"></a>Analysetools für Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Handwerkliches können Prüfliste für Visual Studio  
 Verwenden Sie diese Prüfliste, um Benutzer Erfahrung Qualität Visual und Interaktion von Details auszuwerten.  
  
### <a name="overview"></a>Übersicht  
  
-   Stellen Sie sicher, dass alle Befehle Feedback führen, die Benutzer informiert, dass die eingegebenen Befehle durchgeführt wurden.  
  
-   Stellen Sie sicher, dass alle Elemente der Benutzeroberfläche und Steuerelemente in allen Designs und im Modus für hohe Kontraste sichtbar sind.  
  
-   Stellen Sie sicher, dass inaktive und aktive Auswahl werden immer unterschieden, sowohl in der Standard- und der Modus für hohe Kontraste.  
  
-   Stellen Sie sicher, dass der Fokus immer sichtbar und offensichtlich ist.  
  
### <a name="performance"></a>Leistung  
  
-   Stellen Sie sicher, dass einige Art von "ausgelastet" Indikator angezeigt wird, wenn ein Befehl mehr als einer Sekunde abgeschlossen wird.  
  
-   Überprüfen Sie, ob ein Befehl mehr als 10 Sekunden, um eine explizite Statusanzeige entweder abgeschlossen, akzeptiert bestimmte (bevorzugt) oder unbestimmt ist, wird angezeigt.  
  
### <a name="ui-text"></a>Der Benutzeroberflächentext  
  
-   Stellen Sie sicher, dass alle Bezeichnungen Satz oder Anfangsbuchstaben sind und kein Text vollständig Kleinbuchstaben ist.  
  
    ||Richtig|Falsche|  
    |-|-------------|---------------|  
    |**Befehlstext (alle)**|Groß-/Kleinschreibung Satz:<br /><br /> **Name des Verzeichnisses:**|Name des Verzeichnisses:|  
    |**Als Schaltflächentext (Client)**|Groß-/Kleinschreibung Titel:<br /><br /> **[Als Standard festlegen]**|SET AS DEFAULT|  
    |**Schaltflächentext (online)**|Groß-/Kleinschreibung Satz:<br /><br /> **[Als Standard festlegen]**||  
  
-   Stellen Sie sicher, dass alle Bezeichnungen, mit Ausnahme von Kopfzeilen und Schaltflächen, mit einem Doppelpunkt enden und vorausgehen das Steuerelement, mit dem sie zugeordnet sind.  
  
-   Überprüfen, ob Schaltflächen Befehlen und Befehlslinks, die zum Erfassen von Benutzereingaben-Benutzeroberfläche starten als Ellipse enden **[...]** .  
  
     Beispiele:  
  
    -   Ein **[Erweiterte...]**  auf ein Dialogfeld auf die Schaltfläche.  
  
    -   Der Befehlsoptionen im Menü "Extras" (**Tools > Optionen**) Ellipsen, sollten nicht abgerufen werden, da das Dialogfeld "selbst starten die Absicht des Befehls ist.  
  
-   Stellen Sie sicher, dass die Benutzeroberfläche keine Abkürzungen, mit Ausnahme von Industriestandard-Begriffe enthält. Z. B. müssen HTML weder TCP/IP, geschrieben werden, obwohl OOM (nicht genügend Arbeitsspeicher) und personenbezogene Daten (persönlich identifizierbare Informationen) sollten.  
  
### <a name="keyboard-access"></a>Tastaturzugriff  
  
-   Stellen Sie sicher, dass es eine Möglichkeit, jede Aufgabe mit der Tastatur. In der Regel erfolgt dies über den Zugriff für jedes Steuerelement, aber für einige hoch visual Bereiche, dieses Problem zu umgehen wie möchten in der Codeansicht akzeptabel ist.  
  
-   Stellen Sie sicher, dass Sie über Steuerelemente in einer logischen Reihenfolge (links nach rechts und oben nach unten) Registerkarte können. Dies ist zwar eine bewährte Methode für die meisten Steuerelemente, erfordern nicht alle Steuerelemente dieser Ansatz. Z. B. überprüfen dieses Optionsfeld, die Steuerelemente in einer Gruppe mit einer einzelnen Tabstopp sind.  
  
-   Stellen Sie sicher, dass alle Steuerelemente, die Bezeichnungen verfügen und dass jede Bezeichnung ein mnemonischen Codes (Ausnahmen sind einige nicht bezeichnet Steuerelemente, die folgen können, ein mit der Bezeichnung-Steuerelement in der Registerkarte ").  
  
-   Stellen Sie sicher, dass keine mnemonischen Konflikte bestehen.  
  
### <a name="fonts"></a>Schriftarten  
  
-   Stellen Sie sicher, dass alle Schriftarten (Gesicht, Größe, Farbe) einheitlich verwendet werden und die Hierarchie verwalten.  
  
-   Stellen Sie sicher, dass alle Elemente der Benutzeroberfläche die Umgebung Schriftart-Dienst verwendet. (Siehe [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Um festzustellen, ob der Dienst verwendet wird, wechseln Sie zu **Extras > Optionen > Schriftarten und Farben**. Wählen Sie in der Dropdownliste Einstellungen Umgebungsschriftart aus und ändern Sie die Schriftart in eine stylistically andere (z. B. Harrington oder Comic Sans), und legen Sie die Größe auf 12 pt. Klicken Sie dann auf OK. Müssen Sie möglicherweise die IDE neu zu starten, aber die meisten UI wird sofort geändert. Bereiche, die die Schriftart ändern, selbst bei Neustart übernimmt nicht verwenden die Umgebungsschriftart nicht.  
  
-   Stellen Sie sicher, dass die Schriftarten, die Ableitung des Diensts (z. B. fett oder vergrößerte Text) sind, behalten ihre Größe und Formatierung in Bezug auf "normale" Text, wenn der Schriftgrad der Umgebung geändert wird.  
  
-   Stellen Sie sicher, dass keine Clipping bei Fehlern aufgrund von vergrößerte Schriftarten vorhanden sind. Schriftarten, die abgeschnitten abzurufen sind wahrscheinlich das Ergebnis feste Höhe Steuerelemente oder feste Höhe Container.  
  
### <a name="dialogs"></a>Dialogfelder  
  
-   Überprüfen Sie, ob die Dialogfeldtitel identisch mit dem Befehl, die es gestartet.  
  
-   Stellen Sie sicher, dass alle Standardsteuerelemente konsistent mit dem Betriebssystem sind: Hintergrundfarbe ist standard und müssen keine Steuerelemente eine spezielle Re auf Vorlagen basierende Formatvorlage, die sie sich von Standardsteuerelementen angezeigt wird.  
  
-   Überprüfen Sie die Ränder im Formular müssen 12 Pixel und einheitliches und konsistentes sollte angezeigt werden.  
  
-   Stellen Sie sicher, dass Dialogfelder erscheinen in der IDE-Shell oder das Fenster, das sie erzeugte zentriert.  
  
-   Wenn aussagekräftig sind, sollte Dialogfelder in der Größe veränderbar sein. Für Dialoge, die in der Größe veränderbar sind, stellen Sie sicher, dass beim Ändern der Größe, die entsprechenden Steuerelemente ändern müssen, während andere Teile des Dialogs konstant bleiben.  
  
-   Stellen Sie sicher, dass in der Größe veränderbaren Dialoge jeder Benutzer angepasst Größe (Größe, Position, Erweiterung von Dialogfeld-Steuerelemente usw.) beibehalten.  
  
-   Stellen Sie sicher, dass kein Symbol in der Titelleiste vorhanden ist.  
  
-   Stellen Sie sicher, dass es keine minimieren und Maximieren-Schaltflächen in der Titelleiste stehen.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Dialogfeld vorgangsschaltflächen (gilt nur für Visual Studio-Client)  
  
-   Überprüfen Sie, ob vorgangsschaltflächen in dieser Reihenfolge: **OK**, **"Abbrechen"**, **übernehmen**.  
  
-   Überprüfen Sie, ob **OK** und **"Abbrechen"** Schaltflächen sind die Standardgröße: 75 x 23 Pixel.  
  
-   Überprüfen Sie, ob **OK** und **"Abbrechen"** Schaltflächen sind gleicher Größe unabhängig von der Länge der Zeichenfolge.  
  
-   Wenn die Bezeichnung auf eine Schaltfläche "Vorgang" die Schaltfläche, um breiter als Standard erforderlich ist, vergewissern Sie sich, die den entsprechenden **"Abbrechen"** Schaltfläche gleicher Größe ist.  
  
-   Stellen Sie sicher, dass ein 6-Pixel-Auffüllung zwischen Schaltflächen und die entsprechenden Steuerelemente vorhanden ist.  
  
-   Überprüfen Sie, ob die **OK** und **"Abbrechen"** Schaltflächen verfügen nicht über Zugriffstasten (Zugriffstasten, die durch einen unterstrichenen Buchstaben definiert).  
  
-   Vergewissern Sie sich, eine Schaltfläche (i. d. r. **OK**) standardmäßig den Fokus hat.  
  
-   Überprüfen Sie, ob **Esc** bricht das Dialogfeld "  
  
-   Überprüfen Sie, ob **EINGABETASTE** die Standardschaltfläche ausgeführt wird, wenn der Fokus nicht in einem Steuerelement befindet, die EINGABETASTE verarbeitet.  
  
-   Überprüfen Sie, ob die **OK** und **"Abbrechen"** Schaltflächen werden in der unteren rechten Ecke des Dialogfelds positioniert. In wenigen Ausnahmen ist es akzeptabel sind, um in der oberen rechten Ecke vertikal gestapelt werden.  
  
-   Stellen Sie sicher, dass die vertikale Konfiguration verwendet wird, nur, wenn andere Schaltflächen in eine horizontale Ausrichtung innerhalb des Dialogfelds sind.  
  
### <a name="control-standards"></a>Kontrollstandards  
  
#### <a name="general"></a>Allgemein  
  
-   Stellen Sie sicher, dass, wenn möglich, es gute Standardwerte gibt für die Interaktion des Benutzers und direkte Benutzer auf einem sicheren oder allgemeine Ergebnis zu beschleunigen.  
  
-   Stellen Sie sicher, dass die Standardsteuerelemente dasselbe Verhalten auf, damit Benutzer wissen, was basierend auf frühere Erfahrung ausgeführt wird.  
  
#### <a name="label-controls"></a>Label-Steuerelemente  
  
-   Stellen Sie sicher, dass jedes Steuerelement eine Bezeichnung wurde und jede Bezeichnung visuell das Steuerelement (in der Regel innerhalb eines Pixelbereichs für den 4-6-) zugeordnet ist, und näher an das entsprechende Steuerelement als für andere Steuerelemente ist.  
  
-   Stellen Sie sicher, dass Bezeichnungen leeren positioniert sind Links, mit dem Steuerelement Kante nach links, wenn oben positioniert und horizontal, zentriert, so, dass die Baseline der Bezeichnung die Grundlinie der Eingabetext ausgerichtet ist, wenn links positioniert.  
  
-   Stellen Sie sicher, dass mehrere gestapelte Bezeichnung und Eingabesteuerelemente auf der linken Seite eines Steuerelements positioniert ist, die Bezeichnungen linksbündig werden und denselben Abstand vom Rand des Dialogfelds nie leeren, Recht und die jeweils denselben Abstand von den Steuerelementen. Paare sollten gleichmäßig verteilt werden, es sei denn, sie zusätzliche Abstand um Gruppierung anzugeben.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Eingabesteuerelemente (Textfelder und Kombinationsfelder)  
  
-   Stellen Sie sicher, dass bei der Verwendung der Umgebung Standardschriftart gibt die Anzeigehöhe für Textfelder, Kombinationsfelder und Schaltflächen alle 23 Pixel.  
  
-   Wenn Hinweistext verwendet wird, stellen Sie sicher, dass die Farbe, um festgelegt ist `Environment.ControlEditHintText` mithilfe des Diensts Farbe.  
  
-   Wenn das Feld ein erforderliches Feld, das als solche identifiziert werden müssen, stellen Sie Folgendes sicher:  
  
    -   die die Hintergrundfarbe festlegen, um `Environment.ControlEditRequiredBackground` und Vordergrund festgelegt ist `Environment.ControlEditRequiredHintText`  
  
    -   ergibt sich Hinweistext innerhalb des Steuerelements, das wie **"\<erforderlich >"**  
  
#### <a name="button-controls"></a>Schaltflächen-Steuerelemente  
  
-   Überprüfen Sie die Schaltflächen eine Mindestgröße von 75 x 23 Pixel, es sei denn, die länger Text Statuswerte berücksichtigt werden können.  
  
-   Stellen Sie sicher, dass die Schaltflächen verlassen haben und die Ränder eines 3 bis 5 Pixel sowie Auffüllung für den Inhalt mit der rechten Maustaste.  
  
-   Es ist zulässig, verwenden Sie eine kleine quadratische Schaltfläche mit nur einem Auslassungszeichen **[...]**  darauf anstelle von einer **[durchsuchen...]**  Schaltfläche (oder eine ähnliche Funktion). Wenn verwendet, stellen Sie sicher, dass die Schaltfläche 23 x 23 groß ist.  
  
-   Wenn es mehr als eine **[durchsuchen...]**  in einem Dialog, und klicken Sie dann überprüfen Sie, ob die verkürzte Version (nur Auslassungszeichen **[...]** ) wird für alle verwendet.  
  
-   Vergewissern Sie sich, mit den Auslassungspunkten **[...]**  Schaltflächen verfügen nicht über ein mnemonisches Zeichen. Wenn der Fokus auf das Eingabesteuerelement daneben befindet, sollten eine Registerkarte den Fokus auf die Schaltfläche mit den Auslassungspunkten verschieben.  
  
-   Überprüfen, ob Schaltflächen Befehlen und Befehlslinks, die sekundären-Benutzeroberfläche zu starten, die weitere Benutzereingaben erfasst, als Ellipse beenden müssen **[...]** .  
  
#### <a name="hyperlinks"></a>Hyperlinks  
  
-   Stellen Sie sicher, dass ein Linksteuerelement nie Rot, wenn aktive blinkt. Dies ist ein Indikator, dass der Color-Dienst nicht verwendet wird  
  
-   Stellen Sie sicher, dass die VS-Farben, die verwendet werden:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Stellen Sie sicher, dass links angezeigt, mit "Unterstreichen" keine Blau, es sei denn, in einem Absatz eingebettet werden.  
  
#### <a name="check-boxes"></a>Kontrollkästchen  
  
-   Wenn Sie das Kontrollkästchen mehrzeilige Texteingabe verfügt, stellen Sie sicher, dass das Feld mit der ersten Zeile des Texts, die nicht über alle Zeilen vertikal zentriert ausgerichtet.  
  
-   Stellen Sie sicher, dass Kontrollkästchen immer eine binäre hinweisen und nicht den Benutzer navigieren oder Seiten oder neue Fenster zu öffnen.  
  
-   Wenn Sie das Kontrollkästchen eine Option im Zusammenhang mit eines Eingabesteuerelements darstellt, überprüfen Sie, ob es links und sehr nahe unter das entsprechende Steuerelement an, deren Beziehung leeren positioniert ist.  
  
-   Stellen Sie sicher, dass das Kontrollkästchen ist **nie** als Mittel verwendet werden, um den gesamten Inhalt eines Dialog- oder die Seite zu aktivieren.  
  
#### <a name="group-boxes"></a>Gruppenfelder  
  
-   Stellen Sie sicher, dass ein Dialogfeld, das den gesamten Inhalt des Dialogfelds enthält ein einzelnes Gruppenfeld darin nicht enthält.  
  
-   Stellen Sie sicher, dass mindestens zwei Steuerelemente innerhalb jeder Gruppe vorhanden sind.  
  
-   Selten sollte mehr als zwei Gruppenfelder auf ein Dialogfeld angezeigt werden.  
  
-   Stellen Sie sicher, dass keine geschachtelte Gruppenfelder vorhanden sind.  
  
### <a name="icons"></a>Symbole  
  
-   Überprüfen Sie, ob Symbole ordnungsgemäß invertierten in das Design "dunkel".  
  
-   Stellen Sie sicher, dass alle Symbole auf Kernkonzepte basieren.  
  
-   Überprüfen, ob jedes Symbol distinct, einfach zu erkennen und enthält nicht mehr als zwei Konzepte (ohne Status Modifizierer/Sprache).  
  
-   Stellen Sie sicher, dass das Symbol "Basis" zentriert im Bereich angezeigt wird.  
  
-   Stellen Sie sicher, dass alle Symbole im Modus für hohe Kontraste lesbar angezeigt werden.  
  
-   Stellen Sie sicher, dass jede Farbe verwendet Farbe Nutzung Standards ausgerichtet.  
  
-   Stellen Sie sicher, dass keine Vermeidung von Rändern (Rahmen) vorhanden sind, um Symbole. (Wenn vorhanden ist, sollte der Lichthof die Hintergrundfarbe der angrenzenden Benutzeroberfläche entsprechen).  
  
### <a name="touch-enabled-ui"></a>Touchscreen-Benutzeroberfläche  
  
-   Vergewissern Sie sich die interaktive Steuerelementen groß genug ist, werden einfach touchable – minimale sind **23 x 23 Pixel** Größe  
  
-   Stellen Sie sicher, dass die am häufigsten verwendeten Steuerelemente mindestens **40 x 40 Pixel** Größe.  
  
-   Überprüfen Sie, ob interaktive Steuerelementen mindestens **5 Pixel Abstand** dazwischen