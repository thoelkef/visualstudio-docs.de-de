---
title: UX Essentials für Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698332"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials für Visual Studio

## <a name="best-practices"></a>Bewährte Methoden

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Seien Sie innerhalb der Visual Studio-Umgebung konsistent.

- Folgen Sie vorhandenen [Interaktionsmustern](interaction-patterns-for-visual-studio.md) innerhalb der Shell.

- Design-Features, die mit der visuellen Sprache und [handwerkshandwerklichen Anforderungen](evaluation-tools-for-visual-studio.md)der Schale übereinstimmen.

- Verwenden Sie freigegebene Befehle und Steuerelemente, wenn sie vorhanden sind.

- Verstehen der Visual Studio-Hierarchie und der Einrichtung des Kontexts und der Laufwerke der Benutzeroberfläche.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Verwenden Sie den Umgebungsdienst für Schriftarten und Farben.

- Die Benutzeroberfläche sollte die aktuelle [Umgebungsschriftarteinstellung](fonts-and-formatting-for-visual-studio.md) beachten, es sei denn, sie wird zur Anpassung auf der Seite Schriftarten und Farben im Dialogfeld Optionen verfügbar gemacht.

- UI-Elemente müssen den [VSColor-Dienst](colors-and-styling-for-visual-studio.md)verwenden, indem sie freigegebene Umgebungstoken oder funktionsspezifische Token verwenden.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Machen Sie alle Bilder konsistent mit dem neuen VS-Stil.

- Befolgen Sie Visual Studio-Entwurfsprinzipien für Symbole, Glyphen und andere Grafiken.

- Platzieren Sie Text nicht in grafischen Elementen.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Design aus einer benutzerzentrierten Perspektive.

- Erstellen Sie den Aufgabenfluss vor den einzelnen Features darin.

- Machen Sie sich mit Ihren Benutzern vertraut und machen Sie dieses Wissen in Ihrer Spezifikation explizit.

- Bewerten Sie beim Überprüfen der Benutzeroberfläche die gesamte Erfahrung sowie die Details.

- Entwerfen Sie ihre Benutzeroberfläche so, dass sie funktional und attraktiv bleibt, unabhängig von Gebietsschema oder Sprache.

## <a name="screen-resolution"></a>Bildschirmauflösung

### <a name="minimum-resolution"></a>Mindestauflösung

- Die Mindestauflösung für Visual Studio 2015 beträgt **1280x720**. Dies bedeutet, dass es *möglich* ist, Visual Studio mit dieser Auflösung zu verwenden, obwohl es sich möglicherweise nicht um eine optimale Benutzererfahrung handelt. Es gibt keine Garantie, dass alle Aspekte bei Auflösungen unter 1280x720 verwendet werden können.

- Die Zielauflösung für Visual Studio ist **1366x768**. Dies ist die niedrigste Auflösung, mit der wir eine *gute* Benutzererfahrung versprechen.

- Die anfängliche Dialoghöhe sollte **kleiner als 700 Pixel**sein, sodass sie innerhalb der minimalen Auflösung des IDE-Frames bei 96 dpi passt.

### <a name="high-density-displays"></a>Displays mit hoher Dichte
 Die Benutzeroberfläche in Visual Studio muss bei allen DPI-Skalierungsfaktoren, die Windows sofort unterstützt, gut funktionieren: 150 %, 200 % und 250 %.

## <a name="anti-patterns"></a>Anti-Muster
 Visual Studio enthält viele Beispiele für die Benutzeroberfläche, die unseren Richtlinien und bewährten Methoden entsprechen. Um konsistent zu sein, leihen sich Entwickler häufig Produkt-UI-Entwurfsmuster, die denen ähneln, die sie erstellen. Obwohl dies ein guter Ansatz ist, der uns hilft, Konsistenz in der Benutzerinteraktion und visuellen Design zu fördern, versenden wir gelegentlich Funktionen mit ein paar Details, die unsere Richtlinien aufgrund von Zeitplaneinschränkungen oder Fehlerpriorisierung nicht erfüllen. In diesen Fällen möchten wir nicht, dass Teams eines dieser "Antimuster" kopieren, da sie eine fehlerhafte oder inkonsistente Benutzeroberfläche in der Visual Studio-Umgebung vermehren.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Erforderliche Felder/Einstellungen, die standardmäßig im Fehlerzustand angezeigt werden

#### <a name="feature-team-goals"></a>Feature-Teamziele

- Warnen Sie Benutzer, dass sie ein Element hinzugefügt haben, das konfiguriert werden muss.

- Lenken Sie die Aufmerksamkeit des Benutzers auf die Bereiche, die eingaben müssen.

#### <a name="anti-pattern-solution"></a>Anti-Muster-Lösung
 Sobald der Benutzer eine Aktion initiiert hat und bevor er die Aufgabe abgeschlossen hat, platzieren Sie sofort kritische Stoppsymbole neben den Bereichen, die eine Konfiguration benötigen.

#### <a name="example-manifest-designer-declarations"></a>Beispiel: Manifest Designer-Deklarationen
 Wenn Sie der Liste eine Deklaration hinzufügen, wird sie sofort in einen Fehlerzustand versetzt, der so lange beibehalten wird, bis der Benutzer die erforderlichen Eigenschaften festlegt.

 In diesem Fall gibt es ein zusätzliches Problem, da&times;das für die Warnung verwendete Symbol ein " "-Symbol enthält, sodass das allgemeine Entfernen-Symbol nicht neben ihm verwendet werden kann. Daher verwendet die Benutzeroberfläche eine Schaltfläche Entfernen, ein klobigeres Steuerelement.

 ![Wenn Sie die Benutzeroberfläche standardmäßig in einen Fehlerstatus versetzen, handelt es sich um ein Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-Muster")<br />Wenn Sie die Benutzeroberfläche standardmäßig in einen Fehlerstatus versetzen, handelt es sich um ein Visual Studio-Antimuster.

#### <a name="alternatives"></a>Alternativen

Eine bessere Lösung für dieses Problem ist:

- Erlauben Sie dem Benutzer, eine Deklaration ohne Warnung hinzuzufügen, und wechseln Sie dann sofort, um Eigenschaften für das Element festzulegen.

- Fügen Sie das Warnsymbol (Golddreieck) hinzu, wenn der Fokus vom Element verschoben wird, z. B. um eine weitere Deklaration zur Liste hinzuzufügen oder um zu versuchen, Registerkarten innerhalb des Designers zu ändern.

- Wenn der Benutzer versucht, Registerkarten zu ändern, bevor Eigenschaften für Deklarationen gesetzt werden, öffnen Sie ein Dialogfeld, in dem erklärt wird, dass die Anwendung erst erstellt wird (oder welche Auswirkungen dies ausbleibt), bis die Warnungen aufgelöst sind. Wenn der Benutzer das Dialogfeld trotzdem ablehnt und Registerkarten ändert, wird der Registerkarte Deklarationen ein Symbol (kritisch oder warnung) hinzugefügt.

### <a name="multiple-clicks-to-dismiss-ui"></a>Mehrere Klicks zum Schließen der Benutzeroberfläche

#### <a name="feature-team-goals"></a>Feature-Teamziele
 Erlauben Sie dem Benutzer nicht, die Benutzeroberfläche zu schließen, ohne vorher den Erklärungstext zu sehen.

#### <a name="anti-pattern"></a>Anti-Muster
 Das Team, das die Videolinks an verschiedenen Stellen innerhalb der&times;VS-Benutzeroberfläche einfügte, entschied sich gegen das allgemeine Muster der " Schaltfläche "Schließen" und tooltip- wie von UX angegeben, und implementierte stattdessen einen Dropdown- und "Nicht erneut anzeigen"-Link.

#### <a name="example-video-links-in-team-explorer"></a>Beispiel: Videolinks im Team Explorer
Wenn der Benutzer vor dem Schließen der Benutzeroberfläche erklärenden Text lesen muss, ist dies ein Antimuster in Visual Studio. Richtig gestaltet, sollten Videolinks eine QuickInfo mit zusätzlichen Informationen zum&times;Mauszeiger anzeigen, und wenn Sie auf " klicken, sollte die Nachricht ohne weitere Interaktion verworfen werden.

 ![Erläuternder Text anti&#45;Muster &#45; falsch](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "FalscheVerwendungvon Mehrfachklicks")<br />Falsches Video-Link-Muster

Anstelle einer einfachen Schaltfläche zum Schließen (ein Klick) ist der Benutzer gezwungen, zwei Klicks zu verwenden, um die Benutzeroberfläche einfach an jedem Ort zu schließen, an dem die Videolinks angezeigt werden.

Der richtige Entwurf für diese Situation besteht darin, dem Muster zu folgen, das Internet Explorer, Office und Visual Studio gemeinsam ist: Bei der Maus kann der Benutzer die Beschreibung der QuickInfo sehen, und mit einem Klick wird die Benutzeroberfläche ausgeblendet.

 ![Erläuternder Text anti&#45;Muster &#45; korrekt](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-musterkorrekt")<br />Korrektes Video-Link-Muster

### <a name="using-command-bars-for-settings"></a>Verwenden von Befehlsleisten für Einstellungen

**Abbildung A** stellt dieses Antimuster dar: Setzen Sie eine Einstellung unter eine Befehlsschaltfläche, die für mehr als nur den Befehl gilt. In dieser Skizze gibt es neben Debuggen starten – wie View in Browser, Start Without Debugging und Step Into – Befehle, die die ausgewählte Einstellung berücksichtigen.

![Abbildung A: Befehlsleiste Antimuster](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-Muster-FigurA")<br />Abbildung A: Befehlsleiste Antimuster

Etwas besser, aber immer noch unerwünscht, ist das Setzen von Einstellungen dieses Typs in die Symbolleisten, wie in **Abbildung B**dargestellt. Während Split-Buttons weniger Platz benötigen und daher eine Verbesserung gegenüber Dropdowns sind, verwenden beide Designs immer noch eine Symbolleiste, um etwas zu fördern, das nicht wirklich ein Befehl ist.

![Abbildung B: Besser, aber immer noch ein Befehlsleisten-Antimuster](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Muster-FigurB")<br />Abbildung B: Besser, aber immer noch ein Befehlsleisten-Antimuster

In der richtigen Vorgehensweise in **Abbildung C**ist die Einstellung an eine Reihe von Befehlen gebunden. Es wird keine globale Einstellung festgelegt, und wir wechseln nur zwischen vier Befehlen. Dies ist die einzige Situation, in der Befehle in der Symbolleiste akzeptabel sind.

![Abbildung C: Korrekte Verwendung des Visual Studio-Befehlsleistenmusters](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Muster-FigureC")<br />Abbildung C: Korrekte Verwendung des Visual Studio-Befehlsleistenmusters

### <a name="control-anti-patterns"></a>Kontrolle von Anti-Mustern
 Einige Anti-Muster sind einfach falsche Verwendung oder Darstellung eines Steuerelements oder einer Gruppe von Steuerelementen.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Unterstreichung, die als Gruppenbezeichnung und nicht als Hyperlink verwendet wird
 Unterstreichungstext sollte nur für Hyperlinks verwendet werden.

 **Schlecht:**\
 ![Unterstrichener Text, der kein Hyperlink ist, ist ein Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Unterstrichener Text, der kein Hyperlink ist, ist ein Visual Studio-Antimuster.

 **gut:**\
 ![Richtig formatiert, wird Nicht-Hyperlink-Text in der Umgebungsschriftart ungeschmückt angezeigt.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Richtig formatiert, wird Nicht-Hyperlink-Text in der Umgebungsschriftart ungeschmückt angezeigt.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Ein Klicken auf ein Kontrollkästchen führt zu einem Popup-Dialogfeld
 Wenn Sie im Assistenten "Windows Azure Application veröffentlichen" auf das Kontrollkästchen "Remotedesktop für alle Rollen aktivieren" klicken, wird sofort ein Popup-Dialogfeld, ein Visual Studio-Antimuster, angezeigt. Darüber hinaus wird das Kontrollkästchenfeld nicht mit einem Kontrollkästchen gefüllt, nachdem es ausgewählt wurde, ein anderes Interaktions-Antimuster.

 ![Das Öffnen eines Dialogfelds nach dem Klicken auf ein Kontrollkästchen ist ein Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Das Öffnen eines Dialogfelds nach dem Klicken auf ein Kontrollkästchen ist ein Visual Studio-Antimuster.

### <a name="hyperlink-anti-patterns"></a>Antimuster für Hyperlink
 Das folgende Beispiel enthält zwei Antimuster:

1. Das Rotdrehen im Vordergrund bedeutet, dass die richtige freigegebene Farbe des Schriftartdienstes nicht verwendet wird.

2. "Weitere Informationen" ist nicht der geeignete Text für einen Link zu einem konzeptionellen Thema. Das Ziel des Benutzers ist es nicht, mehr zu erfahren, es ist, die Auswirkungen seiner Wahl zu verstehen.

   ![Das Ignorieren des Farbdienstes und die Verwendung von "Weitere Informationen" für Hyperlinks sind Visual Studio-Antimuster.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Das Ignorieren des Farbdienstes und die Verwendung von "Weitere Informationen" für Hyperlinks sind Visual Studio-Antimuster.

**Bessere Lösung:** Stellen Sie die Frage, die der Benutzer stellen würde, indem Sie auf den Link klicken. Beispiel:

- Wie funktionieren Windows Azure-Dienste?

- Wann benötige ich ein Windows Azure Mobile Services-Projekt?

#### <a name="using-click-here-for-links"></a>Verwenden von "Klicken Sie hier" für Links
 Hyperlinks sollten selbstbeschreibend sein. Es ist ein Anti-Muster, um "Klicken Sie hier" oder eine ähnliche Variation zu verwenden.

 **Schlecht:** "Klicken Sie hier, um Anweisungen zum Erstellen eines neuen Projekts zu erhalten."

 **Gut:** "Wie erstelle ich ein neues Projekt?"
