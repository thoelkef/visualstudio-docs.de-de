---
title: Benachrichtigungen und Fortschritt für Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699883"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Benachrichtigungen und Fortschritt für Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Benachrichtigungssysteme

### <a name="overview"></a>Übersicht
 Es gibt mehrere Möglichkeiten, den Benutzer über die Vorgänge in Visual Studio in Bezug auf seine Softwareentwicklungsaufgaben zu informieren.

 Bei der Implementierung einer Benachrichtigung:

- **Halten Sie die Anzahl der Benachrichtigungen auf die effektive Mindestanzahl.** Benachrichtigungen sollten für die Mehrheit der Visual Studio-Benutzer oder für Benutzer eines bestimmten Feature-/Featurebereichs gelten. Eine übermäßige Verwendung von Benachrichtigungen kann den Benutzer ins Abseits stellen oder die wahrgenommene Benutzerfreundlichkeit des Systems verringern.

- **Stellen Sie sicher, dass Sie klare, umsetzbare Nachrichten präsentieren,** die der Benutzer verwenden kann, um den entsprechenden Kontext aufzurufen, um komplexere Entscheidungen zu treffen und weitere Maßnahmen zu ergreifen.

- **Präsentieren Sie synchrone und asynchrone Nachrichten entsprechend.** Synchrone Benachrichtigungen weisen darauf hin, dass etwas sofort beachtet werden muss, z. B. wenn ein Webdienst abstürzt oder eine Codeausnahme ausgelöst wird. Der Benutzer sollte sofort über diese Situationen in einer Weise informiert werden, die ihre Eingabe erfordert, z. B. in einem modalen Dialogfeld. Asynchrone Benachrichtigungen sind solche, die der Benutzer kennen sollte, aber nicht sofort reagieren muss, z. B. wenn ein Buildvorgang abgeschlossen oder eine Websitebereitstellung abgeschlossen ist. Diese Meldungen sollten mehr Umgebung sein und den Aufgabenfluss des Benutzers nicht unterbrechen.

- **Verwenden Sie modale Dialogfelder nur, wenn dies erforderlich ist, um zu verhindern, dass der Benutzer weitere Maßnahmen ergreift,** bevor er die Nachricht bestätigt oder eine im Dialogfeld dargestellte Entscheidung trifft.

- **Entfernen Sie Umgebungsbenachrichtigungen, wenn sie nicht mehr gültig sind.** Erfordern Sie nicht, dass der Benutzer eine Benachrichtigung absagt, wenn er bereits Maßnahmen ergriffen hat, um das Problem zu beheben, über das er benachrichtigt wurde.

- **Beachten Sie, dass Benachrichtigungen zu falschen Korrelationen führen können.** Benutzer könnten glauben, dass eine oder mehrere ihrer Aktionen eine Benachrichtigung ausgelöst haben, wenn es tatsächlich keinen kausalen Zusammenhang gab. Beachten Sie in der Benachrichtigung über den Kontext, den Trigger und die Quelle der Benachrichtigung.

### <a name="choosing-the-right-method"></a>Die Wahl der richtigen Methode
 Verwenden Sie diese Tabelle, um Sie bei der Auswahl der richtigen Methode zum Benachrichtigen des Benutzers über Ihre Nachricht zu unterstützen.

|Methode|Zweck|Nicht verwenden|
|------------|---------|----------------|
|[Modale Fehlermeldungsdialogfelder](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Verwenden Sie diese Datei, wenn eine Benutzerantwort erforderlich ist, bevor Sie fortfahren.|Nicht verwenden, wenn der Benutzer nicht blockiert und deren Fluss unterbrochen werden muss. Vermeiden Sie die Verwendung von modalen Dialogfeldern, wenn es möglich ist, die Nachricht auf eine andere, weniger aufdringliche Weise anzuzeigen.|
|[IDE-Statusleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Verwenden Sie diese Verwendung, wenn Umgebungstextinformationen zum Status eines Prozesses vorhanden sind.|Nicht allein verwenden. Am besten in Verbindung mit einem anderen Feedback-Mechanismus verwendet.|
|[Eingebettete Infoleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In einem Werkzeugfenster oder Dokumentfenster können Sie über Denprogress, Fehlerstatus, Ergebnisse und/oder umsetzbare Informationen benachrichtigen.|Nicht verwenden, wenn die Informationen für den Speicherort, an dem die Infoleiste platziert ist, nicht relevant sind.<br /><br /> Verwenden Sie es nicht außerhalb eines Dokument-/Werkzeugfensters.|
|[Mauszeiger änderungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Kann verwendet werden, um zu benachrichtigen, dass ein Prozess im Gange ist. Wird auch verwendet, um zu benachrichtigen, dass es eine Zustandsänderung in der Maus gibt, z. B. wenn das Ziehen/Absetzen ausgeführt wird oder dass sich der Mauszeiger in einem bestimmten Modus befindet, z. B. im Zeichnungsmodus.|Verwenden Sie nicht für kurze Fortschrittsänderungen oder wenn das Flattern des Cursors wahrscheinlich ist (z. B. wenn sie an Teile eines länger laufenden Prozesses gebunden sind und nicht an den gesamten Prozess).|
|[Fortschrittsindikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Verwenden Sie diese Verwendung, wenn Sie den Fortschritt melden müssen (entweder bestimmt oder unbestimmt). Es gibt eine Vielzahl von Fortschrittsindikatortypen und spezifische Verwendung für jeden. Siehe [Fortschrittsindikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Visual Studio-Benachrichtigunsfenster](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Das Benachrichtigungsfenster ist nicht öffentlich erweiterbar. Es wird jedoch verwendet, um eine Reihe von Nachrichten über Visual Studio zu kommunizieren, einschließlich kritischer Probleme mit Ihrer Lizenz und Informationsbenachrichtigungen über Updates für Visual Studio oder Pakete.|Nicht für andere Arten von Benachrichtigungen verwenden.|
|[Fehlerliste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Wenn das Problem direkt mit der derzeit offenen Lösung des Benutzers zusammenhängt, die ein Problem aufweist (Fehler/Warnung/Info), müssen sie möglicherweise Maßnahmen für den Code ergreifen.<br /><br /> Dazu gehören z. B.:<br /><br /> - Compilermeldungen (Fehler/Warnung/Info)<br /><br /> - Code Analyzer/Diagnosemeldungen zum Code<br /><br /> - Erstellen von Nachrichten<br /><br /> Kann für Probleme im Zusammenhang mit dem Projekt oder den Projektmappendateien geeignet sein, aber beachten Sie zuerst eine Projektmappen-Explorer-Angabe.|Verwenden Sie sie nicht für Elemente, die keine Beziehung zum offenen Lösungscode des Benutzers haben.|
|Editor-Benachrichtigungen: Glühbirne|Verwenden Sie diese Datei, wenn Sie über eine Korrektur verfügen, um ein in der geöffneten Datei vorhandenes Problem zu beheben.<br /><br /> Beachten Sie, dass die Glühbirne auch zum Hosten von Schnellaktionen verwendet werden sollte, die bei Bedarf für den Code des Benutzers ausgeführt werden, z. B. Umgestaltungen, in diesem Fall jedoch nicht als "Benachrichtigungsstil" angezeigt wird.|Verwenden Sie sie nicht für Elemente, die keine Beziehung zur geöffneten Datei haben.|
|Editor-Benachrichtigungen: Squiggles|Verwenden Sie diese Option, um den Benutzer auf ein Problem mit einer bestimmten Spanne des offenen Codes (z. B. eine rote Wellenlinie für Fehler) aufmerksam zu machen.|Nicht für Elemente verwenden, die sich nicht auf eine bestimmte Spanne ihres offenen Codes beziehen.|
|[Eingebettete Statusleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Hiermit können Sie den Status für Inhalte oder Prozesse im Kontext eines bestimmten Werkzeugfensters, Dokumentfensters oder Dialogfelds angeben.|Verwenden Sie sie nicht für allgemeine Produktbenachrichtigungen, -prozesse oder Artikel, die in keinem Zusammenhang mit dem Inhalt innerhalb des jeweiligen Fensters stehen.|
|[Windows-Fachbenachrichtigungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Verwenden Sie diese Verwendung, um Benachrichtigungen für Out-of-Proc-Prozesse oder Begleitanwendungen anzudecken.|Nicht für Benachrichtigungen verwenden, die für die IDE relevant sind.|
|[Benachrichtigungsblasen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Verwenden Sie diese Datei, um einen Remoteprozess oder eine Änderung **außerhalb** der IDE zu benachrichtigen.|Verwenden Sie dies nicht als Mittel, um den Benutzer über Prozesse **innerhalb** der IDE zu benachrichtigen.|

### <a name="notification-methods"></a>Benachrichtigungsmethoden

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Modale Fehlermeldungsdialogfelder
 Ein Modal-Fehlermeldungsdialogfeld wird verwendet, um eine Fehlermeldung anzuzeigen, die die Bestätigung oder Aktion des Benutzers erfordert.

 ![Modale Fehlermeldung](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Ein Dialogfeld für eine modale Fehlermeldung, in der der Benutzer einer ungültigen Verbindungszeichenfolge für eine Datenbank gewarnt wird.**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE-Statusleiste
 Die Wahrscheinlichkeit, dass Benutzer Statusleistentext bemerken, korreliert mit ihrer Allround-Computererfahrung und spezifischen Erfahrung mit der Windows-Plattform. Der Visual Studio-Kundenstamm ist in beiden Bereichen in der Regel erfahren, obwohl selbst sachkundige Windows-Benutzer Änderungen in der Statusleiste möglicherweise vermissen. Daher wird die Statusleiste am besten für Informationszwecke oder als redundanter Hinweis für Informationen verwendet, die an anderer Stelle dargestellt werden. Alle wichtigen Informationen, die der Benutzer sofort auflösen muss, sollten in einem Dialogfeld oder im Toolfenster Benachrichtigungen bereitgestellt werden.

 Die Visual Studio-Statusleiste ist so konzipiert, dass verschiedene Arten von Informationen angezeigt werden können. Es ist in Regionen für Feedback, Designer, Fortschrittsleiste, Animation und Client unterteilt.

 Die Feedback-Region und die Designerregion sind immer sichtbar. Die Fortschrittsleiste und Animationsbereiche sind immer dynamisch und basieren auf dem Benutzerkontext. Der Designerbereich verfügt über eine statische Breite, die durch die Länge der Zeichenfolge bestimmt wird, die aus einer begleitenden Ressource für die Textnachricht gezogen wird. Dadurch kann die Lokalisierung die Größe der Breite ändern, ohne dass eine Codeänderung erforderlich ist. Für Englisch beträgt die Breite dieser Zeichenfolge etwa 220 Pixel. Die Designerregion verhält sich normal, und der Feedback-Bereich absorbiert den verbleibenden Platz.

 Die Statusleiste ist auch koloriert, um visuelles Interesse und funktionalen Wert hinzuzufügen, indem verschiedene IDE-Statusänderungen kommuniziert werden, z. B. wenn sich die IDE im Debugmodus befindet.

 ![Farbänderungen für IDE-Statusleiste](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **IDE-Statusleistenfarben**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Eingebettete Infoleiste
 Eine Infoleiste kann oben in einem Dokumentfenster oder Toolfenster verwendet werden, um den Benutzer über einen Zustand oder eine Bedingung zu informieren. Es kann auch Befehle anbieten, so dass der Benutzer eine Möglichkeit haben kann, einfach Maßnahmen zu ergreifen. Die Infoleiste ist ein Standard-Shell-Steuerelement. Vermeiden Sie es, eigene zu erstellen, die sich mit anderen in der IDE nicht inkonsistent verhalten und angezeigt wird. Informationen zu Implementierungsdetails und Anwendungsanleitungen finden Sie in [infobars.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)

 ![Eingebettete Infoleiste](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Eine infobar, die in ein Dokumentfenster eingebettet ist und den Benutzer darauf aufmerksam macht, dass sich die IDE im historischen Debugmodus befindet und der Editor nicht auf die gleiche Weise reagiert wie im Standard-Debugmodus.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Mauszeiger änderungen
 Verwenden Sie beim Ändern des Mauszeigers Farben, die an den VSColor-Dienst gebunden sind und dem Cursor bereits zugeordnet sind. Cursoränderungen können verwendet werden, um einen fortlaufenden Vorgang anzuzeigen, sowie auf Trefferzonen, in denen der Benutzer den Mauszeiger über ein Ziel zeigt, das gezogen, auf ein Objekt abgelegt oder zum Auswählen eines Objekts verwendet werden kann.

 Verwenden Sie den Mauszeiger "Beschäftigt/warten" nur, wenn die gesamte verfügbare CPU-Zeit für einen Vorgang reserviert werden muss, wodurch der Benutzer daran gehindert wird, weitere Eingaben auszudrücken. In den meisten Fällen bei gut geschriebenen Anwendungen, die Multithreading verwenden, sollten Zeiten, in denen Benutzer daran gehindert werden, andere Vorgänge durchzuführen, selten sein.

 Beachten Sie, dass Cursoränderungen als redundanter Hinweis für Informationen nützlich sind, die an anderer Stelle dargestellt werden. Verlassen Sie sich nicht auf eine Cursoränderung als einzige Art der Kommunikation mit dem Benutzer, insbesondere wenn Sie versuchen, etwas zu vermitteln, das entscheidend ist, das der Benutzer adressieren muss.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Fortschrittsindikatoren
 Fortschrittsindikatoren sind wichtig, um dem Benutzer Feedback während Prozessen zu geben, die mehr als ein paar Sekunden dauern. Fortschrittsindikatoren können an Ort und Stelle (in der Nähe des Startpunkts der laufenden Aktion), in einer eingebetteten Statusleiste, in einem modalen Dialogfeld oder in der Visual Studio-Statusleiste angezeigt werden. Befolgen Sie die Leitlinien unter [Fortschrittsindikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) in Bezug auf deren Verwendung und Umsetzung.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio-Benachrichtigungsfenster
 Das Fenster Visual Studio Notifications benachrichtigt Entwickler über Lizenzierung, Umgebung (Visual Studio), Erweiterungen und Updates. Benutzer können einzelne Benachrichtigungen schließen oder bestimmte Arten von Benachrichtigungen ignorieren. Die Liste der ignorierten Benachrichtigungen wird auf der Seite **Tools > Options** verwaltet.

 Das Benachrichtigungsfenster ist derzeit nicht erweiterbar.

 ![Visual Studio-Benachrichtigunsfenster](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio Notifications-Toolfenster**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Fehlerliste
 Eine Benachrichtigung in der Fehlerliste weist auf Fehler und Warnungen hin, die während der Kompilierung und des Buildprozesses aufgetreten sind, und ermöglicht es dem Benutzer, im Code zu diesem bestimmten Codefehler zu navigieren.

 ![Fehlerliste](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Fehlerliste in Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Eingebettete Statusleisten
 Da die IDE-Statusleiste dynamisch ist, der Clientbereichskontext auf das aktive Dokumentfenster festgelegt ist und Informationen über den Kontext und/oder die Systemantworten des Benutzers aktualisiert werden, ist es schwierig, eine kontinuierliche Anzeige von Informationen aufrechtzuerhalten oder status für langfristige asynchrone Prozesse zu geben. Die IDE-Statusleiste eignet sich z. B. nicht für Benachrichtigungen über Testlaufergebnisse für mehrere Durchläufe und/oder sofort umsetzbare Elementauswahl. Es ist wichtig, solche Statusinformationen im Kontext des Dokuments oder Werkzeugfensters aufzubewahren, in dem der Benutzer eine Auswahl trifft oder einen Prozess startet.

 ![Eingebettete Statusleiste](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Eingebettete Statusleiste in Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows-Fachbenachrichtigungen
 Der Windows-Benachrichtigungsbereich befindet sich neben der Systemuhr auf der Windows-Taskleiste. Viele Dienstprogramme und Softwarekomponenten stellen Symbole in diesem Bereich bereit, sodass der Benutzer ein Kontextmenü für systemweite Aufgaben wie das Ändern der Bildschirmauflösung oder das Abrufen von Softwareupdates erhalten kann.

 Benachrichtigungen auf Umgebungsebene sollten im Visual Studio Notifications-Hub und nicht im Windows-Benachrichtigungsbereich angezeigt werden.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Benachrichtigungsblasen
 Benachrichtigungsblasen können als Information innerhalb eines Editors/Designers oder als Teil des Windows-Benachrichtigungsbereichs angezeigt werden. Der Benutzer nimmt diese Blasen als Probleme wahr, die er später lösen kann, was ein Vorteil für nicht kritische Benachrichtigungen ist. Blasen sind ungeeignet für wichtige Informationen, die der Benutzer sofort lösen muss. Wenn Sie Benachrichtigungsblasen in Visual Studio verwenden, befolgen Sie die [Windows Desktop-Anleitung für Benachrichtigungsblasen](/windows/desktop/uxguide/mess-notif).

 ![Benachrichtigungssprechblase](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Benachrichtigungsblase im Für Visual Studio verwendeten Windows-Benachrichtigungsbereich**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Fortschrittsindikatoren

### <a name="overview"></a>Übersicht
 Fortschrittsindikatoren sind ein wichtiger Bestandteil eines Benachrichtigungssystems, um dem Benutzer Feedback zu geben. Sie teilen dem Benutzer mit, wann Prozesse und Vorgänge abgeschlossen werden. Bekannte Indikatortypen umfassen Fortschrittsbalken, drehende Cursor und animierte Symbole. Die Art und Platzierung eines Fortschrittsindikators hängt vom Kontext ab, einschließlich der Berichte und der Dauer des Abschlusses des Prozesses oder Vorgangs.

#### <a name="factors"></a>Faktoren
 Um zu bestimmen, welcher Indikatortyp geeignet ist, müssen Sie die folgenden Faktoren bestimmen.

1. **Timing:** Dauer der Operation

2. **Modalität:** Ob der Vorgang für die Umgebung modal ist (sperrt die Benutzeroberfläche, bis der Prozess abgeschlossen ist)

3. **Persistent/Transient:** ob das Endergebnis des Fortschritts zu einem späteren Zeitpunkt gemeldet und/oder sichtbar sein muss

4. **Bestimmen/Unbestimmt:** ob die Betriebsendzeit und der Arbeitsfortschritt berechnet werden können

5. **Grafik/Textposition:** Ob der Fortschritt oder Prozess inline, im Nachrichtentext oder in einem bestimmten Steuerelement erfasst wird, z. B. das Baumsteuerelement

6. **Nähe:** Ob sich der Fortschritt in unmittelbarer Nähe zur Benutzeroberfläche befinden soll, mit der er zusammenhängt. (Kann es sich z. B. in der Statusleiste befinden, die möglicherweise weit entfernt ist, oder muss es sich in der Nähe der Schaltfläche befinden, die den Prozess gestartet hat?)

#### <a name="determinate-progress"></a>Bestimmung des Fortschritts

|Fortschrittstyp|Wann und wie zu verwenden|Notizen|
|-------------------|-------------------------|-----------|
|Fortschrittsbalken (bestimmt)|Erwartete Dauer von >5 Sekunden.<br /><br /> Kann eine textliche Beschreibung von Prozessdetails enthalten.|**DON'T** Text in Animation einbetten.|
|Infoleiste|Messaging, das der kontextbezogenen Benutzeroberfläche zugeordnet ist. Siehe [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Kann eine textliche Beschreibung von Prozessdetails enthalten.|**Verwenden** Sie nicht mehrere Infoleisten, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Fortschrittsbalken.|
|Ausgabefenster|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, dessen Details der Benutzer nach Abschluss **überprüfen** möchten.|**DON'T** verwenden, wenn der Benutzer später auf Daten verweisen muss.|
|Protokolldatei|Gepaart mit einer unnachgiebigen Benachrichtigung in Fällen, in denen es wichtig ist, Details nach Abschluss zu **speichern.**||
|Statusleiste|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, über den der Benutzer nach Abschluss keine Details **benötigt.**<br /><br /> Enthält eine eingebettete Fortschrittsleiste.<br /><br /> Kann eine textliche Beschreibung von Prozessdetails enthalten.||

#### <a name="indeterminate-progress"></a>Unbestimmter Fortschritt

|Fortschrittstyp|Wann und wie zu verwenden|Notizen|
|-------------------|-------------------------|-----------|
|Fortschrittsleiste (unbestimmt)|Erwartete Dauer von >5 Sekunden.<br /><br /> Kann eine textliche Beschreibung von Prozessdetails enthalten.|**DON'T** Text in Animation einbetten.|
|Ameisen (animierte horizontale Punkte)|Roundtrip zum Server.<br /><br /> In der Nähe des Kontexts über den übergeordneten Container platziert.|**DON'T** verwenden, wenn nicht von ganzen Container übergeordnet.|
|Spinner (Fortschrittsring)|Prozess, der der kontextbezogenen Benutzeroberfläche zugeordnet ist oder bei dem Leerzeichen berücksichtigt wird.<br /><br /> Kann eine textliche Beschreibung von Prozessdetails enthalten.||
|Infoleiste|Messaging, das der kontextbezogenen Benutzeroberfläche zugeordnet ist. Siehe [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Verwenden** Sie nicht mehrere Infoleisten, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Fortschrittsbalken.|
|Ausgabefenster|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, dessen Details der Benutzer nach Abschluss **überprüfen** soll.|**DON'T** für Informationen, die über Sitzungen hinweg beibehalten werden müssen.|
|Protokolldatei|Gepaart mit einer unnachgiebigen Benachrichtigung in Fällen, in denen es wichtig ist, Details nach Abschluss zu **speichern.**||
|Statusleiste|Vorübergehende Benachrichtigung: Prozess auf App-Ebene, über den der Benutzer nach Abschluss keine Details **benötigt.**<br /><br /> Enthält die eingebettete Fortschrittsleiste.<br /><br /> Kann eine textliche Beschreibung von Prozessdetails enthalten.||

### <a name="progress-indicator-types"></a>Fortschrittsindikatortypen

#### <a name="progress-bars"></a>Fortschrittsbalken

##### <a name="indeterminate"></a>Unbestimmten
 ![Unbestimmte Statusanzeige](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Unbestimmte Statusanzeige**

 "Unbestimmt" bedeutet, dass der Gesamtfortschritt eines Vorgangs oder Prozesses nicht bestimmt werden kann. Verwenden Sie unbestimmte Fortschrittsbalken für Vorgänge, die einen unbegrenzten Zeitraum erfordern oder auf eine unbekannte Anzahl von Objekten zugreifen. Verwenden Sie eine Textbeschreibung, um das Geschehen zu begleiten. Verwenden Sie Timeouts, um zeitbasierten Vorgängen Grenzen zu geben. Unbestimmte Fortschrittsbalken verwenden Animationen, um anzuzeigen, dass Fortschritte erzielt werden, geben jedoch keine anderen Informationen bereit. Wählen Sie keinen unbestimmten Fortschrittsbalken, der nur auf dem möglichen Mangel an Genauigkeit allein basiert.

##### <a name="determinate"></a>Determinate
 ![Festgelegte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Festgelegte Fortschrittsleiste**

 "Determinieren" bedeutet, dass ein Vorgang oder Prozess eine begrenzte Zeit erfordert, auch wenn diese Zeit nicht genau vorhergesagt werden kann. Deutlich auf Abschluss hinweisen. Lassen Sie einen Fortschrittsbalken nicht zu 100 Prozent gehen, es sei denn, der Vorgang wurde abgeschlossen. Die Animation der Fortschrittsleiste wird von 0 auf 100 % verschoben.

 Bewegen Sie die Fortschrittsanzeige während eines Vorgangs niemals rückwärts. Der Balken sollte sich stetig vorwärts bewegen, wenn der Betrieb beginnt, und 100% erreichen, wenn er endet. Der Punkt der Fortschrittsleiste besteht darin, dem Benutzer eine Vorstellung davon zu geben, wie lange der gesamte Vorgang dauert, unabhängig davon, wie viele Schritte erforderlich sind.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Gleichzeitige Berichterstattung (gestapelte Fortschrittsbalken)
 Wenn eine Operation eine lange Zeit - vielleicht mehrere Minuten - in Anspruch nehmen wird, kann zwei Fortschrittsbalken verwendet werden, einer, der den Gesamtfortschritt für eine Operation und einen anderen für die Progression des aktuellen Schritts anzeigt. Wenn z. B. ein Setupprogramm viele Dateien kopiert, kann eine Fortschrittsleiste verwendet werden, um anzugeben, wie lange der gesamte Prozess dauert, während ein zweiter Vorgang angeben kann, welcher Prozentsatz der aktuellen Datei oder des aktuellen Verzeichnisses kopiert wird. Melden Sie nicht mehr als fünf gleichzeitige Vorgänge oder Prozesse mit gestapelten Fortschrittsbalken. Wenn Sie mehr als fünf gleichzeitige Vorgänge oder Prozesse melden müssen, verwenden Sie ein modales Dialogfeld mit der Schaltfläche Abbrechen, und melden Sie die Fortschrittsdetails an das Ausgabefenster.

##### <a name="textual-descriptions"></a>Textbeschreibungen
 Verwenden Sie eine Textbeschreibung, um das Geschehen und die geschätzte Zeit bis zum Abschluss zu begleiten. Wenn es unmöglich ist, zu bestimmen, wie lange ein Vorgang dauern wird, dann kann eine bessere Wahl für Feedback ein animiertes Symbol und nicht eine Fortschrittsleiste sein.

 Visual Studio stellt eine Standardstatusleiste in der Statusleiste bereit, die von jedem in Visual Studio integrierten Produkt verwendet werden kann. Für Textbeschreibungen, was geschieht, während die Fortschrittsleiste animiert wird, kann der Statusleistentext aktualisiert werden.

#### <a name="other-progress-indicators"></a>Sonstige Fortschrittsindikatoren

##### <a name="ants-animated-horizontal-dots"></a>Ameisen (animierte horizontale Punkte)
 ![Ant-Elemente zum Fortschritt](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Ameisen", animierte horizontale Punkte, bieten eine visuelle Referenz für einen unbestimmten Roundtrip-Serverprozess.

##### <a name="spinner-progress-ring"></a>Spinner (Fortschrittsring)
 ![Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Der Spinner (auch als "Fortschrittsring" bezeichnet) ist ein unbestimmter Fortschrittsindikator, der hauptsächlich in Bezug auf die kontextbezogene Benutzeroberfläche verwendet wird. Zeigen Sie einen Spinner in unmittelbarer Nähe zu den zugehörigen Inhalten an, z. B. einen Textkategoriekopf, ein Messaging oder ein Steuerelement.

##### <a name="cursor-feedback"></a>Cursor-Feedback
 Geben Sie bei Vorgängen, die zwischen 2 und 7 Sekunden dauern, Cursor-Feedback. In der Regel bedeutet dies die Verwendung des vom Betriebssystem bereitgestellten Wartecursors. Eine Anleitung finden Sie im MSDN-Artikel [Cursors.Wait-Eigenschaft](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Statusindikatorpositionen

##### <a name="status-bar"></a>Statusleiste
 Die Statusleiste gibt Ihrer Anwendung einen Ort, an dem Sie dem Benutzer Nachrichten und nützliche Informationen anzeigen können, ohne die Arbeit des Benutzers zu unterbrechen. In der Regel am unteren Rand eines Fensters angezeigt, status for progress wird ein QuickInfo-Bereich sein, der eine Meldung über das Maß des Fortschritts in Kombination mit einem Fortschrittsbalkenindikator enthält.

 ![Statusleiste mit Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Statusleiste mit Fortschrittsleiste**

 ![Statusleiste mit Meldungen](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Statusleiste mit Textbeschreibung**

##### <a name="infobar"></a>Infoleiste
 Ähnlich wie die Statusleiste bietet die Infoleiste kontextbezogene Benachrichtigungen und Nachrichten, die auch mit unbestimmten Fortschrittsindikatoren wie der Fortschrittsleiste oder dem Spinner gekoppelt werden können. Die Infoleiste sollte keine Granularpegelfortschritts- oder Datenfortschrittsanzeige bereitstellen. Siehe [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Infoleiste mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Infoleiste mit Fortschrittsleiste und Textbeschreibung**

 ![Infoleiste in einem Fenster](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Inline
 Die Inline-Fortschrittsanzeige kann durch einen der Fortschrittsladetypen dargestellt werden. In der Regel ist der Fortschrittsindikator mit Messaging gekoppelt, aber dies ist keine Anforderung.

 ![Inline-Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner kombiniert mit Textbeschreibung**

 ![Gestapelte Inline-Fortschrittsleisten](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Bestimmen gestapelte Fortschrittsbalken**

 ![Inline-Fortschrittsmeldungen](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Server Explorer-Inlinetext: Aktualisieren...**

##### <a name="tool-windows"></a>Toolfenster
 Die globale Fortschrittsanzeige wird durch einen unbestimmten Fortschrittsbalken dargestellt, der direkt unter der Werkzeugleiste positioniert ist.

 ![Globale unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer global unbestimmte Fortschrittsleiste**

##### <a name="dialogs"></a>Dialogfelder
 Dialogfelder können alle Fortschrittsladetypen enthalten. Fortschrittsindikatoren können mit Messaging gekoppelt und mit mehreren Stufen der Fortschrittsanzeige kombiniert werden, um granulare und Sub-Prozesse darzustellen.

 ![Dialogfeld mit mehreren Arten von Fortschrittsanzeigen](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Visual Studio-Dialog mit gleichzeitigen Prozessen und mehreren Fortschrittsindikatortypen**

 ![Dialogfeld mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Visual Studio-Dialog mit Fortschrittsladeprogramm und Messaging-Inline-Befehl**

##### <a name="document-well"></a>Dokument gut
 Der Dokumentbrunnen kann mehrere Fortschrittsladetypen in Kombination mit Steuerelementen anzeigen.

 ![Fortschrittsmeldungen in Dokument](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Unbestimmte Fortschrittsleiste unterhalb der Symbolleiste**

##### <a name="output-window"></a>Ausgabefenster
 Das Ausgabefenster eignet sich für die Verarbeitung des Prozessfortschritts und des laufenden Fortschrittsstatus über Inline-Textnachrichten. Sie sollten die Statusleiste zusammen mit allen Fortschrittsberichten im Ausgabefenster verwenden.

 ![Fortschrittsmeldungen in Ausgabefenster](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Ausgabefenster mit fortlaufendem Prozessstatus und Warte-Messaging**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Infobars

### <a name="overview"></a>Übersicht
 Infobars geben dem Benutzer einen Indikator in der Nähe seines Aufmerksamkeitspunkts und die Verwendung der freigegebenen Infoleistensteuerung sorgt für Konsistenz in der visuellen Darstellung und Interaktion.

 ![Infoleiste](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Infobars in Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Geeignete Verwendungen für eine Infoleiste

- So geben Sie dem Benutzer eine nicht blockierende, aber wichtige Nachricht, die für den aktuellen Kontext relevant ist

- So zeigen Sie an, dass sich die Benutzeroberfläche in einem bestimmten Zustand oder Zustand befindet, der einige Interaktionsauswirkungen hat, z. B. historisches Debuggen

- So benachrichtigen Sie den Benutzer, dass das System Probleme erkannt hat, z. B. wenn eine Erweiterung Leistungsprobleme verursacht

- So stellen Sie dem Benutzer eine Möglichkeit zum einfachen Ergreifen von Aktionen zur Verfügung, z. B. wenn der Editor erkennt, dass eine Datei über gemischte Registerkarten und Leerzeichen verfügt

##### <a name="do"></a>Führen Sie Folgendes aus:

- Halten Sie den Infobalken-Nachrichtentext kurz und auf den Punkt.

- Halten Sie den Text auf Links und Schaltflächen kurz und bündig.

- Stellen Sie sicher, dass die "Aktionsoptionen", die Sie Benutzern zur Verfügung stellen, minimal sind und nur die erforderlichen Aktionen anzeigen.

##### <a name="dont"></a>Tue nicht:

- Verwenden Sie eine Infoleiste, um Standardbefehle anzubieten, die in einer Symbolleiste platziert werden sollen.

- Verwenden Sie eine Infoleiste anstelle eines modalen Dialogfelds.

- Erstellen Sie eine unverankerte Nachricht außerhalb eines Fensters.

- Verwenden Sie mehrere Infoleisten an mehreren Speicherorten innerhalb desselben Fensters.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Können mehrere Infobars gleichzeitig angezeigt werden?
 Ja, mehrere Infobars können gleichzeitig angezeigt werden. Sie werden in First-come, First-served-Order mit der ersten Infoleiste oben und zusätzlichen Infobars angezeigt, die unten angezeigt werden.

 Der Benutzer sieht maximal drei Infoleisten gleichzeitig, danach wird der Infoleistenbereich scrollbar, wenn weitere Infoleisten verfügbar sind.

### <a name="creating-an-infobar"></a>Erstellen einer Infoleiste
 Die Infoleiste besteht aus vier Abschnitten, von links nach rechts:

- **Symbol:** Hier fügen Sie ein beliebiges Symbol hinzu, das Sie für die Infoleiste anzeigen möchten, z. B. ein Warnsymbol.

- **Text:** Sie können Text hinzufügen, um das Szenario/die Situation zu beschreiben, in dem sich der Benutzer befindet, zusammen mit Links innerhalb des Textes, falls erforderlich. Denken Sie daran, den Text kurz zu halten.

- **Aktionen:** Dieser Abschnitt sollte Links und Schaltflächen für Aktionen enthalten, die der Benutzer in der Infoleiste ausführen kann.

- **Schaltfläche Schließen:** Der letzte Abschnitt rechts kann eine Schaltfläche zum Schließen haben.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Erstellen einer Standardinfoleiste in verwaltetem Code
 Die InfoBarModel-Klasse kann verwendet werden, um eine Datenquelle für eine Infoleiste zu erstellen. Verwenden Sie einen der vier Konstruktoren:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Im Folgenden finden Sie ein Beispiel, in dem ein InfoBarModel mit Text mit einem Hyperlink, einer Aktionsschaltfläche und einem Symbol erstellt wird.

 ![Infoleiste mit Hyperlink](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Erstellen einer Standardinfoleiste in systemeigenem Code
 Implementieren Sie die IVsInfoBar-Schnittstelle, um eine Infoleiste aus systemeigenem Code bereitzustellen.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Abrufen einer Infobar UIElement aus einer Infoleiste
 Die InfoBarModel- oder IVsInfoBar-Implementierung sind Datenmodelle, die in ein UIElement umgewandelt werden müssen, um in der Benutzeroberfläche angezeigt zu werden. Ein UIElement kann mit dem Dienst SVsInfoBarUIFactory/IVsInfoBarUIFactory abgerufen werden.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Platzierung
 Infobars können an einem oder mehreren der folgenden Speicherorte angezeigt werden:

- Toolfenster

- Innerhalb einer Dokumentregisterkarte

> [!IMPORTANT]
> Es ist möglich, eine Infoleiste zu positionieren, um eine Nachricht über den globalen Kontext zu geben. Dies würde zwischen Symbolleisten und dem Dokument gut angezeigt werden. Dies wird nicht empfohlen, da es Probleme mit "Sprung und Ruck" der IDE verursacht und sollte vermieden werden, es sei denn, absolut notwendig und angemessen.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Platzieren einer Infoleiste in einem ToolWindowPane
 Die ToolWindowPane.AddInfoBar(IVsInfoBar)-Methode kann verwendet werden, um einem Toolfenster eine Infoleiste hinzuzufügen. Diese API kann entweder eine IVsInfoBar (von denen InfoBarModel eine Standardimplementierung ist) oder ein IVsUIElement hinzufügen.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Platzieren einer Infoleiste in einem Dokument oder Nicht-ToolWindowPane
 Um eine Infoleiste in einem beliebigen IVsWindowFrame zu platzieren, verwenden Sie die VSFPROPID_InfoBarHost-Eigenschaft, um den IVsInfoBarHost für den Frame abzusuchen, und fügen Sie dann die Infoleiste UIElement hinzu.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Platzieren einer Infoleiste im Hauptfenster
 Um eine Infoleiste im Hauptfenster zu platzieren, verwenden Sie die VSSPROPID_MainWindowInfoBarHost des IVsShell-Dienstes, um den IVsInfoBarHost des Hauptfensters abzusuchen, und fügen Sie dann die Infoleiste UIElement hinzu.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Werde ich wissen, wann der Benutzer in meiner Infoleiste aktiv wird?
 Ja, wir geben jede Ereignisaktion an den Autor der Infobar zurück. Es liegt dann am Autor der Infoleiste, basierend auf der Benutzerauswahl in der Infoleiste Maßnahmen in der IDE zu ergreifen. Infobars werden automatisch vom Host entfernt, auf dessen Schaltfläche Schließen geklickt wurde, aber zusätzliche Arbeit ist erforderlich, wenn andere Infoleisten nach dem Schließen entfernt werden müssen. Die Telemetrie muss auch von jeder Infoleiste unabhängig protokolliert werden.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Empfangen von Infobar-Ereignissen in einem ToolWindowPane
 ToolWindowPane verfügt über zwei Ereignisse für Infobars. Das InfoBarClosed-Ereignis wird ausgelöst, wenn eine Infoleiste im ToolWindowPane geschlossen wird. Das InfoBarActionItemClicked-Ereignis wird ausgelöst, wenn auf einen Hyperlink oder eine Schaltfläche in der Infoleiste geklickt wird.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Empfangen von Infobar-Ereignissen direkt aus dem UIElement
 IVsInfoBarUIElement.Advise kann verwendet werden, um Ereignisse direkt aus dem UIElement einer Infoleiste zu abonnieren. Durch das Implementieren von IVsInfoBarUIEvents kann der Autor Nah- und Klickereignisse empfangen.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Fehlerüberprüfung
 Wenn ein Benutzer Informationen eingibt, die nicht akzeptabel sind, z. B. wenn ein erforderliches Feld übersprungen wird oder wenn Daten im falschen Format eingegeben werden, ist es besser, die Steuerelementüberprüfung oder das Feedback in der Nähe des Steuerelements zu verwenden, anstatt ein blockierendes Popupfehlerdialogfeld zu verwenden.

### <a name="field-validation"></a>Feldprüfung
 Die Formular- und Feldüberprüfung besteht aus drei Komponenten: einem Steuerelement, einem Symbol und einer QuickInfo. Während mehrere Arten von Steuerelementen dies verwenden können, wird ein Textfeld als Beispiel verwendet.

 ![Feldvalidierung &#40;leere&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Wenn das Feld erforderlich ist, sollte es Wasserzeichentext geben, der ** \<die** erforderliche `Environment.ControlEditRequiredBackground`>und der Feldhintergrund hellgelb (VSColor: ) und der Vordergrund grau sein sollte (VSColor: `Environment.ControlEditRequiredHintText`):

 ![Feldüberprüfung mit Beschriftung "Erforderlich"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Das Programm kann feststellen, dass sich das Steuerelement in einem Zustand *ungültigen Inhalts* befindet, der entweder eingegeben wird, wenn der Fokus auf ein anderes Steuerelement verschoben wird oder wenn der Benutzer auf eine [OK]-Commit-Schaltfläche klickt oder wenn der Benutzer das Dokument oder Formular speichert.

 Wenn der ungültige Inhaltsstatus bestimmt wird, wird ein Symbol entweder innerhalb des Steuerelements oder nur daneben angezeigt. Eine QuickInfo, die den Fehler beschreibt, sollte beim Mauszeiger auf das Symbol oder das Steuerelement angezeigt werden. Darüber hinaus sollte ein 1-Pixel-Rahmen um das Steuerelement herum angezeigt werden, das den ungültigen Status erstellt.

 ![Layoutspezifikationen für Feldüberprüfung](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Layoutspezifikationen für die Feldvalidierung**

#### <a name="acceptable-variations-for-icon-location"></a>Akzeptable Variationen für symbolort
 Es gibt unzählige Einzelfälle, in denen Benutzer über Validierungsfehler informiert werden müssen. Wählen Sie unter Berücksichtigung des Steuerelementtyps und der Konfiguration der Benutzeroberfläche die Symbolplatzierung aus, die Ihrer Situation entspricht.

 ![Zulässige Positionen für Symbolplatzierung](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Akzeptable Variationen für Feldvalidierungssymbolpositionen**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validierung, die einen Roundtrip zu einer Server- oder Netzwerkverbindung erfordert
 In einigen Fällen ist ein Roundtrip zum Server erforderlich, um den Inhalt zu überprüfen, und es wäre wichtig, den Benutzerfortschritt, die überprüften und fehlerweisenden Zustände anzuzeigen. Die folgende Abbildung zeigt ein Beispiel für diesen Fall und die empfohlene Benutzeroberfläche.

 ![Validierung mit Roundtrip zu einem Server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validierung mit Roundtrip zu einem Server**

 Beachten Sie, dass genügend verfügbarer Platz rechts vom Steuerelement zur Verfügung gestellt werden muss, um die "Überprüfung..." und "Wiederholen" Text.

#### <a name="in-place-warning-text"></a>In-Place-Warntext
 Wenn Platz vorhanden ist, um die Fehlermeldung in der Nähe des Steuerelements in einen Fehlerzustand zu versetzen, ist dies der Verwendung der QuickInfo allein vorzuziehen.

 ![An&#45;Stelle Warnung](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **In-Place-Warntext**

#### <a name="watermarks"></a>Wasserzeichen
 Manchmal befindet sich ein ganzes Steuerelement oder Fenster in einem Fehlerzustand. Verwenden Sie in diesem Fall ein Wasserzeichen, um den Fehler anzuzeigen.

 ![Wasserzeichen](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Wasserzeichenfeldvalidierung**
