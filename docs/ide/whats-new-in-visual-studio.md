---
title: Neuerungen in Visual Studio 2017 RC | Microsoft-Dokumentation
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Neuerungen in Visual Studio 2017
Willkommen bei Visual Studio 2017 RC, einer integrierten Suite von Entwicklerproduktivitätstools, Cloud-Diensten und Erweiterungen, mit denen Sie und Ihr Team großartige Apps und Spiele für das Web, den Windows Store, den Desktop, Android und iOS erstellen können.  

In diesem Release Candidate (RC) der neuesten Version von Visual Studio haben wir den Schwerpunkt auf Verbesserungen bei Leistung und Produktivität gelegt. Die verbesserte Leistung zeigt sich im schnelleren Start von Visual Studio, der besseren Reaktionsfähigkeit und der geringeren Arbeitsspeicherauslastung. Zur Steigerung der Produktivität haben wir Funktionen hinzugefügt oder aktualisiert, die Ihre Effizienz bei der Arbeit mit Visual Studio steigern können.

> [!TIP]
> Um den neuen RC in Aktion zu erleben, sehen Sie sich das Video [What's New in Visual Studio](https://channel9.msdn.com/events/connect/2016/159) (Neues in Visual Studio) auf Channel 9 an.   

Hier folgt eine allgemeine Zusammenfassung der vorgenommenen Änderungen:

* **Gesteigerte Produktivität**. Durch Verbesserungen an der Codenavigation, IntelliSense, Refactoring, Codekorrekturen und Debuggen ersparen Sie sich Zeit und Aufwand bei alltäglichen Aufgaben, und zwar unabhängig von Sprache und Plattform. Darüber hinaus optimiert Visual Studio 2017 für mit DevOps arbeitende Teams die innere Entwicklerschleife und beschleunigt den Codefluss mithilfe brandneuer Echtzeitfeatures wie Livekomponententests und Überprüfung von Architekturabhängigkeiten in Echtzeit.
* **Neu definierte Grundlagen**.  Wieder liegt ein Schwerpunkt auf der Steigerung der Effizienz für grundlegende Aufgaben, die Entwickler tagtäglich erledigen müssen. Von einer ganz neuen schlanken und modularen Installation, die an die Anforderungen von Entwicklern angepasst ist, einer schnelleren IDE vom Start bis zum Herunterfahren bis zu einer neuen Weise des Anzeigens, Bearbeitens und Debuggens von Code ohne Projekte und Projektmappen hilft Visual Studio 2017 Entwicklern, das Gesamtbild stets im Blick zu behalten.
* **Optimierte Azure-Entwicklung**. Integrierte Sammlung von Azure-Tools, die das einfache Entwickeln von primär auf die Cloud ausgelegten Anwendungen in Microsoft Azure ermöglichen. Visual Studio vereinfacht das Konfigurieren, Erstellen, Debuggen, Packen und Bereitstellen von Anwendungen und Diensten in Microsoft Azure direkt aus der IDE.
* **Mobile-Entwicklung auf Fünf-Sterne-Niveau**. Dank hochentwickelter Debug- und Profilerstellungstools und Features für das Generieren von Komponententests beschleunigt und vereinfacht Visual Studio 2017 mit Xamarin das Entwickeln, Verbinden und Optimieren mobiler Apps für Android, iOS und Windows. Außerdem können Entwickler mobile Apps auch mithilfe der auf Apache Cordova oder auf Visual C++ basierenden plattformübergreifenden Bibliotheksentwicklung direkt in Visual Studio entwickeln.  

Hier finden Sie weitere Details zu den wichtigsten Änderungen.

> [!NOTE]
> Eine vollständige Liste der neuen Features und Funktionen in Visual Studio 2017 RC und dem nachfolgenden RC Refresh finden Sie in den [Anmerkungen zur Version](https://www.visualstudio.com/news/vs2015-vs). Eine Liste der Fehler und Problemumgehungen finden Sie im Abschnitt [Bekannte Probleme](https://www.visualstudio.com/news/vs2015-vs#knownissues) der Anmerkungen zur Version.   

## <a name="performance-improvements"></a>Leistungsverbesserungen

### <a name="a-new-setup-experience"></a>Ein neues Setuperlebnis  
[Visual Studio Enterprise 2017 RC herunterladen](https://aka.ms/vs/15/preview/vs_enterprise) oder [Visual Studio-Systemanforderungen überprüfen](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Mit der neu entwickelten Setupoberfläche von Visual Studio fällt es Ihnen noch leichter, bedarfsweise nur genau die benötigten Features zu installieren. Wir haben außerdem den Fußabdruck für den günstigsten Installationsfall weiter verkleinert, sodass Visual Studio schneller und mit geringerem Einfluss auf das System installiert wird. Und es lässt sich auch sauber wieder deinstallieren.

 Die wichtigste Änderung, die Ihnen beim Installieren von Visual Studio auffallen wird, ist die neue Installationsoberfläche. Auf der Registerkarte **Arbeitsauslastungen** sehen Sie Installationsoptionen, die so gruppiert sind, dass sie häufig verwendete Frameworks, Sprachen und Plattformen darstellen und alles von der .NET-Desktopentwicklung bis hin zu Data Science mit R, Python und F# abdecken.  

 ![Visual Studio 2017 RC-Setupdialogfeld](../ide/media/willow1.png "VS2017RC_Setup_screen")

Wählen Sie die benötigten Arbeitsauslastungen, und ändern Sie sie bei Bedarf. Die kleinstmögliche Installation umfasst nur ein paar Hundert Megabytes, enthält jedoch grundlegende Unterstützung für die Codebearbeitung für mehr als&20; Sprachen sowie Funktionen für die Quellcodeverwaltung.

Wir haben außerdem verschiedene Installationsarten für Visual Studio hinzugefügt. Möchten Sie Ihre Komponenten lieber selbst aussuchen, statt Arbeitsauslastungen zu verwenden? Wählen Sie einfach im Installationsprogramm die Registerkarte **Einzelne Komponenten** aus. Möchten Sie Sprachpakete installieren, ohne zugleich auch die eingestellte Sprache für Windows ändern zu müssen? Wählen Sie die Registerkarte **Sprachpakete** des Installationsprogramms aus.  

Weitere Informationen über die neue Installationsoberfläche, einschließlich Schritt-für-Schritt-Anweisungen, die Sie durch die Installation führen, finden Sie auf unserer Seite [Installieren von Visual Studio](../install/install-visual-studio.md).


### <a name="start-visual-studio-faster"></a>Schnellerer Start von Visual Studio
Wenn Visual Studio feststellt, dass das Startverhalten der IDE langsam ist, stellt es ein neues Visual Studio-Leistungscenter bereit, mit dem Sie den Verlauf beschleunigen können. Im Leistungscenter werden alle Erweiterungen und Toolfenster aufgelistet, die den Start der IDE verlangsamen. Sie können es zum Verbessern der Startleistung verwenden, indem Sie festlegen, wann Erweiterungen gestartet werden oder ob bestimmte Toolfenster beim Start geöffnet sein sollen.

### <a name="decrease-solution-load-time"></a>Verringern der Ladedauer von Projektmappen
Das Arbeiten mit Projektmappen, die mehr als 100 Projekte enthalten, bedeutet nicht, dass Sie an allen Dateien oder Projekten zugleich arbeiten müssen. Bearbeiten und Debuggen sind jetzt möglich, ohne auf das Laden jedes einzelnen Projekts durch Visual Studio zu warten. Wenn Sie dies mit verwalteten Projekten ausprobieren möchten, aktivieren Sie unter „Extras“ > „Optionen“ > „Projekte und Projektmappen“ den **Lightweight-Ladevorgang für Projektmappen**.

  ![Dialogfeld „Optionen“ in Visual Studio 2017 RC](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "VS2017RC-Dialogfeld „Optionen“ – Lightweight-Ladevorgang für Projektmappen")

### <a name="faster-on-demand-loading-of-extensions"></a>Schnelleres Laden von Erweiterungen bei Bedarf
Die Idee ist einfach: Laden Sie Erweiterungen, wenn sie benötigt werden, statt beim Start von Visual Studio. Im ersten Schritt haben wir unsere Python- und Xamarin-Erweiterungen auf das Laden bei Bedarf umgestellt, und im nächsten Schritt möchten wir alle mit Visual Studio gelieferten &#150; und die von Drittanbietern gelieferten &#150; Erweiterungen auf dieses Modell umstellen. Möchten Sie wissen, welche Erweiterungen sich auf den Start, das Laden von Projektmappen und die Leistung bei der Eingabe auswirken? Sie finden diese Informationen unter „Hilfe“ > „Visual Studio-Leistung verwalten“.

  ![Dialogfeld „Optionen“ in Visual Studio 2017 RC](../ide/media/vs2017ide-ManageVSperf.png "VS2017RC-Dialogfeld „Hilfe“ – Leistungsverwaltung")

## <a name="productivity-improvements"></a>Produktivitätsverbesserungen

### <a name="sign-in-across-multiple-accounts"></a>Anmelden mit mehreren Konten  
Wir haben in Visual Studio 2017 RC einen neuen Identitätsdienst eingeführt, der Ihnen die übergreifende Verwendung von Benutzerkonten in den Microsoft-Entwicklertools ermöglicht, z. B. in Team Explorer, Azure-Tools, Windows Store-Veröffentlichung und mehr.

Ebenfalls können Sie länger angemeldet bleiben – wir bitten Sie nicht mehr alle 12 Stunden um erneute Anmeldung. Weitere Informationen finden Sie im Blogbeitrag [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (Weniger Anmeldeaufforderungen in Visual Studio).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Verwalten von Erweiterungen mit dem Roaming-Erweiterungs-Manager
Es ist jetzt sogar noch einfacher geworden, jede Entwicklungsumgebung mit Ihren bevorzugten Erweiterungen einzurichten, wenn Sie sich bei Visual Studio anmelden. Unser neuer Roaming-Erweiterungs-Manager verfolgt alle Ihre bevorzugten Erweiterungen nach, indem er eine synchronisierte Liste in der Cloud erstellt.  

Um eine Liste Ihrer Erweiterungen in Visual Studio anzuzeigen, klicken Sie auf „Extras“ > „Erweiterungen und Updates“, und klicken Sie dann auf den Roaming-Erweiterungs-Manager.

![Visual Studio 2017 – Dialogfeld „Erweiterungen und Updates“](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 – „Extras“ > Dialogfeld „Erweiterungen und Updates“")

Der Roaming-Erweiterungs-Manager verfolgt alle von Ihnen installierten Erweiterungen nach, Sie können aber wählen, welche Ihrer Roamingliste hinzugefügt werden sollen.

![Visual Studio 2017 – Dialogfeld „Erweiterungen und Updates“](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 – Roaming-Erweiterungs-Manager")

Wenn Sie den Roaming-Erweiterungs-Manager verwenden, werden Sie 3 Symboltypen in Ihrer Liste bemerken:
* ![Symbol für „Roaming erfolgt“](../ide/media/vs2017ide-roamedicon.png "Symbol für „Roaming erfolgt“") ***Symbol für „Roaming erfolgt“***: Eine Erweiterung, die in Ihrer Roamingliste enthalten, auf Ihrem Computer jedoch nicht installiert ist.
  (Erweiterungen dieses Typs können Sie mithilfe der Schaltfläche **Download** herunterladen.)
* ![Symbol für „Roaming und Installation erfolgt“](../ide/media/vs2017ide-roamedinstalledicon.png "Symbol für „Roaming und Installation erfolgt“") ***Symbol für „Roaming und Installation erfolgt“***: Alle Erweiterungen, die Teil dieser Roamingliste und in Ihrer Entwicklungsumgebung installiert sind.
  (Wenn Sie sich gegen das Roaming entscheiden, können Sie zum Entfernen die Schaltfläche **Roaming beenden** verwenden.)
* ![Symbol für „Installiert“](../ide/media/vs2017ide-installedicon.png "Symbol für „Installiert“") ***Symbol für „Installiert“***: Alle Erweiterungen, die in dieser Umgebung installiert, aber nicht in der Roamingliste enthalten sind.
  (Sie können der Roamingliste Erweiterungen mithilfe der Schaltfläche **Roaming starten** hinzufügen.)

Diese Symbole zeigen den aktuellen Status Ihrer Liste an. Sie können Erweiterungen mit jedwedem Status verwenden und je nach Ihren Anforderungen Anpassungen vornehmen. Oder lassen Sie uns diese Aufgabe für Sie übernehmen. Alle Erweiterungen, die Sie bei bestehender Anmeldung herunterladen, werden der Liste mit dem Status **Roaming und Installation erfolgt** hinzugefügt. Sie sind also Teil Ihrer Roamingliste, und daher haben Sie von jedem Computer aus darauf Zugriff!

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Erleben Sie die Echtzeitüberprüfung der Architekturabhängigkeiten und Livekomponententests

Wenn Sie in Visual Studio Enterprise 2017 RC Diagramme zur Abhängigkeitsprüfung eingerichtet haben (auch als Ebenendiagramme bezeichnet), können Sie sich jetzt während der Eingabe von Code im Code-Editor in Echtzeit über Verletzungen von Architekturabhängigkeitsregeln benachrichtigen lassen.

Fehler werden in der Fehlerliste angezeigt, und Wellenlinien im Text-Editor zeigen den genauen Ort einer Verletzung an. Es ist nun weniger wahrscheinlich, dass Sie unerwünschte Abhängigkeiten einführen.

![Echtzeitüberprüfung der Architektur](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Echtzeitüberprüfung der Architekturabhängigkeiten")

#### <a name="live-unit-testing"></a>Livekomponententests:

Livekomponententests sind eine neu eingeführte Funktion, die nur in der Enterprise-Edition von Visual Studio verfügbar ist. Diese Funktion visualisiert Ergebnisse von Komponententests und Codeabdeckungsdaten live für den Editor während Sie codieren. Sie funktioniert mit C#/VB-Projekten für .NET Framework und unterstützt Testframeworks von MSTest, xUnit und NUnit.

### <a name="visual-studio-ide-enhancements"></a>Verbesserungen der Visual Studio-IDE
#### <a name="interact-with-git"></a>Interaktion mit Git:
Mit Steuerelementen in der unteren Ecke der IDE von Visual Studio können Sie schnell einen Commit auszuführen, Ihre Projekte auf Git veröffentlichen und Ihre Git-Repositorys verwalten.

![Visual Studio 2017 RC-Setupdialogfeld](../ide/media/vsIDE-GitInteraction.png "Git-Tools-in-der-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Anzeigen von und Navigation in Code mit der Strukturschnellansicht:
Im Visual Studio-Code-Editor ist ein neues Feature mit der Bezeichnung Strukturschnellansicht verfügbar. Dieses Feature zeigt vertikale Führungslinien zwischen verschachtelten Codebereichen an, die Ihnen das Anzeigen Ihres Codes und die Navigation darin erleichtern. Dieses Feature ist für alle von TextMate unterstützten Sprachen sowie für Visual C#, Visual Basic und XAML verfügbar.

![Visual Studio 2017 RC-Setupdialogfeld](../ide/media/vsIDE-StructureVisualizer.png "Strukturschnellansicht-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>Lernen Sie das verbesserte Navigieren zu kennen:
Wir haben die Funktion Navigieren zu verbessert. Wir haben das Fenster von Navigieren zu vereinfacht und Unterstützung für zusätzliche Filterzeichen hinzugefügt, die verfeinerte Suchen im Code ermöglichen.

#### <a name="create-apps-in-even-more-programming-languages"></a>Erstellung von Apps in noch mehr Programmiersprachen:
Sie können in Visual Studio Apps in einer noch größeren Anzahl Programmiersprachen als in früheren Versionen erstellen, und dazu sind weder Projekte noch Projektmappen erforderlich. Der Code erhält farbige Syntaxhervorhebung, einfache Anweisungsvervollständigung und in manchen Fällen auch Unterstützung für Navigieren zu und weitere Features. Wenn Ihre bevorzugte Sprache nicht unterstützt wird, können Sie die Unterstützung dafür mithilfe von TextMate-Grammatiken erstellen.

### <a name="visual-c"></a>Visual C++
Visual Studio 2017 RC enthält viele Updates und Korrekturen der Visual C++-Umgebung. Wir haben mehr als 250 Fehler und gemeldete Probleme mit dem Compiler und den Tools behoben, von denen viele durch Kunden über [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") übermittelt wurden.

Ferner haben wir eine Reihe von Verbesserungen vorgenommen, um die Verteilung von C++ Core Guidelines mit Visual Studio einzuschließen, den Compiler durch verbesserte Unterstützung für C++11 und C++-Features zu aktualisieren, Funktionalität in den C++-Bibliotheken hinzuzufügen und zu aktualisieren, die Leistung der Arbeitsauslastungen in der C++-IDE zu steigern und mehr.

Eine vollständige Auflistung der Details finden Sie auf der Seite [Neues für Visual C++ in Visual 2017 RC](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  


### <a name="debugging-and-diagnostics"></a>Debuggen und Diagnose
Debuggen erfolgt jetzt schneller und bewirkt keine Verzögerungen bei der Bearbeitung.

Beispiel: In einer früheren Version von Visual Studio führten wir den sogenannten Hostprozess für WPF, Windows Forms und verwaltete Konsolenprojekte ein, um das Debuggen dadurch zu beschleunigen, dass im Hintergrund ein Prozess für die Verwendung in der nächsten Debugsitzung hochgefahren wurde. Dieses in guter Absicht eingeführte Feature führte dazu, dass Visual Studio vorübergehend für einige Sekunden nicht reagierte, wenn das Debuggen beendet wurde oder Visual Studio nach dem Beenden der Debugsitzung verwendet wurde.

In Visual Studio 2017 haben wird den Hostprozess deaktiviert und das Debuggen optimiert, sodass es jetzt ohne den Hostprozess genau so schnell ist und sogar schneller für Projekte, die den Hostprozess ohnehin nicht verwendeten (wie etwa ASP.NET-, universelle Windows- und C++-Projekte).

#### <a name="run-to-click"></a>Ausführung bis Klick:
Jetzt können Sie während des Debuggens auf das Symbol neben einer Codezeile klicken, um die betreffende Zeile auszuführen. Sie brauchen keine temporären Haltepunkte mehr festzulegen, um verschiedene Schritte zur Ausführung Ihres Codes auszuführen und in der gewünschten Zeile anzuhalten.

![Visual Studio 2017 RC-Debuggen – Ausführung bis Klick](../ide/media/vs2017ide-RunToClick.png "Ausführung bis Klick in Visual Studio 2017-Debuggen und Diagnose")

#### <a name="the-new-exception-helper"></a>Die neue Ausnahmen-Hilfe:

Mit der neuen Ausnahmen-Hilfe können Sie Ihre Ausnahmeinformationen auf einen Blick in einem kompakten nicht modalen Dialogfeld mit sofortigem Zugriff auf die inneren Ausnahmen anzeigen.

Sie können direkt in der Ausnahme-Hilfe schnell sehen, was NULL war, wenn Sie eine NullReferenceException diagnostizieren.

Sie können nun das Unterbrechen für Ausnahmetypen ausschließen, die von spezifischen Modulen ausgelöst werden, indem Sie das Kontrollkästchen aktivieren, um für einen Stopp an einer ausgelösten Ausnahme eine Bedingung hinzuzufügen.

![Das neue Dialogfeld „Ausnahmehilfsprogramm“](../ide/media/vs2017ide-ExceptionHelper.png "Das neue Dialogfeld „Ausnahmehilfsprogramm“")

Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

## <a name="talk-to-us"></a>Sprechen Sie mit uns  
 Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.  

Wenn Sie einen Vorschlag zu möglichen Verbesserungen von Visual Studio machen oder ein Problem melden möchten, finden Sie weitere Informationen auf der Seite [Talk to Us](../ide/talk-to-us.md).  

### <a name="report-a-problem"></a>Problem melden  
 Manchmal reicht eine Nachricht nicht aus, um das gesamte Ausmaß eines Problems, auf das Sie gestoßen sind, deutlich zu machen. Wenn bei Ihnen Hängen, Abstürze oder andere Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien (wie etwa Screenshots, Ablaufverfolgungsdateien und Heap-Speicherabbilder) auf einfache Weise mithilfe des Tools **Problem melden** mit uns teilen. Weitere Informationen zur Verwendung dieses Tools finden Sie auf der Seite [Melden eines Problems](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Verfolgen Ihres Problems in Connect  
 Wenn Sie den Status Ihres Visual Studio-Feedbacks verfolgen möchten, rufen Sie [Connect](http://connect.microsoft.com/) auf, und melden Sie den Fehler dort. Nach der Meldung können Sie zu Connect zurückkehren, um den Status zu überprüfen.  

## <a name="see-also"></a>Siehe auch  
* [Neues in Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Neues in C#](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Neues für Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new)
* [Visual Studio – Anmerkungen zu dieser Version](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


