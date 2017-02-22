---
title: "Benachrichtigungen und Fortschritt f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Benachrichtigungen und Fortschritt f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a> Benachrichtigungssysteme  
  
### <a name="overview"></a>Übersicht  
 Es gibt mehrere Möglichkeiten, den Benutzer zu informieren, was in Bezug auf ihre softwareentwicklungsaufgaben in Visual Studio geschieht.  
  
 Wenn die Benachrichtigung beliebigen Typs zu implementieren:  
  
-   **Halten Sie die Anzahl der Benachrichtigungen auf ein Minimum** effektiv Anzahl. Nachrichten sollten auf der Mehrzahl der Visual Studio-Benutzer oder Benutzer von einer bestimmten Funktion/Featurebereich anwenden. Übermäßiger Verwendung von Benachrichtigungen vom eigentlichen Thema abweichen des Benutzers oder wahrgenommene Bedienung des Systems abnehmen.  
  
-   **Stellen Sie sicher, klare, umsetzbare Nachrichten übergeben werden** dass der Benutzer den geeigneten Kontext für komplexere Entscheidungen und führt weitere Aktionen aufrufen kann.  
  
-   **Stellen Sie die synchrone und asynchrone Nachrichten entsprechend.** Synchrone Benachrichtigungen anzugeben, dass etwas Aufmerksamkeit benötigt, z. B. wenn ein Webdienst abstürzt oder einer Code-Ausnahme. Diese Situationen sofort in einer Weise, die die Eingabe z. B. in einem modalen Dialogfeld erfordert, sollte der Benutzer informiert werden. Asynchrone Benachrichtigungen sind diejenigen, die der Benutzer kennen sollte, aber nicht zu sofort reagieren erforderlich, z. B. wenn ein Buildvorgang abgeschlossen ist oder eine Website-Bereitstellung abgeschlossen ist. Diese Nachrichten sollten mehr Ambiente und Aufgabenverlauf des Benutzers nicht unterbrochen.  
  
-   **Verwenden Sie modale Dialogfelder, die nur bei Bedarf, um zu verhindern, dass den Benutzer führt weitere Aktionen** vor der Bestätigung der Nachricht oder eine Entscheidung im Dialogfeld angezeigt.  
  
-   **Entfernen Sie Ambiente-Benachrichtigungen, wenn sie nicht mehr gültig sind.** Erfordern Sie keine des Benutzers eine Benachrichtigung zu schließen, wenn sie bereits unternommen haben, Aktion aus, um das Problem zu beheben, die zu befassen.  
  
-   **Bedenken Sie, dass Benachrichtigungen zu false Korrelationen führen können.** Benutzer gehen davon aus, dass eine oder mehrere der Aktionen eine Benachrichtigung ausgelöst hat, wenn tatsächlich gab es keine kausale Beziehung. Deaktivieren in der Benachrichtigung über den Kontext, der Trigger und die Quelle der Benachrichtigung sein.  
  
### <a name="choosing-the-right-method"></a>Auswählen der richtigen Methode  
 Verwenden Sie diese Tabelle zur Unterstützung bei der Auswahl der richtigen Methode zur Benachrichtigung des Benutzers der Nachricht.  
  
|Methode|Verwendung|Verwenden Sie nicht|  
|------------|---------|----------------|  
|[Modale Meldung Fehlerdialoge](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Wird verwendet, wenn eine Antwort des Benutzers, bevor Sie fortfahren erforderlich ist.|Verwenden Sie nicht beim besteht keine Notwendigkeit des Benutzers und deren Fluss zu unterbrechen. Verwenden Sie modale Dialogfelder, ist es möglich, die Nachricht in eine andere, weniger intrusiv Weise anzuzeigen.|  
|[IDE-Statusleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Wird verwendet, wenn der Textinformationen in Bezug auf den Status eines Prozesses vorhanden ist.|Verwenden Sie nicht allein. Am besten verwendet in Verbindung mit einem anderen Feedbackmechanismus.|  
|[Eingebettete Infoleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Verwenden Sie in einem Toolfenster oder Dokumentfenster zum Fortschritt, Fehlerzustand, Ergebnisse und/oder verwertbare Informationen zu benachrichtigen.|Verwenden Sie nicht, wenn die Informationen nicht an den Speicherort relevant ist, wo die Infoleiste platziert werden.<br /><br /> Verwenden Sie nicht außerhalb eines Fensters Dokument-Tool.|  
|[Mauszeiger ändert sich](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Kann verwendet werden, zu benachrichtigen, dass ein Prozess vor sich geht. Auch verwendet, mitzuteilen, dass es eine Änderung in der Maus, z. B. bei Drag & Drop in Bearbeitung "oder", wird der Mauszeiger in einem bestimmten Modus, z. B. Zeichenmodus.|Verwenden Sie für kurze Status ändert sich nicht, oder der fluttering der Cursor wahrscheinlich (z. B. beim Teilen eines länger ausgeführten Prozesses statt für den gesamten Prozess gebunden) ist.|  
|[Statusanzeigen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Wird verwendet, wenn Sie den Fortschritt (bestimmte oder unbestimmt), müssen. Es gibt verschiedene Arten von Fortschrittsanzeigen und für jede Verwendung. Finden Sie unter [Status Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Visual Studio-benachrichtigunsfenster](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Im Benachrichtigungsfenster ist nicht öffentlich erweiterbar. Allerdings wird es verwendet einen Bereich von Nachrichten über Visual Studio, einschließlich kritische Probleme mit Ihrer Lizenz und die Information über Updates zu Visual Studio oder Pakete zu kommunizieren.|Verwenden Sie nicht für andere Arten von Benachrichtigungen.|  
|[Fehlerliste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Wenn das Problem direkt mit der Benutzer aktuell geöffneten Projektmappe mit einem Problem (Fehler/Warnung/Info) verbunden ist, müssen sie auf den Code ergreifen.<br /><br /> Dies wäre z. B. gehören:<br /><br /> -Compiler Nachrichten (Fehler/Warnung/Informationen)<br /><br /> -Code Analyzer/Diagnosedateien Nachrichten über code<br /><br /> -Erstellen von Nachrichten<br /><br /> Möglicherweise Probleme im Zusammenhang mit der Projektmappen- oder Projektdateien angemessen sein, aber zunächst sollten Sie eine Projektmappen-Explorer-Angabe.|Verwenden Sie für Elemente, die keinen Bezug zu den Code des Benutzers Projektmappe öffnen.|  
|Editor-Benachrichtigungen: Glühbirne|Verwenden, wenn ein Update verfügbar ist, ein Problem zu beheben, die in der geöffneten Datei vorhanden ist.<br /><br /> Beachten Sie, dass die Glühbirne auch verwendet werden soll, für das Hosten von schnellen Aktionen, die ausgeführt werden, auf den Code des Benutzers bei Bedarf, z. B. umgestaltungen, in diesem Fall werden jedoch nicht angezeigt "Benachrichtigung Style."|Verwenden Sie für Elemente, die keinen Bezug auf die geöffnete Datei.|  
|Editor-Benachrichtigungen: Wellenlinien|Verwenden Sie, um den Benutzer auf ein Problem mit einer bestimmten Spanne öffnen Code (z. B. eine rote Wellenlinie Fehler).|Verwenden Sie für Elemente, die nicht auf einen bestimmten Zeitraum Codeprobleme öffnen beziehen.|  
|[Eingebettete Statusleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Verwenden, um den Status im Zusammenhang mit Inhalt oder Prozess im Kontext eines bestimmten Toolfenster, Dokumentfenster oder Dialogfenster bereitzustellen.|Verwenden Sie nicht für allgemeine Produkt Benachrichtigungen, Prozessen oder Elemente, die keinen Bezug zu den Inhalt in das jeweilige Fenster.|  
|[Windows-Taskleiste-Benachrichtigungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Verwenden Sie, um Benachrichtigungen für die Out-of-Proc-Prozesse Oberfläche oder Begleit-Anwendung.|Verwenden Sie nicht für Benachrichtigungen, die in die IDE relevant sind.|  
|[Benachrichtigung Blasen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Verwenden, um einen Remoteprozess zu melden, oder ändern Sie **außerhalb** der IDE.|Verwenden Sie nicht als Mittel zur Benachrichtigung des Benutzers von Prozessen **in** der IDE.|  
  
### <a name="notification-methods"></a>Benachrichtigungsmethoden  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Modale Meldung Fehlerdialoge  
 Ein modales Fehlerdialogfeld wird verwendet, eine Fehlermeldung angezeigt, die Bestätigung oder eine Aktion des Benutzers erfordert.  
  
 ![Modale Fehlermeldung](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")  
  
 **Ein modales Fehlerdialogfeld warnen der Benutzer eine ungültige Verbindungszeichenfolge zu einer Datenbank**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> IDE-Statusleiste  
 Die Wahrscheinlichkeit, dass Benutzer Statusleistentext beachten korreliert auf ihre Erfahrung mit Bestrebens von Computern und bestimmte Erfahrung mit der Windows-Plattform. Die Kunden von Visual Studio ist in beiden Bereichen erfahrene jedoch sogar erfahrene Windows-Benutzer Änderungen in der Statusleiste übersehen werden könnten. Daher wird die Statusleiste am besten für Informationszwecke oder redundante Stichwort verwendet Informationen an anderer Stelle vorgestellt. Jede Art von wichtige Informationen, den der Benutzer sofort behoben werden muss, sollten in einem Dialogfeld oder im Toolfenster Benachrichtigungen bereitgestellt werden.  
  
 Die Visual Studio-Statusleiste soll für verschiedene Arten von Informationen angezeigt werden können. Er ist Feedback, Designer, Statusanzeige, Animation und Client-Regionen aufgeteilt.  
  
 Die Feedback-Region sowie die Designer-Bereich sind immer sichtbar. Die Statusanzeige und Animation Bereiche sind immer dynamische und basierend auf dem Benutzerkontext. Der Designerbereich verfügt über eine statische Breite bestimmt durch die Länge der Zeichenfolge, die aus einer begleitende Ressource für die Nachricht abgerufen wird. Dies ermöglicht die Lokalisierung in die Breite ändern, ohne dass der Code geändert. Für Englisch ist die Breite dieser Zeichenfolge ungefähr 220 Pixel. Der Designerbereich normal verhält, und der Feedback-Bereich wird den verbleibenden Speicherplatz aufnehmen.  
  
 Die Statusleiste wird auch farbig hervorgehoben, um die visuelle Wirkung und funktionale Wert hinzufügen, indem Sie die Kommunikation zwischen verschiedenen IDE Zustand ändert, z. B. wenn die IDE im Debugmodus befindet.  
  
 ![Farbänderungen für IDE-Statusleiste](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")  
  
 **IDE der Farben der Statusleiste**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Eingebettete Infoleiste  
 Infoleiste kann am oberen Rand einer Dokument- oder Toolfenster verwendet werden, die Benutzer über einen Status oder Zustand informieren. Sie können Befehle auch anbieten, so, dass der Benutzer eine Möglichkeit, um Maßnahmen zu ergreifen kann. Infoleiste ist ein standard-Shell-Steuerelement. Erstellen Sie keine eigene, agiert und nicht mit anderen in der IDE angezeigt. Finden Sie unter [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) Implementierungsdetails und Anleitungen.  
  
 ![Eingebettete Infoleiste](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")  
  
 **Infoleiste eingebettet in einem Dokumentfenster warnen der Benutzer, den die IDE im Debugmodus Verlaufsdaten und Editor reagiert nicht auf die gleiche Weise wie im standard-Debug-Modus.**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Mauszeiger ändert sich  
 Wenn Sie den Cursor zu ändern, verwenden Sie die Farben, die an den Dienst VSColor gebunden werden und sind bereits mit dem Cursor zugeordnet. Cursor geändert für, der angibt, einer laufenden Operation verwendet werden können, als auch erreicht Zonen, in denen der Benutzer über ein Ziel, die gezogen bewegt wird, abgelegt oder zum Auswählen eines Objekts verwendet werden können.  
  
 Verwenden Sie den Mauszeiger gebucht/warten, nur, wenn die gesamte verfügbare CPU-Zeit für einen Vorgang, der verhindert, dass des Benutzers weitere Eingabe Ausdrücken reserviert werden muss. In den meisten Fällen gut geschriebene Programme, die Verwendung von multithreading sollte selten Mal, wenn Benutzer keine andere Operationen durchzuführen.  
  
 Bedenken Sie, dass Cursor verändert sich nützlich sind, wie redundanter Cue Informationen an anderer Stelle angezeigt. Verlassen Sie sich nicht auf eine Änderung der Cursor als einzige Möglichkeit der Kommunikation mit dem Benutzer, insbesondere, wenn Sie versuchen, etwas zu vermitteln, die wichtig ist, dass der Benutzer zu berücksichtigen.  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Statusanzeigen  
 Statusanzeigen sind wichtig für das Bereitstellen von des Benutzerfeedback während der Prozesse, die mehr als ein paar Sekunden dauern. Statusanzeigen angezeigt werden direkte (in der Nähe der Startpunkt der Aktion in Bearbeitung), in eine eingebettete Statusleiste, in ein modales Dialogfeld oder in der Statusleiste von Visual Studio. Befolgen Sie die Anleitung im [Status Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) im Hinblick auf ihre Verwendung und Implementierung.  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio-benachrichtigunsfenster  
 Im Visual Studio-Benachrichtigungsfenster benachrichtigt Entwickler zur Lizenzierung, Umgebung (Visual Studio), Erweiterungen und Updates. Benutzer können einzelne Benachrichtigungen verwerfen oder die Möglichkeit, bestimmte Arten von Benachrichtigungen zu ignorieren. Die Liste der ignorierten Benachrichtigungen erfolgt einem **Tools > Optionen** Seite.  
  
 Im Benachrichtigungsfenster ist nicht aktuell erweiterbar.  
  
 ![Visual Studio-Benachrichtigunsfenster](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")  
  
 **Visual Studio-Benachrichtigungen Toolfenster**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a> Fehlerliste  
 Eine Benachrichtigung in der Fehlerliste geben Fehler und Warnungen, die aufgetreten ist, während der Kompilierung und Buildprozess und ermöglicht es dem Benutzer zum Navigieren in Code zu diesem bestimmten Code-Fehler.  
  
 ![Fehlerliste](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")  
  
 **Die Fehlerliste in Visual Studio**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Eingebettete Statusleisten  
 Da IDE-Statusleiste dynamisch mit Client Regionskontext auf das aktive Fenster und die Informationen, die auf dem Kontext des Benutzers und/oder Systemantworten aktualisieren festgelegt ist, ist es schwierig, eine kontinuierliche Anzeige von Informationen zu verwalten, oder gewähren Status für langfristige asynchroner Prozesse. IDE-Statusleiste ist z. B. nicht für Benachrichtigungen der Testergebnisse für mehrere Testläufe und/oder sofort nutzbare Elemente. Es ist wichtig, solche Statusinformationen im Kontext des Fensters Dokument oder Tool beibehalten werden soll, in dem der Benutzer trifft eine Auswahl oder startet einen Prozess.  
  
 ![Eingebettete Statusleiste](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")  
  
 **Eingebettete Statusleiste in Visual Studio**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Windows-Taskleiste-Benachrichtigungen  
 Die Windows-Benachrichtigungsbereich neben das System ist Uhr in der Taskleiste. Viele Hilfsprogramme und Software-Komponenten bieten Symbole in diesem Bereich, damit der Benutzer ein Kontextmenü systemweite Aufgaben, wie die Auflösung ändern oder Abrufen von Softwareupdates abrufen kann.  
  
 Auf Umgebungsebene Benachrichtigungen sollte auf dem Visual Studio-Benachrichtigungen-Hub nicht Windows-Benachrichtigungsbereich angezeigt werden.  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Benachrichtigung Blasen  
 Benachrichtigung Blasen können dient ausschließlich zu Informationszwecken in eine Editor-Designer oder als Teil des Windows-Benachrichtigungsbereich angezeigt werden. Der Benutzer arbeitet diese Blasen als Probleme, die sie später auflösen können also einen Vorteil für nicht kritische Benachrichtigungen. Blasen sind nicht geeignet, um wichtige Informationen, den der Benutzer sofort lösen muss. Wenn Sie Notification Blasen in Visual Studio verwenden, führen Sie die [Windows-Desktop-Anleitung für die Benachrichtigung Blasen](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Benachrichtigungssprechblase](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")  
  
 **Benachrichtigungssprechblase im Windows-Benachrichtigungsbereich verwendet für Visual Studio**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Statusanzeigen  
  
### <a name="overview"></a>Übersicht  
 Statusanzeigen sind ein wichtiger Teil ein Benachrichtigungssystem gibt das Benutzerfeedback. Sie können dem Benutzer mitteilen, wenn die Prozesse und Vorgänge abgeschlossen werden. Vertraute Indikatortypen gehören Statusanzeigen, rotierende Cursor und animierte Symbole. Der Typ und die Platzierung einer Statusanzeige, hängt davon ab, den Kontext, einschließlich was gemeldet wird und wie lange der Prozess oder einen Vorgang bis zum Abschluss.  
  
#### <a name="factors"></a>Faktoren  
 Um zu bestimmen, welche Indikatortyp geeignet ist, müssen Sie die folgenden Faktoren bestimmen.  
  
1.  **Zeitliche Steuerung:** Zeitdauer der Vorgang dauert  
  
2.  **Modalität:** Gibt an, ob der Vorgang ist modal, in der Umgebung (Sperren der Benutzeroberfläche, bis der Vorgang abgeschlossen ist)  
  
3.  **Persistent/vorübergehend:** ob das Endergebnis des Fortschritts muss zu einem späteren Zeitpunkt gemeldeten und/oder angezeigt werden  
  
4.  **Bestimmte/unbestimmt:** Gibt an, ob die Endzeit des Vorgangs und den Fortschritt berechnet werden können  
  
5.  **Grafik/Textual Speicherort:** ob der Status oder Prozess erfassten Inline im Hauptteil einer Nachricht oder ein bestimmtes Steuerelement, z. B. das Strukturansicht-Steuerelement ist  
  
6.  **NEAR:** ob der Status in der Nähe der Benutzeroberfläche sein soll, die mit verknüpft ist. (Beispielsweise kann es sein, in der Statusleiste, die weit entfernt werden kann, oder in der Nähe der Schaltfläche ist, die der Prozess gestartet haben?)  
  
#### <a name="determinate-progress"></a>Bestimmte Status  
  
|Status-Typ|Wann und wie Sie|Notizen|  
|-------------------|-------------------------|-----------|  
|Statusanzeige (bestimmte)|Dauer erwartet > 5 Sekunden.<br /><br /> Sind die Beschreibung des Prozessdetails.|**Nicht** Einbetten von Text in der Animation.|  
|Infoleiste|Messaging mit kontextbezogenen Benutzeroberfläche verknüpft. Finden Sie unter [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Sind die Beschreibung des Prozessdetails.|**Nicht** mehrere Infobars verwenden, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Statusanzeigen.|  
|Ausgabefenster|Vorübergehende Benachrichtigung: Prozess der app-Ebene dieser Benutzer möchten **überprüfen** Details nach Abschluss des Vorgangs.|**Keine** verwenden, wenn der Benutzer später auf Daten verweisen muss.|  
|Protokolldatei|Zusammen mit intransient Benachrichtigung in Fällen, wenn es wichtig ist, **Speichern** Details nach Abschluss des Vorgangs.||  
|Statusleiste|Vorübergehende Benachrichtigung: app-Ebene dieser Benutzer wird **nicht** Details nach Abschluss des Vorgangs.<br /><br /> Enthält eine eingebettete Statusleiste.<br /><br /> Sind die Beschreibung des Prozessdetails.||  
  
#### <a name="indeterminate-progress"></a>Einen unbestimmten Status  
  
|Status-Typ|Wann und wie Sie|Notizen|  
|-------------------|-------------------------|-----------|  
|Statusanzeige (unbestimmt)|Dauer erwartet > 5 Sekunden.<br /><br /> Sind die Beschreibung des Prozessdetails.|**Nicht** Einbetten von Text in der Animation.|  
|ANTS (animierte horizontale Punkte)|Roundtrip zum Server.<br /><br /> Platziert nahe Punkt des Kontexts am oberen Rand der übergeordneten Container.|**Keine** verwenden, wenn nicht gesamte Container untergeordnet.|  
|Drehfeld (Fortschritt Ring)|Der Prozess zugeordnet sind kontextbezogene UI oder, in denen Speicherplatz zu berücksichtigen ist.<br /><br /> Sind die Beschreibung des Prozessdetails.||  
|Infoleiste|Messaging mit kontextbezogenen Benutzeroberfläche verknüpft. Finden Sie unter [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nicht** mehrere Infobars verwenden, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Statusanzeigen.|  
|Ausgabefenster|Vorübergehende Benachrichtigung: Prozess der app-Ebene dieser Benutzer möchten **überprüfen** Details nach Abschluss des Vorgangs.|**Nicht** finden Sie Informationen, die sitzungsübergreifend beibehalten werden soll.|  
|Protokolldatei|Zusammen mit intransient Benachrichtigung in Fällen, wenn es wichtig ist, **Speichern** Details nach Abschluss des Vorgangs.||  
|Statusleiste|Vorübergehende Benachrichtigung: app-Ebene dieser Benutzer wird **nicht** Details nach Abschluss des Vorgangs.<br /><br /> Enthält eingebettete Statusleiste.<br /><br /> Sind die Beschreibung des Prozessdetails.||  
  
### <a name="progress-indicator-types"></a>Arten von Fortschrittsanzeigen  
  
#### <a name="progress-bars"></a>Statusanzeigen  
  
##### <a name="indeterminate"></a>Unbestimmt  
 ![Unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")  
  
 **Unbestimmte Fortschrittsleiste**  
  
 "Unbestimmt" bedeutet, dass der allgemeinen Status eines Vorgangs oder Prozess kann nicht bestimmt werden. Unbestimmt Statusanzeigen für Vorgänge, die eine unbegrenzte Zeit erfordern oder auf eine unbekannte Anzahl von Objekten zugreifen. Verwenden Sie eine Beschreibung zur Ergänzung, was passiert. Verwenden Sie Timeouts zeitbasierten Operationen Grenzen zugewiesen. Verwenden Sie Animationen unbestimmt Statusanzeigen wird angezeigt, dass ausgeführt wird, aber keine anderen Informationen bieten. Wählen Sie keine unbestimmte Fortschrittsleiste basierend auf den Mangel an Genauigkeit allein möglich.  
  
##### <a name="determinate"></a>Bestimmte  
 ![Festgelegte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")  
  
 **Fortschrittsleiste**  
  
 "Bestimmte" bedeutet, dass ein Vorgang oder Prozess eine begrenzte Menge an Zeit erfordert, selbst wenn diese Zeitspanne nicht genau vorhergesagt werden kann. Geben Sie deutlich Beendigung. Lassen Sie keine Statusanzeige 100 Prozent wechseln, wenn der Vorgang abgeschlossen wurde. Bestimmte Leiste Statusanimation verschiebt links-nach-rechts zwischen 0 und 100 %.  
  
 Verschieben Sie nie die Statusanzeige, die während eines Vorgangs rückwärts. Die Leiste sollten vorwärts stetig zu Beginn des Vorgangs und 100 % zu erreichen, wenn diese endet. Die Statusanzeige ist, dem Benutzern eine Vorstellung davon, wie lange der gesamte Vorgang dauert unabhängig davon, wie viele Schritte beteiligt sind.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Gleichzeitige reporting (Statusanzeigen gestapelt)  
 Wenn ein Vorgang sehr lange dauert – möglicherweise mehrere Minuten – dann zwei Statusanzeigen verwendet werden können, zeigt einen, der Gesamtstatus für einen Vorgang und ein weiteres für den Fortschritt des aktuellen Schritts. Z. B. wenn ein Setupprogramm, das viele Dateien kopiert werden, kann eine Statusanzeige verwendet werden um anzugeben, wie lange der gesamte Prozess dauert, während eine zweite, wie viel Prozent der aktuellen Datei angeben kann oder Verzeichnis kopiert werden. Mehr als fünf gleichzeitige Vorgänge oder Prozesse, die mit gestapelten Statusanzeigen nicht gemeldet werden. Wenn Sie mehr als fünf gleichzeitige Vorgänge oder Prozesse Bericht haben, verwenden Sie einem modalen Dialogfeld mit einer Schaltfläche "Abbrechen" und der Bericht die Statusdetails an das Ausgabefenster.  
  
##### <a name="textual-descriptions"></a>Diese textbeschreibungen  
 Verwenden Sie eine Beschreibung zur Ergänzung, was passiert ist und die geschätzte Zeit bis zum Abschluss. Ist es unmöglich, festzustellen, wie lange ein Vorgang dauern wird, möglicherweise die bessere Wahl für das Bereitstellen von Feedback animierte Symbol anstatt eine Statusanzeige sein.  
  
 Visual Studio bietet eine standard-Statusanzeige in der Statusleiste angezeigt, die von Produkten in Visual Studio integriert verwendet werden kann. Text eine Beschreibung, was geschieht, während die Statusanzeige animiert wird kann der Text in der Statusleiste aktualisiert werden.  
  
#### <a name="other-progress-indicators"></a>Andere Statusanzeigen  
  
##### <a name="ants-animated-horizontal-dots"></a>ANTS (animierte horizontale Punkte)  
 ![Ant-Elemente zum Fortschritt](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")  
  
 "Ameisen," animierte horizontale Einheiten bieten eine visuelle Darstellung für einen unbestimmten Round-Trip Serverprozess.  
  
##### <a name="spinner-progress-ring"></a>Drehfeld (Fortschritt Ring)  
 ![Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")  
  
 Das Drehfeld (auch bekannt als ein "Fortschritt-Ring") ist eine unbestimmte Statusanzeige in erster Linie in Bezug auf die kontextbezogene Benutzeroberfläche verwendet. Zeigen Sie ein Drehfeld, in der Nähe der verwandte Inhalte, z. B. Text Kategorieheaders, messaging oder Steuerelement.  
  
##### <a name="cursor-feedback"></a>Cursor-feedback  
 Geben Sie für Vorgänge, die zwischen 2 bis 7 Sekunden dauern, Cursors. In der Regel bedeutet dies mithilfe des Wartecursors, die vom Betriebssystem bereitgestellt werden. Hinweise finden Sie im MSDN-Artikel [Cursors.Wait Eigenschaft](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Fortschritt Indikator Speicherorte  
  
##### <a name="status-bar"></a>Statusleiste  
 Die Statusleiste erhält die Anwendung zur Anzeige Nachrichten und nützliche Informationen für den Benutzer ohne Unterbrechung der Arbeit des Benutzers. In der Regel am unteren Rand eines Fensters angezeigt wird, wird Status zum Status einen Tipp Toolbereich sein, eine Nachricht über das Maß für Fortschritt in Kombination mit einem Fortschrittsbalken.  
  
 ![Statusleiste mit Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")  
  
 **Statusleiste mit Fortschrittsleiste**  
  
 ![Statusleiste mit Meldungen](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")  
  
 **Statusleiste mit Beschreibung**  
  
##### <a name="infobar"></a>Infoleiste  
 Ähnlich wie in der Statusleiste der Informationsleiste zur Verfügung stellt kontextbezogene Benachrichtigung und messaging, auch mit unbestimmten Statusanzeigen wie die Statusanzeige oder das Drehfeld kombiniert werden können. Die Infoleiste sollte nicht präzise Ebene ausgeführt werden oder auf bestimmte Fortschritt Angabe bereitstellen. Finden Sie unter [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Infoleiste mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")  
  
 **Infoleiste mit Fortschrittsanzeige und Beschreibung**  
  
 ![Infoleiste in einem Fenster](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")  
  
 **Infoleiste in das Fenster für die Codeanalyse**  
  
##### <a name="inline"></a>Inline  
 Inline-Status-Angabe kann durch den Fortschritt Loader-Typen dargestellt werden. In der Regel wird die Statusanzeige mit messaging paarweise, aber dies ist nicht erforderlich.  
  
 ![Inline-Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")  
  
 **Drehfeld in Kombination mit der Beschreibung**  
  
 ![Gestapelte Inline-Fortschrittsleisten](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")  
  
 **Bestimmte gestapelte Statusanzeigen**  
  
 ![Inline-Fortschrittsmeldungen](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")  
  
 **Server-Explorer-Inline-Text: aktualisieren...**  
  
##### <a name="tool-windows"></a>Toolfenster  
 Angabe des globalen Status wird durch eine unbestimmte Fortschrittsleiste direkt unter der Symbolleiste positioniert dargestellt.  
  
 ![Globale unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")  
  
 **Team Explorer globale unbestimmte Fortschrittsleiste**  
  
##### <a name="dialogs"></a>Dialogfelder  
 Dialoge können den Fortschritt Ladeprogramm Typen enthalten. Statusanzeigen können werden zusammen mit messaging als auch in Kombination mit mehreren Ebenen Fortschritt Angabe darstellen, die präzise oder Sub-Prozesse.  
  
 ![Dialogfeld mit mehreren Arten von Fortschrittsanzeigen](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")  
  
 **Visual Studio-Dialogfeld mit gleichzeitiger Prozesse und mehreren Arten von Fortschrittsanzeigen**  
  
 ![Dialogfeld mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")  
  
 **Visual Studio-Dialogfeld mit Fortschrittsanzeige und Meldungen Inline-Befehle**  
  
##### <a name="document-well"></a>Dokumentieren Sie gut  
 Das Dokument kann auch mehreren Arten von Ladeprogramm in Kombination mit Steuerelementen angezeigt.  
  
 ![Fortschrittsmeldungen in Dokument](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")  
  
 **Unbestimmte Fortschrittsleiste unter Symbolleiste**  
  
##### <a name="output-window"></a>Ausgabefenster  
 Das Fenster Ausgabe eignet sich für die Verarbeitung Prozess Fortschritt und Status der Fortschritt über Inline Text messaging. Sie sollten die Statusleiste zusammen mit jeder Ausgabe Fenster Fortschrittsberichterstattung verwenden.  
  
 ![Fortschrittsmeldungen in Ausgabefenster](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")  
  
 **Ausgabefenster mit fortlaufender Prozessstatus, und warten Sie messaging**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a> InfoBars  
  
### <a name="overview"></a>Übersicht  
 InfoBars weisen Sie dem Benutzer einen Indikator nahe dem Zeitpunkt der Aufmerksamkeit und mithilfe der freigegebenen Infoleisten-Steuerelement gewährleistet die Konsistenz in Aussehen und Interaktion.  
  
 ![Infoleiste](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **InfoBars in Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Verwendungsmöglichkeiten für eine Infoleiste  
  
-   Um dem Benutzer eine Nachricht nicht blockierend jedoch wichtige relevant für den aktuellen Kontext  
  
-   Um anzugeben, dass die Benutzeroberfläche in einem bestimmten Status oder Zustand haben einige Interaktion folgen, z. B. verlaufsbezogenes debugging  
  
-   Um den Benutzer zu informieren, dass das System Probleme erkannt hat, z. B. wenn eine Erweiterung Leistungsprobleme verursacht  
  
-   Um Benutzern eine Möglichkeit, einfaches ergreifen von Maßnahmen, z. B. wenn der Editor erkennt, dass eine Datei Tabstopps und gemischte aufweist  
  
##### <a name="do"></a>Führen Sie aus:  
  
-   Halten Sie den Meldungstext Infoleiste kurz und präzise.  
  
-   Halten Sie den Text auf Links und Schaltflächen kompakt.  
  
-   Sicherstellen Sie, dass die "Aktion"-Optionen, die Sie Benutzern bereitstellen minimal, nur die erforderliche Aktionen angezeigt.  
  
##### <a name="dont"></a>Tue nicht:  
  
-   Verwenden Sie eine Infoleiste Standardbefehle anzubieten, die in einer Symbolleiste platziert werden soll.  
  
-   Verwenden Sie eine Infoleiste anstelle ein modales Dialogfeld an.  
  
-   Erstellen einer Gleitkommazahlen Nachricht außerhalb eines Fensters.  
  
-   Verwenden Sie mehrere Infobars an verschiedenen Speicherorten in demselben Fenster an.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Werden mehrere Infobars können gleichzeitig angezeigt?  
 Ja, können mehrere Infobars gleichzeitig anzeigen. Sie werden in der Reihenfolge erste Anfrage und zuerst eingegangene mit der ersten Infoleiste anzeigen auf oben und zusätzliche Infobars anzeigen unten angezeigt werden.  
  
 Der Benutzer sieht maximal drei Infobars zu einem Zeitpunkt nach, die weitere Infobars verfügbar ist, sind die Infoleiste Region bildlauffähigen werden wird.  
  
### <a name="creating-an-infobar"></a>Erstellen eine Infoleiste  
 Infoleiste enthält vier Abschnitte, von links nach rechts:  
  
-   **Symbol:** Dies ist, fügen Sie ein Symbol für die Infoleiste, wie z. B. ein Warnsymbol angezeigt werden soll.  
  
-   **Text:** Sie können Text, der den Benutzer Szenario/Situation beschrieben wird, zusammen mit Links innerhalb des Texts bei Bedarf hinzufügen. Denken Sie daran, den Text kompakt zu halten.  
  
-   **Aktionen:** Links und Schaltflächen für Aktionen, die der Benutzer die Nachricht ausführen kann, sollte in diesem Abschnitt enthalten.  
  
-   **Schaltfläche "Schließen":** im letzten Abschnitt rechts haben eine Schaltfläche "Schließen".  
  
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
  
 Hier ist ein Beispiel, eine InfoBarModel mit Text, einen Hyperlink, interaktive Schaltfläche und ein Symbol erstellt.  
  
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
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Erstellen eine standardmäßige Infoleiste in systemeigenem code  
 Implementieren Sie die IVsInfoBar-Schnittstelle, um eine Infoleiste von systemeigenem Code bereitstellen.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Abrufen von UIElement Infoleiste aus Infoleiste  
 Die InfoBarModel oder IVsInfoBar-Implementierung sind Datenmodelle, die in "UIElement" umgewandelt werden müssen, um in der Benutzeroberfläche angezeigt werden. "UIElement" kann mit dem SVsInfoBarUIFactory/IVsInfoBarUIFactory-Dienst abgerufen werden.  
  
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
 InfoBars können in einem oder mehreren der folgenden Orte angezeigt werden:  
  
-   Toolfenster  
  
-   Innerhalb einer Registerkarte "Dokument"  
  
> [!IMPORTANT]
>  Es ist möglich, eine Infoleiste erhalten eine Meldung über den globalen Kontext zu positionieren. Dies scheint zwischen Symbolleisten und das Dokument auch. Dies wird nicht empfohlen, da sie zu Problemen mit "wechseln und ruck" führt der IDE und sollte vermieden werden, es sei denn, dies absolut notwendig und zweckmäßig.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Infoleiste platzieren in einem ToolWindowPane  
 Die ToolWindowPane.AddInfoBar(IVsInfoBar)-Methode kann verwendet werden, ein Toolfenster Infoleiste hinzu. Diese API kann entweder ein IVsInfoBar (welche InfoBarModel ist eine Standardimplementierung), hinzufügen oder eine IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Infoleiste platzieren in einem Dokument oder nicht ToolWindowPane  
 Um eine Infoleiste in jeder IVsWindowFrame einzufügen, verwenden Sie die VSFPROPID_InfoBarHost-Eigenschaft zum Abrufen der IVsInfoBarHost für den Rahmen, und fügen Sie dann die Infoleiste "UIElement".  
  
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
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Platzieren eine Infoleiste im Hauptfenster  
 Um eine Infoleiste im Hauptfenster zu platzieren, verwenden Sie die VSSPROPID_MainWindowInfoBarHost des IVsShell-Diensts, um das Hauptfenster IVsInfoBarHost zu erhalten, und fügen Sie dann die Infoleiste "UIElement" hinzu.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Weiß ich, wenn der Benutzer in meiner Infoleiste Aktion ausführt?  
 Ja, werden wir jede Ereignisaktion an den Autor Infoleiste zurück. Er ist Autor der Infoleiste in der IDE auf Grundlage der Benutzerauswahl in der Infoleiste Maßnahmen ergreifen. InfoBars automatisch vom Host, dessen Schaltfläche "Schließen" geklickt wurde, entfernt, aber zusätzliche Schritte sind erforderlich, wenn schließen Sie andere Infobars müssen nach dem entfernt werden. Telemetriedaten müssen auch unabhängig von jeder Infoleiste protokolliert werden.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Empfangen von Ereignissen Infoleiste in einem ToolWindowPane  
 ToolWindowPane verfügt über zwei Ereignisse für Infobars. Das InfoBarClosed-Ereignis wird ausgelöst, wenn eine Infoleiste in die ToolWindowPane geschlossen wird. Das InfoBarActionItemClicked-Ereignis wird ausgelöst, wenn auf einen Link oder eine Schaltfläche in der Infoleiste geklickt wird.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Infoleiste Ereignisse direkt von der UIElement empfangen  
 IVsInfoBarUIElement.Advise kann verwendet werden, direkt aus einer Infoleiste UIElement, Ereignisse zu abonnieren. Implementieren von IVsInfoBarUIEvents ermöglichen den Autor zum Schließen empfangen, und klicken Sie auf Ereignisse.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a> Fehler-Überprüfung  
 Wenn ein Benutzer Informationen, der nicht akzeptabel ist eingibt, z. B. wenn ein erforderliches Feld ausgelassen wird oder wenn Daten im falschen Format eingegeben werden, ist es besser, Feedback neben dem Steuerelement, statt ein blockierender Fehler Dialogfenster oder Validierung von Steuerelementen verwenden.  
  
### <a name="field-validation"></a>Überprüfung  
 Formular und Feld Überprüfung besteht aus drei Komponenten: ein Steuerelement, ein Symbol und eine QuickInfo. Mehrere Typen von Steuerelementen können dies verwenden, wird ein Textfeld, das als Beispiel verwendet werden.  
  
 ![Überprüfung &#40; leer &#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")  
  
 Wenn das Feld erforderlich ist, dürfte das Wasserzeichen Text, der besagt **\< erforderlich>** Feld Hintergrund sollte auch Licht gelb (VSColor: `Environment.ControlEditRequiredBackground`) und der Vordergrund sollte grau (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Feldvalidierung mit Beschriftung „Erforderlich“](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")  
  
 Das Programm kann feststellen, dass das Steuerelement in einen Zustand der *ungültige Inhalte eingegeben* entweder, wenn der Fokus auf ein anderes Steuerelement verschoben wird oder der Benutzer auf eine Schaltfläche "OK" Commit klickt oder wenn der Benutzer das Dokument oder Formular speichert.  
  
 Wenn der Inhalt ungültig ermittelt wird, wird ein Symbol innerhalb des Steuerelements oder direkt neben. Eine Beschreibung des Fehlers QuickInfo sollte Daraufzeigen des Symbols oder das Steuerelement angezeigt werden. Darüber hinaus sollte ein 1-Pixel-Rahmen um das Steuerelement angezeigt, das einen ungültigen Zustand erstellt.  
  
 ![Layoutspezifikationen für Feldvalidierung](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")  
  
 **Layoutspezifikationen für feldüberprüfung**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Akzeptable Varianten für den Symbolspeicherort  
 Es gibt unzählige eindeutige Fälle, in denen Benutzer über Validierungsfehler informiert werden müssen. Wählen Sie unter Berücksichtigung der Steuerelementtyp und die Konfiguration der Benutzeroberfläche die Symbol-Platzierung für Ihre Situation geeignet.  
  
 ![Zulässige Positionen für Symbolplatzierung](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")  
  
 **Akzeptable Varianten für Außenstellen Überprüfung-Symbol**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Überprüfung, erfordern einen Roundtrip zu einer Verbindung zum Server oder Netzwerk  
 In einigen Fällen ein Roundtrip zum Server ist erforderlich, um den Inhalt zu überprüfen, und wäre es wichtig, den Status der User, überprüft, und Fehlerzustände angezeigt. Die folgende Abbildung zeigt ein Beispiel für diesen Fall und die empfohlenen Benutzeroberfläche.  
  
 ![Validierung mit Roundtrip zu einem Server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")  
  
 **Überprüfung mit Roundtrip zu einem server**  
  
 Beachten Sie, dass ausreichend Speicherplatz auf der rechten Seite des Steuerelements bereitgestellt werden muss, um eine "Überprüfung..." und den Text "Wiederholen".  
  
#### <a name="in-place-warning-text"></a>Direkte Warnung  
 Platz für die Fehlermeldung nahe des Steuerelements in einen Fehler versetzen vorhanden ist, ist dies wünschenswert, die QuickInfo, die allein verwenden.  
  
 ![In &#45; direkte Warnung](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")  
  
 **Direkte Warnung**  
  
#### <a name="watermarks"></a>Wasserzeichen  
 Manchmal ist eine gesamte Steuerelement oder Fenster in einem Fehlerzustand befindet. Verwenden Sie in diesem Fall ein Wasserzeichen den Fehler angibt.  
  
 ![Wasserzeichen](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **Wasserzeichen Überprüfung**