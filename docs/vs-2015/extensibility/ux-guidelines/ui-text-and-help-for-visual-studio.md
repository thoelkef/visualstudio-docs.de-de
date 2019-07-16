---
title: Benutzeroberflächentext und -hilfe
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea4f2b49838340fcee41bc9c41ef94558e44825e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823616"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Benutzeroberflächentext und-Hilfe für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_UITextAndTerminology"></a> Benutzeroberflächentext und Terminologie
 Verständlich Text ist entscheidend, um effektive Benutzeroberfläche. Softwarebenutzer zu lesen sind tendenziell "Bezeichnungen" zuerst, nämlich die wichtigsten, um die aktuelle Aufgabe fertig zu stellen. Statischer Text wird weniger häufig gelesen. Planen Sie für Benutzer, ihre Arbeitssitzungen mit einer schnellüberprüfung, der das gesamte Fenster, gefolgt von der ein Lesen der Benutzeroberfläche in der angegebenen Reihenfolge ungefähre zu beginnen:

1. Interaktive Steuerelemente in der Mitte

2. Commit-Schaltflächen

3. Interaktive Steuerelemente, die an anderer Stelle gefunden.

4. Hauptanleitung

5. Zusätzliche erläuterungen

6. Fenstertitel

7. Anderen statischen Text im Hauptteil

### <a name="usage-patterns-for-ui-text"></a>Verwendungsmuster für Benutzeroberflächen-text

#### <a name="title-bar-text"></a>Titelleistentext
 Text der Titelleiste muss es sich um den Befehl übereinstimmen, der die Benutzeroberfläche erzeugt.

#### <a name="instructional-text-helper-text"></a>Anweisungstext (Hilfsprogramm Text)
 In einigen Dialogfeldern ist es hilfreich, die gut sichtbaren main Anweisungen erläutert, was Sie im Fenster oder auf der Seite. Dies wird manchmal als "Hilfsprogramm-Text" bezeichnet

##### <a name="writing-style-rules-for-helper-text"></a>Schreiben von Formatierungsregeln für Hilfetext

- Erläutern Sie nicht, die offensichtlich. Wenn es absolut notwendig ist, enthalten Sie keine Anweisungstext.

- Anweisungstext befindet sich immer am oberen Rand des Dialogfelds und finden Sie in der Task ausgeführt wird.

- Erklären Sie genau den Benutzern was sie tun müssen. Vermeiden Sie übermäßige Kommunikation und Redundanz.

- Überprüfen Sie jedes Fenster aus, und entfernen Sie doppelte Wörter und Anweisungen.

- Halten Sie kurze Anweisungstext. Wenn weitere Informationen erforderlich für bestimmte Benutzer oder Szenarien sind, geben Sie einen Link zu detaillierten konzeptionellen Themen online.

- Schreiben Sie den Text ein, sodass jedes Wort enthält die Gewichtung und erforderlich ist.

- Führen Sie die vorhandene Microsoft-Sicherheitsleitfaden für [Benutzeroberflächentext](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [Stil und Ton](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).

#### <a name="supplemental-instructions"></a>Zusätzliche Anweisungen
 Zusätzliche Anweisungen bieten zusätzliche Informationen, die den Benutzer verstehen, Steuerelemente oder Gruppierungen zu steuern. Dadurch kann zudem müssen Sie wissen, in welchem Format das Eingabesteuerelement erwartet Hinweistext umfassen. Verwenden Sie zusätzliche Anweisungen nur selten auf. Behalten sie für Fälle, in dem es wahrscheinlich ist, dass der Benutzer wird nicht vollständig die Auswirkungen der Wahl verstehen, die sie vornehmen.

 ![Ergänzender Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601-b_SupplementalText1")

 **Ergänzender Text in Visual Studio**

 ![Ergänzender Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601-c_SupplementalText2")

 **Ergänzender Text in Visual Studio**

#### <a name="infotips"></a>InfoTips
 Anweisungstext kann häufig so umfangreich, dass ein direktes in der Benutzeroberfläche zu positionieren oder kann nur an einen neuen Benutzer wie überladen für erfahrene Benutzern hilfreich sein. In diesem Fall sollte dem Lehrzwecken/Informationstext als QuickInfo in einem Infotipp platziert werden.

 Infotipps sollten in der Nähe von den Steuerelementen, die sie beziehen sich auf und sollten das bestimmte Infotipp-Symbol, das unaufdringliche noch nicht bemerkbar platziert werden.

 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-D_InfoTip")

 **Beispiel für ein Infotipp in Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Schreiben von Stilregeln für Infotipps

- Schreiben Sie Infotipps als vollständigen Sätzen. Sie erfordern bestimmte Verben großgeschrieben und setzen Sie satzendpunkte.

- Verwenden Sie Infotipps, um Ihren hauptanweisung oder Informationen ergänzen. Wenn Sie nur unterschiedliche Wörter die Grundidee wie bereits erwähnt, wird Sie keinen Infotipp erforderlich.

- Halten Sie Infotipps kurz und einfach. Verwenden Sie kurze Wörter und Plain, alltägliche Sprache, die unterstützt und fördert den Benutzer.

- Führen Sie die vorhandene Microsoft-Sicherheitsleitfaden für [Benutzeroberflächentext](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [Stil und Ton](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).

#### <a name="control-labels"></a>Steuerelementbezeichnungen
 Bezeichnungen werden kurze, präzise, und befolgen Sie die [Windows-Desktop-Anleitungen für die Steuerelemente](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx).

 Weitere Informationen zum Steuerelement Bezeichnungsformat und die Platzierung auf der Benutzeroberfläche finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Links zu Hilfethemen
 Links zu Hilfethemen können entweder in Anweisungstext oder im Text der Benutzeroberfläche platziert werden. Sie können rufen Dialogfelder auf interne oder Links zur Hilfe werden.

##### <a name="visual-style-rules-for-help-links"></a>Visuellen Stil-Regeln für Links zu Hilfethemen

- Verwenden Sie die richtige Umgebung-Farben für Links. Ein ordnungsgemäß formatierten Link leuchtet kurz nicht rot, die beim Klicken auf. Wenn dies angezeigt wird, dann ist ein Hinweis, dass die Umgebungsfarben nicht verwendet werden.

- Unterstreichungen sollte nur verwendet werden, wenn darauf gezeigt wird oder wenn der Link in einem Absatz eingebettet ist.

- Ausführlichere Informationen zu Visual und Interaktion von Formaten für Links finden Sie Schaltflächen und Links.

##### <a name="writing-style-rules-for-help-links"></a>Schreiben von Formatierungsregeln für Links zu Hilfethemen

- Beim Starten von Dialogfeldern, behalten Sie die Standards für die Ellipsen: keine mit den Auslassungszeichen für die Navigation, Ellipsen, wenn die Aufgabe weitere Benutzeroberfläche erforderlich sind.

     ![Hilfe-Link in Visual Studio](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601-E_HelpLink")

     **In einen Hilfelink Klicken ein Auslassungszeichen (...) gibt an, dass der Task zusätzliche Benutzeroberfläche benötigen.**

- Links sollte nicht mit "Informieren Sie sich," gestartet, wenn dies nicht die Absicht des Benutzers ist. Der Benutzer möchte eine bestimmte Frage beantworten, erhalten eine allgemeine Bildungseinrichtungen keine ab.

- Ausdruck Hilfe verknüpft, damit sie die Frage, dass das Thema beantwortet werden sollen.

     Falsch:    "Erfahren Sie mehr über die Preise von Windows Azure Mobile Services"

     Richtig:    "Welche Preisoptionen stehen für Windows Azure Mobile Services zur Verfügung?"

- Verwenden Sie niemals *klicken Sie auf...* um den Text des Links.

- Verknüpfen Sie nicht nur das Wort "hier". Dies ist für einige Bildschirmsprachausgaben, die nur das mit einem Link versehenen Wort voice werden problematisch.

     Falsch:    "Informieren Sie sich auf Windows Azure Mobile Services **hier**"

     Richtig:    "Welche Preisoptionen stehen für Windows Azure Mobile Services zur Verfügung?"

- Weitere Informationen zu den richtigen Schreibstil für Links zu Hilfethemen, finden Sie unter den [Windows-Desktop-Anleitung, Hilfe](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx).

#### <a name="hint-text"></a>Hinweistext
 Hinweistext wird als Wasserzeichen in einem Steuerelement oder unterhalb des Steuerelements angezeigt. Richtige Formatierung wird angewendet werden, mit dem entsprechenden VSColors Token `Environment.GrayText`.

 Sie können in verschiedene Formate angezeigt.

- Anstelle der steuerelementbezeichnung:

     ![Text in Visual Studio-Hinweis](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601-f_HintText1")

- Mit einem Verb erhalten Anweisungen:

     ![Text in Visual Studio-Hinweis](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601-g_HintText2")

- Mit dem Text, der angibt, einer erforderlichen Eingabe:

     ![Text in Visual Studio-Hinweis](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Wasserzeichentext
 Auf eine leere Entwurfsoberfläche was Sie tun sowie Links zu anderen verknüpften Fenster angezeigt, öffnen Sie bei Bedarf in den Text angeben:

 ![Wasserzeichen von Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601-I_WatermarkText")

 **Beispiel für Wasserzeichentext in Visual Studio**

### <a name="common-terminology"></a>Allgemeine Terminologie

|Begriff|Erklärung|Kommentar|
|----------|-----------------|-------------|
|Anmelden / Abmelden|Verben, die mit dem Web synonym verwendet wird, für die Darstellung der Authentifizierung in eine webeigenschaft. Innerhalb von-Clients verwenden wir dies einmal als eine Vorstellung der obersten Ebene für die Signierung und IDE-benutzerverbindung, der eine Identität der obersten Ebene, die bietet Funktionen auf höherer Ebene darstellt, wie roaming und Lizenzierung, der nicht mit alle anderen Verbindungen verfügbar sind.|Der IDE-Benutzer ist die einzige Funktion, die darstellen eine Anmeldung / Abmeldung-Verb, sollte, weil sie auf den obersten Ebene IDE-Benutzer darstellt.|
|Eine Verbindung herstellen / trennen|Verwenden Sie in den Orten, in denen ein Feature für eine einzelne Verbindung mit einer online-Dienst verwaltet.|Server-Explorer, in dem Sie nur eine aktive Azure-Verbindung zu einem Zeitpunkt verfügen können, ist ein Beispiel für die Verbindung herstellen/trennen.|
|Hinzufügen / Entfernen|Nichtdestruktive. Verwenden Sie beim Hinzufügen oder entfernen etwas aus der Liste.|Die TFS-Verbindungs-Manager-Dialogfeld "Server Liste" ist ein Beispiel für hinzufügen/entfernen.|
|Löschen|Destruktive. Verwenden Sie nur, wenn die zu entfernende Element dauerhaft verworfen oder vom Datenträger gelöscht werden.|"Delete" müssen in der Regel eine Eingabeaufforderung, wenn das Ergebnis wird eine Datei vom Datenträger gelöscht wird.|

## <a name="error-messages"></a>Fehlermeldungen

### <a name="overview"></a>Übersicht
 Fehler auftreten. Festlegen von Einschränkungen für die Möglichkeiten des Benutzers ist eine sinnvolle zunächst verhindert vermeidbare Fehlermeldungen. Wenn ein Fehler auftritt, kann jedoch eine gut geschriebene Fehlermeldung einen wichtiger Beitrag über das Problem zu entschärfen wechseln. Fehlermeldungen sind wohl eine der wichtigsten Typen von Benachrichtigungen, die dem Benutzer angezeigt wird, da sie synchron sind, und zeigen kein Problem, das gelöst werden muss, wird. Schlecht geschriebenen Fehlermeldungen lassen Sie Benutzer auf ihre eigenen entscheiden, die Ursache der Fehler und alle möglichen Lösungen.

 Benutzer möglicherweise nicht mehr, und achten Sie dabei übermäßig beansprucht oder verwirrende Fehlermeldungen aus, damit Schreibzugriff nur erforderlich, Nachrichten, die Wert für den Benutzer auftreten. Wenn die Nachricht einfach eine Benachrichtigung ist, verwenden Sie eine alternative Darstellung.

### <a name="rules-for-creating-an-error-message"></a>Regeln für das Erstellen einer Fehlermeldung

- Wenn Sie Fehlermeldungen zu erstellen, wählen Sie die entsprechenden Fehler für die Zielgruppe. Streben Sie für einfache Zusammenfassungen, die eine Aktion, mit denen der Benutzer bereitstellen, falls zutreffend. Keine Status alle Elemente, die der Benutzer nicht kennen muss.

- Unterstützen Sie konstruktive. Es ist einfacher zu lesen und reagieren auf eine Fehlermeldung angezeigt, die Anweisung enthält.

- Verwenden Sie keine doppelten negativ.

- Führen Sie eine automatisierte und Fehlermeldungen, die Sie schreiben eine manuelle Grammatik und Rechtschreibung prüfen.

- Vermeiden Sie komplexe Fehlermeldungen sequenzielle Kommunikation. Verwenden Sie niemals ein F1-Einbindung für die Fehlermeldung an. Die Nachricht selbst sollte ausreichend sein.

- Verwenden Sie die korrekte Symbole angezeigt.

- Stellen Sie Fragen einfach zu verstehen und verwenden Sie Schaltflächen, die klare Optionen, wie beispielsweise "Delete" und "Abbrechen".

- Werden Sie für Warnungen deutlich hervorzuheben, was zur Folge, dass Sie den Vorgang fortsetzen kann. Die Schaltflächen sollten die Folge angeben.

- Beschrieben Sie für Fehler, was der Benutzer ausführen kann, um das Problem zu beheben. Schaltflächen müssen Aktionen oder sagen "Schließen". Verwenden Sie eine Schaltfläche "OK" nicht für eine Fehlermeldung an.

- Einige Fragen sich Fragen, wenn Sie eine Fehlermeldung zu erstellen:

  - Kann der Benutzer zur Lösung des Problems zu diesem Fehler allein herausfinden, wie?

  - Wird der Benutzer das gleiche Vokabular wie dieser Fehler verwendet?

  - Ist dieser Fehler mehrdeutig oder in mehreren Fällen freigegeben? Wenn dies der Fall ist, führen Sie wie Sie mit der Lösung Benutzerhandbuch, die sie benötigen?

#### <a name="build-errors"></a>Buildfehler
 Da Visual Studio ein Entwicklungstool für die Software ist, verfügen viele Komponenten eine Kompilierung konvertieren oder Codierung Schritt, um die Arbeit des Entwicklers in das binäre Format zu konvertieren. Diese Konvertierungen können Fehler verursachen, wenn der Compiler nicht ordnungsgemäß erstellte Dateien nicht verarbeiten kann oder Compileroptionen ordnungsgemäß festgelegt wurden nicht.

 Visual Studio-Benutzer können eine enorme Anzahl von Entwicklung Stunden Beheben von Buildfehlern verbringen. Diese Auflösungszeit wird erhöht, wenn Fehler vorliegen, Abhängigkeiten oder wenn Fehlermeldungen schlecht geschriebene sind die können die Ursache des Fehlers aufdecken erschweren.

 Die beste Buildfehler sind diejenigen, die auftreten, nicht in der ersten Stelle, weshalb Visual Studio bietet automatische Vervollständigung und IntelliSense-Wellenlinien. Schema-Validierungssteuerelemente und ähnliche Tools bieten die gleiche Art von Feedback. Diese Mechanismen führen proaktiv den Benutzer um wohlgeformte Code, verringern das Risiko der Buildfehler zu erstellen.

 Visual Studio bietet ein Toolfenster, in denen Benutzer lesen und navigieren Sie durch die in ihren Dokumentfenster aufgetretenen können. Tastenkombinationen in Visual Studio werden bereitgestellt, sodass der Benutzer kann schnell große Mengen von Code navigieren, und wechseln Sie direkt auf den Speicherort des Problems. Visual Studio können auch jede Buildfehler zu einem bestimmten Schlüsselwort/Hilfekontext-ID gebunden werden, sodass der Benutzer direkt zur ein Hilfethema wechseln kann, die ausführlichere Informationen zu diesem Fehler erhalten.

 Schreiben Sie klare und kompakte Buildfehler:

- **Verwenden von einfachen** , um das Problem mit wenigen oder gar keinen Compilerfehler-Jargon zu erläutern. Der Text, der einen Buildfehler darf nicht zu technischen sein.

- **Beschreiben Sie die mögliche Ursachen.** Z. B. "Fehlender Doppelpunkt zwischen der Eigenschaft und Wert in der ' (Eigenschaft): (Wert)' Deklaration."

- Geben Sie Details zu potenziellen Fehlerbehebungen. Wenn nicht genügend Platz vorhanden ist, können zusätzliche Details in das entsprechende Hilfethema abgelegt werden.

### <a name="components-of-a-well-written-error-message"></a>Komponenten einer gut geschriebene Fehlermeldung

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Verwenden Sie den Shell-Dialogfeld-Dienst Fehlermeldungen vorliegen.
 Mit dem Shell-Dialogfeld-Dienst können Sie steuern, die Darstellung der Nachricht – Schriftarten in bestimmten – ohne wesentliche Änderungen auf einzelne Elemente. Verwenden der **IErrorInfo** Mechanismen und mithilfe von **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wählen Sie eine effektive und die entsprechenden Benachrichtigung Präsentation.
 Verwenden Sie ein modales Dialogfeld mit der eine kritische Warnung, wenn sofortige Maßnahmen erforderlich ist, vermeiden von Datenverlust (synchrone Benachrichtigung). Wichtige Symbole sind für Situationen reserviert in der, die Schließen-Nachricht ohne lesen sie zu negativen Konsequenzen führen kann. Verlust von Daten ist einer kritischen Situation, die eine Antwort auf Dokumentebene Warnsignal erforderlich sind. Das Symbol "Kritisch" übermäßige desensitizes Benutzer zu deren Bedeutung. Falls die Fehlermeldung lediglich informativ ist, sollten Sie alternativen für die ein modales Dialogfeld (asynchrone Benachrichtigung) ein.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Geben Sie eine saubere, kurze Erläuterung der Ursache des Problems anstatt eine technische Erklärung.
 Überlasten von Benutzern mit technischen Details in der Erläuterung wird sie eher Fehlermeldungen ignorieren zu machen. Beispiele für gute messaging:

- "Kann nicht auf die gewünschte Datei zu öffnen."

- "Kann nicht mit dem Internet herstellen."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Geben Sie Informationen dazu, wie zum Beheben des Problems.
 Bieten Sie die benutzervorschläge, wie das Problem zu beheben. Ehrlich gesagt, mit dem Benutzer sein, wenn keine Vorschläge vorhanden sind. Geben Sie die direkte Links zu alternativen Onlinequellen, z. B. communitysupport und technischen Support. Versuchen Sie es, um Benutzer auf bestimmte online Informationen für das Problem zu verweisen. Sollten Sie für eine Fehler-ID in der Verknüpfen von Benutzern mit einer Diskussion mit Threads zum jeweiligen Fehler angezeigt. Beispiele für gute messaging:

- "Stellen Sie sicher, dass Sie mit dem Internet verbunden sind, und versuchen Sie es noch mal."

- "Stellen Sie sicher, dass die Datei vorhanden ist und Sie die Berechtigung, um ihn zu öffnen."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Schreiben Sie eine Nachricht, die kurz und präzise ist.
 Kann eine Fehlermeldung zu benachrichtigen, erläutern, und bieten eine Lösung aber weiterhin ignoriert werden, wenn es zu irgendein ist. Eine Lösung ist die Verwendung von schrittweise Anzeige von mit einer Schaltfläche "Details". Geben Sie z. B. eine kurze Beschreibung/der aktuellen Projektmappe und dann weitere Details zum eine Schaltfläche "Details". Wenn der Benutzer auswählen, um weitere Informationen zu diesem Fehler finden, können sie dies tun.

 Die Sprache in der Nachricht sollte sein:

- **Domäne geeignet.** Verwenden Sie die Sprache aus, die der Benutzer verstehen. Obwohl Kunden Entwickler sind, haben sie keine häufig des Kontexts und der Terminologie, mit denen wir haben.

- **Spezifisch.** Vermeiden Sie und formulierungen, und geben Sie Namen und Speicherorte der beteiligten Objekte. Z. B. "Zeichen ist ungültig" ist eine Fehlermeldung z. B. nicht hilfreich. Welches Zeichen? "Datei nicht gefunden." Welche Datei?

- **Höflich.** Keine Verantwortung zuweisen des Benutzers oder ihn dumm aussehen lassen. Vermeiden Sie schädlicher oder anstößige Sprache (Beenden, ausführen, beenden, schwerwiegender, unzulässige). Vermeiden Sie groß geschriebenen Text, der wird häufig als Shouting angezeigt und kann nicht als gelesen. Verwenden Sie keine Humor.

- **Richtig.** Verwenden Sie die richtige Rechtschreibung und Grammatik (auch in der Alphas). Tippfehler sind unprofessionell und peinliche.

- **Je nach Kontext geeignet ist.** Verwenden Sie die entsprechende Schaltflächentext. Vermeiden Sie die Schaltfläche "OK", und verwenden Sie stattdessen "Weiter" oder "Ja/Nein".

### <a name="error-message-examples"></a>Beispiele für Fehler

|Gut|Ungültige|
|----------|---------|
|"Der Nummer, die Sie gewählt ist nicht mehr im Dienst. Überprüfen Sie die Anzahl, und wählen Sie erneut oder wählen Sie 0 für den Operator."|-"Fehler (449): Ungültige Anzahl"<br />-"Diesen Fehler nicht behandelte Ausnahme gibt an, dass der Vorgang erfolgreich abgeschlossen."<br /><br /> ![Ungültige Fehlermeldung in Visual Studio](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602-A_ErrorDialog")|

## <a name="accessing-help"></a>Zugreifen auf die Hilfe

### <a name="overview"></a>Übersicht
 Zusätzlich zur Dokumentation in MSDN verfügt ein Visual Studio-Benutzer mehrere Zugriffspunkte, um die Benutzer klicken Sie auf der Benutzeroberfläche zu unterstützen. Um sicherzustellen, dass diese Zugriffspunkte durchgängig verfügbar sind, müssen Feature-Teams nutzen das Hilfesystem von der Umgebung angeboten werden. Diese Zugriffspunkte sind:

- **Lehre und zusätzlichen Text in Dialogfeldern.** Statischer Text, der Richtung oder Erklärung, entweder auf der Benutzeroberfläche Oberfläche oder bei einer mauszeigerbewegung über ein QuickInfo-Symbol verfügbar zu erhalten.

- **F1-Hilfe** (nur-Editor). Im Visual Studio-Editor kann ein Benutzer vertrauen, dass jederzeit durch Drücken von F1 eines Hilfethemas, die spezifisch für die aktuelle Auswahl angezeigt wird. Sicherstellen Sie, dass Themen über F1 entsprechenden und informativ.

- **Links zu Hilfethemen.** Ein Link in einem Dialogfeld, Toolfenster oder Entwurfsoberfläche, die ein Thema, um den Benutzer zu unterstützen, erfahren Sie mehr über eine Technologie, Funktionen oder Informationen zum Ausführen einer Aufgabe gestartet wird.

- **Hilfsprogramm-UI-basierten Mechanismen, z. B. Smarttags und Erstellen von Dialogfeldern.** Diese Mechanismen bei der der Benutzer ein Element der Benutzeroberfläche zu verstehen, oder eine Aufgabe, z. B. Smarttags oder Generator-Dialogfelder erleichtern.

- **Hilfe zur Benutzeroberfläche Schaltflächen** (veraltet). Ein sichtbar Indikator in der Titelleiste, die Zugriff auf die verwandten F1-Hilfethema möglich.

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Lehre und zusätzlichen Text in Dialogfeldern
 In Dialogfeldern, die komplexe Aufgaben zu unterstützen, möglicherweise Anweisungstext in der Benutzeroberfläche oft am oberen Rand des Dialogfelds oder komplexe Steuerelemente in der Nähe von erhalten werden muss. Finden Sie unter [UI Text und die Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) ausführliche Informationen zum Stil zu schreiben.

#### <a name="infotips"></a>InfoTips
 Anweisungstext kann häufig so umfangreich, dass positionieren direkt in der Benutzeroberfläche oder kann nur an einen neuen Benutzer wie überladen für erfahrene Benutzern hilfreich sein. In diesem Fall sollte dem Lehrzwecken/Informationstext als QuickInfo in einem Infotipp platziert werden.

 Infotipps sollten in der Nähe von den Steuerelementen, die sie beziehen sich auf und sollten das bestimmte Infotipp-Symbol, das unaufdringliche noch nicht bemerkbar platziert werden.

 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-D_InfoTip")

 **Beispiel für ein Infotipp in Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktive Hilfemechanismen

#### <a name="f1-help"></a>F1-Hilfe
 F1-Hilfe ist erforderlich, in einem Editor oder die Entwurfsoberfläche, aber nicht an anderer Stelle in der Visual Studio-Umgebung.

#### <a name="hyperlinks-to-help-topics"></a>Links zu Hilfethemen
 Hyperlinks können verwendet werden, um eine Aktion auszuführen, Navigieren in der IDE oder Hilfe in einem Browser zu starten. Finden Sie unter [UI Text und die Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) Weitere Informationen zu Sprache und 07.10.01 Schaltflächen und Links für Visuals und Layouts Richtlinien.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Hilfe [?]-Schaltflächen im Dialogfeld Titelleisten (veraltet)
 Zum größten Teil, sind die Schaltflächen "Help [?]" in der Titelleiste von Dialogfeldern als veraltet markiert. UI-Themen sind nicht mehr Teil des Modells Doc, und aus diesem Grund gibt es möglicherweise kein relevantes Thema zu verknüpfen. Im Wesentlichen die Titelleistenschaltfläche wurde dasselbe wie die F1-Hilfe, und in Dialogfeldern nicht mehr erforderlich ist. In einigen Fällen kann dies immer noch verwendet werden als Indikator, dass konzeptionelle bzw. prozeduralen Informationen verfügbar, obwohl links häufiger in neueren Benutzeroberfläche verwendet werden.

##### <a name="dialogs-created-through-the-environment"></a>Dialogfelder, die über die Umgebung erstellt wurden
 Viele Shelldialogfelder werden erstellt, über die **VBDialogBoxParam** Funktion. Diese gemeinsame Funktion wurde aktualisiert, um Unterstützung bei der Umstellung der **Hilfe** Schaltfläche im Dialogfeld, um die **?** Schaltfläche ", und behalten Sie eine Architektur, die Abwärtskompatibilität ist kompatibel und erweiterbar.

 Insbesondere die **VBDialogBoxParam** Funktion untersucht die Dialogfeldvorlage für eine Schaltfläche mit der ID **IDHELP** (9) oder die Bezeichnung **Hilfe** oder **&-Hilfe**. Wenn eine Schaltfläche "Hilfe" gefunden wird, wird es ausgeblendet und die **WS_EX_CONTEXTHELP** Format wird hinzugefügt, um das Dialogfeld, in dem platziert die **?** Schaltfläche in der Titelleiste des Dialogfelds.

 Wenn das Dialogfeld erstellt wird, legt die Dialogfeldprozedur auf einen Stapel und ruft Sie das Dialogfeld mit einer vorverarbeitung Dialogfeldprozedur, die mit dem Namen **DialogPreProc**. Wenn die **?** Schaltfläche geklickt wird, sendet er eine **WM_SYSCOMMAND** von **SC_CONTEXTHELP** um das Dialogfeld. Die **DialogPreProc** dieser Befehl erfasst und ändert sich zu einem **WM_HELP** -Nachricht, die an das ursprüngliche Dialogfeld-Prozedur übergeben wird

 Die meisten sind Umgebung erstellten mit einer Schaltfläche "Hilfe" im Dialogfeld. Wenn das Dialogfeld angezeigt wird, wird die Schaltfläche "Hilfe" automatisch ausgeblendete und nur die **?** Schaltfläche funktioniert. Wenn die **?** Schaltfläche je entfernt oder in Windows geändert wird, kann diese Lösung Sie schnell wieder zu der ursprünglichen Hilfe-Schaltflächen gelangen.

 Diese Lösung ist vier Annahmen, die Fehler verursachen könnte:

- Wird das Dialogfeld die Schaltfläche "Hilfe" **IDHELP** (9).

- Das Dialogfeld fehlerfrei ist, wenn die Schaltfläche "Hilfe" ausgeblendet wird.

- Das Dialogfeld ersetzt keine seine Winproc.

- Das Dialogfeld wird in einem anderen Dialog nicht eingebettet werden.

  Wenn das Dialogfeld befindet sich im Msenv befindet und nicht **VBDialogBoxParam**, untersuchen Sie die Nutzung von **VBDialogBoxParam** vor eigene Handler implementieren.

##### <a name="dialogs-created-through-other-packages"></a>Dialogfelder, die mit anderen Paketen erstellt wurden
 Sie können Ihre eigene Lösung für Dialogfelder implementieren, die sich außerhalb der Msenv befinden. Erwägen Sie für eine freigegebene Dialogfeldklasse in einem VSPackage verschieben die Schaltfläche mit den in der Titelleiste, oder implementieren einen Handler auf jedem Dialogfeld. Der folgende Code bildet das Grundgerüst einer Implementierung, die Ihnen beim Einstieg helfen:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Hilfe-Schaltflächen in verwaltetem code
 Überschreiben von Standardverhalten der Fenster Hilfe Titelleistenschaltfläche des ist einfach in verwaltetem Code. Es folgt eine vollständige Demo-Anwendung, die dieses Verhalten veranschaulicht wird. Im Wesentlichen müssen Sie zum Überschreiben des Formulars **WndProc** -Methode und klicken Sie dann Fire deaktiviert; F1-Hilfe, die angefordert werden, wenn ein **SC_CONTEXTHELP** Nachricht abgefangen wird.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Siehe auch
 [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md) [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md) [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
