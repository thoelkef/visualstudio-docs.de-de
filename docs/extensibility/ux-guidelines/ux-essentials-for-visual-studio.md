---
title: 'UX: Grundlagen für Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52081c5a7f88a39ab25cf868164bd0258dd37885
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ux-essentials-for-visual-studio"></a>UX: Grundlagen für Visual Studio
## <a name="best-practices"></a>Bewährte Methoden  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. In der Visual Studio-Umgebung konsistent sein.  
  
-   Führen Sie die vorhandenen [interaktionsmustern](interaction-patterns-for-visual-studio.md) innerhalb der Shell.  
  
-   Entwerfen von Funktionen mit der Shell visuellen Sprache konsistent und [handwerkliches können Anforderungen](evaluation-tools-for-visual-studio.md).  
  
-   Verwenden Sie freigegebene Befehle und steuert, wenn sie vorhanden sind.  
  
-   Verstehen der Visual Studio-Hierarchie und wie Kontext wird und die Benutzeroberfläche steuert.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Verwenden Sie den Dienst Umgebung für Schriftarten und Farben.  
  
-   Berücksichtigt die aktuelle UI [Umgebungsschriftart](fonts-and-formatting-for-visual-studio.md) festlegen, es sei denn, es für die Anpassung auf der Seite für Schriftarten und Farben im Dialogfeld "Optionen" verfügbar gemacht wird.  
  
-   UI-Elemente verwenden, müssen die [VSColor Service](colors-and-styling-for-visual-studio.md), verwenden gemeinsam genutzter Umgebung Token oder featurespezifischen Token.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Stellen Sie alle Bilder konsistent mit den neuen VS-Stil.  
  
-   Führen Sie Visual Studio-Entwurfsprinzipien für Symbole, Symbole und andere Grafik.  
  
-   Fügen Sie Text nicht in grafische Elemente.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Im Hinblick auf benutzerzentrierte entwerfen.  
  
-   Erstellen Sie die Aufgabenverlauf, bevor Sie darin die einzelnen Funktionen.  
  
-   Mit Ihren Benutzern vertraut sein, und stellen Sie dieses Wissen in der Spezifikation explizit.  
  
-   Bei der Überprüfung der Benutzeroberflächenautomatisierungs bewerten Sie die vollständige Benutzeroberfläche als auch die Details.  
  
-   Entwerfen der Benutzeroberfläche, sodass funktionsfähig und unabhängig vom Gebietsschema oder Sprache visuell ansprechender bleibt.  
  
## <a name="screen-resolution"></a>Bildschirmauflösung  
  
### <a name="minimum-resolution"></a>Mindestauflösung  
 - Die minimale Auflösung für Visual Studio-Dev14 wird **1280 x 720**. Dies bedeutet, dass es *mögliche* , Visual Studio bei dieser Auflösung zu verwenden, obwohl es möglicherweise eine optimale benutzererfahrung nicht. Es gibt keine Garantie, dass alle Aspekte bei einer Auflösung von 1280 x 720 unterschritten verwendbar.  
  
 - Die zielauflösung für Visual Studio ist **1366 x 768**. Dies ist die niedrigste Auflösung, an dem wir versprechen, eine *gute* benutzererfahrung.

 - Höhe des ersten Dialogfeld muss **weniger als 700 Pixel**, sodass es in die minimale Auflösung der IDE-Fensterrahmens bei 96 dpi passt.
  
### <a name="high-density-displays"></a>HD zeigt  
 Benutzeroberfläche in Visual Studio muss funktionieren gut in alle DPI-Skalierung Faktoren, die der einsatzbereiten unterstützt: 150 % 200 % und 250 %.  
  
## <a name="anti-patterns"></a>Antimuster für  
 Visual Studio enthält viele Beispiele für die Benutzeroberfläche, die unsere Richtlinien und bewährten Methoden befolgen. In dem Bestreben, konsistent leihen Entwickler häufig aus Produkt UI-Entwurfsmuster ähnelt, die sie entwickeln. Obwohl dies ein guter Ansatz, hilft uns Konsistenz Eingreifen des Benutzers und den visuellen Entwurf Laufwerk, wir gelegentlich Funktionen mit einigen Details mitgeliefert werden, die nicht unsere Richtlinien aufgrund der Einschränkungen in Zeitplan erfüllen oder austragen Priorisierung ist. In diesen Fällen möchten wir nicht kopieren Sie eine der folgenden "Antimuster"-Teams, da sie breiten sich ungültige oder inkonsistente Benutzeroberfläche in Visual Studio-Umgebung.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Erforderliche Felder/Einstellungen, die standardmäßig im Status "Fehler" angezeigt  
  
#### <a name="feature-team-goals"></a>Feature Teamziele  
  
-   Warnen Sie Benutzer, dass sie ein Element hinzugefügt haben, die konfiguriert werden müssen.  
  
-   Der Benutzer Aufmerksamkeit auf die Bereiche, die Eingabe benötigen.  
  
#### <a name="anti-pattern-solution"></a>Antimuster für Projektmappen  
 Platzieren Sie als der Benutzer eine Aktion initiiert hat und bevor die Aufgabe abgeschlossen zu haben, sofort kritische Stop-Symbole neben den Bereichen, die Konfiguration benötigen.  
  
#### <a name="example-manifest-designer-declarations"></a>Beispiel: Manifest-Designer-Deklarationen  
 Eine Deklaration sofort zur Liste hinzufügen werden im Status "Fehler", die erhalten bleibt, bis der Benutzer die erforderlichen Eigenschaften festgelegt.  
  
 In diesem Fall eine zusätzliche Bedeutung vorhanden ist, da das Symbol für die Warnung enthält einen "&times;" Symbol ", sodass das allgemeine Symbol" entfernen "daneben verwendet werden kann. Daher verwendet die Benutzeroberfläche eine Remove-Schaltfläche, ein mehr umständliche-Steuerelement.  
  
 ![Platzieren der Benutzeroberfläche im Status "Fehler" Standardmäßig ist eine Antimuster für Visual Studio. ] (../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-Muster")<br />Platzieren der Benutzeroberfläche im Status "Fehler" Standardmäßig ist eine Antimuster für Visual Studio.
  
#### <a name="alternatives"></a>Alternativen  
 Eine bessere Lösung für dieses Problem zu würde folgendermaßen lauten:  
  
-   Ermöglicht dem Benutzer das Hinzufügen eine Deklaration ohne Warnung, und klicken Sie dann sofort zum Festlegen von Eigenschaften für das Element verschieben.  
  
-   Fügen Sie das Symbol "Warnung" (gold Dreieck) Wenn der Fokus wechselt von einem Element, z. B. eine andere Deklaration aus der Liste hinzuzufügen oder um versuchen, Registerkarten im Designer zu ändern.  
  
-   Wenn der Benutzer versucht, Registerkarten, die vor dem Festlegen von Eigenschaften für alle Deklarationen ändern, pop ein Dialogfeld darauf hingewiesen, dass die Anwendung nicht erstellen (oder die Auswirkungen auf die), bis die Warnungen aufgelöst werden. Wenn der Benutzer das Dialogfeld schließt und Registerkarten ändert wird trotzdem dann ein Symbol (kritisch oder Warnung, je nach Bedarf) auf der Registerkarte "Deklarationen" hinzugefügt.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Mehrere Klicks beim Schließen der Benutzeroberfläche  
  
#### <a name="feature-team-goals"></a>Feature Teamziele  
 Nicht erlaubt dem Benutzer die Benutzeroberfläche zu schließen, ohne dass den Text, der erste angezeigt.  
  
#### <a name="anti-pattern"></a>Antimuster für  
 Das Team, das Einfügen von Videolinks in verschiedenen Stellen in der Visual Studio-Benutzeroberfläche entschieden wird, mit dem allgemeinen Muster der "&times;" Schließen Schaltfläche und QuickInfo Erläuterung als UX gemäß und stattdessen eine Dropdown-implementiert und link "Nicht mehr anzeigen".  

#### <a name="example-video-links-in-team-explorer"></a>Beispiel: Videolinks in Team Explorer
Das Erzwingen des erläuternden Text zu lesen, bevor Sie verworfen wurde die Benutzeroberfläche des Benutzers ist ein Antimuster innerhalb von Visual Studio. Ordnungsgemäß entwickelten, video Links sollte eine QuickInfo mit weiteren Informationen angezeigt, wenn darauf gezeigt wird, und auf die "&times;" sollten verworfen werden, die Nachricht ohne weitere Interaktion erforderlich.


 ![Erläuternden Text anti-&#45;Muster &#45; falsch](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Falsche Videolinks-Muster
  
#### <a name="result"></a>Ergebnis  
 Anstatt eine einfache Schaltfläche "Schließen" (einem Mausklick) wird der Benutzer gezwungen, zwei aufeinander folgende Mausklicks zu verwenden, um die Benutzeroberfläche in jedem Ort einfach zu verwerfen, die Videolinks angezeigt werden.  
  
#### <a name="alternatives"></a>Alternativen  
 Der richtige Entwurf für diese Situation wäre das allgemeine Muster zu Internet Explorer, Office und Visual Studio folgen: Wenn darauf gezeigt wird, sieht der Benutzer kann die QuickInfo-Beschreibung und einem Mausklick Blendet Sie aus der Benutzeroberfläche.  
  
 ![Erläuternden Text anti-&#45;Muster &#45; richtig](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti Muster korrigieren")<br />Richtige video Link-Muster
  
### <a name="using-command-bars-for-settings"></a>Verwenden von Befehlsleisten für Einstellungen  
 **Abbildung A** stellt diese Antimuster: setzen eine Einstellung unter eine Befehlsschaltfläche, die auf mehr als nur den Befehl angewendet wird. In dieser Version stehen die folgenden Befehle neben Debuggen starten – wie im Browser starten ohne Debugging und Einzelschritt – berücksichtigt, die die ausgewählte Einstellung.  

  ![Abbildung A: Befehlsleisten Antimuster](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-Muster-FigureA")<br />Abbildung A: Antimuster Befehlsleiste
  
 Etwas bessere Leistung, aber dennoch unerwünschtem bedeutet die nichtkonfiguration Einstellungen dieses Typs in den Symbolleisten entsprechend **Abbildung B**. Während Steuerelemente für unterteilte Schaltflächen weniger Speicherplatz belegen und sind daher eine Verbesserung über Dropdowns, sind beide Entwürfe eine Symbolleiste weiterhin verwenden, um etwas höher stufen, die tatsächlich ein Befehl nicht.  
 
 ![Abbildung B: besser, aber dennoch eine Antimuster für Befehlsleiste](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Muster-FigureB")<br />Abbildung B: besser, aber immer noch eine Antimuster für Befehlsleiste
 
  In der richtige Ansatz gezeigt **Abbildung C**, die Einstellung an eine Reihe von Befehlen gebunden ist. Es gibt keine globale Einstellung wird festgelegt, und es sind nur Wechsel zwischen den vier Befehle. Dies ist die einzige Situation, in der Befehle auf der Symbolleiste zulässig sind. 

 ![Abbildung "c:" beheben Sie die Verwendung von Visual Studio-Befehlsleiste Muster](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Muster-FigureC")<br />Abbildung "c:" richtige Verwendung von Visual Studio-Befehlsleiste Muster
   
### <a name="control-anti-patterns"></a>Anti-Steuerelementmuster  
 Antimuster für einige sind einfach falsche Verwendung oder eine Präsentation eines Steuerelements oder einer Gruppe von Steuerelementen.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Unterstreichung verwendet wird, während eine gruppenbezeichnung nicht auf einen Link  
 Unterstrichenen Text sollte nur für Links verwendet werden.  
  
 **Ungültige:**    
 ![Unterstrichener Text, der nicht auf einen Link ist ist eine Antimuster für Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 G_GroupLabelIncorrect")<br />Unterstrichener Text, der nicht auf einen Link ist ist eine Antimuster für Visual Studio.
  
 **Gute:**   
 ![Richtig formatiert wurde, wird angezeigt, nicht Hyperlinktext einfacher in der Umgebungsschriftart. ] (../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 H_GroupLabelCorrect")<br />Richtig formatiert wurde, wird angezeigt, nicht Hyperlinktext einfacher in der Umgebungsschriftart.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Durch Klicken auf ein Kontrollkästchen-Ergebnisse in einem Popup-Dialogfeld  
 Durch Klicken auf das Kontrollkästchen "Remotedesktop für alle Rollen aktivieren" im Assistenten "Windows Azure-Anwendung veröffentlichen" sofort wird ein Popup-Dialogfeld eine Antimuster für Visual Studio. Darüber hinaus das Kontrollkästchen-Feld wird nicht aufgefüllt werden mit einem Kontrollkästchen nach ausgewählt wird, eine andere Aktivität Antimuster.  
  
 ![Schalten ein Dialogfeld, nachdem Sie ein Kontrollkästchen auf eine Antimuster für Visual Studio ist. ] (../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 I_CheckboxPopup")<br />Schalten ein Dialogfeld, nachdem Sie ein Kontrollkästchen auf eine Antimuster für Visual Studio ist.
  
### <a name="hyperlink-anti-patterns"></a>Antimuster für Hyperlink  
 Das folgende Beispiel enthält zwei Anti-Muster.  
  
1.  Hover einschalten roten Vordergrund bedeutet, dass die richtige freigegebene Farbe aus der Schriftartdienst nicht verwendet wird.  
  
2.  "Weitere" ist nicht die entsprechenden Text für einen Link auf ein grundlegendes Thema. Der Benutzer-Ziel ist nicht mehr zu erfahren, es um die Auswirkungen ihrer Wahl zu verstehen.  
  
 ![Ignorieren den Dienst für die Farbe und Verwenden von "Weitere" für Links sind Antimuster für Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 J_HyperlinkIncorrect")<br />Ignorieren den Dienst für die Farbe und Verwenden von "Weitere" für Links sind Antimuster für Visual Studio.  
  
 **Eine bessere Lösung:** die Frage, der Benutzer gefragt werden würde, indem Sie auf den Link, darstellen.  
  
-   Wie funktionieren die Windows Azure-Dienste?  
  
-   Wann benötige ich ein Windows Azure Mobile Services-Projekt?  
  
#### <a name="using-click-here-for-links"></a>Verwenden von "Klicken Sie hier" für Verknüpfungen zusammenfassen  
 Hyperlinks sollte selbstbeschreibend sein. Es ist ein Antimuster "Klicken Sie hier" verwenden oder eine ähnliche Variante.  
  
 **Ungültige:** "Klicken Sie hier, um Anweisungen zum Erstellen eines neuen Projekts."
  
 **Gut:** "Wie erstelle ich ein neues Projekt aus?"