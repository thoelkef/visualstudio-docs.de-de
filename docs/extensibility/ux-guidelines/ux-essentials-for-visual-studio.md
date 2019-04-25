---
title: UX Essentials für Visual Studio | Microsoft-Dokumentation
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e97aa60a983eef3034eab28f7835edc1abb6734
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098661"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials für Visual Studio

## <a name="best-practices"></a>Bewährte Methoden

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. In Visual Studio-Umgebung konsistent sein.

- Führen Sie die vorhandenen [Interaktionsmuster](interaction-patterns-for-visual-studio.md) innerhalb der Shell.

- Entwerfen Sie Funktionen zur visuellen Sprache von der Shell und [handwerkliches können Anforderungen](evaluation-tools-for-visual-studio.md).

- Verwenden Sie freigegebene Befehle und Steuerelemente aus, wenn sie vorhanden sind.

- Verstehen Sie die Visual Studio und wie die Anwendung Kontext wird und die Benutzeroberfläche steuert.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Verwenden Sie die Umgebung-Dienst für Schriftarten und Farben.

- Benutzeroberfläche berücksichtigt die aktuelle [Umgebungsschriftart](fonts-and-formatting-for-visual-studio.md) festlegen, es sei denn, es für die Anpassung auf der Seite "Schriftarten und Farben" in das Dialogfeld "Optionen" verfügbar gemacht wird.

- UI-Elemente verwenden, müssen die [VSColor Service](colors-and-styling-for-visual-studio.md), verwenden der freigegebenen Umgebung Token oder featurespezifische-Token.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Stellen Sie alle Bilder konsistent mit dem neuen Visual Studio-Stil.

- Führen Sie Visual Studio-Entwurfsprinzipien für Symbole, Symbole und andere Grafik aus.

- Platzieren Sie Text in grafischen Elementen nicht.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Vom Standpunkt der benutzerorientierten entwerfen.

- Erstellen Sie die Aufgabenverlauf, bevor Sie darin die einzelnen Funktionen.

- Mit Ihren Benutzern vertraut sein, und machen Sie dieses Wissen in Ihrem-Spezifikationen explizit.

- Bei der Überprüfung der Benutzeroberflächenautomatisierungs bewerten Sie die vollständige Benutzeroberfläche als auch die Details.

- Entwerfen Sie die Benutzeroberfläche so, dass sie funktionsfähig und unabhängig vom Gebietsschema oder der Sprache attraktive bleibt.

## <a name="screen-resolution"></a>Bildschirmauflösung

### <a name="minimum-resolution"></a>Mindestauflösung

- Wird die mindestauflösung für Visual Studio 2015 **1280 x 720**. Dies bedeutet, dass es *möglich* mit Visual Studio diese Auflösung, obwohl es nicht die optimale benutzerfreundlichkeit möglicherweise. Es gibt keine Garantie, dass alle Aspekte bei einer Auflösung von 1280 x 720 kleiner verwendet werden können.

- Die zielauflösung für Visual Studio ist **1366 x 768**. Dies ist die niedrigsten Auflösung, an dem wir versprechen, einer *gute* benutzererfahrung.

- Erste Dialogfeld Höhe muss **weniger als 700 Pixel**, sodass sie in die minimale Auflösung der des IDE-Fensterrahmens mit 96 dpi passt.

### <a name="high-density-displays"></a>Mit hoher Dichte zeigt
 Benutzeroberfläche in Visual Studio muss auch in alle DPI-Skalierungsfaktoren arbeiten, die von Windows standardmäßig unterstützt: 150 %, 200 % und 250 %.

## <a name="anti-patterns"></a>Anti-Muster
 Visual Studio enthält viele Beispiele der Benutzeroberfläche, die unsere Richtlinien und bewährte Methoden befolgen. In dem Bestreben konsistent ist nutzen die Entwickler häufig aus Produkt UI-Entwurfsmuster ähnelt, was sie erstellen. Obwohl dies ein guter Ansatz, hilft uns Konsistenz bei der Interaktion des Benutzers und den visuellen Entwurf fördern, wir gelegentlich Funktionen mit ein paar Details mitgeliefert werden, die nicht erfüllt unsere Richtlinien aufgrund der Einschränkungen in Zeitplan oder vollziehen des Austritts Priorisierung ist. In diesen Fällen möchten wir Teams, kopieren Sie eine der folgenden "Anti-Muster" nicht, weil sie ungültige oder inkonsistente UI in Visual Studio-Umgebung angelegt.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Erforderliche Felder/Einstellungen, die standardmäßig im Status "Fehler" angezeigt

#### <a name="feature-team-goals"></a>Feature-Team-Ziele

- Warnen Sie Benutzer, dass sie ein Element hinzugefügt haben, die konfiguriert werden müssen.

- Zeichnen Sie die Aufmerksamkeit des Benutzers auf die Bereiche, die Eingabe benötigen.

#### <a name="anti-pattern-solution"></a>Antimuster für Projektmappen
 Platzieren Sie, sobald der Benutzer eine Aktion initiiert hat und bevor sie die Aufgabe abgeschlossen haben, sofort kritische Hand Symbole neben den Bereichen, die Konfiguration erforderlich.

#### <a name="example-manifest-designer-declarations"></a>Beispiel: Manifest-Designer-Deklarationen
 Eine Deklaration direkt zur Liste hinzufügen werden in einem Fehlerzustand befindet, die persistent gespeichert, bis der Benutzer die erforderlichen Eigenschaften festlegt.

 In diesem Fall eine zusätzliche Bedeutung vorhanden ist, da das Symbol, das verwendet wird, für die Warnung enthält einen "&times;" Symbol, sodass das allgemeine Remove-Symbol neben verwendet werden kann. Daher wird die Benutzeroberfläche eine Schaltfläche "entfernen" ein mehr umständlich Steuerelement verwendet.

 ![Benutzeroberfläche in einem Fehlerzustand platzieren, in der Standardeinstellung ist ein Visual Studio-Anti-Muster. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-Muster")<br />Benutzeroberfläche in einem Fehlerzustand platzieren, in der Standardeinstellung ist ein Visual Studio-Anti-Muster.

#### <a name="alternatives"></a>Alternativen

Eine bessere Lösung für dieses Problem ist auf:

- Erlaubt dem Benutzer eine Deklaration ohne Warnung hinzufügen, und klicken Sie dann sofort zum Festlegen von Eigenschaften für das Element verschieben.

- Fügen Sie das Symbol "Warnung" (gold Dreieck) Wenn der Fokus aus dem Element, wie z. B. eine andere Deklaration zur Liste hinzufügen oder versuchen, die Registerkarten im Designer zu ändern.

- Wenn der Benutzer versucht, die Registerkarten ändert, vor dem Festlegen von Eigenschaften für alle Deklarationen, pop ein Dialogfeld darauf hingewiesen, dass die Anwendung nicht erstellt werden (oder alle der Auswirkungen), bis die Warnungen aufgelöst werden. Wenn der Benutzer das Dialogfeld schließt und Registerkarten wird trotzdem klicken Sie dann ein Symbol (kritisch oder Warnung, je nach Bedarf) zur Registerkarte "Deklarationen" hinzugefügt.

### <a name="multiple-clicks-to-dismiss-ui"></a>Mehrere Klicks, um die Benutzeroberfläche zu schließen.

#### <a name="feature-team-goals"></a>Feature-Team-Ziele
 Keine ermöglicht dem Benutzer um die Benutzeroberfläche zu schließen, ohne zuerst den erläuternden Text anzeigen zu lassen.

#### <a name="anti-pattern"></a>Anti-Muster
 Das Einfügen von diese Videolinks in verschiedenen Stellen in der Benutzeroberfläche von Visual Studio-Team entschieden, dem allgemeinen Muster der "&times;" Schließen Schaltfläche und QuickInfo Erklärung, wie von UX angegeben, und stattdessen eine Dropdown-Liste implementiert, und verknüpfen Sie die "Nicht mehr anzeigen".

#### <a name="example-video-links-in-team-explorer"></a>Beispiel: Videolinks in Team Explorer
Das Erzwingen eines erklärenden Text zu lesen, vor dem Schließen der Benutzeroberfläche des Benutzers ist ein Anti-Muster in Visual Studio. Richtig entworfene und Videofunktionen Links sollte eine QuickInfo mit weiteren Informationen angezeigt, wenn darauf gezeigt wird, und klicken auf die "&times;" sollte die Meldung ohne weitere Interaktion zu schließen.

 ![Erklärender Text anti-&#45;Muster &#45; falsche](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Falsche Videolink-Muster

Anstelle einer einfachen Schaltfläche "Schließen" (einem Klick) wird der Benutzer gezwungen, zwei aufeinander folgende Mausklicks zu verwenden, um die Benutzeroberfläche an jeder Stelle einfach zu verwerfen, die diese Videolinks angezeigt werden.

Der richtige Entwurf für diese Situation ist das allgemeine Muster zur Internet Explorer, Office und Visual Studio folgen: Wenn darauf gezeigt wird, kann dem Benutzer die QuickInfo-Beschreibung angezeigt, und nur einem Klick wird die Benutzeroberfläche ausgeblendet.

 ![Erklärender Text anti-&#45;Muster &#45; richtig](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-Muster-korrigieren")<br />Richtige Videolink-Muster

### <a name="using-command-bars-for-settings"></a>Mithilfe der Befehlsleisten für Einstellungen

**Abbildung A** dieses Antimuster darstellt: platzieren eine Einstellung unter eine Befehlsschaltfläche, die auf mehr als nur den Befehl angewendet wird. Bei dieser Version stehen die folgenden Befehle, die neben dem Debugging starten –-ähnliche Ansicht in Browser starten ohne Debugging sowie schrittweise ausführen –, die die ausgewählte Einstellung berücksichtigt.

![Abbildung A: Antimuster für Befehlsleiste](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-Muster – FigureA")<br />Abbildung A: Antimuster für Befehlsleiste

Etwas bessere Leistung, der aber dennoch unerwünschtem, wäre, Einstellungen dieses Typs in den Symbolleisten, siehe **Abbildung B**. Unterteilte Schaltflächen belegen weniger Speicherplatz und sind daher eine Verbesserung über die Dropdown-Elemente, werden beide Entwürfe eine Symbolleiste weiterhin verwendet, um etwas höher zu stufen, die einen Befehl handelt es sich nicht.

![Abbildung b Besser, aber dennoch ein Antimuster für Befehlsleiste](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Muster – FigureB")<br />Abbildung b Besser, aber dennoch ein Antimuster für Befehlsleiste

In den richtigen Lösungsansatz **Abbildung C**, die Einstellung an eine Reihe von Befehlen gebunden ist. Es gibt keine globale Einstellung festgelegt wird, und wir nur zwischen vier Befehle wechseln. Dies ist die einzige Situation, in der Befehle auf der Symbolleiste zulässig sind.

![Abbildung "c:" Korrigieren Sie die Verwendung von Visual Studio-Befehlsleiste Befehlsmuster](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Muster – FigureC")<br />Abbildung "c:" Richtige Verwendung von Visual Studio-Befehlsleiste Befehlsmuster

### <a name="control-anti-patterns"></a>Anti-Steuerelementmuster
 Einige Antimuster für sind einfach falsche Verwendung oder eine Präsentation eines Steuerelements oder einer Gruppe von Steuerelementen.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Unterstreichungen, die verwendet werden, während eine gruppenbezeichnung, nicht auf einen Link
 Unterstrichenen Text sollte nur für Links verwendet werden.

 **Bad:**\
 ![Unterstrichener Text, der keinen Link ist ein Visual Studio-Anti-Muster. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-G_GroupLabelIncorrect")<br />Unterstrichener Text, der keinen Link ist ein Visual Studio-Anti-Muster.

 **Gute:**\
 ![Richtig formatiert wurde, wird angezeigt, nicht-Hyperlink-Text nicht erweiterten in die Umgebungsschriftart. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-H_GroupLabelCorrect")<br />Richtig formatiert wurde, wird angezeigt, nicht-Hyperlink-Text nicht erweiterten in die Umgebungsschriftart.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Durch Klicken auf ein Kontrollkästchen-Ergebnisse in einem Popupdialogfeld
 Klicken im Assistenten "Windows Azure-Anwendung veröffentlichen" das Kontrollkästchen "Remotedesktop für alle Rollen aktivieren" sofort wird ein Popup-Dialogfeld ein Visual Studio-Anti-Muster. Darüber hinaus das Kontrollkästchen ist nicht ausfüllen des Feldes mit einem Kontrollkästchen nach ausgewählt wird, ein weiteres Anti-Interaktionsmuster.

 ![Nach dem Klicken auf ein Kontrollkästchen ein Visual Studio-Anti-Muster wird aufzurufen ein Dialogfeld. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-I_CheckboxPopup")<br />Nach dem Klicken auf ein Kontrollkästchen ein Visual Studio-Anti-Muster wird aufzurufen ein Dialogfeld.

### <a name="hyperlink-anti-patterns"></a>Antimuster für Hyperlink
 Das folgende Beispiel enthält zwei Anti-Muster:

1. Im Vordergrund roten aktivieren, wenn darauf gezeigt wird also nicht die richtige freigegebene Farbe aus dem Schriftartdienst verwendet wird.

2. "Weitere Informationen" ist nicht den entsprechenden Text einen Link auf ein grundlegendes Thema. Des Benutzers Ziel ist nicht mehr, erfahren, um die Auswirkungen ihrer Wahl zu verstehen ist.

   ![Ignorieren den Dienst für die Farbe, und Verwenden von "Erfahren Sie mehr" für Links sind Antimuster für Visual Studio. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-J_HyperlinkIncorrect")<br />Ignorieren den Dienst für die Farbe, und Verwenden von "Erfahren Sie mehr" für Links sind Antimuster für Visual Studio.

**Eine bessere Lösung:** Stellen Sie die Frage, die der Benutzer aufgefordert werden würde, auf den Link. Zum Beispiel:

- Wie funktionieren die Windows Azure-Dienste?

- Wann benötige ich ein Windows Azure Mobile Services-Projekt?

#### <a name="using-click-here-for-links"></a>Mithilfe von "Hier klicken", links
 Links sollte erklären sich von selbst. Es ist ein Anti-Muster verwenden "Hier klicken" oder eine ähnliche Variante.

 **Ungültige:** "Klicken Sie hier, um Anweisungen zum Erstellen eines neuen Projekts."

 **Gute:** "Wie erstelle ich ein neues Projekt?"
