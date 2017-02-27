---
title: "Benutzeroberfl&#228;chen-Text und die Hilfe f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Benutzeroberfl&#228;chen-Text und die Hilfe f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> Benutzeroberflächen\-Text und Terminologie  
 Verständlich Text ist entscheidend für effektiven Benutzeroberfläche. Softwarebenutzer dazu neigen, lesen Sie Bezeichnungen zuerst, nämlich die relevantesten zum Durchführen der jeweiligen Aufgabe. Statischer Text wird weniger oft gelesen. Planen Sie für Benutzer, ihre Arbeitssitzungen mit einen schnell\-Scan das gesamte Fenster, gefolgt von einer Lesen der Benutzeroberfläche in dieser Reihenfolge ungefähre zu starten:  
  
1.  Interaktive Steuerelemente in der Mitte  
  
2.  Commit\-Schaltflächen  
  
3.  Interaktive Steuerelemente, die an anderer Stelle gefunden  
  
4.  Haupt\-Anweisungen  
  
5.  Zusätzliche Erläuterung  
  
6.  Fenstertitel  
  
7.  Anderen statischen Text im Hauptteil  
  
### Verwendungsmuster für Benutzeroberflächen\-text  
  
#### Titelleiste  
 Titelleistentext muss mit dem Befehl übereinstimmen, der die Benutzeroberfläche erzeugt.  
  
#### Hinweistext \(Hilfsprogramm Text\)  
 In einigen Dialogfeldern ist es hilfreich zu bedeutenden main Anweisungen erläutert, was Sie im Fenster oder auf der Seite. Dies wird manchmal als "Helper Text." bezeichnet  
  
##### Schreiben von Formatierungsregeln für Hilfetext  
  
-   Erläutern Sie nicht offensichtlich. Wenn es absolut notwendig ist, enthalten Sie keine Anweisungstext.  
  
-   Hinweistext befindet sich immer am oberen Rand des Dialogfelds, und Lesen Sie die Aufgabe ausgeführt wird.  
  
-   Erklären Sie genau den Benutzern was sie tun müssen. Vermeiden Sie übermäßige Kommunikation und Redundanz.  
  
-   Überprüfen Sie jedes Fenster, und entfernen Sie doppelte Wörter und Anweisungen.  
  
-   Halten Sie kurze Anweisungstext. Wenn weitere Informationen erforderlich für bestimmte Benutzer oder Szenarien sind, geben Sie einen Link zu detaillierten konzeptionelle Themen online.  
  
-   Schreiben Sie den Text, sodass jedes Wort Gewichtung enthält und erforderlich ist.  
  
-   Führen Sie die vorhandenen Microsoft\-Anleitung für [Benutzeroberflächentext](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [Stil](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Zusätzliche Hinweise  
 Zusätzliche Anweisungen bieten zusätzliche Informationen, mit denen den Benutzer verstehen, Steuerelemente oder Gruppierungen steuern kann. Dies kann auch notwendig, welches Format zu verstehen, das Eingabesteuerelement erwartet, Hinweistext umfassen. Verwenden Sie die zusätzliche Anweisungen sparsam. Reservieren sie für Fälle, in denen es wahrscheinlich ist, dass der Benutzer wird nicht vollständig die Auswirkungen der Wahl verstehen, die sie vorgenommen werden.  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601\-b\_SupplementalText1")  
  
 **Ergänzender Text in Visual Studio**  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601\-c\_SupplementalText2")  
  
 **Ergänzender Text in Visual Studio**  
  
#### Infotipps  
 Häufig der Anweisungstext möglicherweise so umfangreich, dass in der Benutzeroberfläche an position oder kann nur für neue Benutzer, wie Überfrachtung erfahrenen Benutzern hilfreich sein. In diesem Fall sollte der Anweisungstext\/Informationstext als QuickInfo in einem Infotipp platziert werden.  
  
 Infotipps sollte in der Nähe von den Steuerelementen, die sie beziehen sich auf und verwende das bestimmte Infotipp\-Symbol, das unauffällig noch nicht bemerkbar platziert werden.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Beispiel für einen Infotipp in Visual Studio**  
  
##### Schreiben von Formatierungsregeln für Infotipps  
  
-   Schreiben Sie vollständige Sätze Infotipps. Sie erfordern bestimmte Verben Großbuchstaben und Zeichensetzung.  
  
-   Verwenden Sie ergänzen die Informationen oder Anweisung Infotipps. Wenn Sie unterschiedliche Wörter nur verwenden die Grundidee wie bereits erwähnt, benötigen Sie keinen Infotipp.  
  
-   Halten Sie Infotipps kurz und einfach. Verwenden Sie kurze Wörter und Plain, alltägliche Sprache, die unterstützt und fördert den Benutzer.  
  
-   Führen Sie die vorhandenen Microsoft\-Anleitung für [Benutzeroberflächentext](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) und [Stil](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Bezeichnungen  
 Bezeichnungen kurz und knapp werden, und befolgen Sie die [Windows\-Desktop\-Leitfaden für Steuerelemente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Weitere Informationen zu Steuerelement Bezeichnungsformat und Platzierung der Benutzeroberfläche finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### Links zu Hilfethemen  
 Links zu Hilfethemen können entweder in Hinweistext oder im Hauptteil der Benutzeroberfläche platziert werden. Sie können Links zur Hilfe oder interne Dialoge zu starten.  
  
##### Visual Formatierungsregeln für Links zu Hilfethemen  
  
-   Verwenden Sie die richtige Umgebung\-Farben für Hyperlinks. Ein ordnungsgemäß formatierte Hyperlink wird rot beim nicht kurz. Wenn Sie dies sehen, ist es ein Hinweis, dass die Farben der Umgebung nicht verwendet werden.  
  
-   Unterstrichen sollte nur verwendet werden, auf die gezeigt wird, oder wenn die Verknüpfung eines Absatzes eingebettet ist.  
  
-   Weitere Informationen zu visuellen und Interaktion Formatvorlagen für Hyperlinks finden Sie unter Schaltflächen und Hyperlinks.  
  
##### Schreiben von Formatierungsregeln für Links zu Hilfethemen  
  
-   Beim Starten von Dialogfeldern, verwalten Sie die Standards für die Ellipsen: keine Ellipse für die Navigation, Ellipsen, wenn der Task zusätzliche Benutzeroberfläche erforderlich ist.  
  
     ![Help link in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601\-e\_HelpLink")  
  
     **Auslassungspunkte \(...\) in der Hilfe zu einem deutet Link der Task zusätzliche Benutzeroberfläche erforderlich ist.**  
  
-   Links sollte nicht mit "Lernen", beginnen, da dies nicht die Absicht des Benutzers ist. Der Benutzer möchte eine bestimmte Frage zu beantworten, eine allgemeine Education nicht empfangen.  
  
-   Ausdruck Hilfelinks, damit sie die Frage, dass das Thema beantwortet werden sollen.  
  
     Falsch:  
     "Erfahren Sie mehr über Windows Azure Mobile Services Preise"  
  
     Korrigieren:  
     "Welche Preisoptionen stehen für Windows Azure Mobile Services zur Verfügung?"  
  
-   Verwenden Sie niemals *Klicken Sie auf...* auf den Text des Links.  
  
-   Keine Verknüpfung nur das Wort "hier". Dies ist für einige Bildschirmsprachausgaben, die nur die als Hyperlink formatierte Wort voice werden problematisch.  
  
     Falsch:  
     "Informieren Sie sich Windows Azure Mobile Services **hier**"  
  
     Korrigieren:  
     "Welche Preisoptionen stehen für Windows Azure Mobile Services zur Verfügung?"  
  
-   Weitere Informationen zu den richtigen Schreibstil für Links zu Hilfethemen, finden Sie unter der [Windows\-Desktop\-Anleitung für die Hilfe](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### Hinweistext  
 Hinweistext wird als Wasserzeichen in einem Steuerelement oder unterhalb des Steuerelements angezeigt. Richtige Formatierung mit dem entsprechenden VSColors\-Token angewendet `Environment.GrayText`.  
  
 Sie können in eine Reihe von Formularen angezeigt.  
  
-   Anstelle der Steuerelement\-Bezeichnung:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601\-f\_HintText1")  
  
-   Mit einem Verb, erläutert:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601\-g\_HintText2")  
  
-   Mit Text, der angibt, einer erforderlichen Eingabe:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601\-h\_HintText3")  
  
#### Wasserzeichentext  
 Auf eine leere Entwurfsoberfläche was Sie tun sowie Links, um die zugehörigen Windows, öffnen Sie gegebenenfalls in den Text angeben:  
  
 ![Watermark text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601\-i\_WatermarkText")  
  
 **Beispiel für Wasserzeichentext in Visual Studio**  
  
### Allgemeine Terminologie  
  
|Begriff|Erklärung|Kommentar|  
|-------------|---------------|---------------|  
|Anmelden \/ Abmelden|Verben, die mit dem Web synonym verwendet wird, für die Authentifizierung in einer Web\-Eigenschaft darstellt. Clients verwenden wir dies einmal als eine Art der obersten Ebene für das Signieren und IDE Verbindung, die eine Identität der obersten Ebene, die bietet Funktionen darstellt wie roaming und Lizenzierung auf höherer Ebene nicht mit allen anderen Verbindungen verfügbar sind.|Der IDE\-Benutzer ist das einzige Feature, das eine Anmeldung darstellen \/ Abmelden Verb verwendet wird, sollte, wie den obersten Ebene IDE\-Benutzer dar.|  
|Verbindung herstellen \/ trennen|Verwenden Sie in stellen eine Funktion eine einzelne Verbindung zu einem online\-Dienst verwaltet.|Server\-Explorer, wenn Sie nur eine aktive Azure\-Verbindung zu einem Zeitpunkt verfügen können, ist ein Beispiel für die Verbindung herstellen\/trennen.|  
|Hinzufügen \/ Entfernen|Nichtdestruktive. Verwenden Sie beim Hinzufügen oder entfernen etwas aus einer Liste.|Dialogfeld mit der TFS\-Verbindungs\-Manager\-Server ist ein Beispiel für das hinzufügen\/entfernen.|  
|Löschen|Destruktive. Verwenden Sie nur, wenn das Element entfernt werden dauerhaft verworfen oder vom Datenträger gelöscht.|"Löschen" ist eine Aufforderung im Allgemeinen erforderlich, wenn das Ergebnis eine Datei von der Festplatte gelöscht wird.|  
  
## Fehlermeldungen  
  
### Übersicht  
 Fehler auftreten. Festlegen von Einschränkungen für die Schritte des Benutzers ist ein sinnvoller erster Schritt verhindert vermeidbare Fehlermeldungen. Wenn ein Fehler auftritt, kann eine gut geschriebene Fehlermeldung entscheidend verringern das Problem wechseln. Fehlermeldungen sind wohl eines der wichtigsten Typen der Benachrichtigung, die dem Benutzer angezeigt wird, da sie synchron sind und ein Problem, das gelöst werden muss. Schlecht geschriebenen Fehlermeldungen haben Benutzer auf ihre eigenen entscheiden, die Ursache der Fehler und alle möglichen Lösungen.  
  
 Benutzer möglicherweise beenden, achten Sie auf übermäßig beansprucht oder verwirrenden Fehlermeldungen, damit schreiben nur erforderlich, Nachrichten, die dem Benutzer Mehrwert auftreten. Wenn die Nachricht einfach eine Benachrichtigung ist, verwenden Sie eine alternative Darstellung.  
  
### Regeln für das Erstellen einer Fehlermeldung  
  
-   Wenn Sie Fehlermeldungen zu erstellen, wählen Sie die entsprechende Fehlermeldung für die Zielgruppe. Testziel einfach zusammengefasst, die eine Aktion, die der Benutzer ausführen kann, die Geben Sie bei Bedarf. Status ist nicht alle Elemente, die der Benutzer nicht bekannt sein muss.  
  
-   Unterstützen Sie faktisch. Es ist einfacher zu lesen und darauf reagiert eine Fehlermeldung, die Anweisung enthält.  
  
-   Verwenden Sie keine doppelten negative.  
  
-   Führen Sie eine automatisierte, und eine manuelle Grammatik überprüfen auf eine beliebige Fehlermeldung, die Sie schreiben.  
  
-   Vermeiden Sie bei komplexen Fehlermeldungen sequenzielle Kommunikation. Verwenden Sie niemals ein F1\-Einbindung für die Fehlermeldung. Die Nachricht selbst sollte ausreichen.  
  
-   Verwenden Sie das richtige Symbol.  
  
-   Stellen Sie Fragen einfach zu verstehen und verwenden die Schaltflächen, clear Optionen, wie beispielsweise "Löschen" und "Abbrechen".  
  
-   Werden Sie für Warnungen zur zur Folge, dass Sie den Vorgang fortsetzen. Die Schaltflächen sollten zur Folge, dass angeben.  
  
-   Beschrieben Sie für Fehler, was der Benutzer tun kann, um das Problem zu beheben. Schaltflächen müssen Aktionen oder sagen Sie "Schließen". Verwenden Sie für eine Fehlermeldung einer Schaltfläche "OK".  
  
-   Einige Fragen sich selbst beim Erstellen einer Fehlermeldung angezeigt:  
  
    -   Kann der Benutzer zur Lösung des Problems mit diesem Fehler allein herausfinden, wie?  
  
    -   Verwendet der Benutzer das gleiche Vokabular wie dieser Fehler?  
  
    -   Ist dieser Fehler mehrdeutig oder in mehreren Situationen freigegeben? In diesem Fall erhalten wie Benutzer die Lösung, die sie benötigen?  
  
#### Buildfehler  
 Da Visual Studio ein Software\-Entwicklungstool ist, verfügen viele Komponenten eine Kompilierung konvertieren, oder codieren Sie Schritt, um die Arbeit des Entwicklers in binärer Form zu konvertieren. Diese Konvertierungen können Fehler verursachen, wenn der Compiler nicht ordnungsgemäß erstellte Dateien nicht verarbeiten kann oder wenn Compileroptionen ordnungsgemäß festgelegt wurden nicht.  
  
 Visual Studio\-Benutzer können eine enorme Anzahl von Entwicklung Stunden Beheben von Buildfehlern verbringen. Diesmal Auflösung erhöht, wenn Fehler vorliegen, Abhängigkeiten oder wenn Fehlermeldungen schlecht geschrieben werden die kann die Quelle des Fehlers aufdecken erschweren.  
  
 Die beste Buildfehler sind diejenigen, die auftreten, nicht in der ersten Stelle, weshalb Visual Studio bietet AutoVervollständigen und IntelliSense Wellenlinien. Validierungssteuerelemente werden Schemas und ähnliche Tools bieten die gleiche Art von Feedback. Diese Mechanismen führen proaktiv den Benutzer zum Erstellen von wohlgeformte Code, verringern die Wahrscheinlichkeit von Buildfehlern.  
  
 Visual Studio bietet ein Toolfenster können Benutzer lesen und navigieren Sie durch die Fehler, die in ihren Dokumentfenster aufgetreten. Tastenkombinationen werden bereitgestellt, sodass die Benutzer kann schnell große Mengen von Code navigieren und direkt auf den Speicherort des Problems. Visual Studio können auch jede Buildfehler, die an ein bestimmtes Schlüsselwort\/Hilfekontext\-ID gebunden werden, sodass der Benutzer direkt zu einem Hilfethema wechseln kann, die ausführlichere Informationen über den Fehler zu erhalten.  
  
 Schreiben Sie klare und prägnante Buildfehler:  
  
-   **Verwenden von einfachen** die das Problem mit wenigen oder gar keinen Compiler\-Jargon erläutert. Der Text, der ein Buildfehler darf nicht zu technischen sein.  
  
-   **Beschreiben Sie mögliche Ursachen.** Z. B. "Fehlender Doppelpunkt zwischen Eigenschaft und Wert in der ' \(Eigenschaft\): \(Wert\)' Deklaration."  
  
-   Geben Sie Details über potenzielle Fehlerbehebungen an. Wenn nicht genügend Platz vorhanden ist, können zusätzliche Details in das entsprechende Hilfethema gebracht.  
  
### Komponenten einer gut geschriebene Fehlermeldung  
  
#### Verwenden des Shell Dialogfeld\-Diensts Fehlermeldungen vorliegen.  
 Mit der Shell Dialogfeld\-Dienst können Sie die Darstellung der Nachricht zu steuern – insbesondere Schriftarten – ohne wesentliche Änderungen auf einzelne Elemente. Verwenden der **IErrorInfo** Mechanismen und mit **IVsUIShell::SetErrorInfo\/ReportErrorInfo**.  
  
#### Wählen Sie eine effektive und entsprechende Benachrichtigung Präsentation.  
 Verwenden Sie ein modales Dialogfeld mit eine kritische Warnung, wenn sofortige Maßnahmen zum Vermeiden von Datenverlust \(synchrone Benachrichtigung\) erforderlich ist. Wichtige Symbole sind für Situationen reserviert der Schließen\-Nachricht ohne lesen sie negative Auswirkungen führen kann. Datenverlust ist einer kritischen Situation, die eine Antwort Alarm\-Ebene erforderlich sind. Das Symbol "Kritisch" übermäßige desensitizes Benutzern, ihre Bedeutung. Wenn die Fehlermeldung lediglich informativ, sollten Sie alternativen für ein modales Dialogfeld \(asynchrone Benachrichtigung\).  
  
#### Geben Sie eine saubere, kurze Erläuterung der Ursache des Problems anstatt eine Erklärung.  
 Benutzer mit technischen Details in der Erläuterung überlasten machen sie eher Fehlermeldungen ignorieren. Beispiele für gute messaging:  
  
-   "Kann nicht zum Öffnen der angeforderten Datei."  
  
-   "Keine Verbindung mit dem Internet."  
  
#### Geben Sie Informationen dazu, wie Sie das Problem beheben.  
 Bieten Sie die Benutzer Vorschläge zum Beheben des Problems. Werden Sie ehrlich gesagt, mit dem Benutzer, befinden sich keine Vorschläge. Geben Sie direkte Links zu weiteren Informationsquellen online, z. B. communitysupport und technischen Support. Versuchen Sie, zeigen Sie Benutzer auf bestimmte online\-Informationen für das Problem relevant sind. Berücksichtigen Sie für eine Fehler\-ID Verknüpfen von Benutzern mit einer Diskussion über diesen bestimmten Fehler. Beispiele für gute messaging:  
  
-   "Stellen Sie sicher, dass Sie mit dem Internet verbunden sind, und wiederholen Sie diesen Vorgang."  
  
-   "Stellen Sie sicher, dass die Datei vorhanden ist und Sie die Berechtigung, um ihn zu öffnen."  
  
#### Schreiben Sie eine Nachricht, die kurz und bündig ist.  
 Eine Fehlermeldung kann benachrichtigt, erläutern, und bieten eine Lösung jedoch weiterhin ignoriert werden, wenn es zu umfangreich ist. Eine Lösung ist die Verwendung von schrittweise Anzeige von mit einer detailschaltfläche. Geben Sie z. B. eine kurze Beschreibung\/Lösung, und setzen Sie dann weitere Informationen unter eine Schaltfläche "Details". Wenn Benutzer auswählen, um weitere Informationen zu diesem Fehler erhalten, können sie dies tun.  
  
 Die Sprache in der Nachricht sollte sein:  
  
-   **Domäne geeignet.** Verwenden Sie die Sprache, die der Benutzer zu informieren. Obwohl Kunden Entwickler sind, haben nicht sie häufig den Kontext und die Terminologie, die wir.  
  
-   **Bestimmte.** Vermeiden Sie unklare Wortwahl, und geben Sie Namen und Speicherorte der beteiligten Objekte. Z. B. "Zeichen ist ungültig" ist eine Fehlermeldung z. B. nicht hilfreich. Welches Zeichen? "Datei nicht gefunden." Welche Datei?  
  
-   **Höflich.** Keine Arbeit des Benutzers, oder dass sie die dumm. Vermeiden Sie feindlichen oder anstößiger Sprache \(kill, ausführen, beenden, schwerwiegender, nicht zulässig\). Vermeiden Sie Großbuchstaben, die häufig als Shouting und nicht als lesbar. Verwenden Sie keine Humor.  
  
-   **Korrigieren.** Verwenden Sie die richtige Rechtschreibung und Grammatik \(auch im premultiplied\). Tippfehler sind unprofessionell und peinliche.  
  
-   **Angemessen.** Verwenden Sie die entsprechende Schaltflächentext. Vermeiden Sie die Schaltfläche "OK", und verwenden Sie stattdessen "Continue" oder "Yes\/No"  
  
### Beispiele für Fehler  
  
|Gut|Ungültige|  
|---------|---------------|  
|"Der Ihnen Rufnummer ist nicht mehr im Dienst. Bitte überprüfen Sie die Anzahl und wählen Sie erneut, oder wählen Sie 0 für den Operator."|-   "Fehler \(449\): Ungültige Anzahl"<br />-   "Dieser Fehler nicht behandelte Ausnahme gibt an, dass der Vorgang erfolgreich abgeschlossen."<br /><br /> ![Bad error message in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602\-a\_ErrorDialog")|  
  
## Zugreifen auf die Hilfe  
  
### Übersicht  
 Neben der Dokumentation in MSDN hat ein Visual Studio\-Benutzer mehrere Zugriffspunkte, um den Benutzer in der Benutzeroberfläche unterstützen. Um sicherzustellen, dass diese Zugriffspunkte ständig verfügbar sind, müssen die Feature\-Teams Nutzen der Hilfe von der Umgebung bereitgestellt. Diese Zugriffspunkte sind:  
  
-   **Anweisungstext und zusätzlichen Text in Dialogfeldern.** Statischer Text, der Richtung oder eine Erläuterung, entweder auf der Benutzeroberfläche Fläche oder zeigen Sie auf ein Symbol Infotipp verfügbar zu erhalten.  
  
-   **F1\-Hilfe** \(nur\-Editor\). Innerhalb der Visual Studio\-Editor kann ein Benutzer vertrauen, dass jederzeit durch Drücken von F1 ein Hilfethema für die aktuelle Auswahl angezeigt wird. Sicherstellen Sie, dass Themen über F1 entsprechende und informativ.  
  
-   **Links zu Hilfethemen.** Ein Hyperlink in ein Dialogfeld, ein Toolfenster oder Entwurfsoberfläche, die ein Thema, um den Benutzer zu unterstützen, mehr über eine Technologie, Funktion oder Informationen zum Ausführen eines Tasks startet.  
  
-   **Hilfsprogramm\-UI Mechanismen, wie Smarttags und Erstellen von Dialogfeldern.** Diese Mechanismen unterstützen den Benutzer ein Element der Benutzeroberfläche verstehen oder eine Aufgabe, z. B. Smarttags oder Builder Dialoge erleichtern.  
  
-   **Hilfe zur Benutzeroberfläche Schaltflächen** \(veraltet\). Ein sichtbaren Indikator in der Titelleiste, die auf das verwandte Thema F1\-Hilfe zugreifen kann.  
  
### Text  
  
#### Anweisungstext und zusätzlichen Text in Dialogfeldern  
 In Dialogfeldern, die komplexe Aufgaben unterstützen, möglicherweise zu Hinweistext innerhalb der Benutzeroberfläche oft die oben im Dialogfeld oder in der Nähe komplexe Steuerelemente gibt. Finden Sie unter [Benutzeroberflächen-Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) ausführliche Informationen zum Schreiben von.  
  
#### Infotipps  
 Häufig Hinweistext möglicherweise so umfangreich, dass Sie direkt in der Benutzeroberfläche positionieren oder kann nur für neue Benutzer, wie Überfrachtung erfahrenen Benutzern hilfreich sein. In diesem Fall sollte der Anweisungstext\/Informationstext als QuickInfo in einem Infotipp platziert werden.  
  
 Infotipps sollte in der Nähe von den Steuerelementen, die sie beziehen sich auf und verwende das bestimmte Infotipp\-Symbol, das unauffällig noch nicht bemerkbar platziert werden.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Beispiel für einen Infotipp in Visual Studio**  
  
### Interaktive Hilfemechanismen  
  
#### F1\-Hilfe  
 F1\-Hilfe ist erforderlich, in den Editor oder in der Entwurfsoberfläche, aber nicht an anderer Stelle in der Visual Studio\-Umgebung.  
  
#### Links zu Hilfethemen  
 Hyperlinks können verwendet werden, um eine Aktion auszuführen, Navigieren in der IDE oder Hilfe in einem Browser laden. Finden Sie unter [Benutzeroberflächen-Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) Weitere Informationen zu Sprache und 07.10.01 Schaltflächen und Hyperlinks Visual und Layout\-Richtlinien.  
  
#### Hilfe \[?\] Schaltflächen im Dialogfeld Titelleisten \(veraltet\)  
 Zum größten Teil sind die Schaltflächen Hilfe \[?\] in der Titelleiste des Dialogs veraltet. UI\-Themen sind nicht mehr Teil unserer Doc\-Modells, und daher möglicherweise kein relevantes Thema zu verknüpfen. Im Wesentlichen die Titelleistenschaltfläche war das gleiche wie die F1\-Hilfe und in Dialogfeldern nicht mehr erforderlich ist. In einigen Fällen kann dies immer noch verwendet werden als ein Indikator, dass konzeptionelle oder prozeduraler Informationen verfügbar, obwohl Hyperlinks in neueren Benutzeroberfläche häufig verwendet werden.  
  
##### Dialoge, die über die Umgebung erstellt  
 Viele Shelldialogfelder werden erstellt, durch die **VBDialogBoxParam** Funktion. Diese freigegebene Funktion wurde aktualisiert, um Unterstützung bei der Umstellung der **Hilfe** im Dialogfeld, um die Schaltfläche der **?** Schaltfläche Beibehaltung einer Architektur, die Abwärtskompatibilität kompatibel und erweiterbar.  
  
 Insbesondere die **VBDialogBoxParam** Funktion untersucht die Dialogfeldvorlage für eine Schaltfläche mit der ID **IDHELP** \(9\) oder ein Etikett **Hilfe** oder **& Hilfe**. Wenn eine Schaltfläche "Hilfe" gefunden wird, wird es ausgeblendet und die **WS\_EX\_CONTEXTHELP** Format wird hinzugefügt, um das Dialogfeld, in dem platziert die **?** Schaltfläche in der Titelleiste des Dialogfelds.  
  
 Wenn das Dialogfeld erstellt wird, legt das Dialogfeld Proc auf einen Stapel und ruft das Dialogfeld mit dem eine vorverarbeitet Dialogfeldprozedur mit dem Namen **DialogPreProc**. Wenn die **?** Schaltfläche geklickt wird, sendet er eine **WM\_SYSCOMMAND** von **SC\_CONTEXTHELP** zum Dialogfeld. Die **DialogPreProc** dieser Befehl erfasst und ändert die zu einer **WM\_HELP** \-Nachricht, die an die ursprüngliche Dialogfeld Prozedur übergeben wird  
  
 Die meisten Dialogfelder der Umgebung erstellt haben eine Hilfeschaltfläche im Dialogfeld. Wenn das Dialogfeld angezeigt wird, ist die Schaltfläche Hilfe automatisch ausgeblendet und nur die **?** Schaltfläche funktioniert. Wenn die **?** Schaltfläche jemals entfernt oder in Windows geändert wird, wird dieser Lösung können Sie schnell wieder auf den ursprünglichen Hilfe\-Schaltflächen verschieben.  
  
 Diese Lösung enthält vier Annahmen, die Fehler verursachen:  
  
-   Schaltfläche "Hilfe" im Dialogfeld ist **IDHELP** \(9\).  
  
-   Das Dialogfeld sieht richtig, wenn die Hilfeschaltfläche ausgeblendet ist.  
  
-   Das Dialogfeld wird nicht seine Winproc ersetzen.  
  
-   Das Dialogfeld wird nicht in ein anderes Dialogfeld eingebettet.  
  
 Wenn Ihr Dialogfeld befindet sich im Msenv und nicht **VBDialogBoxParam**, untersuchen Sie die Nutzung von **VBDialogBoxParam** vor der Implementierung Ihrer eigenen Handlers.  
  
##### Dialoge, die durch andere Pakete erstellt  
 Sie können Ihre eigene Lösung für Dialogfelder implementieren, die sich außerhalb der Msenv befinden. Erwägen Sie für eine freigegebene Dialogfeldklasse in Ihr VSPackage verschieben die Schaltfläche in der Titelleiste oder implementieren einen Handler für jedes Dialogfeld. Der folgende Code ist ein Gerüst für eine Implementierung, die Ihnen beim Einstieg helfen:  
  
```  
struct DLGPROCITEM { FARPROC proc; // The info used to create the dialog. DLGPROCITEM* procPrev; }; DLGPROCITEM* g_dlgProcStack = NULL; // A dialog starter/wrapper function is used to push the new // dialog proc to the top of our dialog proc stack. int SomeDialogStarterFunction(hinst, id, proc, etc) { if (g_dlgProcStack == NULL) { g_dlgProcStack = new DLGPROCITEM; g_dlgProcStack->procPrev = NULL; } else { DLGPROCITEM* procItem = new DLGPROCITEM; g_dlgProcStack->procPrev = g_dlgProcStack; g_dlgProcStack = procItem; } } // Pop this dialog proc off the dialog proc stack. DialogBoxIndirectParam...(...) { DLGPROCITEM* procItem = g_dlgProcStack->procPrev; delete g_dlgProcStack; g_dlgProcStack = procItem; } // A wrapper dialog procedure will allow us to capture the // SC_CONTEXTHELP button on the title bar from Windows and // forward it as a simple WM_HELP message back to the dialog. INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg, WPARAM wParam, LPARAM lParam) { if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP) { uMsg = WM_HELP; wParam = 0; lParam = 0; } return CallWindowProc((WNDPROC)g_dlgProcStack->proc, hwndDlg, uMsg, wParam, lParam); }  
```  
  
##### Hilfe\-Schaltflächen in verwaltetem code  
 Überschreiben von Standardverhalten der Fenster Hilfe Titelleistenschaltfläche des ist einfach in verwaltetem Code. Es folgt eine vollständige demoanwendung, die dieses Verhalten veranschaulicht wird. Im Wesentlichen müssen Sie des Formulars überschreiben **WndProc** \-Methode und anschließend Fire deaktiviert F1\-Hilfe angefordert wird bei einer **SC\_CONTEXTHELP** Nachricht abgefangen wird.  
  
```  
using System; using System.Windows.Forms; public class HelpForm : Form { private const int SC_CONTEXTHELP = 0xF180; private const int WM_SYSCOMMAND = 0x0112; public HelpForm() { this.ClientSize = new System.Drawing.Size(300, 250); this.HelpButton = true; this.MaximizeBox = false; this.MinimizeBox = false; this.Name = "HelpForm"; this.Text = "Help Form"; } protected override void WndProc(ref Message m) { if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam) ShowHelp(); else base.WndProc(ref m); } private void ShowHelp() { MessageBox.Show("F1 Help goes here."); } [STAThread] static void Main() { Application.EnableVisualStyles(); Application.EnableRTLMirroring(); Application.Run(new HelpForm()); } }  
```  
  
## Siehe auch  
 [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)