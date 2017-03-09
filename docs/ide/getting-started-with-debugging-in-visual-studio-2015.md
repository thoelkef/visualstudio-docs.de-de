---
title: "Erste Schritte beim Debuggen in Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erste Schritte beim Debuggen in Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 2015 bietet einen leistungsfähigen integrierten Satz von Projektbuild\- und Debugtools.  Sie erfahren in diesem Thema, wie Sie die grundlegenden Funktionen zum Debuggen von Benutzeroberflächenfunktionen verwenden.  
  
 Hinweis: Links zu erweiterten Features und plattform\- oder featurespezifischen Themen sind unten auf dieser Seite.  
  
## Mein Code funktioniert nicht.Ich benötige Hilfe in Visual Studio 2015.  
 Sie haben also herausgefunden, wie der Editor funktioniert, und Code erstellt.  Nun möchten Sie mit dem Debuggen von Code beginnen.  In Visual Studio 2015 besteht das Debuggen wie bei den meisten IDEs aus zwei Phasen: Erstellen des Codes zum Abfangen und Beheben von Projekt\- und Compilerfehlern und Ausführen dieses Codes in der Umgebung zum Abfangen und Beheben von Laufzeit\- und dynamischen Fehlern.  
  
### Konfigurieren von Builds  
 Es gibt zwei grundlegende Arten der Buildkonfiguration: **Debug** und **Release**.  Die erste Konfiguration erzeugt eine langsamere und größere ausführbare Datei, die für ein umfangreicheres interaktives Debuggen zur Laufzeit verwendet werden kann, aber nie ausgeliefert werden sollte.  Mit der zweiten wird eine schnellere, optimierte ausführbare Datei erstellt, die \(zumindest aus Sicht des Compilers\) ausgeliefert werden kann.  
  
 Die Standardbuildkonfiguration ist **Debug**.  
  
 Sie können auch eine bestimmte Zielplattform für den Build angeben, z. B. **x86** \(32\-Bit\-Intel\-CPUs\), **x64** \(64\-Bit\-Intel\-CPUs\) oder **ARM** \(ARM\-CPUs, nur für bestimmte App\-Typen unterstützt\).  Die Standardeinstellung ist **x86** für verwaltete und systemeigene Projekte.  Um dies zu ändern, klicken Sie auf die Dropdownliste für die Buildplattform und wählen eine andere Plattform oder den **Konfigurations\-Manager** aus.  
  
 Sie können im **Konfigurations\-Manager** die gewünschte Buildkonfiguration angeben.  Starten Sie ihn, und klicken Sie auf eine der Dropdownlisten **Konfiguration** oder **CPU**. Wählen Sie **Neu...** aus, um einen neuen Build oder eine Plattform zu erstellen.  
  
 Verwenden Sie zunächst **Debug** und **x86** als Buildkonfiguration bzw. Plattform.  Wenn Sie mit dem Programmieren und Debuggen fertig sind, ändern Sie die Konfiguration in **Release** und die gewünschte Plattform.  \(In älteren Versionen von Visual Studio wurde die Standardplattform **AnyCPU** für .NET\-Codeprojekte bereitgestellt.\)  
  
 Hinweis: Wenn Sie das Projekt erstellen, werden die Werte für Konfiguration und Plattform auch verwendet, um den Verzeichnispfad des Projekts zum Speichern der ausführbaren Datei zu bestimmen.  Dies ist normalerweise **\<path\-to\-project\>\\\<project\-name\>\\\<configuration\>\\\<platform\>**.  Ein Projekt mit der Konfiguration `Debuggen` mit der Plattform `x86` würden Sie z. B. unter `Projects\MeinProjektName\MeinProjektName\bin\Debug\x86` finden.  Dies kann hilfreich sein, wenn Sie eigene Tools oder Skripts zum Verwalten dieser ausführbaren Builddateien verwenden.  
  
### Erstellen von Code  
 Mit Ihrem konfigurierten Build können Sie nun das Projekt erstellen.  Die einfachste Möglichkeit besteht darin, dass Sie  F7drücken. Sie können den Build aber auch starten, indem Sie im Hauptmenü **Erstellen \-\> Projektmappe erstellen** auswählen.  
  
 Sie können den Buildprozess im Statusfenster **Ausgabe** am unteren Rand der Visual Studio\-Benutzeroberfläche beobachten.  Dort werden Fehler, Warnungen und Buildvorgänge angezeigt.  Wenn Fehler \(oder Warnungen über die konfigurierte Stufe hinaus\) auftreten, schlägt der Build fehl.  Sie können auf die Fehler und Warnungen klicken, um zu der Zeile zu wechseln, in der der Fehler aufgetreten ist.  Erstellen Sie Ihr Projekt neu, indem Sie entweder **F7** erneut drücken \(um nur die Dateien mit Fehlern neu zu kompilieren\) oder indem Sie **STRG\+ALT\+F7** drücken \(für eine vollständige Neuerstellung\).  
  
 Im Ergebnisfenster unterhalb des Editors finden Sie zwei Buildfenster als Registerkarten: Das Fenster **Ausgabe** enthält die unformatierte Compilerausgabe \(einschließlich Fehlermeldungen\), und das Fenster **Fehlerliste** enthält eine sortierbare und filterfähige Liste aller Fehler und Warnungen.  
  
 Bei erfolgreicher Ausführung werden die Ergebnisse wie folgt im Fenster **Ausgabe** dargestellt.  
  
### Überprüfen der Fehlerliste  
 Sofern Sie keine Änderungen am Code vorgenommen haben, den Sie zuvor erfolgreich kompiliert hatten, tritt vermutlich ein Fehler auf.  Wenn Sie noch nie programmiert haben, werden wahrscheinlich viele Fehler auftreten.  Fehler sind manchmal offensichtlich, z. B. einfache Syntaxfehler oder falsche Variablennamen, manchmal aber auch schwer zu verstehen, wenn Ihnen nur schwer lesbarer Code zur Verfügung steht.  Für eine übersichtlichere Ansicht der Probleme navigieren Sie zum Ende des Fensters **Ausgabe** für den Build, und klicken Sie auf die Registerkarte **Fehlerliste**.  Dadurch gelangen Sie zu einer besser angeordneten Ansicht der Fehler und Warnungen für das Projekt mit einigen zusätzlichen Optionen.  
  
 Klicken Sie im Fenster **Fehlerliste** auf die Zeile mit dem Fehler, um direkt in die Zeile zu springen, in der der Fehler aufgetreten ist.  \(Oder blenden Sie die Zeilennummern ein, indem Sie oben rechts auf die **Schnellstartleiste** klicken, "Zeilennummern" eingeben und die EINGABETASTE drücken.  Dies ist die schnellste Möglichkeit zum Aufrufen des Fensters **Optionen**, in dem Sie Zeilennummern aktivieren können.  Machen Sie sich mit der Verwendung der **Schnellstartleiste** vertraut, denn sie erspart Ihnen viele Klicks auf der Benutzeroberfläche\!\)  
  
 Verwendung                                                Strg\+G                                                , um die Nummer der Zeile abzurufen, in der der Fehler aufgetreten ist.  
  
 Der Fehler wird durch eine rote Wellenlinie gekennzeichnet.  Bewegen Sie den Mauszeiger darüber, um weitere Informationen anzuzeigen.  Wenn Sie die Korrektur vornehmen, wird die Markierung aufgehoben. Es ist natürlich trotzdem möglich, dass Sie mit Ihrer Änderung einen neuen Fehler einfügen.  \(Dies wird als "Regression" bezeichnet.\)  
  
 Bearbeiten Sie die Fehlerliste, und beheben Sie alle Fehler im Code.  
  
### Überprüfen der Fehler im Detail  
 Einige Fehler erscheinen Ihnen möglicherweise nicht sinnvoll, wenn sie wie vom Compiler formuliert angezeigt werden.  In diesen Fällen benötigen Sie weitere Informationen.  Sie können aus dem Fenster **Fehlerliste** heraus eine automatische Suche in Bing nach weiterführenden Informationen über den Fehler \(oder die Warnung\) durchführen. Klicken Sie dazu mit der rechten Maustaste auf die entsprechende Zeile, und wählen Sie im Kontextmenü **Hilfe zu Fehlern anzeigen** aus.  
  
 Dadurch wird in Visual Studio 2015 eine Registerkarte mit den Ergebnissen einer Bing\-Suche nach dem Fehlercode und dem Text angezeigt.  Die Ergebnisse stammen aus verschiedenen Quellen im Internet und sind möglicherweise nicht alle hilfreich.  
  
 Sie können auch auf den als Hyperlink formatierten Fehlercode in der Spalte **Code** in der **Fehlerliste** klicken.  Hierdurch wird eine Suche in Bing nur nach dem Fehlercode durchgeführt.  
  
### Ausführen statischer Codeanalysen  
 Die "statische Codeanalyse" stellt eine praktische Möglichkeit dar, den eigenen Code automatisch auf allgemeine Probleme überprüfen zu lassen, die zu Laufzeitfehlern führen oder Probleme bei der Codeverwaltung verursachen können.  Gewöhnen Sie sich die Ausführung an, sobald Sie offensichtliche Fehler behoben haben, die das Erstellen verhindern würden. Nehmen Sie sich etwas Zeit, auch die Warnungen zu behandeln.  Sie ersparen sich damit einige spätere Probleme und lernen etwas über Stiltechniken beim Codieren.  
  
 Drücken                                                Alt\+F11                              \(oder wählen Sie im oberen Menü **Analysieren \-\> Codeanalyse für Lösung ausführen** aus\), um die statische Codeanalyse zu starten.  Dieser Vorgang kann bei umfangreichem Code einige Zeit dauern.  
  
 Alle neuen oder aktualisierten Warnungen werden auf der Registerkarte **Fehlerliste** am unteren Rand der IDE angezeigt.  Klicken Sie auf die Warnungen, um zu diesen zu wechseln.  
  
 Die Warnungen werden mit einer hellen gelb\-grünen Wellenlinie anstelle der roten gekennzeichnet.  Bewegen Sie den Mauszeiger darüber, um weitere Details anzuzeigen, und klicken Sie mit der rechten Maustaste darauf, um ein Kontextmenü anzuzeigen, das Optionen zur Korrektur oder Umgestaltung enthält.  
  
### Verwenden von Glühbirnen zum Beheben oder Umgestalten von Code  
 Glühbirnen sind ein neues Feature von Visual Studio 2015, mit dem Sie Code inline umgestalten können.  Damit können allgemeine Warnungen schnell und effektiv behoben werden.  Um darauf zuzugreifen, klicken Sie mit der rechten Maustaste auf die Wellenlinie einer Warnung \(oder drücken Sie  STRG\+. während Sie auf die Wellenlinie zeigen\), und wählen Sie dann **Schnelle Aktionen** aus.  
  
 Es wird eine Liste der möglichen Korrekturen oder Umgestaltungen angezeigt, die Sie auf diese Codezeile anwenden können.  
  
 Glühbirnen können überall dort angewendet werden, wo die Codeanalyse Möglichkeiten zur Problembehebung, Umgestaltung oder Verbesserung Ihres Codes erkannt hat.  Klicken Sie mit der rechten Maustaste auf eine beliebige Codezeile, um das Kontextmenü zu öffnen, und wählen Sie **Schnelle Aktionen** aus \(oder drücken Sie  STRG\+.\).  Wenn es Möglichkeiten zur Umgestaltung oder Verbesserung gibt, werden diese angezeigt. Andernfalls wird die Meldung `No quick actions available here` in der unteren linken Ecke der IDE angezeigt.  
  
 Mit etwas Erfahrung können Sie rasch mithilfe der Pfeiltasten und                                                STRG\+.                                                überprüfen, ob schnelle Aktionen zur Umgestaltung und Bereinigung Ihres Codes verfügbar sind.  
  
 Weitere Informationen zu Glühbirnen finden Sie unter [Ausführen von schnellen Aktionen mit Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md).  
  
### Debuggen von ausgeführtem Code  
 Nachdem Sie Code erstellt und einige Bereinigungen durchgeführt haben, führen Sie ihn aus, indem Sie                                                F5                              drücken oder **Debug \-\> Debugging starten** auswählen.  Dadurch wird Ihre App in einer Debugumgebung gestartet, damit Sie ihr Verhalten im Detail beobachten können.  Die Visual Studio 2015\-IDE ändert sich während der Ausführung Ihrer App: Das Fenster **Ausgabe** wird \(in der Standardfensterkonfiguration\) durch zwei neue ersetzt, und zwar die Registerkartenfenster **Auto\/Lokal\/Module\/Überwachung** und **Aufrufliste\/Haltepunkte\/Ausnahmeeinstellungen\/Ausgabe**.  Diese Fenster enthalten mehrere Registerkarten, mit denen Sie Variablen, Threads, Aufruflisten und andere Verhaltensweisen während der Ausführung Ihrer App überprüfen und bewerten können.  
  
 Führen Sie verschiedene Aktionen mit Ihrer App durch, und beobachten Sie die Änderungen.  Wenn etwas Ungewöhnliches angezeigt wird, halten Sie die App durch Drücken von  STRG\+ALT\+UNTBR \(oder durch Klicken auf die Schaltfläche **Anhalten**\) an.  
  
 Drücken                                                F5                                                , um die App weiter auszuführen \(oder klicken Sie auf die Schaltfläche **Weiter**\).  
  
 Sie können Ihre App durch Drücken von                                                UMSCHALTTASTE\+F5                              oder durch Klicken auf die Schaltfläche **Beenden** beenden.  Sie können die App auch einfach durch Schließen des Hauptfensters \(oder über die Befehlszeile\) schließen.  
  
 Wenn Ihr Code ohne besondere Vorkommnisse genau wie erwartet ausgeführt wurde, sind Sie damit fertig\!  Ändern Sie die Buildkonfiguration in **Release**, und erstellen Sie den Build für die Bereitstellung neu.  \(IT\-Experten sollten allerdings mit dem Abschnitt zum Testen der Komponenten am Ende fortfahren.\) Wenn der Code jedoch nicht mehr reagiert oder abgestürzt, oder wenn Sie unerwartete Ergebnissen erhalten, müssen Sie die Ursache dieser Probleme suchen und die Fehler beheben.  
  
### Festlegen einfacher Haltepunkte  
 Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen.  Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.  Sie müssen ein Projekt NICHT neu erstellen, nachdem Sie Haltepunkte festgelegt oder entfernt haben.  
  
 Legen Sie einen Haltepunkt fest, indem Sie auf den äußeren Rand der Zeile klicken, in der Sie die Unterbrechung einfügen möchten, oder wählen Sie die Codezeile aus, und drücken Sie                                                F9                              .  Wenn Sie Code ausführen, wird er direkt vor der Ausführung der Anweisungen für diese Codezeile angehalten.  
  
 Wenn der Code unterbrochen wird, wurde die markierte Codezeile noch nicht ausgeführt.  An diesem Punkt können Sie die Anweisungen für die Codezeile ausführen, die durch den Haltepunkt markiert wurde, und die geänderten Werte überprüfen.  Dies wird als "schrittweises Durchlaufen des Codes" bezeichnet.  Ist der gekennzeichnete Code ein Methodenaufruf, durchlaufen Sie diesen durch Drücken von  F11.  Sie können die Codezeile auch überspringen durch Drücken von  F10.  Weitere Informationen zu den Haltepunktaktionen finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).  
  
 Für Folgendes werden Haltepunkte häufig verwendet:  
  
1.  Zum Eingrenzen der Ursache eines Absturzes oder einer Blockade können Sie im gesamten Code Haltepunkte verteilen. Außerdem können Sie in der Nähe des Codes für den Methodenaufruf, von dem Sie annehmen, dass er den Fehler verursacht, ebenfalls Haltepunkte platzieren.  Wenn Sie den Code durchlaufen, entfernen Sie die Haltepunkte und platzieren sie dann näher beieinander, um die fehlerhafte Codezeile einzugrenzen.  
  
2.  Wenn Sie neuen Code einführen, platzieren Sie einen Haltepunkt am Anfang dieses Codes und durchlaufen diesen dann, um sicherzustellen, dass er sich wie erwartet verhält.  
  
3.  Wenn Sie kompliziertes Verhalten implementiert haben, legen Sie Haltepunkte für den algorithmischen Code fest, damit Sie die Werte von Variablen und die Daten überprüfen können, wenn das Programm unterbrochen wird.  
  
4.  Wenn Sie Code in C\# oder C\+\+ schreiben, verwenden Sie Haltepunkte zum Anhalten des Codes, um die Adresswerte \(Suche nach NULL\) und Verweiszähler beim Debuggen von speicherbezogenen Fehlern zu überprüfen.  
  
 Weitere Informationen zur Verwendung von Haltepunkten finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md) \(Haltepunkte: Verwenden von Trefferanzahl, Funktionen der Aufrufliste und Bedingungen, um im Visual Studio Debugger jederzeit zu unterbrechen, in englischer Sprache\)  
  
### Festlegen bedingter Haltepunkte  
 Verwenden Sie bei Haltepunkten in einer Schleife oder Rekursion oder bei sehr vielen Haltepunkten, die Sie häufig schrittweise durchlaufen, einen bedingten Haltepunkt, damit die Codeausführung NUR unterbrochen wird, wenn bestimmte Bedingungen erfüllt sind.  Andernfalls müssen Sie sehr häufig F11 drücken.  
  
 Für das Festlegen eines bedingten Haltepunkts, bei dem die Ausführung automatisch fortgesetzt wird, wenn eine Variable auf einen bestimmten Wert festgelegt ist oder einen bestimmten Schwellenwert übersteigt, klicken Sie auf den Rand, um einen Haltepunkt festzulegen, und wählen Sie dann im angezeigten Menü das "Zahnrad" aus.  
  
 Es wird ein Dialogfeld angezeigt, das wie folgt aussieht und in dem Sie bestimmte Bedingungen für die Unterbrechung festlegen können.  
  
 Weitere Informationen zum Deklarieren der Ausdrücke für das Auswerten bedingter Haltepunkte finden Sie im Channel9\-Video [Breakpoint Configuration Experience in Visual Studio 2015](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711) \(Haltepunktkonfiguration in Visual Studio 2015, in englischer Sprache\).  
  
### Überprüfen von Code zur Laufzeit  
 Wenn der ausgeführte Code an einem Haltepunkt anhält, können Sie die Variablen und Aufruflisten untersuchen, um die gerade ausgeführte Aktion zu ermitteln.  Liegen die Werte in den erwarteten Bereichen?  Werden die Aufrufe in der richtigen Reihenfolge ausgeführt?  
  
 Zeigen Sie auf eine Variable, um die Werte und Verweise anzuzeigen, die sie zurzeit enthält.  Wenn Sie einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler.  Verschieben Sie Haltepunkte nach oben, oder fügen Sie vorhandenen Haltepunkten Bedingungen hinzu, um die Suche weiter einzugrenzen.  
  
 Darüber hinaus zeigt Visual Studio 2015 das Fenster mit den Diagnosetools an, in dem Sie den CPU\- und Speicherverbrauch Ihrer App im Zeitverlauf beobachten können.  Verwenden Sie diese, um nach unerwartet hoher CPU\-Auslastung oder Arbeitsspeicherzuordnungen zu suchen.  Zusammen mit dem Fenster **Überwachung** und Haltepunkten können Sie so sehr schnell ermitteln, wodurch eine unerwartete Auslastung oder nicht freigegebene Ressourcen verursacht werden.  
  
### Ausführen von Komponententests  
 Komponententests sind Programme, die Codepfade in Ihrer App oder Ihrem Dienst ausführen.  Visual Studio 2015 enthält die Komponententest\-Frameworks von Microsoft für sowohl verwalteten als auch systemeigenen Code.  Verwenden Sie ein Komponententest\-Framework, um Komponententests zu erstellen, auszuführen und Berichte mit den Ergebnissen dieser Tests zu erstellen.  Führen Sie Komponententests erneut durch, wenn Sie Änderungen vorgenommen haben, um zu testen, dass der Code weiterhin ordnungsgemäß ausgeführt wird.  Wenn Sie Visual Studio 2015 Enterprise verwenden, können die Tests automatisch nach jedem Build ausgeführt werden.  
  
 Weitere Informationen finden Sie unter [Generieren von Komponententests für Code mit IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  
  
 Weitere Informationen zu Komponententests in Visual Studio 2015 und wie sie Ihnen helfen, besseren Code zu erstellen, finden Sie unter [Grundlagen zum Komponententest](../test/unit-test-basics.md) \(Grundlagen zu Komponententests, in englischer Sprache\).  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Debuggen von 64\-Bit\-Anwendungen](../debugger/debug-64-bit-applications.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)