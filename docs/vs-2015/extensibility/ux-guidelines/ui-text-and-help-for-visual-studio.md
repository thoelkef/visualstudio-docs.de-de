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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301242"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Benutzeroberflächentext und -hilfe für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>UI-Text und Terminologie
 Verständlicher Text ist entscheidend für eine effektive Benutzeroberfläche. Software-Benutzer neigen dazu, zuerst Etiketten zu lesen, nämlich diejenigen, die für den Abschluss der anstehenden Aufgabe am relevantesten sind. Statischer Text wird mit weniger Häufigkeit gelesen. Planen Sie, dass Benutzer ihre Arbeitssitzungen mit einem schnellen Scan des gesamten Fensters beginnen, gefolgt von einem Lesen der Benutzeroberfläche in dieser ungefähren Reihenfolge:

1. Interaktive Steuerungen in der Mitte

2. Commit-Schaltflächen

3. Interaktive Steuerelemente an anderer Stelle

4. Hauptanweisungen

5. Ergänzende Erläuterungen

6. Fenstertitel

7. Anderer statischer Text im Haupttext

### <a name="usage-patterns-for-ui-text"></a>Verwendungsmuster für UI-Text

#### <a name="title-bar-text"></a>Titelleistentext
 Der Text der Titelleiste muss mit dem Befehl übereinstimmen, der die Benutzeroberfläche ausgelöst hat.

#### <a name="instructional-text-helper-text"></a>Lehrtext (Hilfstext)
 In einigen Dialogfeldern ist es hilfreich, prominente Hauptanweisungen bereitzustellen, um zu erklären, was im Fenster oder auf der Seite zu tun ist. Dies wird manchmal als "Helfertext" bezeichnet.

##### <a name="writing-style-rules-for-helper-text"></a>Schreiben von Stilregeln für Hilfstext

- Erklären Sie nicht das Offensichtliche. Es sei denn, es ist unbedingt erforderlich, schließen Sie keinen Lehrtext ein.

- Instruktionstext wird immer oben im Dialogfeld platziert und sollte sich auf die auszuführende Aufgabe beziehen.

- Erklären Sie den Benutzern genau, was sie tun müssen. Vermeiden Sie übermäßige Kommunikation und Redundanz.

- Überprüfen Sie jedes Fenster, und entfernen Sie doppelte Wörter und Anweisungen.

- Halten Sie den Anweisungstext kurz. Wenn für bestimmte Benutzer oder Szenarien weitere Informationen erforderlich sind, stellen Sie einen Link zu einem detaillierten konzeptionellen Onlinethema bereit.

- Schreiben Sie Ihren Text so, dass jedes Wort Gewicht hat und notwendig ist.

- Befolgen Sie die vorhandenen Microsoft-Richtlinien für [Benutzeroberflächentext](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [-stil und Ton](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).

#### <a name="supplemental-instructions"></a>Ergänzende Anweisungen
 Zusätzliche Anweisungen enthalten zusätzliche Informationen, die dem Benutzer helfen, Steuerelemente oder Steuerelementgruppierungen zu verstehen. Dies kann auch Hinweistext enthalten, der erforderlich ist, um zu verstehen, welches Format das Eingabesteuerelement erwartet. Verwenden Sie zusätzliche Anweisungen sparsam. Reservieren Sie sie für Fälle, in denen es wahrscheinlich ist, dass der Benutzer die Auswirkungen der Wahl, die er trifft, nicht vollständig versteht.

 ![Ergänzender Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601-b_SupplementalText1")

 **Ergänzender Text in Visual Studio**

 ![Ergänzender Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601-c_SupplementalText2")

 **Ergänzender Text in Visual Studio**

#### <a name="infotips"></a>InfoTipps
 Häufig ist der Anweisungstext zu langwierig, um ihn in der Benutzeroberfläche zu positionieren, oder er ist nur für neue Benutzer nützlich, da er sich für erfahrene Benutzer wie unübersichtlich anfühlt. In diesem Fall sollte der Lehr-/Informationstext als QuickInfo unter einem InfoTip platziert werden.

 InfoTips sollten in der Nähe der Steuerelemente platziert werden, mit denen sie verwandt sind, und das spezifische InfoTip-Symbol verwenden, das unauffällig und doch spürbar ist.

 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-d_InfoTip")

 **Beispiel für einen InfoTip in Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Schreiben von Stilregeln für InfoTips

- Schreiben Sie InfoTips als vollständige Sätze. Sie erfordern bestimmte Verben, Satzfall und Endsatz.

- Verwenden Sie InfoTips, um Ihre Hauptanleitung oder Informationen zu ergänzen. Wenn Sie nur andere Wörter verwenden, um die Hauptidee zu wiederholen, benötigen Sie kein InfoTip.

- Halten Sie InfoTips kurz und süß. Verwenden Sie kleine Wörter und einfache, alltägliche Sprache, die den Benutzer unterstützt und ermutigt.

- Befolgen Sie die vorhandenen Microsoft-Richtlinien für [Benutzeroberflächentext](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [-stil und Ton](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).

#### <a name="control-labels"></a>Kontrolletiketten
 Steuerelementbeschriftungen sollten kurz und prägnant sein und den [Windows Desktop-Anleitungen für Steuerelemente](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)folgen.

 Weitere Informationen zum Steuerelementbeschriftungsformat und zur Platzierung innerhalb der Benutzeroberfläche finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Hilfelinks
 Hilfelinks können entweder im Anweisungstext oder im Textkörper der Benutzeroberfläche platziert werden. Dabei kann es sich um Links zur Hilfe oder zum Starten interner Dialoge handelt.

##### <a name="visual-style-rules-for-help-links"></a>Visuelle Stilregeln für Hilfelinks

- Verwenden Sie die richtigen Umgebungsfarben für Hyperlinks. Ein ordnungsgemäß formatierter Hyperlink blinkt nicht kurz rot, wenn darauf geklickt wird. Wenn Sie dies sehen, dann ist es ein Hinweis darauf, dass Umgebungsfarben nicht verwendet werden.

- Unterstreichungen sollten nur bei der Maus verwendet werden oder wenn die Verknüpfung in einen Absatz eingebettet ist.

- Ausführlichere Informationen zu visuellen und Interaktionsstilen für Hyperlinks finden Sie unter Schaltflächen und Hyperlinks.

##### <a name="writing-style-rules-for-help-links"></a>Schreiben von Stilregeln für Hilfelinks

- Behalten Sie beim Starten von Dialogen die Standards für Ellipsen bei: keine Auslassungspunkte für die Navigation, Ellipsen, wenn die Aufgabe eine zusätzliche Benutzeroberfläche erfordert.

     ![Hilfelink in Visual Studio](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601-e_HelpLink")

     **Eine Auslassungspunkte (...) in einem Hilfelink gibt an, dass die Aufgabe eine zusätzliche Benutzeroberfläche benötigt.**

- Links sollten nicht mit "Lernen" beginnen, da dies nicht die Absicht des Benutzers ist. Der Benutzer möchte eine bestimmte Frage beantworten, keine allgemeine Ausbildung erhalten.

- Phrasenhilfe-Links, so dass sie die Frage stellen, die das Thema beantworten wird.

     Falsch: "Erfahren Sie mehr über die Preise für Windows Azure Mobile Services"

     Richtig: "Welche Preisoptionen sind für Windows Azure Mobile Services verfügbar?"

- Verwenden Sie niemals *Click...* auf den Linktext.

- Verknüpfen Sie niemals nur das Wort "hier". Dies ist problematisch für einige Bildschirmleser, die nur das mit Deminemten verknüpfte Wort sprechen.

     Falsch: "Informationen zu Windows Azure Mobile Services **finden Sie hier**"

     Richtig: "Welche Preisoptionen sind für Windows Azure Mobile Services verfügbar?"

- Weitere Informationen zum richtigen Schreibstil für Hilfelinks finden Sie in der [Windows-Desktopanleitung für Hilfe](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx).

#### <a name="hint-text"></a>Hinweistext
 Hinweistext wird als Wasserzeichen innerhalb eines Steuerelements oder unterhalb des Steuerelements angezeigt. Die korrekte Formatierung wird mithilfe des `Environment.GrayText`entsprechenden VSColors-Tokens , angewendet.

 Es kann in einer Reihe von Formularen angezeigt werden.

- Anstelle des Steueretiketts:

     ![Hinweistext in Visual Studio](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601-f_HintText1")

- Mit einem Verb, das Anweisungen gibt:

     ![Hinweistext in Visual Studio](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601-g_HintText2")

- Mit Text, der einen erforderlichen Eintrag angibt:

     ![Hinweistext in Visual Studio](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Wasserzeichentext
 Auf einer leeren Entwurfsoberfläche sollte der Text angeben, was zu tun ist, sowie Links zum Öffnen anderer verwandter Fenster bereitstellen, falls zutreffend:

 ![Wasserzeichentext in Visual Studio](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601-i_WatermarkText")

 **Beispiel für Wasserzeichentext in Visual Studio**

### <a name="common-terminology"></a>Gemeinsame Terminologie

|Begriff|Erklärung|Comment|
|----------|-----------------|-------------|
|Anmelden / Abmelden|Verben werden synonym mit dem Web für die Darstellung der Authentifizierung in einer Webeigenschaft verwendet. Innerhalb von Clients verwenden wir dies einmal als einen Begriff auf oberster Ebene für die Anmeldung und Aus-aus-ID-Benutzerverbindung, die eine Identität der obersten Ebene darstellt, die Funktionen auf höherer Ebene wie Roaming und Lizenzierung bereitstellt, die nicht mit allen anderen Verbindungen verfügbar sind.|Der IDE-Benutzer ist das einzige Feature, das ein Anmelde-/Abmeldeverb darstellen sollte, da er den IDE-Benutzer der obersten Ebene darstellt.|
|Verbinden / Trennen|Verwendung an Orten, an denen ein Feature eine einzelne Verbindung zu einem Onlinedienst unterhält.|Der Server-Explorer, bei dem Sie jeweils nur über eine aktive Azure-Verbindung verfügen können, ist ein Beispiel für Verbinden/Trennen.|
|Hinzufügen / Entfernen|Nicht destruktiv. Wird beim Hinzufügen oder Entfernen von etwas aus einer Liste verwendet.|Das Dialogfeld TFS Connection Manager-Serverlisten ist ein Beispiel für Hinzufügen/Entfernen.|
|Löschen|Destruktive. Wird nur verwendet, wenn das zu entfernende Element dauerhaft verworfen oder vom Datenträger gelöscht wird.|"Löschen" erfordert in der Regel eine Eingabeaufforderung, wenn das Ergebnis das Löschen einer Datei vom Datenträger ist.|

## <a name="error-messages"></a>Fehlermeldungen

### <a name="overview"></a>Übersicht
 Fehler passieren. Das Festlegen von Einschränkungen für das, was der Benutzer tun kann, ist ein sinnvoller erster Schritt, um vermeidbare Fehlermeldungen zu verhindern. Wenn jedoch ein Fehler auftritt, kann eine gut geschriebene Fehlermeldung einen langen Weg zur Milderung des Problems gehen. Fehlermeldungen sind wohl eine der wichtigsten Arten von Benachrichtigungen, die der Benutzer sieht, da sie synchron sind und auf ein Problem hinweisen, das gelöst werden muss. Schlecht geschriebene Fehlermeldungen lassen Benutzer auf sich allein gestellt, um die Ursache der Fehler und mögliche Lösungen zu entscheiden.

 Benutzer können aufhören, auf überstrapazierte oder verwirrende Fehlermeldungen zu achten, also schreiben Sie nur die erforderlichen Nachrichten, die der Benutzererfahrung einen Mehrwert verleihen. Wenn es sich bei der Nachricht lediglich um eine Benachrichtigung handelt, verwenden Sie eine alternative Darstellung.

### <a name="rules-for-creating-an-error-message"></a>Regeln zum Erstellen einer Fehlermeldung

- Wählen Sie beim Erstellen von Fehlermeldungen die entsprechende Fehlerstufe für die Zielgruppe aus. Ziel für einfache Zusammenfassungen, die eine Aktion bereitstellen, die der Benutzer ggf. ergreifen kann. Geben Sie nichts an, was der Benutzer nicht wissen muss.

- Bieten Sie konstruktive Hilfe. Es ist einfacher, eine Fehlermeldung zu lesen und zu reagieren, die Anweisungen enthält.

- Verwenden Sie keine doppelten Negative.

- Führen Sie sowohl eine automatisierte als auch eine manuelle Grammatik- und Rechtschreibprüfung für jede Fehlermeldung durch, die Sie schreiben.

- Vermeiden Sie bei komplexen Fehlermeldungen die sequenzielle Kommunikation. Verwenden Sie niemals einen F1-Anschluss für die Fehlermeldung. Die Botschaft selbst sollte ausreichen.

- Verwenden Sie das richtige Symbol.

- Machen Sie Fragen leicht verständlich und verwenden Sie Schaltflächen, die klare Auswahlmöglichkeiten haben, z. B. "Löschen" und "Abbrechen".

- Seien Sie bei Warnungen klar, welche Folgen das Verfahren haben wird. Die Schaltflächen sollten die Folge anzeigen.

- Beschreiben Sie bei Fehlern, was der Benutzer tun kann, um das Problem zu beheben. Schaltflächen sollten Aktionen sein oder "Schließen" sagen. Verwenden Sie für eine Fehlermeldung keine "OK"-Schaltfläche.

- Einige Fragen, die Sie sich beim Erstellen einer Fehlermeldung stellen müssen:

  - Kann der Benutzer herausfinden, wie das Problem mit diesem Fehler allein zu lösen?

  - Verwendet der Benutzer dasselbe Vokabular wie dieser Fehler?

  - Ist dieser Fehler unbigious oder in mehreren Situationen geteilt? Wenn ja, wie führen Sie Benutzer zu der Lösung, die sie benötigen?

#### <a name="build-errors"></a>Buildfehler
 Da Visual Studio ein Softwareentwicklungstool ist, verfügen viele seiner Komponenten über einen Kompilierungs-, Konvertierungs- oder Codierungsschritt, um die Arbeit des Entwicklers in binäre Form zu konvertieren. Diese Konvertierungen können Fehler verursachen, wenn der Compiler nicht falsch erstellte Dateien verarbeiten kann oder wenn Compileroptionen nicht richtig festgelegt wurden.

 Visual Studio-Benutzer können eine enorme Anzahl von Entwicklungsstunden aufwenden, um Buildfehler zu beheben. Diese Auflösungszeit erhöht sich, wenn Fehler Abhängigkeiten aufweisen oder Fehlermeldungen schlecht geschrieben sind, was das Aufdecken der Fehlerquelle erschweren kann.

 Die besten Buildfehler sind diejenigen, die überhaupt nicht auftreten, weshalb Visual Studio AutoComplete- und IntelliSense-Squiggles bereitstellt. Schemavalidierer und ähnliche Tools bieten die gleiche Art von Feedback. Diese Mechanismen führen den Benutzer proaktiv dazu, wohlgeformten Code zu erstellen, wodurch die Wahrscheinlichkeit von Buildfehlern verringert wird.

 Visual Studio stellt ein Toolfenster bereit, in dem Benutzer die Fehler in ihren Dokumentfenstern lesen und navigieren können. Tastenkombinationen werden bereitgestellt, damit der Benutzer schnell durch große Mengen an Code navigieren und direkt zum Speicherort des Problems wechseln kann. Visual Studio ermöglicht auch, dass jeder Buildfehler an ein bestimmtes Hilfeschlüsselwort/eine bestimmte Kontext-ID gebunden wird, sodass der Benutzer direkt zu einem Hilfethema wechseln kann, das ausführlichere Informationen zu dem Fehler enthält.

 Schreiben Sie klare, prägnante Buildfehler:

- **Verwenden Sie eine einfache Sprache,** die das Problem mit wenig oder gar keinem Compilerjargon erklärt. Der Text eines Buildfehlers sollte nicht übermäßig technisch sein.

- **Skizzieren Sie mögliche Ursachen.** Beispiel: "Fehlen eines Doppelpunkts zwischen der Eigenschaft und dem Wert in der '(property) : (value)' Deklaration."

- Geben Sie Details zu möglichen Korrekturen an. Wenn nicht genügend Platz vorhanden ist, können zusätzliche Details in das entsprechende Hilfethema eingefügt werden.

### <a name="components-of-a-well-written-error-message"></a>Komponenten einer gut geschriebenen Fehlermeldung

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Verwenden Sie den Shelldialogdienst für Fehlermeldungen.
 Mit dem Shell-Dialogdienst können Sie die Darstellung der Nachricht – insbesondere Schriftarten – ohne wesentliche Änderungen an einzelnen Elementen steuern. Verwenden Sie die **IErrorInfo-Mechanismen,** und melden Sie sie mit **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wählen Sie eine effektive und geeignete Benachrichtigungspräsentation aus.
 Verwenden Sie ein modales Dialogfeld mit einer kritischen Warnung, wenn sofortige Maßnahmen erforderlich sind, um Datenverlust zu vermeiden (synchrone Benachrichtigung). Kritische Symbole sind für Situationen reserviert, in denen das Schließen der Nachricht ohne Lesen zu negativen Folgen führen kann. Datenverlust ist eine kritische Situation, die eine Reaktion auf Alarmebene erfordert. Die Überbeanspruchung des kritischen Symbols deensizipiert Benutzer auf seine Bedeutung. Wenn die Fehlermeldung informationsbasiert ist, sollten Sie Alternativen zu einem modalen Dialogfeld (asynchrone Benachrichtigung) in Betracht ziehen.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Geben Sie eine saubere, prägnante Erklärung dafür, warum das Problem aufgetreten ist, und nicht eine technische Erklärung.
 Wenn Benutzer mit technischen Details in der Erklärung überlastet werden, ist die Wahrscheinlichkeit größer, dass sie Fehlermeldungen ignorieren. Beispiele für gute Nachrichten:

- "Die angeforderte Datei kann nicht geöffnet werden."

- "Es kann keine Verbindung zum Internet hergestellt werden."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Geben Sie Informationen zum Beheben des Problems an.
 Bieten Sie den Benutzern Vorschläge an, wie Sie das Problem beheben können. Seien Sie ehrlich mit dem Benutzer, wenn es keine Vorschläge gibt. Stellen Sie direkte Links zu alternativen Online-Quellen bereit, z. B. technische unterstützung oder Community-Support. Versuchen Sie, Benutzer auf bestimmte Onlineinformationen hinzuweisen, die für das Problem relevant sind. Wenn Sie eine Fehler-ID erhalten, sollten Sie Benutzer mit einem Diskussionsthread zu diesem bestimmten Fehler verknüpfen. Beispiele für gute Nachrichten:

- "Stellen Sie sicher, dass Sie mit dem Internet verbunden sind, und wiederholen Sie diesen Vorgang."

- "Stellen Sie sicher, dass die Datei vorhanden ist und dass Sie über die Berechtigung zum Öffnen verfügen."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Schreiben Sie eine Nachricht, die kurz und auf den Punkt ist.
 Eine Fehlermeldung kann benachrichtigen, erklären und eine Lösung anbieten, aber trotzdem ignoriert werden, wenn sie zu wortwörtlich ist. Eine Lösung besteht darin, die progressive Offenlegung mit einem Detail-Button zu verwenden. Geben Sie z. B. eine kurze Beschreibung/Lösung an und geben Sie dann weitere Details unter eine Detailschaltfläche. Wenn Benutzer weitere Informationen zu dem Fehler lesen möchten, können sie dies tun.

 Die Sprache in der Nachricht sollte wie:

- **Domänentauglich.** Verwenden Sie die Sprache, die der Benutzer versteht. Obwohl unsere Kunden Entwickler sind, haben sie oft nicht den Kontext und die Terminologie, die wir haben.

- **Bestimmten.** Vermeiden Sie vage Formulierungen und geben Sie bestimmte Namen und Orte der beteiligten Objekte an. Beispielsweise ist eine Fehlermeldung wie "Zeichen ist ungültig" nicht hilfreich. Welcher Charakter? "Datei wurde nicht gefunden." Welche Datei?

- **Höflich.** Geben Sie dem Benutzer keine Schuld oder lassen Sie ihn sich dumm fühlen. Vermeiden Sie feindliche oder anstößige Sprache (töten, ausführen, beenden, tödlich, illegal). Vermeiden Sie Großbuchstaben, die oft als schreiend angesehen werden und nicht so lesbar sind. Verwenden Sie keinen Humor.

- **Richtig.** Verwenden Sie die richtige Rechtschreibung und Grammatik (auch in Alphas). Typos sind unprofessionell und peinlich.

- **Kontextuell angemessen.** Verwenden Sie den entsprechenden Schaltflächentext. Vermeiden Sie die Schaltfläche "OK" und verwenden Sie stattdessen "Weiter" oder "Ja/Nein".

### <a name="error-message-examples"></a>Fehlermeldungsbeispiele

|Gut|Schlecht|
|----------|---------|
|"Die gewählte Nummer ist nicht mehr in Betrieb. Bitte überprüfen Sie die Nummer und wählen Sie erneut oder wählen Sie 0 für den Bediener."|- "Fehler (449): Illegale Zahl"<br />- "Dieser nicht behandelte Ausnahmefehler gibt an, dass der Vorgang erfolgreich abgeschlossen wurde."<br /><br /> ![Ungültige Fehlermeldung in Visual Studio](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Zugreifen auf die Hilfe

### <a name="overview"></a>Übersicht
 Zusätzlich zur Dokumentation in MSDN verfügt ein Visual Studio-Benutzer über mehrere Zugriffspunkte, die den Benutzer während der Benutzeroberfläche unterstützen. Um sicherzustellen, dass diese Zugriffspunkte konsistent verfügbar sind, müssen Feature-Teams das von der Umgebung angebotene Hilfesystem nutzen. Diese Access Points sind:

- **Lehr- und Ergänzungstext in Dialogen.** Statischer Text, der Richtung oder Erklärung gibt, entweder auf der UI-Oberfläche oder verfügbar, wenn sie mit der Maus auf ein InfoTip-Symbol zeigt.

- **F1-Hilfe** (nur Editor). Im Visual Studio-Editor kann ein Benutzer darauf vertrauen, dass durch Drücken von F1 jederzeit ein Hilfethema angezeigt wird, das für die aktuelle Auswahl spezifisch ist. Stellen Sie sicher, dass die mit F1 verknüpften Themen angemessen und informativ sind.

- **Hyperlinks zu Hilfethemen.** Ein Hyperlink in einem Dialogfeld, einem Toolfenster oder einer Entwurfsoberfläche, der ein Thema startet, um den Benutzer dabei zu unterstützen, mehr über eine Technologie, Funktion oder Informationen zum Ausführen einer Aufgabe zu erfahren.

- **Hilfemechanismen für die Benutzeroberflächen, z. B. Smarttags und Erstellen von Dialogfeldern.** Diese Mechanismen unterstützen den Benutzer beim Verständnis eines UI-Elements oder beim Erleichtern einer Aufgabe, z. B. Smarttags oder Builderdialogen.

- **UI-Hilfeschaltflächen** (veraltet). Ein sichtbarer Indikator in der Titelleiste, der Zugriff auf das zugehörige F1-Hilfethema gewährt.

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Lehr- und Ergänzungstext in Dialogen
 In Dialogfeldern, die komplexe Aufgaben unterstützen, kann es erforderlich sein, Anweisungstext innerhalb der Benutzeroberfläche zu geben, häufig oben im Dialogfeld oder in der Nähe komplexer Steuerelemente. Weitere Informationen zum Schreibstil finden Sie unter [UI-Text und Terminologie.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="infotips"></a>InfoTipps
 Häufig ist Anweisungstext zu langwierig, um ihn in der Benutzeroberfläche zu positionieren, oder er ist nur für neue Benutzer nützlich, da er sich für erfahrene Benutzer wie Unordnung anfühlt. In diesem Fall sollte der Lehr-/Informationstext als QuickInfo unter einem InfoTip platziert werden.

 InfoTips sollten in der Nähe der Steuerelemente platziert werden, mit denen sie verwandt sind, und das spezifische InfoTip-Symbol verwenden, das unauffällig und doch spürbar ist.

 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-d_InfoTip")

 **Beispiel für einen InfoTip in Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktive Hilfemechanismen

#### <a name="f1-help"></a>F1-Hilfe
 F1 Hilfe ist innerhalb eines Editors oder einer Entwurfsoberfläche erforderlich, jedoch nicht an anderer Stelle in der Visual Studio-Umgebung.

#### <a name="hyperlinks-to-help-topics"></a>Hyperlinks zu Hilfethemen
 Hyperlinks können verwendet werden, um eine Aktion auszuführen, innerhalb der IDE zu navigieren oder die Hilfe in einem Browser zu starten. Weitere Informationen zur Sprache und 07.10.01 Schaltflächen und Hyperlinks finden Sie unter [UI-Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) für visuelle und Layoutrichtlinien.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Hilfe [?] Schaltflächen in Dialogtitelleisten (veraltet)
 Die Schaltflächen "Hilfe [?] in der Titelleiste von Dialogfeldern sind größtenteils veraltet. UI-Themen sind nicht mehr Teil unseres Doc-Modells, und daher gibt es möglicherweise kein relevantes Thema, mit dem ein Link verknüpft werden kann. Im Wesentlichen war die Titelleistenschaltfläche dasselbe wie die F1-Hilfe, und das ist in Dialogfeldern nicht mehr erforderlich. In einigen Fällen kann dies immer noch als Indikator dafür verwendet werden, dass mehr konzeptionelle oder prozedurale Informationen verfügbar sind, obwohl Hyperlinks häufiger in neueren Benutzeroberflächen verwendet werden.

##### <a name="dialogs-created-through-the-environment"></a>Dialoge, die über die Umgebung erstellt wurden
 Viele Shell-Dialoge werden über die **Funktion VBDialogBoxParam** erstellt. Diese freigegebene Funktion wurde aktualisiert, um das Verschieben der **Hilfeschaltfläche** aus dem Dialogfeld in den **?** unter Beibehaltung einer Architektur, die abwärtskompatibel und erweiterbar ist.

 Insbesondere sucht die **Funktion VBDialogBoxParam** in der Dialogfeldvorlage nach einer Schaltfläche, deren ID **IDHELP** (9) oder Bezeichnung **Hilfe** oder **&Hilfe**ist. Wenn eine Hilfeschaltfläche gefunden wird, wird sie ausgeblendet, und der **WS_EX_CONTEXTHELP-Stil** wird dem Dialogfeld hinzugefügt, der die **?** In der Titelleiste des Dialogfelds.

 Wenn das Dialogfeld erstellt wird, wird das Dialogverfahren proc auf einen Stapel übertragen und das Dialogfeld mit einem Dialogfeld proc vor der Verarbeitung namens **DialogPreProc**aufgerufen. Wenn die **?** klicken, sendet es eine **WM_SYSCOMMAND** **von SC_CONTEXTHELP** an das Dialogfeld. **DialogPreProc** erfasst diesen Befehl und ändert ihn in eine **WM_HELP** Nachricht, die an das ursprüngliche Dialogfeld proc übergeben wird.

 Die meisten in der Umgebung erstellten Dialogfelder verfügen über eine Hilfeschaltfläche im Dialogfeld. Wenn das Dialogfeld angezeigt wird, wird die Hilfeschaltfläche automatisch ausgeblendet und nur die **?** Taste funktioniert. Wenn die **?** In Windows wird die Schaltfläche entfernt oder geändert, mit dieser Lösung können Sie schnell zu den ursprünglichen Hilfeschaltflächen zurückkehren.

 Diese Lösung stellt vier Annahmen auf, die Fehler verursachen können:

- Die Hilfeschaltfläche des Dialogfelds ist **IDHELP** (9).

- Das Dialogfeld sieht korrekt aus, wenn die Hilfeschaltfläche ausgeblendet ist.

- Das Dialogfeld ersetzt seine Winproc nicht.

- Das Dialogfeld ist nicht in ein anderes Dialogfeld eingebettet.

  Wenn sich Ihr Dialogfeld in msenv befindet und **VBDialogBoxParam**nicht verwendet, untersuchen Sie die Nutzung von **VBDialogBoxParam,** bevor Sie Ihren eigenen Handler implementieren.

##### <a name="dialogs-created-through-other-packages"></a>Dialoge, die über andere Pakete erstellt wurden
 Sie können Ihre eigene Lösung für Dialogfelder implementieren, die sich außerhalb von msenv befinden. Für eine freigegebene Dialogklasse in Ihrem VSPackage sollten Sie die Schaltfläche in die Titelleiste verschieben oder einen Handler in jedem Dialogfeld implementieren. Der folgende Code ist ein Skelett einer Implementierung, die Ihnen den Einstieg erleichtern soll:

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

##### <a name="help-buttons-in-managed-code"></a>Hilfeschaltflächen im verwalteten Code
 Das Standardverhalten der Fenstertitelleiste Hilfeistin ist im verwalteten Code einfach. Unten ist eine vollständige Demo-Anwendung, die dieses Verhalten veranschaulicht. Im Wesentlichen müssen Sie die **WndProc-Methode** Ihres Formulars überschreiben und dann F1-Hilfeanforderungen abfeuern, wenn eine **SC_CONTEXTHELP** Nachricht abgefangen wird.

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

## <a name="see-also"></a>Weitere Informationen
 [Schriftarten und Formatierungen für Visual](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md) [Studio-Layout für Visual](../../extensibility/ux-guidelines/layout-for-visual-studio.md) Studio-Benachrichtigungen [und -Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
