---
title: UX Essentials für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a5f59dcb99c149e860244cde5f7dc0a30822578
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520738"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [UX Essentials für Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/ux-essentials-for-visual-studio).  
  
## <a name="best-practices"></a>Bewährte Methoden  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. In Visual Studio-Umgebung konsistent sein.  
  
-   Führen Sie die vorhandenen Interaktionsmuster innerhalb der Shell.  
  
-   Entwerfen Sie Funktionen mit der Shell visual Sprache und handwerkliches können Anforderungen konsistent sein.  
  
-   Verwenden Sie freigegebene Befehle und Steuerelemente aus, wenn sie vorhanden sind.  
  
-   Verstehen Sie die Visual Studio und wie die Anwendung Kontext wird und die Benutzeroberfläche steuert.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Verwenden Sie die Umgebung-Dienst für Schriftarten und Farben.  
  
-   Benutzeroberfläche sollte die aktuelle Schriftart umgebungseinstellung berücksichtigen, es sei denn, es für die Anpassung auf der Seite "Schriftarten und Farben" in das Dialogfeld "Optionen" verfügbar gemacht wird.  
  
-   UI-Elemente müssen die VSColor Service mit gemeinsam genutzten Umgebung Token oder featurespezifische-Token verwenden.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Stellen Sie alle Bilder konsistent mit dem neuen Visual Studio-Stil.  
  
-   Führen Sie Visual Studio-Entwurfsprinzipien für Symbole, Symbole und andere Grafik aus.  
  
-   Platzieren Sie Text in grafischen Elementen nicht.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Vom Standpunkt der benutzerorientierten entwerfen.  
  
-   Erstellen Sie die Aufgabenverlauf, bevor Sie darin die einzelnen Funktionen.  
  
-   Mit Ihren Benutzern vertraut sein, und machen Sie dieses Wissen in Ihrem-Spezifikationen explizit.  
  
-   Bei der Überprüfung der Benutzeroberflächenautomatisierungs bewerten Sie die vollständige Benutzeroberfläche als auch die Details.  
  
-   Entwerfen Sie die Benutzeroberfläche so, dass sie funktionsfähig und unabhängig vom Gebietsschema oder der Sprache attraktive bleibt.  
  
## <a name="screen-resolution"></a>Bildschirmauflösung  
  
### <a name="minimum-resolution"></a>Mindestauflösung  
 Die minimale Auflösung für Visual Studio-Dev14 wird 1280 x 1024. Dies bedeutet, dass es *möglich* mit Visual Studio diese Auflösung, obwohl es nicht die optimale benutzerfreundlichkeit möglicherweise. Es gibt keine Garantie, dass alle Aspekte bei einer Auflösung von 1280 x 1024 kleiner verwendet werden können.  
  
 Größe des ersten Dialogfelds sollte 1000 Pixel hoch, um im Rahmen der IDE innerhalb dieser minimale Auflösung mit 96 dpi passen nicht überschreiten.  
  
### <a name="high-density-displays"></a>Mit hoher Dichte zeigt  
 Benutzeroberfläche in Visual Studio muss funktionieren gut in alle DPI-Skalierung von Faktoren, die von Windows unterstützt: 150 %, 200 % und 250 %.  
  
## <a name="anti-patterns"></a>Anti-Muster  
 Visual Studio enthält viele Beispiele der Benutzeroberfläche, die unsere Richtlinien und bewährte Methoden befolgen. In dem Bestreben konsistent ist nutzen die Entwickler häufig aus Produkt UI-Entwurfsmuster ähnelt, was sie erstellen. Obwohl dies ein guter Ansatz, hilft uns Konsistenz bei der Interaktion des Benutzers und den visuellen Entwurf fördern, wir gelegentlich Funktionen mit ein paar Details mitgeliefert werden, die nicht erfüllt unsere Richtlinien aufgrund der Einschränkungen in Zeitplan oder vollziehen des Austritts Priorisierung ist. In diesen Fällen möchten wir Teams, kopieren Sie eine der folgenden "Anti-Muster" nicht, weil sie ungültige oder inkonsistente UI in Visual Studio-Umgebung angelegt.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Erforderliche Felder/Einstellungen, die standardmäßig im Status "Fehler" angezeigt  
  
#### <a name="feature-team-goals"></a>Feature-Team-Ziele  
  
-   Warnen Sie Benutzer, dass sie ein Element hinzugefügt haben, die konfiguriert werden müssen.  
  
-   Zeichnen Sie die Aufmerksamkeit des Benutzers auf die Bereiche, die Eingabe benötigen.  
  
#### <a name="anti-pattern-solution"></a>Antimuster für Projektmappen  
 Platzieren Sie, sobald der Benutzer eine Aktion initiiert hat und bevor sie die Aufgabe abgeschlossen haben, sofort kritische Hand Symbole neben den Bereichen, die Konfiguration erforderlich.  
  
#### <a name="example-manifest-designer-declarations"></a>Beispiel: Manifest-Designer-Deklarationen  
 Eine Deklaration direkt zur Liste hinzufügen werden in einem Fehlerzustand befindet, die persistent gespeichert, bis der Benutzer die erforderlichen Eigenschaften festlegt.  
  
 In diesem Fall gibt es eine zusätzliche Bedeutung ist, da das Symbol für die Warnung, das ein "X" enthält, daher entfernen die allgemeinen kann nicht das Symbol neben verwendet werden. Daher wird die Benutzeroberfläche eine Schaltfläche "entfernen" ein mehr umständlich Steuerelement verwendet.  
  
 ![Manifest-Designer-Fehler Deklaration anti-&#45;Muster](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-Muster")  
  
 **Benutzeroberfläche in einem Fehlerzustand platzieren, in der Standardeinstellung ist ein Visual Studio-Anti-Muster.**  
  
#### <a name="alternatives"></a>Alternativen  
 Eine viel bessere Lösung für dieses Problem wäre auf:  
  
-   Erlaubt dem Benutzer eine Deklaration ohne Warnung hinzufügen, und klicken Sie dann sofort zum Festlegen von Eigenschaften für das Element verschieben.  
  
-   Fügen Sie das Symbol "Warnung" (gold Dreieck) Wenn der Fokus aus dem Element, wie z. B. eine andere Deklaration zur Liste hinzufügen oder versuchen, die Registerkarten im Designer zu ändern.  
  
-   Wenn der Benutzer versucht, die Registerkarten ändert, vor dem Festlegen von Eigenschaften für alle Deklarationen, pop ein Dialogfeld darauf hingewiesen, dass die Anwendung nicht erstellt werden (oder alle der Auswirkungen), bis die Warnungen aufgelöst werden. Wenn der Benutzer das Dialogfeld schließt und Registerkarten wird trotzdem klicken Sie dann ein Symbol (kritisch oder Warnung, je nach Bedarf) zur Registerkarte "Deklarationen" hinzugefügt.  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Erzwingen des Benutzers Text zu lesen, vor dem Schließen der Benutzeroberfläche  
  
#### <a name="feature-team-goals"></a>Feature-Team-Ziele  
 Keine ermöglicht dem Benutzer um die Benutzeroberfläche zu schließen, ohne zuerst den erläuternden Text anzeigen zu lassen.  
  
#### <a name="anti-pattern"></a>Anti-Muster  
 Das Team diese Videolinks an verschiedenen Stellen innerhalb der Visual Studio-Benutzeroberfläche entschieden, das allgemeine Muster, der ein "X" Einfügen Schaltfläche und QuickInfo Erklärung gemäß der UX zu schließen, und stattdessen implementiert eine Dropdownliste und einen Link "Nicht mehr anzeigen".  
  
 ![Erklärender Text anti-&#45;Muster &#45; falsche](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **Falsch: Erzwingen von erklärendem Text lesen Sie vor dem Schließen der Benutzeroberfläche der Benutzer ist ein Anti-Muster in Visual Studio.**  
  
#### <a name="result"></a>Ergebnis  
 Anstelle einer einfachen Schaltfläche "Schließen" (einem Klick) wird der Benutzer gezwungen, zwei aufeinander folgende Mausklicks zu verwenden, um die Benutzeroberfläche an jeder Stelle einfach zu verwerfen, die diese Videolinks angezeigt werden.  
  
#### <a name="alternatives"></a>Alternativen  
 Der richtige Entwurf für diese Situation wäre das allgemeine Muster zur Internet Explorer, Office und Visual Studio folgen: Wenn darauf gezeigt wird, kann dem Benutzer die QuickInfo-Beschreibung angezeigt, und nur einem Klick wird die Benutzeroberfläche ausgeblendet.  
  
 ![Erklärender Text anti-&#45;Muster &#45; richtig](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-Muster-korrigieren")  
  
 **Richtig: wie vorgesehen ist, sollte Videolinks eine QuickInfo mit weiteren Informationen angezeigt, wenn darauf gezeigt wird, und klicken Sie auf das "X" sollte die Meldung ohne weitere Interaktion schließen.**  
  
### <a name="using-command-bars-for-settings"></a>Mithilfe der Befehlsleisten für Einstellungen  
 ![Befehlsleiste anti-&#45;Muster &#45; Abbildung A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-Muster – FigureA")  
  
 **Abbildung A: Antimuster Befehlsleiste**  
  
 **Abbildung A** dieses Antimuster darstellt: platzieren eine Einstellung unter eine Befehlsschaltfläche, die auf mehr als nur den Befehl angewendet wird. Bei dieser Version stehen die folgenden Befehle, die neben dem Debugging starten –-ähnliche Ansicht in Browser starten ohne Debugging sowie schrittweise ausführen –, die die ausgewählte Einstellung berücksichtigt.  
  
 ![Befehlsleiste anti-&#45;Muster &#45; Abbildung B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Muster – FigureB")  
  
 **Abbildung b besser, aber immer noch ein Antimuster für Befehlsleiste**  
  
 Etwas bessere Leistung, der aber dennoch unerwünschtem, wäre, Einstellungen dieses Typs in den Symbolleisten, siehe **Abbildung B**. Unterteilte Schaltflächen belegen weniger Speicherplatz und sind daher eine Verbesserung über die Dropdown-Elemente, werden beide Entwürfe eine Symbolleiste weiterhin verwendet, um etwas höher zu stufen, die einen Befehl handelt es sich nicht.  
  
 ![Befehlsleiste anti-&#45;Muster &#45; Abbildung C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Muster – FigureC")  
  
 **Abbildung "c:" richtige Verwendung von Visual Studio-Befehlsleiste Befehlsmuster**  
  
 In **Abbildung C**, die Einstellung an eine Reihe von Befehlen gebunden ist. Es gibt keine globale Einstellung festgelegt wird, und wir nur zwischen vier Befehle wechseln. Dies ist die einzige Situation, in der Befehle auf der Symbolleiste zulässig sind.  
  
### <a name="control-anti-patterns"></a>Anti-Steuerelementmuster  
 Einige Antimuster für sind einfach falsche Verwendung oder eine Präsentation eines Steuerelements oder einer Gruppe von Steuerelementen.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Unterstreichungen, die verwendet werden, während eine gruppenbezeichnung, nicht auf einen Link  
 Unterstrichenen Text sollte nur für Links verwendet werden.  
  
 **Ungültige:**  
  
 ![Anti-Unterstreichung&#45;Muster in gruppenbeschriftungen](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102-G_GroupLabelIncorrect")  
  
 **Unterstrichener Text, der keinen Link ist ein Visual Studio-Anti-Muster.**  
  
 **Gute:**  
  
 ![Anti-Unterstreichung&#45;Muster in gruppenbeschriftungen &#40;richtig&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102-H_GroupLabelCorrect")  
  
 **Richtig formatiert wurde, wird angezeigt, nicht-Hyperlink-Text nicht erweiterten in die Umgebungsschriftart.**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Durch Klicken auf ein Kontrollkästchen-Ergebnisse in einem Popupdialogfeld  
 Klicken im Assistenten "Windows Azure-Anwendung veröffentlichen" das Kontrollkästchen "Remotedesktop für alle Rollen aktivieren" sofort wird ein Popup-Dialogfeld ein Visual Studio-Anti-Muster. Darüber hinaus das Kontrollkästchen ist nicht ausfüllen des Feldes mit einem Kontrollkästchen nach ausgewählt wird, ein weiteres Anti-Interaktionsmuster.  
  
 ![Kontrollkästchen Pop&#45;Stand Anti&#45;Muster](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102-I_CheckboxPopup")  
  
 **Nach dem Klicken auf ein Kontrollkästchen ein Visual Studio-Anti-Muster wird aufzurufen ein Dialogfeld.**  
  
### <a name="hyperlink-anti-patterns"></a>Antimuster für Hyperlink  
 Das folgende Beispiel enthält zwei Antimuster.  
  
1.  Im Vordergrund roten aktivieren, wenn darauf gezeigt wird also nicht die richtige freigegebene Farbe aus dem Schriftartdienst verwendet wird.  
  
2.  "Weitere Informationen" ist nicht den entsprechenden Text einen Link auf ein grundlegendes Thema. Des Benutzers Ziel ist nicht mehr, erfahren, um die Auswirkungen ihrer Wahl zu verstehen ist.  
  
 ![Hyperlink anti-&#45;Muster](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102-J_HyperlinkIncorrect")  
  
 **Ignorieren den Dienst für die Farbe, und Verwenden von "Erfahren Sie mehr" für Links sind Antimuster für Visual Studio.**  
  
 **Bessere Lösung:** stellten die Frage, die der Benutzer auf den Link bitten würden.  
  
-   Wie funktionieren die Windows Azure-Dienste?  
  
-   Wann benötige ich ein Windows Azure Mobile Services-Projekt?  
  
#### <a name="using-click-here-for-links"></a>Mithilfe von "Hier klicken", links  
 Links sollte erklären sich von selbst. Es ist ein Anti-Muster verwenden "Hier klicken" oder eine ähnliche Variante.  
  
 **Ungültige:** "Klicken Sie hier, um Anweisungen zum Erstellen eines neuen Projekts."  
  
 **Gut:** "Wie erstelle ich ein neues Projekt aus?"

