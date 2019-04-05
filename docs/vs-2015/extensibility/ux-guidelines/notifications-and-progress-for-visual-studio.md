---
title: Benachrichtigungen und Status
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1e409f5c1487925ecfb9980878360cb60c1c447
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960690"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Benachrichtigungen und Fortschritt für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_NotificationSystems"></a> Benachrichtigungssysteme

### <a name="overview"></a>Übersicht
 Es gibt mehrere Möglichkeiten, den Benutzer zu informieren, was in Bezug auf ihre softwareentwicklungsaufgaben in Visual Studio passiert.

 Wenn Sie jede Art von Benachrichtigung zu implementieren:

-   **Behalten Sie die Anzahl der Benachrichtigungen auf ein Minimum** effektive Anzahl. Benachrichtigungen sollten auf der Mehrzahl der Visual Studio-Benutzer oder für Benutzer von einem spezifischen Features und Feature-Bereich anwenden. Eine übermäßige Beanspruchung von Benachrichtigungen vom eigentlichen Thema abweichen des Benutzers oder abnehmen wahrgenommene benutzerfreundlichkeit des Systems.

-   **Stellen Sie sicher, präsentieren Sie klare und Aktionen erfordernde Nachrichten** , dass der Benutzer verwenden kann, um den geeigneten Kontext für eine komplexere Entscheidungen und weitere Aktionen durchführen aufzurufen.

-   **Stellen Sie die synchrone und asynchrone Nachrichten entsprechend.** Synchrone Benachrichtigungen angeben, dass etwas erfordert sofortige Bearbeitung, wie z. B. wenn ein Webdienst stürzt ab, oder mit einem Code Ausnahme ausgelöst. Diese Situationen sofort in einer Weise, die die Eingabe wie z. B. in einem modalen Dialogfeld erfordert, sollte der Benutzer informiert werden. Asynchrone Benachrichtigungen sind diejenigen, die der Benutzer kennen sollten, aber nicht zu sofort reagieren erforderlich, z. B. wenn ein Buildvorgang abgeschlossen ist, oder eine Website-Bereitstellung abgeschlossen ist. Diese Nachrichten mehr ambient trennen und die Abfolge der Aufgaben des Benutzers nicht unterbrochen.

-   **Verwenden Sie modale Dialogfelder, die nur bei Bedarf, um zu verhindern, dass den Benutzer führt weitere Aktionen** vor der Bestätigung der Nachricht oder einer Entscheidung, die im Dialogfeld angezeigt.

-   **Entfernen Sie Ambiente-Benachrichtigungen, wenn sie nicht mehr gültig sind.** Erfordern Sie keine des Benutzers eine Benachrichtigung zu schließen, wenn sie bereits unternommen haben, Aktion aus, um das Problem zu beheben, die, dem Sie über benachrichtigt wurden.

-   **Denken Sie daran, dass Benachrichtigungen, um falsche Korrelationen führen können.** Benutzer gehen davon aus, dass eine oder mehrere ihrer Aktionen eine Benachrichtigung ausgelöst hat, wenn es tatsächlich keine kausale Beziehung gab. Löschen in der Benachrichtigung über den Kontext, der Trigger und die Quelle der Benachrichtigung sein.

### <a name="choosing-the-right-method"></a>Auswählen der richtigen Methode
 Verwenden Sie diese Tabelle, die Ihnen helfen, bei der Auswahl der richtigen Methode zur Benachrichtigung des Benutzers der Nachricht.

|Methode|Mit|Verwenden Sie keine|
|------------|---------|----------------|
|[Modale Meldung Fehlerdialoge](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Wird verwendet, wenn eine Antwort des Benutzers, bevor Sie fortfahren erforderlich ist.|Verwenden Sie nicht bei keine Notwendigkeit besteht, blockieren den Benutzer zu identifizieren und deren Fluss. Verwenden Sie modale Dialogfelder, wenn es möglich ist, die die Nachricht in eine andere und weniger intrusiv Weise anzeigen.|
|[IDE-Statusleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Verwenden Sie Wenn ambient Textinformationen in Bezug auf den Status eines Prozesses vorhanden ist.|Verwenden Sie nicht allein. Am besten verwendet in Verbindung mit einem anderen Feedbackmechanismus.|
|[Eingebettete Infoleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Verwenden Sie in einem Toolfenster oder Dokumentfenster zum Status, Zustand "Fehler", Ergebnisse, und/oder handlungsrelevante Informationen zu benachrichtigen.|Verwenden Sie nicht, wenn die Informationen nicht an den Speicherort relevant ist, in dem die Infoleiste platziert wird.<br /><br /> Verwenden Sie nicht außerhalb eines Dokuments/Toolfensters.|
|[Mauszeiger ändert sich](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Kann verwendet werden, um mitzuteilen, dass ein Prozess vor sich geht. Auch verwendet benachrichtigt, dass eine Zustandsänderung bei der Maus vorhanden ist, z. B. bei Drag & Drop in Bearbeitung "oder", wird der Mauszeiger in einem bestimmten Modus, z. B. Zeichnungsmodus des.|Verwenden Sie nicht für Änderungen des kurzen Status oder der fluttering der Cursor wahrscheinlich (z. B., wenn auf Teile ein längerer ausgeführten Prozess statt für den gesamten Prozess gebunden) ist.|
|[Statusanzeigen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Wird verwendet, wenn der Status (bestimmte oder unbestimmt) benötigen. Es gibt verschiedene Arten von Fortschrittsanzeigen und die anwendungsspezifische Nutzung für jede. Finden Sie unter [Fortschritt Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Visual Studio-benachrichtigunsfenster](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Das Fenster "Benachrichtigungen" ist nicht öffentlich erweiterbar. Es wird jedoch verwendet, um einen Bereich von Meldungen über die Visual Studio, z. B. kritische Probleme mit Ihrer Lizenz und informativen Benachrichtigungen von Updates für Visual Studio oder Pakete zu kommunizieren.|Verwenden Sie nicht für andere Arten von Benachrichtigungen.|
|[Fehlerliste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Wenn das Problem direkt an des Benutzers aktuell geöffneten Projektmappe ist ein Problem (Fehler/Warnung/Info) verbunden ist, müssen sie möglicherweise Maßnahmen ergreifen, auf dem Code.<br /><br /> Dies würde, z. B. Folgendes umfassen:<br /><br /> -Compiler Nachrichten (Fehler/Warnung/Info)<br /><br /> -Code Analyzer/Diagnosedateien Nachrichten über den code<br /><br /> – Erstellen von Nachrichten<br /><br /> Kann für Probleme im Zusammenhang mit der Projektmappen- oder Projektdateien geeignet, aber Sie sollten eine Angabe über das Projektmappen-Explorer zuerst.|Verwenden Sie nicht für Elemente, die keinen Bezug zu den Code des Benutzers Projektmappe öffnen.|
|Editor für Benachrichtigungen: Glühbirne|Verwenden Sie haben eine Lösung zur Verfügung, um ein Problem zu beheben, die in der geöffneten Datei vorhanden ist.<br /><br /> Beachten Sie, dass die Glühbirne auch verwendet werden soll, für das Hosten von Schnellaktionen, die auf den Code des Benutzers bei Bedarf, z. B. Refactorings, stammen in diesem Fall wird jedoch nicht angezeigt "Notification-Style".|Verwenden Sie nicht für Elemente, die nicht über Beziehung mit der geöffneten Datei verfügen.|
|Editor für Benachrichtigungen: Wellenlinien|Benachrichtigung des Benutzers auf ein Problem mit einer bestimmten Spanne des Codes öffnen (z. B. eine rote Wellenlinie für Fehler) verwenden.|Verwenden Sie nicht für Elemente, die nicht auf eine bestimmte Spanne des Codes öffnen beziehen.|
|[Eingebettete Statusleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Zum Bereitstellen von Status, die im Zusammenhang mit Inhalt oder der Prozess im Kontext eines bestimmten Toolfenster, Dokumentfenster oder Dialogfenster verwenden.|Verwenden Sie nicht für allgemeine Benachrichtigungen, Prozessen oder Elemente, die nicht über Beziehung zu den Inhalt in das jeweilige Fenster verfügen.|
|[Windows-Taskleiste-Benachrichtigungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Verwenden Sie, um Benachrichtigungen für die Out-of-Proc-Prozesse Oberfläche oder Begleit-Anwendungen.|Verwenden Sie nicht für Benachrichtigungen, die für die IDE relevant sind.|
|[Benachrichtigung Blasen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Verwenden, um einen Remoteprozess, zu melden, oder ändern Sie **außerhalb** der IDE.|Verwenden Sie nicht als Mittel zum Benachrichtigen des Benutzers von Prozessen **in** der IDE.|

### <a name="notification-methods"></a>Benachrichtigungsmethoden

####  <a name="BKMK_ModalErrorMessageDialogs"></a> Modale Meldung Fehlerdialoge
 Eine modale Fehlerdialogfeld wird verwendet, eine Fehlermeldung angezeigt, die Bestätigung des Benutzers oder eine Aktion erforderlich sind.

 ![Modale Fehlermeldung](../../extensibility/ux-guidelines/media/0901-01-modalerrormessage.png "0901-01_ModalErrorMessage")

 **Eine modale Fehlerdialogfeld warnen der Benutzer, der eine ungültige Verbindungszeichenfolge in einer Datenbank**

####  <a name="BKMK_IDEStatusBar"></a> IDE-Statusleiste
 Die Wahrscheinlichkeit, dass Benutzer Statusleistentext Beachten Sie, dass entspricht ihre Erfahrung mit umfassenden Computern und Anwendungsverhalten mit der Windows-Plattform. Die Kunden von Visual Studio ist meist erfahrene in beiden Bereichen, obwohl auch erfahrene Windows-Benutzer Änderungen in der Statusleiste verpassen würde. Aus diesem Grund wird die Statusleiste am besten für Informationszwecke oder redundante Stichwort verwendet für Informationen, die an anderer Stelle angezeigt. Jede Art von wichtigen Informationen, den der Benutzer sofort beheben muss, muss in einem Dialogfeld oder im Toolfenster, Benachrichtigungen bereitgestellt werden.

 Die Statusleiste von Visual Studio wurde entwickelt, um verschiedene Arten von Informationen zu ermöglichen, die angezeigt werden. Es ist in Regionen für Feedback, Designer, Statusanzeige, Animation und Client unterteilt.

 Das Feedback und Designer Region sind immer sichtbar. Die Statusanzeige und eine Animation Regionen sind immer dynamisch und basieren auf den Benutzerkontext. Der Designerbereich hat es sich um eine statische Breite bestimmt, indem die Länge der Zeichenfolge, die aus einer zugehörigen Ressource für die Nachricht abgerufen werden. Dadurch wird die Lokalisierung in die Breite des zu ändern, ohne dass eine Änderung des Codes. Für Englisch ist die Breite dieser Zeichenfolge etwa 220 Pixel. Der Designerbereich verhält sich normal, und die Feedbackbereich wird den verbleibenden Speicherplatz absorb.

 Die Statusleiste wird auch zum Hinzufügen von visuellem Reiz und funktionale Wert durch Kommunikation verschiedener statusänderungen der IDE z. B. wenn die IDE im Debugmodus wird eingefärbt.

 ![IDE-Statusleiste farbänderungen](../../extensibility/ux-guidelines/media/0901-02-idestatusbar.png "0901-02_IDEStatusBar")

 **IDE-statusleistenfarben**

####  <a name="BKMK_EmbeddedInfobar"></a> Eingebettete Infoleiste
 Eine Infoleiste kann am oberen Rand eines Dokument- oder Toolfenster verwendet werden, die Benutzer über einen Status oder Zustand informiert. Sie können auch Befehle bieten, damit, dass der Benutzer eine Möglichkeit, problemlos Maßnahmen ergreifen kann. Die Infoleiste ist ein standard-Shell-Steuerelement. Erstellen Sie keine eigene die fungieren und nicht mit anderen Benutzern in der IDE angezeigt wird. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) Implementierungsdetails und Anleitungen.

 ![Eingebettete Infoleiste](../../extensibility/ux-guidelines/media/0901-03-embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Eine Infoleiste eingebettet in einem Dokumentfenster warnen der Benutzer, den der IDE befindet sich im Modus "verlaufsbezogenes debugging" und der Editor reagiert nicht auf die gleiche Weise wie im standard-debugging-Modus.**

####  <a name="BKMK_MouseCursorChanges"></a> Mauszeiger ändert sich
 Wenn Sie den Mauszeiger zu ändern, verwenden Sie Farben, die an den Dienst VSColor gebunden werden und sind bereits mit dem Cursor zugeordnet. Cursor geändert für, der angibt, einer laufenden Operation verwendet werden können, als auch erreichen Zonen, in denen der Benutzer über ein Ziel, die gezogen bewegt wird, abgelegt oder zum Auswählen eines Objekts verwendet werden können.

 Verwenden Sie den Mauszeiger ausgelastet/warten, nur, wenn alle verfügbaren CPU-Zeit für einen Vorgang, der verhindert, dass des Benutzers weitere Eingabe Ausdrücken reserviert werden muss. In den meisten Fällen gut geschriebene Anwendungen, die Verwendung von multithreading sollte nur selten Mal, wenn Benutzer daran gehindert werden andere Vorgänge ausführen.

 Bedenken Sie, dass Cursor Änderungen nützlich sind, wie ein redundanter Cue Informationen, die an anderer Stelle angezeigt. Verlassen Sie sich nicht auf eine Änderung der Cursor als die einzige Möglichkeit der Kommunikation mit dem Benutzer, insbesondere, wenn Sie versuchen, etwas zu vermitteln, die wichtig sind, dass der Benutzer erfüllen muss.

####  <a name="BKMK_NotSysProgressIndicators"></a> Statusanzeigen
 Statusanzeigen sind wichtig für die Benutzerfeedback dazu, während der Prozesse, die mehr als ein paar Sekunden dauern. Statusanzeige angezeigt werden direkte (in der Nähe der Startpunkt der Aktion wird ausgeführt), in eine eingebettete Statusleiste, in ein modales Dialogfeld oder in der Statusleiste von Visual Studio. Führen Sie die Anleitung im [Fortschritt Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) im Hinblick auf ihre Verwendung und Implementierung.

####  <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio-benachrichtigunsfenster
 Die Visual Studio-benachrichtigunsfenster benachrichtigt Entwickler zu Lizenzierung, Umgebung (Visual Studio), Erweiterungen und Updates. Benutzer können können die Benachrichtigung verwerfen oder, um bestimmte Arten von Benachrichtigungen zu ignorieren. Die Liste der ignorierten Benachrichtigungen wird verwaltet, einem **Tools > Optionen** Seite.

 Das Fenster "Benachrichtigungen" ist nicht aktuell erweiterbar.

 ![Visual Studio-benachrichtigunsfenster](../../extensibility/ux-guidelines/media/0901-06-vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Toolfenster für Visual Studio-Benachrichtigungen**

####  <a name="BKMK_ErrorList"></a> Fehlerliste
 Eine Benachrichtigung in der Fehlerliste anzugeben, Fehler und Warnungen, die aufgetreten sind, während der Kompilierung oder und Buildprozess und ermöglicht dem Benutzer, die im Code, um diesen Fehler für bestimmten Code navigieren.

 ![Fehlerliste](../../extensibility/ux-guidelines/media/0901-08-errorlist.png "0901-08_ErrorList")

 **Fehlerliste in Visual Studio**

####  <a name="BKMK_EmbeddedStatusBars"></a> Eingebettete Statusleisten
 Da die IDE-Statusleiste dynamisch, mit der Region-Clientkontext, die auf das aktive Fenster und die Informationen, die Aktualisierung auf den Kontext des Benutzers und/oder Systemantworten festgelegt ist, ist es schwierig, eine kontinuierliche Anzeige von Informationen zu verwalten, oder geben Sie Status für langfristige asynchroner Prozesse. Beispielsweise eignet sich die IDE-Statusleiste nicht für Benachrichtigungen über Ergebnisse für mehrere Ausführungen und/oder sofort umsetzbare Elemente aus. Es ist wichtig, diese Statusinformationen im Kontext des Fensters Dokument- oder Toolfenster, in denen der Benutzer stellt eine Auswahl oder startet einen Prozess, beibehalten werden sollen.

 ![Eingebettete Statusleiste](../../extensibility/ux-guidelines/media/0901-09-embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Eingebettete Statusleiste in Visual Studio**

####  <a name="BKMK_WindowsTray"></a> Windows-Taskleiste-Benachrichtigungen
 Der Infobereich neben das System ist Windows Systemzeit auf dem der Windows-Taskleiste. Viele Hilfsprogramme und Software-Komponenten bieten Symbole in diesem Bereich an, damit der Benutzer ein Kontextmenü für eine systemweite-Aufgaben, z. B. Änderung der Bildschirmauflösung oder Abrufen von Softwareupdates abrufen kann.

 Auf Umgebungsebene Benachrichtigungen sollten im Visual Studio-Benachrichtigungs-Hubs, nicht die Windows-Infobereich eingeblendet werden.

####  <a name="BKMK_NotificationBubbles"></a> Benachrichtigung Blasen
 Benachrichtigung Blasen können als informationsmeldung in einem Designer/Editor oder als Teil der Windows-Infobereich der Taskleiste angezeigt werden. Der Benutzer nimmt diese Blasen als Probleme, die sie später auflösen können dies ist ein Vorteil für nicht kritische Benachrichtigungen wahr. Blasen sind nicht geeignet, um wichtige Informationen, den der Benutzer sofort gelöst werden muss. Wenn Sie Benachrichtigungen Blasen in Visual Studio verwenden, führen Sie die [Windows-Desktop-Anleitungen für die Benachrichtigung Blasen](https://msdn.microsoft.com/library/windows/desktop/dn742472\(v=vs.85\).aspx).

 ![Benachrichtigungssprechblase](../../extensibility/ux-guidelines/media/0901-07-notificationbubbles.png "0901-07_NotificationBubbles")

 **Benachrichtigungssprechblase im Windows-Infobereich der Taskleiste für Visual Studio verwendet**

##  <a name="BKMK_ProgressIndicators"></a> Statusanzeigen

### <a name="overview"></a>Übersicht
 Statusanzeigen sind ein wichtiger Teil ein Benachrichtigungssystem, für die Benutzerfeedback dazu geben. Sie können dem Benutzer mitgeteilt, wenn Prozesse und Vorgänge abgeschlossen werden. Vertraute Indikator zählen Statusanzeigen, rotierende Cursor und animierter Symbole. Der Typ und die Platzierung einer Statusanzeige hängt davon ab, den Kontext, einschließlich welche gemeldet wird und wie lange der Prozess oder Vorgang bis zum Abschluss.

#### <a name="factors"></a>Faktoren
 Um zu bestimmen, welche Indikatortyp geeignet ist, müssen Sie die folgenden Faktoren zu bestimmen.

1.  **Zeitliche Steuerung:** Zeitdauer der Vorgang dauert

2.  **Modalität:** gibt an, ob der Vorgang ist modal ist, in der Umgebung (Sperren der Benutzeroberfläche, bis der Vorgang abgeschlossen ist)

3.  **Persistente/vorübergehend:** gibt an, ob das endgültige Ergebnis über den Fortschritt zu einem späteren Zeitpunkt gemeldeten und/oder angezeigt werden muss

4.  **Bestimmte/unbestimmt:** gibt an, ob die Endzeit des Vorgangs und den Fortschritt berechnet werden können

5.  **Grafik zu/Textual-Speicherort:** gibt an, ob der Status oder Prozess aufgezeichneten Inline im Hauptteil einer Nachricht oder ein bestimmtes Steuerelement, z. B. das Strukturansicht-Steuerelement ist

6.  **NEAR:** , ob der Status in der Nähe der Benutzeroberfläche sein soll, die mit dem es verknüpft ist. (Beispielsweise kann es sein, in der Statusleiste, die weit entfernt sein kann, oder hat er sich in der Nähe der Schaltfläche, die der Prozess gestartet?)

#### <a name="determinate-progress"></a>Bestimmte Status

|Statustyp|Wann und wie Sie mit|Hinweise|
|-------------------|-------------------------|-----------|
|Statusanzeige (bestimmte)|Dauer der erwarteten > 5 Sekunden.<br /><br /> Textbeschreibung des Prozessdetails herausgeberkontos ausgewiesenen Form.|**Keine** Einbetten von Text in der Animation.|
|Infoleiste|Messaging kontextbezogene Benutzeroberfläche zugeordnet ist. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Textbeschreibung des Prozessdetails herausgeberkontos ausgewiesenen Form.|**Keine** mehrere Infoleisten verwenden, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Statusanzeigen.|
|Ausgabefenster|Vorübergehenden Benachrichtigung: app-basierten Prozess dieser Benutzer möchten **überprüfen** Details nach dem Abschluss.|**Keine** verwenden, wenn der Benutzer muss zum Verweisen auf Daten später noch mal.|
|Protokolldatei|Zusammen mit intransient Notification in Fällen, wenn es darauf ankommt, **speichern** Details nach dem Abschluss.||
|Statusleiste|Vorübergehenden Benachrichtigung: app-basierten Prozess dieser Benutzer wird **nicht** Details nach dem Abschluss.<br /><br /> Enthält eine Statusanzeige für embedded.<br /><br /> Textbeschreibung des Prozessdetails herausgeberkontos ausgewiesenen Form.||

#### <a name="indeterminate-progress"></a>Unbestimmte Statusanzeige

|Statustyp|Wann und wie Sie mit|Hinweise|
|-------------------|-------------------------|-----------|
|Statusanzeige (unbestimmt)|Dauer der erwarteten > 5 Sekunden.<br /><br /> Textbeschreibung des Prozessdetails herausgeberkontos ausgewiesenen Form.|**Keine** Einbetten von Text in der Animation.|
|ANTS (animierte horizontale Punkte)|Der Roundtrip zum Server.<br /><br /> Platziert nahe Punkt des Kontexts am oberen Rand der übergeordneten Container.|**Keine** verwenden, wenn der gesamte Container nicht untergeordnet.|
|Drehfeld (statuskreis)|Der Prozess, zugeordnet ist kontextbezogene Benutzeroberfläche, in dem Speicherplatz zu berücksichtigen ist.<br /><br /> Textbeschreibung des Prozessdetails herausgeberkontos ausgewiesenen Form.||
|Infoleiste|Messaging kontextbezogene Benutzeroberfläche zugeordnet ist. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Keine** mehrere Infoleisten verwenden, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Statusanzeigen.|
|Ausgabefenster|Vorübergehenden Benachrichtigung: Prozess der app-Ebene, Benutzer sollten **überprüfen** Details nach dem Abschluss.|**Keine** verwenden, um Informationen, die über Sitzungen hinweg beibehalten werden muss.|
|Protokolldatei|Zusammen mit intransient Notification in Fällen, wenn es darauf ankommt, **speichern** Details nach dem Abschluss.||
|Statusleiste|Vorübergehenden Benachrichtigung: app-basierten Prozess dieser Benutzer wird **nicht** Details nach dem Abschluss.<br /><br /> Enthält eingebettete Statusanzeige an.<br /><br /> Textbeschreibung des Prozessdetails herausgeberkontos ausgewiesenen Form.||

### <a name="progress-indicator-types"></a>Arten von Fortschrittsanzeigen

#### <a name="progress-bars"></a>Statusanzeigen

##### <a name="indeterminate"></a>Unbestimmt
 ![Unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-04-indeterminate.png "0901-04_Indeterminate")

 **Unbestimmte Fortschrittsleiste**

 "Unbestimmt" bedeutet, dass der allgemeinen Status eines Vorgangs oder Prozess kann nicht bestimmt werden. Verwenden Sie unbestimmt Statusanzeigen für Vorgänge, die eine ungebundene Menge an Zeit erfordern, oder, die auf eine unbekannte Anzahl von Objekten. Verwenden Sie eine Beschreibung, begleitet, was passiert. Verwenden Sie Timeouts Grenzen auf Zeit-basierte Vorgänge zu gewähren. Unbestimmte Statusanzeige Balken verwenden Sie Animationen an, dass der Status wird ausgeführt, aber keine weiteren Informationen bereitstellen. Wählen Sie keine unbestimmte Fortschrittsleiste nur aufgrund der möglichen Mangel an Genauigkeit, die allein.

##### <a name="determinate"></a>Bestimmte
 ![Festgelegte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-05-determinate.png "0901-05_Determinate")

 **Festgelegte Fortschrittsleiste**

 "Bestimmte" bedeutet, dass eine Operation oder ein Prozess eine begrenzte Menge an Zeit erfordert, selbst wenn Sie der angegebenen Zeitraum nicht genau vorhergesagt werden kann. Geben Sie die Vervollständigung eindeutig an. Lassen Sie keine Statusanzeige an, wechseln zu 100 Prozent, wenn der Vorgang abgeschlossen ist. Bestimmte Leiste Statusanimation verschiebt links-nach-rechts-zwischen 0 und 100 %.

 Nie verschoben Sie die Statusanzeige ändert sich während eines Vorgangs rückwärts werden. Die Leiste sollte fortfahren stetig zu Beginn des Vorgangs und erreichen 100 %, wenn sie endet. Der Punkt der Statusanzeige ist, Benutzern eine Vorstellung davon, wie lange der gesamte Vorgang dauert unabhängig davon, wie viele Schritte erforderlich sind.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Gleichzeitige reporting (gestapelten Statusanzeigen)
 Wenn ein Vorgang wird sehr lange dauern möglicherweise mehrere Minuten – dann zwei Statusanzeigen verwendet werden können, wird eine dargestellt, die Gesamtfortschritt für einen Vorgang und eine für den Fortschritt des aktuellen Schritts. Z. B. wenn ein Setupprogramm, das viele Dateien kopiert werden, kann dann eine Statusanzeige verwendet werden, um anzugeben, wie lange dauert der gesamte Prozess während eine Sekunde, welcher Prozentsatz der aktuellen Datei angeben kann oder Verzeichnis kopiert werden. Melden Sie mehr als fünf Prozesse, die mit gestapelten Statusanzeigen oder gleichzeitigen Vorgängen nicht. Wenn Sie mehr als fünf gleichzeitige Vorgänge oder Prozesse zum Bericht haben, verwenden Sie einem modalen Dialogfeld mit einer Schaltfläche "Abbrechen" und der Bericht die Statusdetails im Ausgabefenster.

##### <a name="textual-descriptions"></a>Textbeschreibungen
 Verwenden Sie eine Beschreibung, die begleitet, was passiert ist und die geschätzte Zeit bis zum Abschluss. Ist dies nicht möglich, um zu bestimmen, wie lange ein Vorgang dauert, kann eine bessere Wahl für das Bereitstellen von Feedback eine Statusanzeige, anstatt eine animierte Symbol sein.

 Visual Studio bietet eine standard-Statusanzeige in der Statusleiste, die ein Produkt in Visual Studio integriert verwendet werden kann. Für textbeschreibungen, was geschieht, während die Statusanzeige animiert wird kann der Text der Statusleiste aktualisiert werden.

#### <a name="other-progress-indicators"></a>Andere Statusanzeigen

##### <a name="ants-animated-horizontal-dots"></a>ANTS (animierte horizontale Punkte)
 ![Status der Ants](../../extensibility/ux-guidelines/media/0903-01-ants.png "0903-01_Ants")

 "Ameisen," animierte horizontale Punkte, bieten eine visuelle Referenz für einen unbestimmten Round-Trip Serverprozess.

##### <a name="spinner-progress-ring"></a>Drehfeld (statuskreis)
 ![Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-02-spinner.png "0903-02_Spinner")

 Das Drehfeld (auch bekannt als ein "statuskreis") ist eine unbestimmte Statusanzeige hauptsächlich in Bezug auf die kontextbezogene Benutzeroberfläche verwendet. Zeigen Sie ein Drehfeld, in der Nähe der verwandtem Inhalt, wie Text Kategorieheaders, messaging oder Steuerelement.

##### <a name="cursor-feedback"></a>Cursor-feedback
 Zu Vorgängen, die zwischen 2 bis 7 Sekunden dauern, Feedback Cursor. In der Regel bedeutet dies mithilfe des Wartecursors, die vom Betriebssystem bereitgestellt werden. Anleitungen finden Sie im MSDN-Artikel [Cursors.Wait Eigenschaft](https://msdn.microsoft.com/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).

#### <a name="progress-indicator-locations"></a>Status Indicator Speicherorte

##### <a name="status-bar"></a>Statusleiste
 Die Statusleiste kann Ihre Anwendung einer Nachrichten und nützliche Informationen für den Benutzer anzuzeigen, ohne Unterbrechung der Arbeit. In der Regel am unteren Rand eines Fensters angezeigt wird, werden Status für den Status einer QuickInfo-Toolbereich, die eine Meldung über das Maß für Fortschritt in Kombination mit einer Statusanzeige für die Leiste enthält.

 ![Statusleiste mit Statusanzeige](../../extensibility/ux-guidelines/media/0903-03-statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Statusleiste mit Statusanzeige**

 ![Statusleiste mit Meldungen](../../extensibility/ux-guidelines/media/0903-04-statusbarmessage.png "0903-04_StatusBarMessage")

 **Statusleiste mit textbeschreibung**

##### <a name="infobar"></a>Infoleiste
 Ähnlich wie in der Statusleiste der Infoleiste bietet kontextbezogene Benachrichtigungen und messaging, die auch mit einer unbestimmten Statusanzeigen wie die Statusanzeige oder das Drehfeld gekoppelt werden kann. Die Infoleiste sollten keine präzise Ebene ausgeführt werden oder bestimmte Fortschrittsanzeige bereit. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Infoleiste mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-05-infobar.png "0903-05_InfoBar")

 **Infoleiste mit Fortschrittsanzeige und Beschreibung**

 ![Infoleiste in einem Fenster](../../extensibility/ux-guidelines/media/0903-06-infobarinwindow.png "0903-06_InfoBarInWindow")

 **Infoleiste in das Fenster "Codeanalyse"**

##### <a name="inline"></a>Inline
 Inline-Fortschrittsanzeige kann von jedem der Progress-Ladeprogramm-Typen dargestellt werden. In der Regel ist die Statusanzeige mit messaging kombiniert, aber dies ist nicht erforderlich.

 ![Drehelement zum Fortschritt der Inline](../../extensibility/ux-guidelines/media/0903-07-inlinespinner.png "0903-07_InlineSpinner")

 **Drehfeld, in Kombination mit textbeschreibung**

 ![Gestapelte Inline-Fortschrittsleisten](../../extensibility/ux-guidelines/media/0903-08-inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Bestimmte gestapelte Statusanzeigen**

 ![Inline-fortschrittsmeldungen](../../extensibility/ux-guidelines/media/0903-09-inlinetext.png "0903-09_InlineText")

 **Server-Explorer-inlinetext: Wird aktualisiert...**

##### <a name="tool-windows"></a>Toolfenster
 Globale Fortschrittsanzeige wird durch eine unbestimmte Fortschrittsleiste direkt unterhalb der Symbolleiste positioniert dargestellt.

 ![Globale unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-23-globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer globale unbestimmte Fortschrittsleiste**

##### <a name="dialogs"></a>Dialogfelder
 Dialoge können die Status-Ladeprogramm-Typen enthalten. Statusanzeigen können werden zusammen mit messaging als auch in Kombination mit mehreren Ebenen der Fortschrittsanzeige darstellen, die präzise oder Sub-Prozesse.

 ![Dialogfeld mit mehreren Arten von Fortschrittsanzeigen](../../extensibility/ux-guidelines/media/0903-11-dialog.png "0903-11_Dialog")

 **Visual Studio-Dialogfeld mit gleichzeitiger Prozesse und mehreren Arten von Fortschrittsanzeigen**

 ![Dialogfeld mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-12-dialog2.png "0903-12_Dialog2")

 **Visual Studio-Dialogfeld mit Fortschrittsanzeige und Meldungen, Inline-Befehle**

##### <a name="document-well"></a>Dokumentursprung
 Das Dokument kann mehrere Status-Ladeprogramm-Typen auch in Kombination mit Steuerelementen angezeigt werden.

 ![Fortschrittsmeldungen in Dokument auch](../../extensibility/ux-guidelines/media/0903-13-documentwell.png "0903-13_DocumentWell")

 **Unbestimmte Fortschrittsleiste unter Symbolleiste**

##### <a name="output-window"></a>Ausgabefenster
 Das Fenster "Ausgabe" eignet sich für die Behandlung von Prozess Fortschritt und Fortschrittstatus von laufenden über Text Inline-messaging. Sie sollten die Statusleiste zusammen mit jeder Ausgabe Fenster statusberichterstellung verwenden.

 ![Fortschrittsmeldungen in Ausgabefenster](../../extensibility/ux-guidelines/media/0903-14-outputwindow.png "0903-14_OutputWindow")

 **Ausgabefenster mit dem Status des laufenden Prozess und warten Sie, messaging**

##  <a name="BKMK_Infobars"></a> Infobars

### <a name="overview"></a>Übersicht
 Infoleisten weisen Sie dem Benutzer einen Indikator in der Nähe ihrer Punkt Aufmerksamkeit und mithilfe des freigegebenen Infoleiste-Steuerelements, wird die Konsistenz in visual Erscheinungsbild und Wechselwirkung sichergestellt wird.

 ![Infobar](../../extensibility/ux-guidelines/media/0904-01-infobar.png "0904-01_Infobar")

 **Infoleisten in Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Entsprechende verwendet für eine Infoleiste

-   Um dem Benutzer eine nicht blockierende, jedoch wichtige Meldung, die für den aktuellen Kontext relevant geben.

-   Um anzugeben, dass die Benutzeroberfläche in einem bestimmten Status oder Zustand ausführt, die Interaktion Auswirkungen, wie verlaufsbezogenes debugging

-   Um den Benutzer zu benachrichtigen, dass das System Probleme, z. B. wenn eine Erweiterung Leistungsprobleme wohl verursacht werden erkannt hat

-   Um Benutzern eine Möglichkeit, problemlos Maßnahmen ergreifen, z.B. wenn der Editor erkennt, dass eine Datei, Registerkarten und Leerzeichen gemischt hat

##### <a name="do"></a>Führen Sie aus:

-   Behalten Sie den Meldungstext Infoleiste kurz und sachlich.

-   Behalten Sie den Text auf die Links und Schaltflächen kompakt.

-   Stellen Sie sicher, dass die "Action"-Optionen, die Sie für Benutzer bereitstellen, sehr einfach gehalten und zeigt nur die erforderliche Aktionen sind.

##### <a name="dont"></a>Tue nicht:

-   Verwenden Sie eine Infoleiste Standardbefehle anbieten, die in einer Symbolleiste platziert werden soll.

-   Verwenden Sie eine Infoleiste anstelle ein modales Dialogfeld an.

-   Erstellen Sie eine unverankerte Nachricht außerhalb eines Fensters.

-   Verwenden Sie mehrere Infoleisten an mehreren Standorten in demselben Fenster an.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Werden mehrere Infoleisten können gleichzeitig angezeigt?
 Ja, können mehrere Infoleisten gleichzeitig anzeigen. Sie werden mit der ersten Infoleiste anzeigen auf der oberen und zusätzliche Infoleisten mit folgenden datagrammbasierte paketschaltertechnologie, First-served-Reihenfolge angezeigt werden.

 Der Benutzer sieht maximal drei Infoleisten zu einem Zeitpunkt nach, die, wenn weitere Infoleisten verfügbar sind, werden die Infoleiste Region bildlauffähigen werden soll.

### <a name="creating-an-infobar"></a>Erstellen eine Infoleiste
 Die Infoleiste verfügt über vier Abschnitte, von links nach rechts:

-   **Icon:** Dies ist, in dem Sie alle Symbol hinzufügen würden Sie möchten für die Infoleiste, z. B. ein Warnsymbol angezeigt werden soll.

-   **Text:** Sie können, dass Text, der den Benutzer-Szenario/Situation zu beschreiben, zusammen mit Links innerhalb des Texts, wird bei Bedarf hinzufügen. Denken Sie daran, um den Text kompakt zu halten.

-   **Aktionen:** Dieser Abschnitt sollte enthalten, Links und Schaltflächen für Aktionen, die der Benutzer in Ihrer Infoleiste aufnehmen kann.

-   **Schaltfläche "Schließen":** Im letzten Abschnitt rechts kann es sich um eine Schaltfläche "Schließen" verfügen.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Erstellen eine standardmäßige Infoleiste in verwaltetem code
 Die InfoBarModel-Klasse kann verwendet werden, um eine Datenquelle für eine Infoleiste zu erstellen. Verwenden Sie eine dieser vier Konstruktoren:

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

 Hier ist ein Beispiel, eine InfoBarModel mit etwas Text mit einem Hyperlink, einer Aktionsschaltfläche und ein Symbol erstellt.

 ![Infoleiste mit Hyperlink](../../extensibility/ux-guidelines/media/0904-02-infobarhyperlink.png "0904-02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Erstellen eine standardmäßige Infoleiste in nativem code
 Implementieren Sie die IVsInfoBar-Schnittstelle, um eine Infoleiste von nativem Code zu gewährleisten.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Abrufen einer Infoleiste "UIElement" über eine Infoleiste
 Die InfoBarModel oder IVsInfoBar-Implementierung sind die Datenmodelle, die in "UIElement" umgewandelt werden müssen, um in der Benutzeroberfläche angezeigt werden. Eine "UIElement" kann mit dem Dienst SVsInfoBarUIFactory/IVsInfoBarUIFactory abgerufen werden.

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
 Infoleisten können in einer oder mehreren der folgenden Speicherorte angezeigt werden:

-   Toolfenster

-   Innerhalb einer Registerkarte "Dokument"

> [!IMPORTANT]
>  Es ist möglich, die position einer Infoleiste, um eine Nachricht zum globalen Kontext zu gewähren. Dies wird zwischen Symbolleisten und Dokumentursprung angezeigt. Dies wird nicht empfohlen, da es Probleme mit "wechseln und ruck" bewirkt, dass der IDE und sollte vermieden werden, es sei denn, absolut notwendig und zweckmäßig.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Platzieren eine Infoleiste in einem ToolWindowPane
 Die ToolWindowPane.AddInfoBar(IVsInfoBar)-Methode kann verwendet werden, eine Infoleiste eines Toolfensters hinzu. Diese API kann entweder ein IVsInfoBar (welche InfoBarModel ist eine standardmäßige Implementierung), hinzufügen oder eine IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Platzieren eine Infoleiste in einem Dokument oder die nicht von ToolWindowPane
 Um eine Infoleiste in jeder IVsWindowFrame platzieren möchten, verwenden Sie die VSFPROPID_InfoBarHost-Eigenschaft, um die IVsInfoBarHost für den Frame zu erhalten, und fügen Sie dann die Infoleiste "UIElement" hinzu.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Platzieren im Hauptfenster von einer Infoleiste
 Um eine Infoleiste im Hauptfenster von platzieren möchten, verwenden Sie die VSSPROPID_MainWindowInfoBarHost des IVsShell-Diensts, um das Hauptfenster IVsInfoBarHost abzurufen, und klicken Sie dann die Infoleiste "UIElement" hinzugefügt.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Kann ich erkennen, wenn der Benutzer in Mein Infoleiste eine Aktion ausführt?
 Ja, gibt es jede Aktion des Ereignisses an den Autor Infoleiste zurück. Er ist Autor der Infoleiste Maßnahmen zu ergreifen, in der IDE auf Grundlage der Benutzerauswahl in der Infoleiste. Infoleisten werden automatisch entfernt werden, auf dem Host, dessen Schaltfläche "Schließen" geklickt wurde, jedoch zusätzliche Schritte sind erforderlich, wenn andere Infoleisten müssen nach dem zu entfernenden schließen. Telemetriedaten müssen außerdem unabhängig von jeder Infoleiste protokolliert werden.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Empfangen von Ereignissen Infoleiste in einem ToolWindowPane
 ToolWindowPane verfügt über zwei Ereignisse für Infoleisten. Die InfoBarClosed-Ereignis wird ausgelöst, wenn eine Infoleiste in die ToolWindowPane geschlossen wird. Die InfoBarActionItemClicked-Ereignis wird ausgelöst, wenn auf einen Link oder eine Schaltfläche in der Infoleiste geklickt wird.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Empfangen von Ereignissen Infoleiste direkt über das "UIElement"
 IVsInfoBarUIElement.Advise kann verwendet werden, Ereignisse direkt über eine Infoleiste die "UIElement" abonniert. Implementieren von IVsInfoBarUIEvents lässt sich auf den Autor zum Schließen empfangen, und klicken Sie auf Ereignisse aus.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

##  <a name="BKMK_ErrorValidation"></a> Fehler-Überprüfung
 Wenn ein Benutzer Informationen, der nicht zulässig eingibt, z. B. wenn ein erforderliches Feld ausgelassen wird oder wenn Daten im falschen Format eingegeben werden, ist es besser, die Validierung von Steuerelementen verwenden oder Feedback in der Nähe des Steuerelements, anstatt eine blockierende Popupdialogfeld-Fehler.

### <a name="field-validation"></a>Feldvalidierung
 Formular und Feld-Überprüfung besteht aus drei Komponenten: ein Steuerelement, ein Symbol und eine QuickInfo. Verschiedene Typen von Steuerelementen können dies verwenden, wird ein Textfeld als Beispiel verwendet werden.

 ![Feldüberprüfung &#40;leere&#41;](../../extensibility/ux-guidelines/media/0905-01-fieldvalidation.png "0905-01_FieldValidation")

 Wenn das Feld erforderlich ist, dürfte das Wasserzeichen Text, der besagt  **\<erforderlichen >** und der Hintergrund des Felds muss ein Licht gelb (VSColor: `Environment.ControlEditRequiredBackground`) und der Vordergrund grau (VSColor: `Environment.ControlEditRequiredHintText`):

 ![Feldüberprüfung mit Beschriftung "Erforderlich"](../../extensibility/ux-guidelines/media/0905-02-fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Das Programm kann bestimmen, dass das Steuerelement in einem *ungültige Inhalte eingegeben* entweder wenn der Fokus auf ein anderes Steuerelement verschoben wird oder der Benutzer auf eine Schaltfläche "OK" Commit klickt, oder wenn der Benutzer das Dokument oder die Form speichert.

 Wenn Sie der ungültige Inhalt Status bestimmt wird, wird ein Symbol angezeigt, entweder innerhalb des Steuerelements oder einfach neben. Eine QuickInfo, die Beschreibung des Fehlers sollten bei einer mauszeigerbewegung über das Symbol oder das Steuerelement angezeigt werden. Darüber hinaus sollte ein 1-Pixel-Rahmen um das Steuerelement aufgeführt, die einen ungültigen Zustand erstellt.

 ![Layoutspezifikationen für feldvalidierung Feld](../../extensibility/ux-guidelines/media/0905-03-layoutspecs.png "0905-03_LayoutSpecs")

 **Layoutspezifikationen für feldvalidierung**

#### <a name="acceptable-variations-for-icon-location"></a>Zulässige Variationen für symbolplatzierung
 Es gibt unzählige besonderen Fällen, in denen Benutzer über Validierungsfehler informiert werden müssen. Wählen Sie unter Berücksichtigung der Steuerelementtyp vorliegt und die Konfiguration der Benutzeroberfläche die Symbol-Platzierung für Ihre Situation geeignet.

 ![Zulässige Positionen für symbolplatzierung](../../extensibility/ux-guidelines/media/0905-04-iconlocation.png "0905-04_IconLocation")

 **Zulässige Variationen für Feld Überprüfung Symbol Speicherorte**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validierung, erfordern einen Roundtrip zu einer Server- oder Netzwerk-Verbindung
 In einigen Fällen ein Roundtrip zum Server ist erforderlich, um den Inhalt zu verifizieren, und wäre es wichtig, um die Benutzer ausgeführt wird, überprüft, und die Fehlerzustände anzuzeigen. Die folgende Abbildung zeigt, ein Beispiel für diesen Fall und die empfohlenen-Benutzeroberfläche.

 ![Validierung mit Roundtrip zu einem Server](../../extensibility/ux-guidelines/media/0905-05-roundtrip.png "0905-05_RoundTrip")

 **Validierung mit Roundtrip zu einem server**

 Beachten Sie, dass ausreichend Speicherplatz auf der rechten Seite des Steuerelements bereitgestellt werden muss, damit die sich die "wird überprüft..." und dem Text "Wiederholen".

#### <a name="in-place-warning-text"></a>Direktes Warnungstext
 Wenn Platz verfügbar ist, platzieren Sie die Fehlermeldung in der Nähe des Steuerelements in einem Zustand des Fehlers verfügbar ist, ist dies besser als mit die QuickInfo, die allein.

 ![In&#45;platzieren Warnung](../../extensibility/ux-guidelines/media/0905-06-inplacewarning.png "0905-06_InPlaceWarning")

 **Direktes Warnungstext**

#### <a name="watermarks"></a>Wasserzeichen
 Manchmal ist eine gesamte Steuerelement oder das Fenster, in einem Fehlerzustand befindet. Verwenden Sie in diesem Fall ein Wasserzeichen den Fehler angibt.

 ![Watermark](../../extensibility/ux-guidelines/media/0905-07-watermark.png "0905-07_Watermark")

 **Feldvalidierung Wasserzeichen**
