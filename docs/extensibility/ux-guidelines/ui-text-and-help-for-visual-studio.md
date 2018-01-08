---
title: "Der Benutzeroberflächentext und Hilfe für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 555fd622f5655a69ba77f3905a39635e01831c76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ui-text-and-help-for-visual-studio"></a>Der Benutzeroberflächentext und Hilfe für Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a>Der Benutzeroberflächentext und Terminologie  
 Verständlich Text ist entscheidend, um effektive UI. Softwarebenutzer lesen tendenziell "Bezeichnungen" zuerst, nämlich die relevantesten zum Abschließen der Aufgabe. Statischer Text wird mit weniger Häufigkeit gelesen. Planen Sie Benutzern, ihre Arbeitssitzungen mit einer schnellüberprüfung, der das gesamte Fenster, gefolgt von einem Lesen der Benutzeroberfläche in dieser Reihenfolge ungefähre beginnen:  
  
1.  Interaktiven Steuerelementen in der Mitte  
  
2.  Commit-Schaltflächen  
  
3.  Interaktive Steuerelemente, die an anderer Stelle gefunden  
  
4.  Hauptanleitung  
  
5.  Zusätzliche erläuterungen  
  
6.  Window-Titel  
  
7.  Anderen statischen Text im Hauptteil  
  
### <a name="usage-patterns-for-ui-text"></a>Verwendungsmuster für Benutzeroberflächen-text  
  
#### <a name="title-bar-text"></a>Text der Titelleiste  
 Text der Fenstertitelleiste muss den Befehl übereinstimmen, durch die die Benutzeroberfläche generiert.  
  
#### <a name="instructional-text-helper-text"></a>Hinweistext (Hilfetext)  
 In einigen Dialogfeldern ist es hilfreich, deutliche hauptanleitung erläutert, was im Fenster oder auf der Seite bereitstellen. Dies wird manchmal als "Hilfetext" bezeichnet  
  
##### <a name="writing-style-rules-for-helper-text"></a>Schreiben von Formatierungsregeln für Hilfetext  
  
-   Keine wird erläutert, die offensichtlich. Wenn es absolut notwendig ist, verwenden Sie keine Anweisungstext.  
  
-   Hinweistext befindet sich immer oben im Dialogfeld und die konkrete auszuführende Aufgabe lesen sollten.  
  
-   Genau kannst du Benutzer was sie tun müssen. Vermeiden Sie übermäßige Kommunikation und Redundanz.  
  
-   Überprüfen Sie jedes Fenster, und entfernen Sie doppelte Wörter und Anweisungen.  
  
-   Behalten Sie kurze Anweisungstext. Wenn weitere Informationen erforderlich für bestimmte Benutzer oder Szenarien sind, geben Sie einen Link zu detaillierten konzeptionellen Themen online.  
  
-   Schreiben Sie den Text ein, sodass jedes Wort Gewichtung enthält und erforderlich ist.  
  
-   Führen Sie die vorhandenen Microsoft-Leitfaden für [Benutzeroberflächentext](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [Stil und einem Ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Zusätzliche Anweisungen  
 Zusätzliche Anweisungen bieten zusätzliche Informationen, mit denen den Benutzer verstehen, Steuerelemente oder Gruppierungen steuern kann. Dies kann auch erforderlich, um zu verstehen, in welchem Format das Eingabesteuerelement erwartet Hinweistext enthalten. Verwenden Sie zusätzliche Anweisungen nur selten auf. Reservieren sie für Fälle, in denen es wahrscheinlich ist, dass der Benutzer die vollständig von der Auswahl bekannt wird nicht, die sie vornehmen.  
  
 ![Ergänzender Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Ergänzender Text in Visual Studio**  
  
 ![Ergänzender Text in Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Ergänzender Text in Visual Studio**  
  
#### <a name="infotips"></a>Infotipps  
 Häufig der Anweisungstext möglicherweise so umfangreich, dass direkte in der Benutzeroberfläche positionieren oder kann nur an neue Benutzer, wie übersichtliche erfahrenen Benutzern nützlich sein. In diesem Fall sollte der Anweisungstext/Informationstext als QuickInfo unter einem Infotipp platziert werden.  
  
 Infotipps sollten in der Nähe von den Steuerelementen, die sie beziehen sich auf und die bestimmte Infotipp-Symbol, das unaufdringlichen noch ist die zu verwendende bemerkbar gespeichert werden.  
  
 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 D_InfoTip")  
  
 **Beispiel für einen Infotipp in Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Schreiben von Formatierungsregeln für Infotipps  
  
-   Schreiben Sie Infotipps als vollständigen Sätze. Sie benötigen bestimmte Verben Satz Groß-/Kleinschreibung und Zeichensetzung.  
  
-   Verwenden Sie Infotipps Haupt-Anweisung oder in der Informationen zu ergänzen. Wenn Sie unterschiedliche Wörter nur dazu verwenden, um die Grundidee bereits erwähnt, benötigen Sie nicht mit einen Infotipp.  
  
-   Behalten Sie Infotipps kurz und knapp. Verwenden Sie kurze Wörter und Plain, alltägliche Sprache, die unterstützt und fördert die Benutzer.  
  
-   Führen Sie die vorhandenen Microsoft-Leitfaden für [Benutzeroberflächentext](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [Stil und einem Ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Steuerelementbezeichnungen  
 Steuerelementbezeichnungen sollte kurz und knapp werden, und befolgen Sie die [Windows-Desktop-Leitfaden für Steuerelemente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Weitere Informationen zum Steuerelement Bezeichnungsformat und Platzierung innerhalb der Benutzeroberfläche finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Links zu Hilfethemen  
 Hilfelinks können entweder in Anweisungstext oder im Text der Benutzeroberfläche platziert werden. Sie werden von Links zur Hilfe oder interne Dialogfelder zu starten.  
  
##### <a name="visual-style-rules-for-help-links"></a>Der visuelle Stilregeln für Links zu Hilfethemen  
  
-   Verwenden Sie die richtige Umgebungsfarben für Links. Ein ordnungsgemäß formatierte Hyperlink wird rot, wenn geklickt nicht kurz. Wenn Sie diesen sehen, ist es ein Hinweis, dass Umgebungsfarben nicht verwendet werden.  
  
-   Unterstreichungen sollte nur verwendet werden, wenn darauf gezeigt wird oder wenn die Verknüpfung eines Absatzes eingebettet ist.  
  
-   Finden Sie ausführlichere Informationen zu visuellen und Interaktion von Formaten für Links Schaltflächen und Links.  
  
##### <a name="writing-style-rules-for-help-links"></a>Schreiben von Formatierungsregeln für Links zu Hilfethemen  
  
-   Beim Starten von Dialogen verwalten den Standards für Ellipsen: keine mit den Auslassungspunkten für die Navigation, Ellipsen, wenn die Aufgabe weitere Benutzeroberfläche erfordert.  
  
     ![Hilfelink in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 E_HelpLink")  
  
     **Auslassungspunkte (...) in einen Hilfelink gibt an, dass die Aufgabe eine weitere Benutzeroberfläche benötigen.**  
  
-   Links darf nicht mit "Weitere Informationen," beginnen, wie dies nicht die Absicht des Benutzers ist. Der Benutzer möchte eine bestimmte Frage zu beantworten, erhalten eine allgemeine Education nicht ab.  
  
-   Ausdruck Hilfelinks, damit sie die Frage, dass das Thema beantwortet werden sollen.  
  
     Falsche:  
     "Weitere Informationen zu Preisen von Windows Azure Mobile Services"  
  
     Richtig:  
     "Welche Preisoptionen stehen für Windows Azure Mobile Services zur Verfügung?"  
  
-   Verwenden Sie niemals *klicken Sie auf...*  auf den Text des Links.  
  
-   Verknüpfen Sie nie nur das Wort "hier". Dies ist für einige Sprachausgaben, die nur den als Hyperlink dargestellten Wort voice werden problematisch.  
  
     Falsche:  
     "Finden Sie Informationen zu Windows Azure Mobile Services **hier**"  
  
     Richtig:  
     "Welche Preisoptionen stehen für Windows Azure Mobile Services zur Verfügung?"  
  
-   Weitere Informationen zu den richtigen Handschrift für Links zu Hilfethemen, finden Sie unter der [Windows-Desktop-Leitfaden für Hilfe](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Hinweistext  
 Hinweistext wird als Wasserzeichen in einem Steuerelement oder unterhalb des Steuerelements angezeigt. Richtige Formatierung mit dem entsprechenden VSColors Token angewendet `Environment.GrayText`.  
  
 Sie können in verschiedene Formate angezeigt.  
  
-   Anstelle der Steuerelement-Bezeichnung:  
  
     ![Text in Visual Studio-Hinweis](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   Erteilen mit einem Verb Anweisungen ein:  
  
     ![Text in Visual Studio-Hinweis](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   Mit Text, der angibt, eines Eintrags erforderlichen:  
  
     ![Text in Visual Studio-Hinweis](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>Wasserzeichentext  
 Auf eine leere Entwurfsoberfläche sollte der Text angeben, was Sie tun sowie Links zu anderen verwandten Windows bei Bedarf zu öffnen:  
  
 ![Text in Visual Studio Wasserzeichen](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 I_WatermarkText")  
  
 **Beispiel für Wasserzeichentext in Visual Studio**  
  
### <a name="common-terminology"></a>Allgemeine Terminologie  
  
|Begriff|Erklärung|Kommentar|  
|----------|-----------------|-------------|  
|Melden Sie sich bei / Abmelden|Verben gleichbedeutend mit dem Web für die Darstellung der Authentifizierung in einer Web-Eigenschaft verwendet. Clients verwenden wir dieses einmal als Konzept der obersten Ebene für die Signierung und IDE-benutzerverbindung, das eine Identität der obersten Ebene, die auf höherer Ebene Funktionen darstellt wie roaming und Lizenzierung stehen nicht für alle anderen Verbindungen zur Verfügung stellt.|Der IDE-Benutzer ist die einzige Funktion, die sollten darstellen einer Anmeldung / Abmeldung Verbs an, wie es den obersten Ebene IDE-Benutzer darstellt.|  
|Eine Verbindung herstellen / trennen|Verwenden Sie in der Orte, in denen eine Funktion für eine einzelne Verbindung mit einer online-Dienst verwaltet.|Server-Explorer, in dem Sie nur eine aktive Azure-Verbindung zu einem Zeitpunkt verfügen können, ist ein Beispiel für die Verbindung herstellen/trennen.|  
|Hinzufügen / Entfernen|Nicht destruktiver. Verwenden Sie beim Hinzufügen oder entfernen ein Element aus einer Liste.|Dialogfeld mit der TFS-Verbindungs-Manager Server ist ein Beispiel für hinzufügen/entfernen.|  
|Löschen|Destruktiven. Verwenden Sie nur, wenn das entfernte Element dauerhaft verworfen oder vom Datenträger gelöscht werden.|"Delete" müssen in der Regel eine Aufforderung, wenn das Ergebnis eine Datei vom Datenträger gelöscht wird.|  
  
## <a name="error-messages"></a>Fehlermeldungen  
  
### <a name="overview"></a>Übersicht  
 Arbeitsspeicherfehler. Festlegen von Einschränkungen für die Möglichkeiten des Benutzers ist ein aussagefähiger erster Schritt verhindert vermeidbaren Fehlermeldungen. Wenn ein Fehler auftritt, kann eine gut geschriebene Fehlermeldung entscheidend verringern das Problem wechseln. Fehlermeldungen sind wohl mit einer der wichtigsten Typen Benachrichtigungstyp, der dem Benutzer angezeigt wird, da sie synchron sind, und zeigen kein Problem, das gelöst werden muss, wird. Schlecht geschriebene Fehlermeldungen lassen Sie Benutzer auf ihre eigenen, um zu entscheiden, die Ursache der Fehler und alle möglichen Lösungen.  
  
 Benutzer möglicherweise nicht mehr achten übermäßig beansprucht oder Fehlermeldungen, verwirrend erscheinen, damit nur erforderliche Write-Nachrichten, die Wert für den Benutzer hinzufügen auftreten. Wenn die Nachricht einfach eine Benachrichtigung ist, verwenden Sie eine alternative Präsentation.  
  
### <a name="rules-for-creating-an-error-message"></a>Regeln zum Erstellen einer Fehlermeldung  
  
-   Wenn Sie Fehlermeldungen zu erstellen, wählen Sie die entsprechende Fehlermeldung-Ebene für die Zielgruppe. Testziel: einfach Zusammenfassungen, die eine Aktion, mit denen der Benutzer bereitstellen, falls zutreffend. Status stimmen nicht alle Funktionen, die der Benutzer nicht kennen muss.  
  
-   Geben Sie schneller ein konstruktives um Unterstützung zu erhalten. Es ist einfacher zu lesen und wirken sich auf eine Fehlermeldung angezeigt, die Anweisung enthält.  
  
-   Verwenden Sie keine doppelten negative.  
  
-   Führen Sie eine automatisierte, und eine manuelle Grammatik überprüfen auf eine beliebige Fehlermeldung, die Sie schreiben.  
  
-   Vermeiden Sie für komplexe Fehlermeldungen laufende Kommunikation. Verwenden Sie niemals ein F1-ereigniseinbindung für die Fehlermeldung an. Die Nachricht selbst sollten ausreichen.  
  
-   Verwenden Sie das richtige Symbol.  
  
-   Stellen Sie Fragen leicht zu verstehen und verwenden die Schaltflächen, die klar Auswahlmöglichkeiten, z. B. "Delete" und "Abbrechen".  
  
-   Werden Sie für Warnungen zur zur Folge, dass Sie den Vorgang fortsetzen. Das Ergebnis sollte die Schaltflächen angegeben werden.  
  
-   Beschrieben Sie für Fehler, was der Benutzer ausführen kann, um das Problem zu beheben. Schaltflächen sollten Aktionen sein, und sagen Sie "Schließen". Verwenden Sie keine Schaltfläche "OK" für eine Fehlermeldung angezeigt.  
  
-   Einige Fragen zu sich selbst beim Erstellen einer Fehlermeldung angezeigt:  
  
    -   Kann der Benutzer zur Lösung des Problems zu diesem Fehler aufrufen allein herausfinden, wie?  
  
    -   Wird der Benutzer die gleiche Vokabular wie dieser Fehler verwendet?  
  
    -   Ist dieser Fehler mehrdeutig oder in mehrere Situationen freigegeben? Wenn dies der Fall ist, führen Sie wie Sie Benutzer der Projektmappe geführt, die sie benötigen?  
  
#### <a name="build-errors"></a>Buildfehler  
 Seit Visual Studio ein Software Development-Tool handelt, verfügen viele Komponenten eine Kompilierung konvertieren oder Codierung Schritt, um die Arbeit des Entwicklers in binärer Form konvertieren. Diese Konvertierungen können Fehler verursachen, wenn der Compiler nicht ordnungsgemäß geschriebenes Dateien nicht verarbeiten kann oder wenn Compileroptionen ordnungsgemäß festgelegt wurden nicht.  
  
 Visual Studio-Benutzer können eine enorme Anzahl von Entwicklung Stunden Buildfehler behoben verbringen. Diese Auflösungszeit steigt, wenn Fehler auftreten, Abhängigkeiten oder wenn Fehlermeldungen schlecht geschrieben werden die an die Quelle des Fehlers aufdecken erschwert.  
  
 Die beste Buildfehler sind those, die occur an nicht in der ersten Stelle, weshalb Visual Studio bietet die AutoVervollständigen-Funktion, und IntelliSense Wellenlinien. Schema Validierungssteuerelemente und ähnliche Tools bieten die gleiche Art von Feedback. Diese Mechanismen geführt proaktiv den Benutzer zum Erstellen von wohlgeformte Code, verringern die Wahrscheinlichkeit von Buildfehlern.  
  
 Visual Studio bietet ein Toolfenster, in denen Benutzer lesen können, und Navigieren durch die Fehler, die in ihren Dokumentfenster aufgetreten ist. Tastenkombinationen werden bereitgestellt, sodass der Benutzer kann schnell große Mengen von Code navigieren und fahren Sie direkt mit den Speicherort des Problems. Visual Studio ermöglicht auch jede Buildfehler, um auf ein bestimmtes Schlüsselwort/Hilfekontext-ID gebunden werden, sodass der Benutzer direkt zu einem Hilfethema wechseln kann, die ausführlichere Informationen zu diesem Fehler erhalten.  
  
 Schreiben Sie klare und prägnante Buildfehler:  
  
-   **Verwenden Sie einfachen Sprache** , die das Problem mit wenigen oder gar keinen Compilerfehler Jargon erläutert. Der Text, der ein Buildfehler darf nicht übermäßig technische sein.  
  
-   **Mögliche Ursachen werden kann.** Z. B. "Fehlender Doppelpunkt zwischen der Eigenschaft und Wert in der ' (Eigenschaft): (Wert)' Deklaration."  
  
-   Geben Sie Details zu potenziellen Fehlerbehebungen. Wenn nicht genügend Speicherplatz vorhanden ist, können zusätzliche Details in den entsprechenden Hilfethema abgelegt werden.  
  
### <a name="components-of-a-well-written-error-message"></a>Komponenten einer gut geschriebene Fehlermeldung  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Verwenden Sie die Shell Dialogfeld Dienst Fehlermeldungen vorliegen.  
 Mithilfe des Shell-Dialogfeld-Diensts können Sie die Darstellung der Nachricht, Schriftarten insbesondere ohne wesentliche Änderungen an einzelnen Elementen. Verwenden der **IErrorInfo** Mechanismen und melden Sie diese mit **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wählen Sie eine Präsentation wirksam und entsprechende Benachrichtigung.  
 Verwenden Sie ein modales Dialogfeld mit einer kritischen Warnung, wenn sofortige Maßnahmen, zur Vermeidung von Datenverlust (synchrone Benachrichtigung erforderlich ist). Wichtige Symbole sind für Situationen reserviert in die durch die Schließen der Nachricht ohne lesen sie negative Auswirkungen führen kann. Verlust von Daten ist eine wichtige Situation, die eine Antwort Alarm auf Dokumentebene erfordert. Das Symbol "Kritisch" übermäßige desensitizes Benutzer dessen Bedeutung. Falls die Fehlermeldung zur Information ist, sollten Sie alternativen für ein modales Dialogfeld (asynchrone Benachrichtigung).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Geben Sie eine bereinigen, kompakte Erklärung der Ursache des Problems anstatt eine Erklärung an.  
 Benutzer mit technischen Details in der Erläuterung überlasten sind eher Fehlermeldungen ignorieren werden. Beispiele für gute messaging:  
  
-   "Die angeforderte Datei öffnen kann."  
  
-   "Eine Verbindung mit dem Internet herstellen kann."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Geben Sie Informationen zum Beheben des Problems.  
 Bieten Sie Vorschläge für die Benutzer dazu, wie zum Beheben des Problems. Werden Sie ehrlich mit dem Benutzer, wenn keine Vorschläge vorhanden sind. Geben Sie direkte Links zu alternativen online-Informationsquellen, z. B. den technischen Support oder Unterstützung durch die Community. Versuchen Sie, um Benutzer auf bestimmte online-Informationen für das Problem zu verweisen. Fehler-ID sollten Sie in der Verknüpfen von Benutzern zu einem Diskussionsthread zu diesem Fehler. Beispiele für gute messaging:  
  
-   "Stellen Sie sicher, dass Sie mit dem Internet verbunden sind, und versuchen Sie es erneut."  
  
-   "Stellen Sie sicher, dass die Datei vorhanden ist und dass Sie die Berechtigung, um ihn zu öffnen."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Schreiben Sie eine Nachricht, die kurz und zu dem Punkt ist.  
 Eine Fehlermeldung kann benachrichtigen, erläutern, und bieten eine Lösung jedoch weiterhin ignoriert, wenn es zu umfangreich ist. Eine Lösung besteht darin progressiven Offenlegung von mit einer Schaltfläche "Details" verwenden. Geben Sie z. B. eine kurze Beschreibung/die Projektmappe, und veröffentlichen Sie weitere Informationen unter einer Schaltfläche "Details". Wenn Benutzer sich entscheiden, Weitere Informationen zum Fehler zu lesen, können sie dies tun.  
  
 Die Sprache in der Nachricht sollte Folgendes sein:  
  
-   **Domäne geeignet.** Verwenden Sie die Sprache aus, die der Benutzer verstehen. Obwohl unseren Kunden Entwickler sind, nicht sie häufig verfügen über den Kontext und die Terminologie, das wir haben.  
  
-   **Spezifisch.** Vermeiden Sie unklare Formulierung "", und weisen Sie bestimmte Namen und Speicherorte der beteiligten Objekte. Z. B. "Zeichen ist ungültig" ist eine Fehlermeldung z. B. nicht hilfreich. Welches Zeichen? "Datei nicht gefunden." Welche Datei?  
  
-   **Höflich.** Nicht den Benutzer Informationen geben oder ihn dumm aussehen lassen. Vermeiden Sie feindlichen oder anstößige Sprache (kill, ausführen, beenden, schwerwiegender, nicht zulässig). Vermeiden Sie Großbuchstaben-Text, der häufig als Shouting angezeigt wird, und ist nicht als lesbar. Verwenden Sie keine Humor.  
  
-   **Richtig.** Verwenden Sie die richtige Rechtschreibung und Grammatik (auch im Alphawerte). Tippfehler sind unprofessionell und peinliche.  
  
-   **Angemessen.** Verwenden Sie die entsprechenden Schaltflächentext. Vermeiden Sie die Schaltfläche "OK", und verwenden Sie stattdessen "Weiter" oder "Ja/Nein".  
  
### <a name="error-message-examples"></a>Beispiele für Fehler  
  
|Gut|Ungültige|  
|----------|---------|  
|"Die Anzahl, die Sie gewählt ist nicht mehr im Dienst. Bitte überprüfen Sie die Anzahl, und wählen Sie erneut oder wählen Sie 0 für den Operator."|-"Fehler (449): Ungültige Anzahl"<br />-"Dieser Fehler nicht behandelte Ausnahme gibt an, dass der Vorgang erfolgreich abgeschlossen."<br /><br /> ![Ungültige Fehlermeldung in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 A_ErrorDialog")|  
  
## <a name="accessing-help"></a>Zugreifen auf die Hilfe  
  
### <a name="overview"></a>Übersicht  
 Zusätzlich zu den in der MSDN-Dokumentation wurde ein Visual Studio-Benutzer mehrere Zugriffspunkte an den Benutzer klicken Sie auf der Benutzeroberfläche zu unterstützen. Um sicherzustellen, dass diese Zugriffspunkte ständig verfügbar sind, müssen Featureteams das Hilfesystem angeboten, die von der Umgebung nutzen. Diese Zugriffspunkte sind:  
  
-   **Anweisungstext und zusätzlichen Text in Dialogfeldern.** Statischer Text, der Richtung oder eine Erläuterung, entweder auf der Benutzeroberfläche Fläche oder zur Verfügung, wenn darauf gezeigt wird, über ein Symbol Infotipp bietet.  
  
-   **F1-Hilfe** (nur-Editor). In der Visual Studio-Editor kann ein Benutzer vertrauen, dass jederzeit durch Drücken von F1 ein Hilfethema, das speziell für die aktuelle Auswahl angezeigt wird. Sicherstellen Sie, dass F1 zugeordnete Themen geeignet und diesen informativ sind.  
  
-   **Links zu Hilfethemen.** Ein Link in ein Dialogfeld, Toolfenster oder Entwurfsoberfläche, die ein Thema, um den Benutzer zu unterstützen, erfahren Sie mehr über eine Technologie, die Funktion oder die Informationen zur Ausführung einer Aufgabe gestartet wird.  
  
-   **Hilfsprogramm-UI Mechanismen, z. B. Smarttags und Erstellen von Dialogfeldern** Diese Mechanismen helfen den Benutzer zum Verständnis dafür sind ein Benutzeroberflächenelement oder ein Task, z. B. Smarttags oder Builder Dialoge erleichtern.  
  
-   **Hilfe zur Benutzeroberfläche Schaltflächen** (veraltet). Ein sichtbar Indikator in der Titelleiste, die Zugriff auf die verwandten F1-Hilfethema gewährt.  
  
### <a name="text"></a>Text  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Anweisungstext und zusätzlichen Text in Dialogfeldern  
 In Dialogfeldern, die komplexe Aufgaben unterstützen, möglicherweise eine Anforderung von Anweisungstext innerhalb der Benutzeroberfläche häufig oben im Dialogfeld oder in der Nähe komplexe Steuerelemente. Finden Sie unter [UI Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) ausführliche Informationen zum Format schreiben.  
  
#### <a name="infotips"></a>Infotipps  
 Häufig Anweisungstext möglicherweise so umfangreich, dass Sie direkt in der Benutzeroberfläche positionieren oder kann nur an neue Benutzer, wie übersichtliche erfahrenen Benutzern nützlich sein. In diesem Fall sollte der Anweisungstext/Informationstext als QuickInfo unter einem Infotipp platziert werden.  
  
 Infotipps sollten in der Nähe von den Steuerelementen, die sie beziehen sich auf und die bestimmte Infotipp-Symbol, das unaufdringlichen noch ist die zu verwendende bemerkbar gespeichert werden.  
  
 ![Infotipp in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 D_InfoTip")  
  
 **Beispiel für einen Infotipp in Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Interaktive Hilfemechanismen  
  
#### <a name="f1-help"></a>F1-Hilfe  
 F1-Hilfe erforderlich ist in einem Editor oder die Entwurfsoberfläche, aber nicht an anderer Stelle in der Visual Studio-Umgebung.  
  
#### <a name="hyperlinks-to-help-topics"></a>Links zu Hilfethemen  
 Hyperlinks können verwendet werden, eine Aktion auszuführen, Navigieren in der IDE oder Hilfe in einem Browser zu starten. Finden Sie unter [UI Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) ausführliche Informationen zu Sprache und 07.10.01 Schaltflächen und Hyperlinks visuelles Element und Layout-Richtlinien.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Hilfe [?] Schaltflächen im Dialogfeld Titelleisten (veraltet)  
 Den meisten Fällen sind die Schaltflächen Hilfe [?] in der Titelleiste von Dialogen veraltet. UI-Themen sind nicht mehr Teil unserer Doc-Modells, und daher möglicherweise kein relevantes Thema zu verknüpfen. Im Wesentlichen die Titelleistenschaltfläche war das gleiche wie die F1-Hilfe und in Dialogfeldern nicht mehr erforderlich ist. In einigen Fällen kann diese weiterhin verwendet werden dies ein Hinweis darauf, dass weitere konzeptionelle oder prozeduraler Informationen verfügbar sind, obwohl Hyperlinks in Benutzeroberflächen mit neueren häufiger verwendet werden.  
  
##### <a name="dialogs-created-through-the-environment"></a>Dialoge, die über die Umgebung erstellt  
 Zahlreiche Shell Dialoge werden erstellt, über die **VBDialogBoxParam** Funktion. Diese freigegebenen Funktion wurde aktualisiert, um Unterstützung bei der Umstellung die **Hilfe** Schaltfläche im Dialogfeld, um die **?** Schaltfläche Beibehaltung der vorhandenen eine Architektur, die Abwärtskompatibilität ist kompatibel und erweiterbar.  
  
 Insbesondere die **VBDialogBoxParam** Funktion prüft der Dialogfeldvorlage für eine Schaltfläche mit der ID **IDHELP** (9) oder die Bezeichnung **Hilfe** oder **&-Hilfe**. Wenn eine Schaltfläche "Hilfe" gefunden wird, wird es ausgeblendet und die **WS_EX_CONTEXTHELP** Format wird hinzugefügt, um das Dialogfeld, in dem platziert die **?** Schaltfläche in der Titelleiste des Dialogfelds.  
  
 Wenn das Dialogfeld "erstellt wird, wird das Dialogfeld Proc auf einen Stapel und ruft das Dialogfeld mit einer vorab verarbeitete Dialogfeldprozedur, die mit dem Namen **DialogPreProc**. Wenn die **?** Schaltfläche geklickt wird, sendet er eine **WM_SYSCOMMAND** von **SC_CONTEXTHELP** im Dialog "". Die **DialogPreProc** dieser Befehl erfasst und ändert sich zu einem **WM_HELP** Nachricht, die an der ursprünglichen Dialogfeld Prozedur übergeben wird  
  
 Die meisten Dialogfelder der Umgebung erstellt haben eine Schaltfläche "Hilfe" im Dialog. Wenn das Dialogfeld angezeigt wird, ist die Schaltfläche "Hilfe" automatisch ausgeblendet und nur die **?** Schaltfläche funktioniert. Wenn die **?** Schaltfläche jemals entfernt oder in Windows geändert wird, können diese Lösung schnell wieder den ursprünglichen Hilfe-Schaltflächen verschieben.  
  
 Diese Lösung Annahmen aus vier, die Fehler verursachen könnte:  
  
-   Schaltfläche "Hilfe" im Dialogfeld wird **IDHELP** (9).  
  
-   Das Dialogfeld sieht richtig, wenn die Schaltfläche "Hilfe" ausgeblendet ist.  
  
-   Das Dialogfeld wird nicht seine Winproc ersetzen.  
  
-   Das Dialogfeld "ist nicht in ein weiteres Dialogfeld eingebettet.  
  
 Wenn Ihr Dialogfeld befindet sich im Msenv und verwendet keine **VBDialogBoxParam**, untersuchen Sie die Nutzung von **VBDialogBoxParam** vor der Implementierung Ihrer eigenen Handlers.  
  
##### <a name="dialogs-created-through-other-packages"></a>Dialoge, die in anderen Paketen erstellt  
 Sie können Ihre eigene Lösung für Dialoge implementieren, die sich außerhalb der Msenv befinden. Erwägen Sie bei einer gemeinsam genutzten Dialogfeldklasse in Ihrem VSPackage verschieben die Schaltfläche mit den in der Titelleiste oder implementieren einen Handler auf jedem Dialogfeld ein. Der folgende Code ist ein Gerüst für eine Implementierung, die Ihnen beim Einstieg helfen:  
  
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
 Überschreiben von Standardverhalten der Fenster Hilfe Titelleistenschaltfläche des ist einfach in verwaltetem Code. Es folgt eine vollständige demoanwendung, die dieses Verhalten veranschaulicht wird. Im Wesentlichen müssen Sie des Formulars überschreiben **WndProc** -Methode und anschließend Feuer deaktiviert F1-Hilfe fordert bei einer **SC_CONTEXTHELP** Nachricht abgefangen wird.  
  
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
 [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)