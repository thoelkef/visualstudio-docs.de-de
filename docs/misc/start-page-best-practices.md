---
title: "Startseite – Bew&#228;hrte Methoden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Startseite – Tipps"
  - "Startseite – Bewährte Methoden"
  - "Startseite – Entwurf"
ms.assetid: f6ce1ce0-746e-4004-a37f-6f176f6f5851
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Startseite – Bew&#228;hrte Methoden
Da die Startseite auf Visual Studio\-Befehle zugreifen kann und bei jedem Laden von Visual Studio geöffnet wird, sollten Sie die Stabilität aller benutzerdefinierten Startseiten sicherstellen, bevor Sie diese verwenden oder verteilen. In diesem Abschnitt werden bewährte Vorgehensweisen für einen stabilen Entwurf der Startseite empfohlen. Zudem sind Richtlinien zum Erstellen einer nützlichen Benutzeroberfläche \(UI\) enthalten.  
  
## Richtlinien zur Stabilität  
  
### Ressourcenverfügbarkeit  
 Der wichtigste Aspekt bei der Erstellung einer stabilen benutzerdefinierten Startseite besteht darin sicherzustellen, dass alle erforderlichen Ressourcen verfügbar sind:  
  
-   Alle erforderlichen Pakete sind installiert.  
  
-   Die Pakete werden vorab geladen.  
  
-   Alle erforderlichen Assemblys befinden sich im Ordner „\\PrivateAssemblies\\“.  
  
-   Jede Komponente, die eine Netzwerk\- oder Internetverbindung verwendet, verfügt über alternative Pfade für Offlineszenarien und unterbrochene Verbindungen.  
  
### Leistung  
 Berücksichtigen Sie die Auswirkungen auf die Leistung beim Start, wenn Ihre Startseite hohe Anforderungen an den Arbeitsspeicher stellt oder viele Ressourcen lädt. Programmieren Sie diese Startseiten entsprechend, dass Komponenten bedarfsgesteuert oder nach Möglichkeit im Hintergrund geladen werden, damit sich die Startzeit nicht maßgeblich erhöht.  
  
### Entwicklungsprozess  
 Wenn Sie die aktive Startseite direkt ändern, können Sie versehentlich Fehler einführen, die einen Absturz von Visual Studio verursachen können. Da die Startseite bei jedem Öffnen von Visual Studio ebenfalls geöffnet wird, ist das Problem einer abstürzenden Startseite schwer zu beheben. Aus diesem Grund wird empfohlen, dass Sie Kopien der Startseitendateien ändern und diese in einer experimentellen Instanz von Visual Studio auf ihre Zuverlässigkeit testen. Wenn die neue Startseite einwandfrei funktioniert, können Sie sie in der primären Instanz von Visual Studio ausführen.  
  
> [!NOTE]
>  Außerdem wird empfohlen, dass sämtliche Startseiten von Drittanbietern in einer experimentellen Instanz von Visual Studio getestet werden, bevor Sie sie in der primären Instanz verwenden.  
  
##### So testen Sie eine Startseite in einer experimentellen Instanz von Visual Studio  
  
1.  Wenn Sie die Projektvorlage für Startseiten verwenden, drücken Sie F5. Andernfalls gilt:  
  
    1.  Kopieren Sie die XAML\-Datei und sämtlichen unterstützenden Text oder Markup nach „\\%USERPROFILE%\\My Documents\\Visual Studio *\<Version\>*\\StartPages\\“.  
  
    2.  Kopieren Sie alle erforderlichen Assemblys nach „*\<Visual Studio\-Installationspfad\>*\\Common7\\IDE\\PrivateAssemblies\\“.  
  
    3.  Öffnen Sie eine experimentelle Instanz von Visual Studio über den folgenden Befehl an einer Visual Studio\-Eingabeaufforderung.  
  
         **Devenv \/rootsuffix exp**  
  
2.  Klicken Sie im Menü **Extras** auf **Optionen**. Wählen Sie **Umgebung** und dann **Start** aus. Wählen Sie in der Liste **Startseite anpassen** die umbenannte Datei „StartPage.xaml“ aus, und klicken Sie dann auf **OK**.  
  
3.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Die benutzerdefinierten Startseite wird geöffnet. Wenn die von Ihnen bearbeitete Startseite abstürzt, können Sie die primäre Instanz von Visual Studio neu starten, die erforderlichen Korrekturen vornehmen und dann eine andere experimentelle Instanz öffnen, damit Sie die Änderung an der benutzerdefinierten Startseite fortsetzen können.  
  
 Wenn die primäre Instanz von Visual Studio durch Ihre Startseite abstürzt, können Sie benutzerdefinierte Startseiten vorübergehend deaktivieren, indem Sie für den Registrierungswert von „HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\CustomizationEnabled“ den Wert „0“ festlegen. Alternativ können Sie die XAML\-Datei für Ihre aktuelle Standardstartseite vorübergehend umbenennen. Beide Methoden ermöglichen es Ihnen, Visual Studio ausreichend lange zu öffnen, um den Fehler zu beheben.  
  
### Debugging  
 Das Toolfenster der Startseite erfasst Ausnahmen beim Laden einer Startseite ab, aber anschließend werden keine Ausnahmen mehr erfasst. Sie können Visual Studio entsprechend anweisen, dass alle nicht behandelten Ausnahmen angezeigt werden, indem Sie den folgenden Registrierungswert auf „1“ festlegen.  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\General\\EnableUnhandledExceptionDisplay  
  
 Die Informationen zur Ausnahme werden in einem Meldungsfeld angezeigt, wodurch Sie Steuerelemente auf einer Startseite oder an anderen unbehandelten Positionen debuggen können, d. h. selbst in der primären Instanz von Visual Studio. Wenn das Debuggen nach dem Auslösen der Ausnahme nicht möglich ist, können Sie Visual Studio mit dem Befehl „devenv\/safemode“ neu starten, zur vorherigen Startseite zurückkehren und dann das Debuggen in der experimentellen Instanz fortsetzen.  
  
### Relative Pfade  
 Wenn Sie auf einer Startseite auf Dateipfade verweisen, verwenden Sie immer einen relativen Pfad, um unterschiedliche Systemkonfigurationen zu ermöglichen. Allerdings löst der Stamm aller relativen Pfade auf einer Startseite nicht den Ordner „\\StartPages\\“ in „..\\*Visual Studio\-Installationsordner*\\Common7\\IDE“ auf, in dem sich die Datei „devenv.exe“ befindet. Verwenden Sie den Konverter von Visual Studio für relative Pfade auf Startseiten, um einen Pfad relativ zum Ordner „\\StartPages\\“ festzulegen. Legen Sie dazu die `Source`\-Eigenschaft des Objekts auf `vs:StartPageRelative` fest, wie im folgenden Beispiel gezeigt.  
  
 XAML  
  
```  
<Image Source="{vs:StartPageRelative myImage.png}" .../>  
```  
  
 Verwenden Sie die standardmäßige relative Pfadsyntax beim Zugriff auf in Visual Studio enthaltene Ressourcen oder auf in anderen Paketen einbezogene Dateien.  
  
### Bereitstellung  
 Die folgenden bewährten Methoden werden zum Bereitstellen einer benutzerdefinierten Startseite für andere Benutzer empfohlen.  
  
#### Benutzereinstellungen  
  
-   Berücksichtigen Sie die Benutzereinstellungen. Überschreiben Sie keine vorhandenen Einstellungen der Startseite.  
  
#### VSIX  
 Diese Methoden gelten für die VSIX\-Bereitstellung:  
  
-   Verwenden Sie das [GettingStartedGuide](http://msdn.microsoft.com/de-de/261bb1fd-abae-4ed6-80a8-90d5fc3bb8c6)\-Element im VSIX\-Manifest, um auf Anweisungen zum Festlegen der Standardstartseite zu verweisen.  
  
-   Verwenden Sie die Elemente [Name](http://msdn.microsoft.com/de-de/d99d38d1-060b-401a-9b9f-ede2c6213a11) und [Description](http://msdn.microsoft.com/de-de/24ddc57e-e991-4a43-b0c9-0e76da293e99) des VSIX\-Manifests, um die Erweiterung eindeutig als Startseite zu kennzeichnen und ihren Zweck zu beschreiben.  
  
-   Stellen Sie sicher, dass das VSIX\-Manifest keine absoluten Pfade enthält.  
  
-   Beziehen Sie beim Hochladen auf die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847)\-Website die relevanten Tags ein, damit die Erweiterung von Benutzern als Startseite erkannt werden kann.  
  
#### MSI  
 Wenn Sie eine Startseite als Teil einer größeren Erweiterung erstellen, die Sie in einem MSI\-Paket \(Windows Installer\) bereitstellen, können Sie für die Startseite festlegen, dass sie als Standardstartseite auf dem Zielcomputer installiert wird. Zu diesem Zweck geben Sie den Namen der XAML\-Datei der Startseite als URI\-Wert des folgenden Registrierungsschlüssels ein: „HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\“. Verwenden Sie beim Festlegen dieses Registrierungswerts die folgenden Richtlinien:  
  
-   Stellen Sie im Installer eine Benutzeroberfläche bereit, damit der Benutzer auswählen kann, ob die neue Startseite als Standard festgelegt werden soll.  
  
-   Wenn der Benutzer die Erweiterung deinstalliert, stellen Sie den vorherigen Registrierungswert wieder her.  
  
### Windows Presentation Framework \(WPF\)  
 Das XAML\-Markup muss die für das WPF bewährten Methoden befolgen. Informationen zu den bewährten Methoden für [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] und [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] für die Anwendungsentwicklung finden Sie entsprechend unter den folgenden Themen.  
  
|Bereich|Thema|  
|-------------|-----------|  
|Barrierefreiheit|[Accessibility Best Practices](../Topic/Accessibility%20Best%20Practices.md)|  
|Lokalisierung|[Übersicht über WPF\-Globalisierung und \-Lokalisierung](../Topic/WPF%20Globalization%20and%20Localization%20Overview.md)|  
|Leistung|[Optimieren der WPF\-Anwendungsleistung](../Topic/Optimizing%20WPF%20Application%20Performance.md)|  
|Sicherheit|[Sicherheit \(WPF\)](../Topic/Security%20\(WPF\).md)|  
  
## Richtlinien zur Benutzeroberfläche  
 Verwenden Sie die folgenden Richtlinien zur Benutzeroberfläche, sofern zutreffend, um eine einfache, intuitive und benutzerfreundliche Startseite zu gewährleisten.  
  
### Oberste Zeile  
  
#### Banner  
  
-   Verwenden Sie für die Höhe des Bannerbilds dieselbe Höhe wie für die Höhe der Zeilendefinition der Zeile, in der es enthalten ist.  
  
-   Gestalten Sie das Bannerbild in beliebiger Breite optisch ansprechend, damit es sich entsprechend an die verschiedenen Fensterformate und Bildschirmauflösungen anpasst.  
  
-   Sorgen Sie für einen übersichtlichen Bannerbereich. Überlagern Sie das Logo nicht mit zusätzlichen Schaltflächen oder Grafiken.  
  
### Linke Spalte  
  
#### Schaltflächenbereich  
  
-   Fügen Sie nur die am häufigsten verwendeten Steuerelemente zum Schaltflächenbereich hinzu, damit ausreichend Platz für die Namen der zuletzt geöffneten Projekte vorhanden ist. Es wird empfohlen, weniger als fünf Schaltflächen zu verwenden.  
  
#### Zuletzt geöffnete Projekte  
  
-   Über dieses Steuerelement können Benutzer auf zuletzt geöffnete Projekte zugreifen. Sie können für die Anzahl der anzuzeigenden Projekte einen Wert zwischen 0 und 24 festlegen. Da dies der am häufigsten verwendete Bereich der Startseite ist, wird empfohlen, ihn nicht zu entfernen.  
  
#### Startseitenoptionen  
  
-   Stellen Sie sicher, dass die Optionen **Seite nach dem Laden des Projekts schließen** und **Seite beim Start anzeigen** auf der Startseite angezeigt werden.  
  
-   Wenn Sie weitere Steuerelemente in diesem Bereich verwenden möchten, wird empfohlen, dass Sie Kontrollkästchen oder Optionsfelder verwenden und sicherstellen, dass sich die Steuerelemente auf die Einstellungen der Startseite beziehen.  
  
### Inhaltsbereich  
  
#### Registerkarten der obersten Ebene  
  
-   Vermeiden Sie das Hinzufügen zu vieler Registerkarten, damit das Registerkarten\-Steuerelement nicht bei üblichen Bildschirmbreiten umgebrochen wird.  
  
-   Verwenden Sie kurze, beschreibende Namen für die Registerkarten.  
  
-   Stellen Sie sicher, dass Registerkarten gruppierte Inhaltsbereiche darstellen.  
  
#### Registerkarten der Unterebene  
  
-   Verwenden Sie die untergeordnete Navigation nur, wenn Sie über mehr als zwei Unterthemen verfügen.  
  
-   Vermeiden Sie das Hinzufügen zu vieler Registerkarten, damit das Registerkarten\-Steuerelement nicht bei üblichen Bildschirmbreiten umgebrochen wird.  
  
-   Verwenden Sie kurze, beschreibende Namen für die Registerkarten.  
  
#### Registerkarteninhalte der Unterebene  
  
-   Zeigen Sie nicht mehr als fünf Inhaltselemente auf einer Registerkarte der Unterebene an.  
  
#### Elementinhalt  
  
-   Zeigen Sie nicht mehr als vier Links pro Inhaltselement an.  
  
-   Wenn Sie Inhaltselementen Bilder zuordnen, stellen Sie sicher, dass jedes Bild 175x125 Pixel umfasst.  
  
-   Verwenden Sie kurze, beschreibende Titel für Inhaltselemente.  
  
-   Beschränken Sie Beschreibungen für Inhaltselemente auf zwei oder weniger Sätze.  
  
### Allgemein  
  
#### Animations  
  
-   Wenn Sie Animationen verwenden, beschränken Sie diese auf 0,5 Sekunden oder weniger, um zu verhindern, dass dies zu schlechten Leistungen führt.  
  
#### Umgebungsfarben  
  
-   Berücksichtigen Sie die Systemeinstellungen für Schriftarten und Farben.  
  
-   Verwenden Sie helle Farben für Hintergründe.  
  
-   Verwenden Sie die Remotedesktoperkennung, um eine ordnungsgemäße Herabstufung von Farben in Remotesitzungen sicherzustellen.  
  
## Siehe auch  
 [Architektur der Startseite](../misc/start-page-architecture.md)   
 [Bereitstellen von benutzerdefinierte Startseiten](../extensibility/deploying-custom-start-pages.md)   
 [Hinzufügen von Visual Studio\-Befehle zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)