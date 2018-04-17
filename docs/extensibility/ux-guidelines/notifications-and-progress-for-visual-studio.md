---
title: Benachrichtigungen und Fortschritt für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 237ed5c382a6ac880b0be59165a33ad338370976
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="notifications-and-progress-for-visual-studio"></a>Benachrichtigungen und Fortschritt für Visual Studio
##  <a name="BKMK_NotificationSystems"></a> Benachrichtigungssystemen  
  
### <a name="overview"></a>Übersicht  
 Es gibt mehrere Möglichkeiten, um den Benutzer zu informieren, was geschieht in Visual Studio hinsichtlich ihrer Software-Entwicklungsaufgaben.  
  
 Wenn die Benachrichtigung beliebigen Typs zu implementieren:  
  
-   **Die Anzahl der Benachrichtigungen auf ein Minimum halten** effektive Anzahl. Benachrichtigungsmeldungen sollte auf der Mehrzahl der Visual Studio-Benutzer oder Benutzer, der eine bestimmte Funktion/Funktionsbereich angewendet. Eine übermäßige Verwendung von Benachrichtigungen vom eigentlichen Thema abweichen des Benutzers oder herabstufen wahrgenommene Vereinfachung der Nutzung des Systems.  
  
-   **Stellen Sie sicher, Sie deaktivieren, ausführbare Nachrichten Kundennamen** , dass der Benutzer verwendet werden kann, um den geeigneten Kontext für komplexere entscheiden und führt weitere Aktionen aufrufen.  
  
-   **Stellen Sie die synchrone und asynchrone Nachrichten entsprechend.** Synchrone Benachrichtigungen anzugeben, dass etwas sofortigen Aufmerksamkeit benötigt, z. B. wenn ein Webdienst stürzt ab, oder mit einem Code-Ausnahme. Diese Situationen sofort in einer Weise, die Eingaben, z. B. in ein modales Dialogfeld erfordert, sollte der Benutzer informiert werden. Asynchrone Benachrichtigungen sind Argumente, die der Benutzer kennen sollte, jedoch nicht auf sofort reagieren erforderlich, z. B. wenn ein Buildvorgang abgeschlossen ist oder eine Website-Bereitstellung abgeschlossen ist. Diese Nachrichten sollte mehr ambient und Aufgabenverlauf des Benutzers nicht unterbrochen.  
  
-   **Verwenden Sie modale Dialogfelder, die nur bei Bedarf, um zu verhindern, dass den Benutzer führt weitere Aktionen** vor Bestätigung der Nachricht oder eine Entscheidung im Dialogfeld angezeigt.  
  
-   **Entfernen Sie Ambiente-Benachrichtigungen, wenn sie nicht mehr gültig sind.** Den Benutzer eine Benachrichtigung zu schließen, wenn sie bereits haben Aktion aus, um das Problem zu behandeln, dem sie informiert wurden ist nicht erforderlich.  
  
-   **Denken Sie daran, dass Benachrichtigungen zu "false" Korrelationen führen können.** Benutzer gehen davon aus, dass eine oder mehrere der dazugehörigen Aktionen eine Benachrichtigung ausgelöst werden, hat wenn tatsächlich gab es keine kausale Beziehung. Deaktivieren in der Benachrichtigung über den Kontext, der Trigger und die Quelle der Benachrichtigung sein.  
  
### <a name="choosing-the-right-method"></a>Auswählen der richtigen Methode  
 Verwenden Sie diese Tabelle, die Sie bei der Wahl der richtigen Methode zum Benachrichtigen des Benutzers Ihrer Nachricht unterstützen.  
  
|Methode|Mit|Verwenden Sie keine|  
|------------|---------|----------------|  
|[Modale Meldung Fehlerdialogfelder](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Wird verwendet, wenn eine Antwort des Benutzers, bevor Sie fortfahren erforderlich ist.|Verwenden Sie nicht beim besteht keine Notwendigkeit, blockieren den Benutzer und deren Ablauf unterbrochen. Vermeiden Sie modale Dialogfelder verwenden, wenn es möglich ist, die Meldung in eine andere, weniger intrusiv Weise angezeigt werden.|  
|[IDE-Statusleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Wird verwendet, wenn ambient Textinformationen hinsichtlich des Status eines Prozesses vorhanden ist.|Verwenden Sie nicht allein. Am besten verwendet in Verbindung mit einem anderen Feedbackmechanismus.|  
|[Eingebettete Infoleiste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Verwenden Sie in einem Toolfenster oder Dokumentfenster zum Fortschritt, Status "Fehler", Ergebnisse und/oder aussagekräftiger Informationen zu benachrichtigen.|Verwenden Sie nicht, wenn die Informationen nicht an den Speicherort relevant ist, in dem die Infoleiste platziert wird.<br /><br /> Verwenden Sie nicht außerhalb eines Dokuments/Toolfensters.|  
|[Mauszeiger ändert sich](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Kann verwendet werden, benachrichtigen, dass ein Prozess auf abgelaufen ist. Auch verwendet zum Benachrichtigen ergibt sich eine statusänderung in der Maus, z. B. bei Drag & Drop in Bearbeitung "oder", wird der Mauszeiger in einem bestimmten Modus, z. B. Zeichnungsmodus.|Verwenden Sie keine Änderungen des kurzen Status oder der fluttering der Cursor wahrscheinlich (z. B., wenn die Teile eines ausgeführten Prozesses statt für den gesamten Prozess länger gebunden) ist.|  
|[Statusanzeigen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Verwenden Sie, wann der Status (bestimmte oder unbestimmt). Es gibt verschiedene Arten von Fortschrittsanzeigen und ein spezifischer für jede. Finden Sie unter [Status von Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Visual Studio-benachrichtigunsfenster](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Das Fenster Benachrichtigungen ist nicht öffentlich erweiterbar. Es wird jedoch verwendet, einen Bereich von Meldungen über Visual Studio, einschließlich der kritische Probleme mit Ihrer Lizenz und nur zu Informationszwecken Benachrichtigungen des Updates zu Visual Studio oder Pakete zu kommunizieren.|Verwenden Sie nicht für andere Arten von Benachrichtigungen.|  
|[Fehlerliste](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Wenn das Problem direkt auf der Benutzer gerade geöffneten Projektmappe mit einem Problem (Fehler/Warnung/Informationen) bezieht, müssen sie möglicherweise Aktionen für den Code ausführen können.<br /><br /> Dies würde, z. B. Folgendes umfassen:<br /><br /> -Compilermeldungen (Fehler/Warnung/Informationen)<br /><br /> -Code Analyzer/Diagnose Nachrichten über den code<br /><br /> -Erstellen von Nachrichten<br /><br /> Kann für die Probleme im Zusammenhang mit der Projektmappen- oder Projektdateien geeignet sein, aber erwägen zuerst eine Angabe über das Projektmappen-Explorer.|Verwenden Sie nicht für Elemente, die keinen Bezug zu den Benutzercode geöffneten Projektmappe.|  
|Editor-Benachrichtigungen: Glühbirne|Wird verwendet, wenn Sie einen Fix verfügbar ist haben, ein Problem zu beheben, die in die geöffnete Datei vorhanden ist.<br /><br /> Beachten Sie, dass die Glühbirne auch verwendet werden soll, für das Hosten von Schnellaktionen, die auf den Benutzercode bei Bedarf, z. B. Refactorings, stammen in diesem Fall wird jedoch nicht angezeigt "Benachrichtigung Style".|Verwenden Sie nicht für Elemente, die nicht über eine Beziehung an die geöffnete Datei verfügen.|  
|Editor-Benachrichtigungen: Wellenlinien|Verwenden Sie, um die Benachrichtigung des Benutzers für ein Problem mit einer bestimmten Spanne des Codes öffnen (z. B. eine rote Wellenlinie nach Fehlern).|Verwenden Sie nicht für Elemente, die nicht auf einen bestimmten Zeitraum Codeprobleme öffnen beziehen.|  
|[Eingebettete Statusleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Verwenden Sie, um den Status im Zusammenhang mit Inhalt oder Prozess im Kontext einer bestimmten Toolfenster Dokumentfenster oder Dialogfenster bereitzustellen.|Verwenden Sie nicht für allgemeine Produkt Benachrichtigungen, Prozesse oder Elemente, die keinen Bezug zu den Inhalt in das jeweilige Fenster.|  
|[Windows-Taskleiste-Benachrichtigungen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Mit der Oberfläche von Benachrichtigungen für die Out-of-Proc-Prozesse oder Begleit-Anwendungen.|Verwenden Sie nicht für Benachrichtigungen, die für die IDE relevant sind.|  
|[Benachrichtigung Blasen](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Benachrichtigen eines remote-Prozesses oder ändern **außerhalb** der IDE.|Verwenden Sie nicht als Mittel zur Benachrichtigung des Benutzers von Prozessen **in** der IDE.|  
  
### <a name="notification-methods"></a>Benachrichtigungsmethoden  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> Modale Meldung Fehlerdialogfelder  
 Eine modale Meldung Fehlerdialogfeld wird verwendet, um eine Fehlermeldung angezeigt, die Bestätigung des Benutzers oder eine Aktion erforderlich sind.  
  
 ![Modale Fehlermeldung](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Eine modale Meldung Fehlerdialogfeld warnen der Benutzer eine ungültige Verbindungszeichenfolge zu einer Datenbank**  
  
####  <a name="BKMK_IDEStatusBar"></a> IDE-Statusleiste  
 Die Wahrscheinlichkeit, dass Benutzer Statusleistentext beachten korreliert für ihre Bestrebens Computerfunktionen und bestimmte Kenntnisse in Bezug auf die Windows-Plattform. Visual Studio-Kundenstamm tendenziell erfahrenen in beiden Bereichen werden zwar auch erfahrene Windows-Benutzer Änderungen in der Statusleiste verpassen könnte. Aus diesem Grund wird die Statusleiste am besten für Informationszwecke oder als eine redundante Cue verwendet für Informationen, die an anderer Stelle angezeigt. Jede Art von wichtigen Informationen, den der Benutzer sofort auflösen müssen sollten in einem Dialogfeld oder im Toolfenster Benachrichtigungen angegeben werden.  
  
 Die Statusleiste von Visual Studio wurde entwickelt, um verschiedene Arten von Informationen zu ermöglichen, die angezeigt werden. Er ist in Regionen für das Feedback, Designer, Statusleiste, Animation und Client unterteilt.  
  
 Die Feedbackbereich und Designerbereich sind immer sichtbar. Die Statusanzeige und Animation Regionen sind immer dynamisch und basierend auf den Benutzerkontext. Des Designerbereichs verfügt über eine statische Breite bestimmt anhand der Länge der Zeichenfolge, die aus einer zugehörigen Ressource für die Nachricht abgerufen wird. Dadurch werden Lokalisierung, um die Breite des zu ändern, ohne dass eine Änderung des Codes. Für Englisch ist die Breite dieser Zeichenfolge ungefähr 220 Pixel. Des Designerbereichs normal verhält, und die Feedbackbereich wird den restlichen Speicherplatz in verschiedene Abschnitte gegliedert.  
  
 Die Statusleiste wird auch farbig hervorgehoben, Informationen zum Hinzufügen von visuellem Reiz und funktionalen Wert über die Kommunikation verschiedene IDE-Zustandsänderungen, z. B. wenn die IDE im Debugmodus befindet.  
  
 ![IDE-Statusleiste farbänderungen](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **IDE-statusleistenfarben**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> Eingebettete Infoleiste  
 Eine Infoleiste kann am oberen Rand Dokument- oder Toolfenster verwendet werden, um die Benutzer über ein Bundesland oder eine Bedingung zu informieren. Sie können Befehle auch anbieten, so, dass der Benutzer eine Möglichkeit, leicht Maßnahmen ergreifen kann. Infoleiste ist ein standard-Shell-Steuerelement. Erstellen Sie keine eigene, dem fungieren und nicht mit anderen Benutzern in der IDE angezeigt wird. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) für Implementierungsdetails und Anleitungen.  
  
 ![Eingebettete Infoleiste](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Infoleiste eingebettet in einem Dokumentfenster warnen der Benutzer, den die IDE befindet sich im verlaufsbezogenen Debugmodus, und der Editor reagiert nicht auf die gleiche Weise wie in debugging Modus "standard".**  
  
####  <a name="BKMK_MouseCursorChanges"></a> Mauszeiger ändert sich  
 Wenn Sie den Cursor zu ändern, verwenden Sie die Farben, die an den Dienst VSColor gebunden werden und sind bereits mit dem Cursor zugeordnet. Cursor Änderungen dient zum Angeben eines laufenden Vorgangs sowie erreicht Zonen, in denen der Benutzer über ein Ziel, das gezogen bewegen, abgelegt oder zum Auswählen eines Objekts verwendet werden kann.  
  
 Verwenden Sie den Mauszeiger gebucht/Wait, nur, wenn alle verfügbaren CPU-Zeit für einen Vorgang, der verhindert, dass des Benutzers keine weitere Eingabe Ausdrücken reserviert werden muss. In den meisten Fällen gut geschriebene Anwendungen, die Verwendung von multithreading sollte selten Zeiten, wenn Benutzer keine andere Operationen durchzuführen.  
  
 Bedenken Sie, dass Cursor Änderungen nützlich sind, wie ein redundanter Cue Informationen, die an anderer Stelle angezeigt. Verlassen Sie sich nicht auf eine Änderung der Cursor als die einzige Möglichkeit der Kommunikation mit dem Benutzer, insbesondere, wenn Sie versuchen, etwas zu vermitteln, die wichtig sind, dass der Benutzer berücksichtigt werden muss.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> Statusanzeigen  
 Statusanzeigen sind wichtig für das Feedback der Benutzer zu erteilen, während der Prozesse, die mehr als ein paar Sekunden dauert. Statusanzeigen können angezeigt werden direkte (in der Nähe der Ausgangspunkt der Aktion in Bearbeitung), in eine eingebettete Statusleiste, in ein modales Dialogfeld oder in der Statusleiste von Visual Studio. Befolgen Sie die Anleitung in [Status von Indikatoren](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) im Hinblick auf ihre Verwendung und Implementierung.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio-benachrichtigunsfenster  
 Der Visual Studio-benachrichtigunsfenster benachrichtigt Entwickler zu Lizenzierung, Umgebung (Visual Studio), Erweiterungen und Updates. Benutzer können können einzelne Benachrichtigungen verwerfen oder, um bestimmte Arten von Benachrichtigungen zu ignorieren. Die Liste der ignorierten Benachrichtigungen erfolgt einem **Tools > Optionen** Seite.  
  
 Das Fenster Benachrichtigungen ist nicht aktuell erweiterbar.  
  
 ![Visual Studio-benachrichtigunsfenster](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Toolfenster für Visual Studio-Benachrichtigungen**  
  
####  <a name="BKMK_ErrorList"></a> Fehlerliste  
 Eine Benachrichtigung in der Fehlerliste anzugeben, Fehler und Warnungen, die bei der Kompilierung und Buildprozess und ermöglicht es dem Benutzer zum Navigieren in Code auf diesen bestimmten Code-Fehler.  
  
 ![Fehlerliste](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Fehlerliste in Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> Eingebettete Statusleisten  
 Da die IDE-Statusleiste dynamisch, mit der Region-Clientkontext, die auf das aktive Fenster und die Informationen, die auf dem Kontext des Benutzers und/oder Systemantworten aktualisieren festgelegt ist, ist es schwierig, eine kontinuierliche Anzeige von Informationen zu verwalten, oder gewähren Status für langfristige asynchroner Prozesse. IDE-Statusleiste ist z. B. nicht für Benachrichtigungen des Testlaufergebnisse für mehrere Ausführungen und/oder sofort ausführbares Elementauswahl geeignet. Es ist wichtig, diese Statusinformationen im Kontext des Fensters Dokument- oder Toolfenster beibehalten werden sollen, in denen der Benutzer stellt eine Auswahl oder startet einen Prozess.  
  
 ![Eingebettete Statusleiste](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Eingebettete Statusleiste in Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a> Windows-Taskleiste-Benachrichtigungen  
 Die Windows-Infobereich neben dem System ist clock auf der Windows-Taskleiste. Viele Hilfsprogramme und Softwarekomponenten bieten Symbole in diesem Bereich, sodass der Benutzer ein Kontextmenü für eine systemweite Aufgaben, wie z. B. Bildschirmauflösung ändern oder Abrufen von Softwareupdates abrufen kann.  
  
 Umgebung Anwendungsebene Benachrichtigungen sollten auf dem Hub für Visual Studio-Benachrichtigungen, nicht die Windows-Infobereich angefügt werden sollen.  
  
####  <a name="BKMK_NotificationBubbles"></a> Benachrichtigung Blasen  
 Benachrichtigung Blasen können als informativ in eine Editor-Designer oder im Rahmen des Windows-Benachrichtigungsbereich angezeigt werden. Der Benutzer wahrnimmt diese Blasen als Probleme, die sie später zu beheben, können die liegt der Vorteil für nicht kritische Benachrichtigungen. Blasen sind ungeeignet für wichtige Informationen, den der Benutzer sofort gelöst werden muss. Wenn Sie Benachrichtigungen Blasen in Visual Studio verwenden, führen Sie die [Windows-Desktop-Anleitung für die Benachrichtigung Blasen](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Benachrichtigungssprechblase](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Benachrichtigungssprechblase in der Windows-Infobereich für Visual Studio verwendet**  
  
##  <a name="BKMK_ProgressIndicators"></a> Statusanzeigen  
  
### <a name="overview"></a>Übersicht  
 Statusanzeigen sind ein wichtiger Teil ein Benachrichtigungssystem für das Feedback der Benutzer zu gewähren. Sie können dem Benutzer mitteilt, wenn die Prozesse und Vorgänge abgeschlossen werden. Vertraute Indikator Anweisungstypen Statusanzeigen Spinvorgänge Cursor und animierte Symbole. Der Typ und die Platzierung des eine Statusanzeige eingeblendet, hängt davon ab, den Kontext, einschließlich was gemeldet wird und wie lange der Prozess oder einen Vorgang bis zum Abschluss.  
  
#### <a name="factors"></a>Faktoren  
 Um zu bestimmen, welche Indikatortyp geeignet ist, müssen Sie die folgenden Faktoren zu ermitteln.  
  
1.  **Ein Timeout:** Zeitdauer der Vorgang dauert  
  
2.  **Modalität:** gibt an, ob der Vorgang ist modal an der Umgebung (Sperren der Benutzeroberfläche, bis der Vorgang abgeschlossen ist)  
  
3.  **Persistent/vorübergehend:** gibt an, ob das endgültige Ergebnis des Status zu einem späteren Zeitpunkt gemeldeten und/oder angezeigt werden muss  
  
4.  **Bestimmte/unbestimmt:** gibt an, ob die Endzeit des Vorgangs und den Fortschritt berechnet werden können  
  
5.  **Grafik zu/Textual Speicherort:** gibt an, ob der Status oder Prozess erfassten Inline im Text einer Nachricht oder ein bestimmtes Steuerelement, z. B. des Strukturansicht-Steuerelements ist  
  
6.  **NEAR:** , ob der Status in der Nähe der Benutzeroberfläche sein soll, die mit der Sie verknüpft ist. (Beispielsweise kann es sein, in der Statusleiste, die weit möglicherweise, oder gibt es in der Nähe der Schaltfläche ist, die der Prozess gestartet?)  
  
#### <a name="determinate-progress"></a>Bestimmte Status  
  
|Status Typ|Wann und wie verwendet|Hinweise|  
|-------------------|-------------------------|-----------|  
|Statusanzeige (bestimmte)|Erwartete Dauer des > 5 Sekunden.<br /><br /> Eventuell die textbeschreibung des Prozessdetails.|**Nicht** Einbetten von Text in der Animation.|  
|Infoleiste|Messaging mit kontextbezogenen UI verknüpft. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Eventuell die textbeschreibung des Prozessdetails.|**Nicht** mehrere Infoleisten verwenden, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Statusanzeigen.|  
|Ausgabefenster|Vorübergehender Benachrichtigung: app-Ebene Prozess dieser Benutzer soll **überprüfen** Details nach Abschluss des Vorgangs.|**Nicht** verwenden, wenn der Benutzer zum Verweisen auf Daten später benötigen.|  
|Protokolldatei|Gepaart mit intransient Benachrichtigung in Fällen, wenn es darauf ankommt, **speichern** Details nach Abschluss des Vorgangs.||  
|Statusleiste|Vorübergehender Benachrichtigung: app-Ebene Prozess dieser Benutzer wird **müssen nicht** Details nach Abschluss des Vorgangs.<br /><br /> Enthält eine eingebetteten Statusanzeige an.<br /><br /> Eventuell die textbeschreibung des Prozessdetails.||  
  
#### <a name="indeterminate-progress"></a>Einen unbestimmten Status  
  
|Status Typ|Wann und wie verwendet|Hinweise|  
|-------------------|-------------------------|-----------|  
|Statusanzeige (unbestimmt)|Erwartete Dauer des > 5 Sekunden.<br /><br /> Eventuell die textbeschreibung des Prozessdetails.|**Nicht** Einbetten von Text in der Animation.|  
|Ameisen (animierte horizontale dpi)|Der Roundtrip zum Server.<br /><br /> Platziert Near Punkt des Kontexts am oberen Rand der übergeordneten Container.|**Nicht** verwenden, wenn Sie nicht durch den gesamten Container übergeordnet ist.|  
|"Spinner" (Status Ring)|Der Prozess, zugeordnet ist kontextbezogene Benutzeroberfläche, auf dem Speicherplatz zu berücksichtigen ist.<br /><br /> Eventuell die textbeschreibung des Prozessdetails.||  
|Infoleiste|Messaging mit kontextbezogenen UI verknüpft. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nicht** mehrere Infoleisten verwenden, wenn Sie mehrere Prozesse angeben müssen. Verwenden Sie stattdessen gestapelte Statusanzeigen.|  
|Ausgabefenster|Vorübergehender Benachrichtigung: app-Ebene Prozess dieser Benutzer sollten **überprüfen** Details nach Abschluss des Vorgangs.|**Nicht** finden Sie Informationen, die sitzungsübergreifend beibehalten werden muss.|  
|Protokolldatei|Gepaart mit intransient Benachrichtigung in Fällen, wenn es darauf ankommt, **speichern** Details nach Abschluss des Vorgangs.||  
|Statusleiste|Vorübergehender Benachrichtigung: app-Ebene Prozess dieser Benutzer wird **müssen nicht** Details nach Abschluss des Vorgangs.<br /><br /> Enthält eingebettete Statusleiste an.<br /><br /> Eventuell die textbeschreibung des Prozessdetails.||  
  
### <a name="progress-indicator-types"></a>Arten von Fortschrittsanzeigen  
  
#### <a name="progress-bars"></a>Statusanzeigen  
  
##### <a name="indeterminate"></a>Unbestimmt  
 ![Unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Unbestimmte Fortschrittsleiste**  
  
 "Unbestimmt" bedeutet, dass den Gesamtstatus eines Vorgangs oder Prozess kann nicht bestimmt werden. Verwenden für Vorgänge, die eine unbegrenzte Zeitspanne erfordern, unbestimmt Statusanzeigen oder, die Zugriff auf eine unbekannte Anzahl von Objekten. Verwenden Sie eine textbeschreibung, was geschieht begleitet. Verwenden Sie Timeouts Grenzen auf zeitbasierte Vorgänge gewähren. Unbestimmt Statusanzeigen verwenden Animationen, um anzuzeigen, dass Status erfolgt, aber keine anderen Informationen bieten. Wählen Sie eine unbestimmte Fortschrittsleiste allein basierend auf der möglichen Mangel an Genauigkeit allein.  
  
##### <a name="determinate"></a>Bestimmte  
 ![Festgelegte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Festgelegte Fortschrittsleiste**  
  
 "Bestimmte" bedeutet, dass ein Vorgang oder ein Prozess eine begrenzte Zeitspanne erfordert auch, wenn diese Zeitspanne nicht präzise vorhergesagt werden kann. Geben Sie klar Abschluss des Vorgangs an. Lassen Sie keine Statusanzeige und 100 Prozent zu wechseln, es sei denn, der Vorgang abgeschlossen wurde. Bestimmte Leiste Statusanimation verschiebt links-nach-rechts zwischen 0 und 100 % an.  
  
 Verschoben Sie die Statusanzeige, die während eines Vorgangs rückwärts die nie werden. Die Leiste sollte vorwärts stetig Wenn der Vorgang gestartet und 100 % erreicht, wenn diese endet. Der Punkt der Statusanzeige ist dem Benutzer erhält einen Überblick darüber, wie lange der gesamte Vorgang dauert unabhängig davon, wie viele Schritte beteiligt sind.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Gleichzeitige reporting (gestapelten Statusanzeigen)  
 Wenn ein Vorgang lange - dauert möglicherweise mehrere Minuten – dann zwei Statusanzeigen verwendet werden können, eine, die zeigt, Gesamtstatus für einen Vorgang und ein anderes für den Fortschritt des aktuellen Schritts. Z. B. wenn ein Setupprogramm, das viele Dateien kopiert werden, können Sie dann eine Statusanzeige verwendet werden, um anzugeben, wie lange der gesamte Prozess dauert, während eine zweite, welcher Prozentsatz der aktuellen Datei angeben kann oder Verzeichnis kopiert werden. Mehr als fünf gleichzeitige Vorgänge oder Prozesse, die mit gestapelten Statusanzeigen, aber nicht gemeldet werden. Wenn Sie mehr als fünf gleichzeitige Vorgänge oder Prozesse Bericht haben, verwenden Sie einem modalen Dialogfeld mit einer Schaltfläche "Abbrechen" und den Bericht Statusdetails, um das Fenster "Ausgabe".  
  
##### <a name="textual-descriptions"></a>Textbeschreibungen  
 Verwenden Sie eine Beschreibung, was geschieht begleitet sowie die geschätzte Zeit bis zum Abschluss. Wenn es nicht möglich ist, um zu bestimmen, wie lange ein Vorgang dauern wird, kann die bessere Wahl für das Bereitstellen von Feedback eine Statusanzeige angezeigt, statt eine animierte Symbol sein.  
  
 Visual Studio bietet eine standard-Statusanzeige auf der Statusleiste, die von einem Produkt in Visual Studio integriert verwendet werden kann. Für textbeschreibungen, was geschieht, während die Statusanzeige animiert wird kann die Statusleistentext aktualisiert werden.  
  
#### <a name="other-progress-indicators"></a>Andere Statusanzeigen  
  
##### <a name="ants-animated-horizontal-dots"></a>Ameisen (animierte horizontale dpi)  
 ![Ant-Elemente zum Fortschritt](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Ameisen," animierte horizontale dpi, bieten eine visuelle Referenz für einen unbestimmten Round-Trip Serverprozess an.  
  
##### <a name="spinner-progress-ring"></a>"Spinner" (Status Ring)  
 ![Drehelement zum Fortschritt](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 Das Drehfeld (auch bekannt als einen "Bearbeitung-Ring") ist eine unbestimmte Statusanzeige, die in erster Linie in Bezug auf kontextabhängige UI verwendet. Zeigen Sie eine "Spinner" in der Nähe zu seiner verwandten Inhalten, z. B. Text Category-Header, messaging oder Steuerelement.  
  
##### <a name="cursor-feedback"></a>Cursor-feedback  
 Bereitstellen Sie für Vorgänge, die zwischen 2 bis 7 Sekunden dauern Cursor-Feedback. In der Regel bedeutet dies die Nutzung des Wartecursors vom Betriebssystem bereitgestellt. Anweisungen finden Sie im MSDN-Artikel [Cursors.Wait Eigenschaft](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Fortschritt Indikator Speicherorte  
  
##### <a name="status-bar"></a>Statusleiste  
 Die Statusleiste kann Ihre Anwendung einen Ort, an die Nachrichten und nützliche Informationen für den Benutzer anzuzeigen, ohne den Benutzer Arbeit zu unterbrechen. In der Regel am unteren Rand eines Fensters angezeigt wird, werden Status für den Status einer QuickInfo Toolbereich, die eine Nachricht über das Maß für Fortschritt in Kombination mit einem Fortschrittsbalken enthält.  
  
 ![Statusleiste mit Statusanzeige](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **Statusleiste mit Fortschrittsleiste**  
  
 ![Statusleiste mit Meldungen](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Statusleiste mit textbeschreibung**  
  
##### <a name="infobar"></a>Infoleiste  
 Ähnlich wie in der Statusleiste der Informationsleiste enthält kontextbezogene Benachrichtigung und messaging, die auch unbestimmt Statusanzeigen z. B. die Statusanzeige oder eine "Spinner" zugeordnet werden können. Der Informationsleiste sollte nicht präzise Ebene ausgeführt werden oder auf bestimmte Status Hinweis darauf bereitstellen. Finden Sie unter [Infoleisten](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Infoleiste mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **Infoleiste mit Fortschrittsanzeige und textbeschreibung**  
  
 ![Infoleiste in einem Fenster](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>Inline  
 Inline-Status-Angabe kann durch den Status-Ladeprogramm-Typen dargestellt werden. In der Regel die Statusanzeige mit messaging gekoppelt ist, aber dies ist nicht erforderlich.  
  
 ![Drehelement zum Fortschritt "Inline"](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **In Kombination mit textbeschreibung "Spinner"**  
  
 ![Gestapelte Inline-Fortschrittsleisten](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Bestimmte gestapelte Statusanzeigen**  
  
 ![Inline-fortschrittsmeldungen](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Server-Explorer inlinetext: aktualisieren...**  
  
##### <a name="tool-windows"></a>Toolfenster  
 Angabe des globalen Status wird durch eine unbestimmte Fortschrittsleiste direkt unterhalb der Symbolleiste positioniert dargestellt.  
  
 ![Globale unbestimmte Fortschrittsleiste](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Team Explorer globale unbestimmte Fortschrittsleiste**  
  
##### <a name="dialogs"></a>Dialogfelder  
 Dialoge können den Fortschritt Ladeprogramm Typen enthalten. Statusanzeigen können werden in Verbindung mit messaging als auch in Kombination mit mehreren Ebenen Fortschritt Angabe darstellen, die präzise oder Sub-Prozesse.  
  
 ![Dialogfeld mit mehreren Arten von Fortschrittsanzeigen](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Visual Studio-Dialogfeld gleichzeitige Prozesse mit mehreren Arten von Fortschrittsanzeigen**  
  
 ![Dialogfeld mit Fortschrittsanzeige und Meldungen](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **Visual Studio-Dialogfeld mit Fortschrittsanzeige und Meldungen Inline Befehle**  
  
##### <a name="document-well"></a>Dokumentursprung  
 Das Dokument kann mehrere Status-Ladeprogramm-Typen auch in Kombination mit Steuerelementen angezeigt werden.  
  
 ![Fortschrittsmeldungen in Dokument auch](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Unbestimmte Fortschrittsleiste unter Symbolleiste**  
  
##### <a name="output-window"></a>Ausgabefenster  
 Das Fenster "Ausgabe" eignet sich für die Behandlung von Prozess Fortschritts- und laufende Fortschrittsanzeige über Text Inline-messaging. Sie sollten die Statusleiste zusammen mit jeder Ausgabe Fenster Fortschrittsberichterstattung verwenden.  
  
 ![Fortschrittsmeldungen in Ausgabefenster](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Ausgabefenster mit dem Status des laufenden Prozess und warten Sie, messaging**  
  
##  <a name="BKMK_Infobars"></a> Infoleisten  
  
### <a name="overview"></a>Übersicht  
 Infoleisten weisen Sie dem Benutzer einen Indikator nahe dem Zeitpunkt der Aufmerksamkeit, und mit dem freigegebenen Infoleiste-Steuerelement wird sichergestellt, dass die Konsistenz in visuelle Darstellung und Interaktion.  
  
 ![Infoleiste](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904 01_Infobar")  
  
 **Infoleisten in Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Verwendungsmöglichkeiten für einer Infoleiste  
  
-   So erteilen Sie dem Benutzer eine nicht blockierende jedoch wichtige Meldung, die im aktuellen Kontext irrelevant  
  
-   Um anzugeben, dass die Benutzeroberfläche in einem bestimmten Status oder Bedingung zur Folge haben Auswirkungen Interaktion, z. B. verlaufsbezogenes debugging  
  
-   Um Benutzer zu benachrichtigen, dass das System Probleme, z. B. wenn eine Erweiterung Leistungsprobleme verursacht erkannt wurde  
  
-   Dem Benutzer stellt eine Möglichkeit, leicht Maßnahmen, z. B. wenn der Editor erkennt, dass eine Datei Registerkarten und Leerzeichen im gemischten hat  
  
##### <a name="do"></a>Führen Sie aus:  
  
-   Halten Sie den Meldungstext Infoleiste, kurz und zu dem Punkt.  
  
-   Behalten Sie den Text auf Links und Schaltflächen prägnanten.  
  
-   Stellen Sie sicher, dass "Aktion"-Optionen, die Sie für Benutzer bereitstellen minimal, nur die erforderliche Aktionen angezeigt werden.  
  
##### <a name="dont"></a>Tue nicht:  
  
-   Verwenden einer Infoleiste Standardbefehle anbieten, die in einer Symbolleiste platziert werden soll.  
  
-   Verwenden einer Infoleiste anstelle ein modales Dialogfeld an.  
  
-   Erstellen Sie eine unverankerte Nachricht außerhalb eines Fensters.  
  
-   Verwenden Sie mehrere Infoleisten an mehreren Standorten innerhalb des gleichen Fensters.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Werden mehrere Infoleisten können gleichzeitig angezeigt?  
 Ja, können mehrere Infoleisten gleichzeitig angezeigt werden. Sie werden in der Reihenfolge First-Come und First-served-Prinzip mit der ersten Infoleiste anzeigen auf Top und zusätzliche Infoleisten zeigt unten angezeigt werden.  
  
 Der Benutzer sieht maximal drei Infoleisten zu einem Zeitpunkt nach dem, wenn weitere Infoleisten verfügbar sind die Infoleiste Region bildlauffähigen werden soll.  
  
### <a name="creating-an-infobar"></a>Erstellen einer Infoleiste  
 Infoleiste verfügt über vier Abschnitte, die von links nach rechts:  
  
-   **Symbol:** sieht, in dem Sie ein Symbol hinzufügen möchten, die für die Infoleiste, z. B. ein Warnsymbol angezeigt.  
  
-   **Text:** Sie können hinzufügen Text zur Beschreibung des Szenario/Situation-Benutzers sich befindet, können zusammen mit Links innerhalb des Texts, wenn erforderlich. Denken Sie daran, den Text kompakt zu halten.  
  
-   **Aktionen:** Links und Schaltflächen für Aktionen, die der Benutzer in Ihrer Infoleiste dauern kann, sollte in diesem Abschnitt enthalten.  
  
-   **Schaltfläche "Schließen":** im letzten Abschnitt rechts kann eine Schaltfläche "Schließen" haben.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Erstellen eine standardmäßige Infoleiste in verwaltetem code  
 Die InfoBarModel-Klasse kann verwendet werden, erstellen Sie eine Datenquelle für eine Infoleiste. Verwenden Sie eine dieser vier Konstruktoren:  
  
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
  
 Hier ist ein Beispiel, das eine InfoBarModel mit Text, einen Link, ein Aktionsschaltfläche und ein Symbol erstellt.  
  
 ![Infoleiste mit Hyperlink](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
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
 Implementieren Sie die IVsInfoBar-Schnittstelle, um einer Infoleiste von systemeigenem Code bereitstellen.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Abrufen einer Infoleiste UIElement aus einer Infoleiste  
 Die Implementierung InfoBarModel oder IVsInfoBar sind Datenmodelle, die in einem UIElement eingeschaltet bleiben müssen, um auf der Benutzeroberfläche angezeigt werden. Einem UIElement kann mit dem Dienst SVsInfoBarUIFactory/IVsInfoBarUIFactory abgerufen werden.  
  
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
 Infoleisten können eine oder mehrere der folgenden Speicherorte angezeigt werden:  
  
-   Toolfenster  
  
-   Innerhalb einer Registerkarte "Dokument"  
  
> [!IMPORTANT]
>  Es ist möglich, eine Infoleiste so erteilen Sie eine Benachrichtigung erhalten, globalen Kontext zu positionieren. Dies würde zwischen Symbolleisten und Dokumentursprung angezeigt. Dies wird nicht empfohlen, da er bewirkt, Probleme mit "wechseln und jerk dass" der IDE und sollte vermieden werden, es sei denn, dies absolut notwendig und.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Platzieren einer Infoleiste in einem ToolWindowPane  
 Die ToolWindowPane.AddInfoBar(IVsInfoBar)-Methode kann verwendet werden, ein Toolfenster einer Infoleiste hinzu. Diese API kann entweder ein IVsInfoBar (welche InfoBarModel ist eine Standardimplementierung), hinzufügen oder eine IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Platzieren einer Infoleiste in einem Dokument oder nicht ToolWindowPane  
 Um einer Infoleiste in jeder IVsWindowFrame einzufügen, verwenden Sie die VSFPROPID_InfoBarHost-Eigenschaft, um die IVsInfoBarHost für den Frame zu erhalten, und fügen Sie dann die Infoleiste UIElement.  
  
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
 Um einer Infoleiste im Hauptfenster zu platzieren, verwenden Sie die VSSPROPID_MainWindowInfoBarHost des Diensts IVsShell, um das Hauptfenster IVsInfoBarHost abzurufen, und fügen Sie die Infoleiste UIElement hinzu.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Weiß ich, wenn der Benutzer in meiner Infoleiste Aktion durchführt?  
 Ja, gibt es alle Ereignisaktion an den Autor Infoleiste zurück. Es ist dann bis zu der Infoleiste Autor in der IDE basierend auf der Auswahl des Benutzers in der Infoleiste Maßnahmen ergreifen. Infoleisten werden automatisch entfernt werden, auf dem Host, dessen Schaltfläche "Schließen" geklickt wurde, aber zusätzliche Schritte sind erforderlich, wenn andere Infoleisten müssen nach dem zu entfernenden schließen. Telemetrie müssen auch unabhängig von jeder Infoleiste protokolliert werden.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Empfangen von Infoleiste Ereignisse in einem ToolWindowPane  
 ToolWindowPane verfügt über zwei Ereignisse für Infoleisten. Die InfoBarClosed-Ereignis wird ausgelöst, wenn eine Infoleiste in die ToolWindowPane geschlossen wird. Die InfoBarActionItemClicked-Ereignis wird ausgelöst, wenn auf einen Link oder eine Schaltfläche in der Infoleiste geklickt wird.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Empfangen von Infoleiste Ereignissen direkt von der UIElement  
 IVsInfoBarUIElement.Advise können Sie Ereignisse abonnieren, direkt aus einer Infoleiste UIElement verwendet werden. IVsInfoBarUIEvents implementieren, kann den Autor zum Schließen empfangen und click-Ereignisse.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> Fehler-Überprüfung  
 Wenn der Benutzer Informationen ein, die nicht zulässig sein, z. B. wenn ein erforderliches Feld ausgelassen wird oder wenn Daten in die falschen Format eingegeben werden, ist es besser, die Validierung von Steuerelementen verwenden oder Feedback neben dem Steuerelement, statt eine blockierende Popupdialogfeld Fehler.  
  
### <a name="field-validation"></a>Feldvalidierung  
 Formular und Feld Überprüfung besteht aus drei Komponenten: ein Steuerelement, ein Symbol und eine QuickInfo. Obgleich unterschiedliche Typen von Steuerungsmechanismen dies verwenden können, wird ein Textfeld, das als Beispiel verwendet werden.  
  
 ![Feld Überprüfung &#40;leere&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Wenn das Feld erforderlich ist, es darf Wasserzeichen Text, der besagt  **\<erforderlich >** Hintergrund Feld sollte auch hellen Gelb (VSColor: `Environment.ControlEditRequiredBackground`) Vordergrund sollte auch grau (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Überprüfung mit Beschriftung "Erforderlich" Feld](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 Das Programm kann bestimmen, dass das Steuerelement in einem *ungültige Inhalte eingegeben* entweder bei der Fokus auf ein anderes Steuerelement oder der Benutzer auf eine Schaltfläche "OK" Commit klickt oder wenn der Benutzer das Dokument oder eine Form speichert.  
  
 Wenn der Status ist ungültige Inhalt bestimmt wird, wird ein Symbol angezeigt, auf das Steuerelement oder direkt neben. Eine Beschreibung des Fehlers QuickInfo sollte darauf gezeigt wird, der das Symbol oder Steuerelement angezeigt werden. Darüber hinaus sollte ein 1-Pixel-Rahmen um das Steuerelement aufgeführt, die einen ungültigen Zustand erstellt wird.  
  
 ![Layoutspezifikationen für feldüberprüfung Feld](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Layoutspezifikationen für feldvalidierung**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Akzeptable Varianten für symbolplatzierung  
 Es gibt unzählige besonderen Fällen, in denen Benutzer über Validierungsfehler informiert werden müssen. Wählen Sie unter Berücksichtigung der Steuerelementtyp vorliegt und die Konfiguration der Benutzeroberfläche die Symbol-Platzierung für Ihre Situation geeignet.  
  
 ![Zulässige Positionen für symbolplatzierung](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Akzeptable Varianten für Feld Überprüfung Symbol Speicherorte**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validierung, erfordern einen Roundtrip zu einer Verbindung zum Server oder Netzwerk  
 In einigen Fällen ein Roundtrip zum Server ist erforderlich, um den Inhalt zu überprüfen und wäre es wichtig, den Status der User, überprüft, und den Fehlerstatus an. Die folgende Abbildung zeigt ein Beispiel für diesen Fall und die empfohlenen-Benutzeroberfläche.  
  
 ![Überprüfung mit Roundtrip zu einem Server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Überprüfung mit Roundtrip zu einem server**  
  
 Beachten Sie, dass ausreichend Speicherplatz auf der rechten Seite des Steuerelements bereitgestellt werden muss, um den Text "Überprüfen..." und "Wiederholen" aufzunehmen.  
  
#### <a name="in-place-warning-text"></a>Direktes Warnungstext  
 Wird Platz zur Verfügung, die Fehlermeldung in der Nähe des Steuerelements in einem Zustand des Fehlers eingefügt werden soll, ist dies mithilfe der QuickInfo allein vorzuziehen.  
  
 ![In&#45;platzieren Warnung](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Direktes Warnungstext**  
  
#### <a name="watermarks"></a>Wasserzeichen  
 Manchmal ist eine gesamte Steuerelement oder Fenster im Status "Fehler" ein. Verwenden Sie in diesem Fall ein Wasserzeichen der Fehler an.  
  
 ![Wasserzeichen](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 07_Watermark")  
  
 **Wasserzeichen feldvalidierung**