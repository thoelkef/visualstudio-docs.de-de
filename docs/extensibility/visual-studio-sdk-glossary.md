---
title: "Glossar f&#252;r Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glossar [Visual Studio SDK]"
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Glossar f&#252;r Visual Studio SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Glossar enthält Definitionen für Begriffe, mit denen in der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Dokumentation.  
  
## Begriffe  
 Add\-Ins  
 Ein Hilfsprogramm\-Anwendung, Treiber oder andere Software, die eine primäre Anwendung hinzugefügt. In der Visual Studio IDE \(IDE\) ist ein Add\-in eine Automatisierung basierende Anwendung, die die Funktionen der IDE erweitert.  
  
 Benutzeroberflächenautomatisierungs\-Modell  
 Das Automatisierungsmodell in früheren Versionen von Visual Studio als das Erweiterbarkeitsmodell bekannt ist eine Programmierschnittstelle, die Ihnen sofortigen Zugriff auf die zugrunde liegenden Routinen der IDE. Von Add\-Ins, Assistenten und Makros verwenden Objekte im Automatisierungsmodell zu steuern oder Erweitern der Funktionen der IDE.  
  
 Befehl Benutzeroberflächenkontext  
 Die Zuordnung einer GUID mit der Sichtbarkeit eines UI\-Befehl oder ein Element wie z. B. eine Symbolleiste. Benutzeroberflächenkontext Befehl ist im Gegensatz zu den Auswahlkontext, da es nicht mit einem Fenster verbunden ist.  
  
 Befehl Benutzeroberflächenkontext verwendet werden kann:  
  
-   Weisen Sie eine GUID in eine Symbolleiste, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert wird.  
  
-   Weisen Sie eine GUID für die Verfügbarkeit eines Befehls, ohne zu laden, oder führen Sie ein VSPackage.  
  
-   Weisen Sie eine GUID zur aktiven Tastenkombination auswirken.  
  
-   Weisen Sie eine GUID zur Aufzeichnung von Makros zu aktivieren.  
  
-   Weisen Sie eine GUID zum Aktivieren der Debug\-Modus oder zum Umschalten zwischen Entwurfs\- und Ausführungsmodus in einem Editor.  
  
 component  
 Softwarekomponente, die Teil der Funktionalität einer Anwendung ohne die Anwendung alle bereits vorhandenen Informationen zur Implementierung der Software vorgenommen werden können. Kommunikation zwischen einer Komponente und eine Anwendung ist ausschließlich über Schnittstellen für OLE\-Stil.  
  
 Der Standortkomponenten\-manager  
 Ein Dienst `SOleComponentManager`, die nicht\-Benutzeroberfläche Koordinierung Services für die Komponenten der obersten Ebene bereitstellt. Die `SOleComponentManager` \-Dienst implementiert die `IOleComponentManager` Schnittstelle.  
  
 UI\-Standortkomponenten\-manager  
 Ein Dienst `SOleComponentUIManager`, die Schnittstelle Koordinierung Dienste bereitstellt. Die `SOleComponentUIManager` \-Dienst implementiert die `IOleComponentUIManager` und `IOleInPlaceComponentUIManager` Schnittstellen.  
  
 kontextbehälter  
 Ein `IVsUserContext` \(COM\-Objekt\) zu einer Umgebung Komponente angefügt. Dieses Objekt enthält die Lookup\-Schlüsselwörter, F1\-Schlüsselwörter und Attribute, die der Komponente zugeordnet sind. Kontext Taschen zeigen Sie außerdem auf alle Unterkontext\-Sammlungen, die mit ihnen verknüpft werden.  
  
 Kontextanbieter  
 Eine Komponente in der IDE, die einen kontextbehälter zugeordnet wurde. Diese Komponenten umfassen ein Toolfenster, Editor oder Projekthierarchie.  
  
 Designer  
 Eine Programmierschnittstelle, die Benutzern ermöglicht, Elemente der Benutzeroberfläche \(Formulare, Schaltflächen und andere Steuerelemente\) bearbeiten.  
  
 DocData  
 Ein COM\-Objekt, das die zugrunde liegenden Daten eines Dokuments in einer Welt kapseln Trennung von Dokument\/Ansicht vorhanden ist \(z. B. im Text\-Editor Fall wäre dies Textpuffer zugrunde liegenden alle Ansichten der Text\-Editor\). Wenn der EditorFactory dieses Objekt nicht angegeben wird, wird die IDE eine in seinem Auftrag produzieren. Die Verantwortung für dieses Objekt wird zum Verwalten der Dauerhaftigkeit von Daten und die Freigabe Semantik für mehrere Ansichten über diese dieselbe `DocData`. Wenn die `DocData` \-Objekt unterstützt die `IOleCommandTarget` \-Schnittstelle wird in der Befehlsrouting die UIShell aufgenommen.  
  
 DocObject  
 Technologie für die UI innerhalb eines Frames, die vom Host bereitgestellt wurde. Genauer gesagt, dieser Begriff verweist auf alle einbetten, die unterstützt die `IOleDocument` und entsprechende Schnittstellen. Diese Technologie hat viele potenzielle Clientanwendungen wie z. B. ein Implementierungsdetail des COM\-Dokumente, Toolfenster in Visual Basic 5.0, ActiveX\-Designer in Visual Basic 6.0, und So weiter.  
  
 Dokument  
 Oberbegriff für das Dokument als Ganzes verwendet – sowohl die `DocData` und `DocView`. Ein DocumentFrame enthält z. B. eine `DocView`, aber auch behält einen Verweis auf die `DocData` Dauerhaftigkeit zu behandeln.  
  
 DocView  
 Die mit dem der Benutzer interagiert, um anzeigen und Bearbeiten der zugrunde liegenden DocObject\/Embedding\/Fensterbereichs `DocData`. Beachten Sie, dass Benutzer nicht die Trennung von Dokument\/Ansicht nutzen, die Teil der `DocObject` Schnittstellenentwurf. Benutzer verwenden eine gesamte DocObject als eine Ansicht anstatt Konzept abstrakter \(und weniger formalisierte\) der zugrunde liegenden Daten genannt `DocData`.`DocView` Objekte werden immer mit Frame\-Dokumentobjekte \(untergeordnete MDI\-Fenster\) der IDE eingebettet.  
  
 DTE  
 Die `DTE` \(Development Tools Extensibility\)\-Objekt ist das oberste Zugriffspunkt in Visual Studio\-Automatisierungsmodells, wodurch Sie programmgesteuert automatisieren und Erweitern der IDE.  
  
 Dynamisches Hilfefenster  
 Toolfenster, die von der IDE implementiert wird, und zeigt eine Liste der Lookup\-Schlüsselwort oder F1\-Hilfethemen.  
  
 Editor  
 Code \(Klassen, CLSID\) für die Implementierung der `DocView`. Es implementiert auch `DocData` wenn die Trennung der Daten anzeigen\/unterstützt wird.  
  
 Erweiterung  
 Eine Funktion, die geändert werden, passt, oder einer IDE hinzugefügt. Erstellen Sie mithilfe des Automatisierungsmodells oder VSPackages Erweiterungen.  
  
 externen editor  
 Ein Editor, der nicht spezifisch für die IDE, z. B. Microsoft Word ist. Es wurde durch eine eigene Mechanismen registriert und außerhalb der IDE verwendet werden kann. Wenn dieser Editor eingebettet werden kann, wird es in einem Fenster in der IDE angezeigt. Wenn er nicht eingebettet werden kann, wird ein separates Fenster oberster Ebene erstellt.  
  
 Hierarchie  
 Struktur von Knoten, die jedem Knoten, der einen Satz von Eigenschaften zugeordnet.  
  
 unabhängige Komponente der obersten Ebene  
 Eine Komponente, die ein nicht modales Fenster oberster Ebene verwendet und kann als eigenständige Anwendungsfenster effektiv eingesetzt, aber als in\-Process\-Objekt implementiert wird. Aus diesem Grund muss eine unabhängige Komponente der obersten Ebene Modalität und Message Loop\-Dienste mit der IDE koordinieren. In\-Process\-Objekte keine eigene Meldungsschleife.  
  
 Anbieter  
 Der Informationsanbieter ist ein Modul, die Schlüsselwörter suchen und eine Liste mit Themen, in Form von zurückgeben kann `IVsUserContextItem` Objekte. Um F1 und Lookup\-Schlüsselwort für den Informationsanbieter bereitstellen, registrieren Sie die kompilierte Hilfedatei \(. HxS\) mit dem System. Die Hilfethemen in diesen Dateien werden verwendet, um die Liste der Themen, ob ein Benutzer F1 drückt, und klicken Sie im Fenster Dynamische Hilfe angezeigt.  
  
 in\-Place\-Komponente  
 Ein VSPackage\-Objekt, das die `IOleInPlaceComponent` Schnittstelle, um ein Fenster zu verwalten, die in einem Dokumentfenster der IDE Besitz visuell enthalten ist. In\-Place\-Komponenten sind an der standard OLE\-Zusammenführungsfunktion nicht beteiligt; Stattdessen können sie die Elemente der Benutzeroberfläche in die IDE integrieren.  
  
 Es gibt zwei Arten von Komponenten an: konfigurierbares direktes Komponenten und Komponentensteuerelemente.  
  
 Konfigurierbares in\-Place\-Komponenten sind Menüs, Symbolleisten und Befehle, die eng integriert sind, in die Benutzeroberfläche der IDE, als angezeigt werden, wenn sie direkt in der IDE erstellt wurden.  
  
 Component\-Steuerelemente weisen keine eigene Elemente der Benutzeroberfläche in die IDE integriert. Stattdessen verwenden sie der IDE\-Menüs, Befehle und Symbolleisten. Beispielsweise kann der Befehl fett ein markierten Worts in einem rich\-Text\-Steuerelement in ein Formular eingebettet fett formatiert verwendet werden. Component\-Steuerelemente können jedoch anfordern, dynamisch installierte Komponente\-spezifische UI\-Elemente angezeigt werden.  
  
 Sprachdienst  
 Ein Satz von Objekten, das zum Implementieren von Features der Computer Sprache Code\-Editoren, z. B. Text markieren und die farbliche Kennzeichnung VSPackage erlaubt.  
  
 Projekt für verschiedene Dateien  
 Projekt, Haus geöffneten Dateien, die nicht in jedem Projekt enthalten sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.  
  
 Projekt  
 Projekte bestehen aus einer Hierarchie von Objekten oder COM\-Objekte implementieren die `IVsHierarchy` Schnittstelle.  
  
 projektspezifische Designer oder editor  
 Ein Designer, der unabhängig von Projekttyp verwendet werden kann. Alle projektspezifischen Designer müssen in der Registrierung ihrer Factory\-Editors Informationen eingeben. Die IDE kann dann den Designer instanziieren, immer ein bestimmten Dateityp in einem bestimmten Projekt geöffnet wird.  
  
 Projekt\-Fenster  
 Ein Fenster, das ständig die derzeit aktiven Projekthierarchie und das Element aus dem globalen Auswahlkontext verfolgt. Verwenden Sie Windows Projekttyp der `SVsTrackSelectionEx` Dienst die IDE Änderungen Warnung und Feedback für den Benutzer anzuzeigen. Projektmappen\-Explorer ist ein Beispiel für ein Projekt\-Fenster.  
  
 Eigenschaftenfenster  
 Früher Eigenschaftenbrowser.  
  
 verweisbasierte Projekte  
 Projekt, das die Dateien für das Projekt im selben Verzeichnis nicht benötigen. Stattdessen werden Verweise auf Dateien von anderen unabhängigen Verzeichnissen gespeichert und durch das Projekt selbst verwaltet.  
  
 Dokumenttabelle der ausgeführten  
 Interne Struktur, die IDE die Liste aller geöffneten Dokumente verwaltet. Diese Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob die Dokumente derzeit bearbeitet wird. Ein Dokument ist jedes Element, das gespeichert wird, einschließlich der gespeicherten Prozeduren, die in einem Editor, Dateien in einem Projekt oder in der Hauptprojektdatei \(z. B. VCPROJ\-Datei\) geöffnet.  
  
 Auswahlkontext  
 Daten, die Teil der Details aller Fenster in der IDE und dient zum Nachverfolgen der aktiven Auswahl. Auswahlkontext besteht aus:  
  
-   Zeiger auf die `IVsHierarchy` Schnittstelle der Projekthierarchie  
  
-   Element\-ID des Projektelements.  
  
-   Zeiger auf die `ISelectionContainer` \-Schnittstelle bietet Zugriff auf Eigenschaften für die aktive Objekte.  
  
-   Array von Elementwerten.  
  
 service  
 Ein Vertrag für einen Satz von COM\-Schnittstellen, die in ein einzelnes COM\-Objekt befinden. Wenn Sie einen Dienst, der durch eine GUID identifiziert wird erstellen, definieren Sie den Satz von COM\-Schnittstellen, der den Dienst ausführt. COM\-Objekte mithilfe Dienste miteinander kommunizieren.  
  
 Lösung  
 Eine Gruppe von verwandten Projekten, die mit denen ein Benutzer arbeitet.  
  
 Standard\-designer  
 Ein Designer, der unabhängig vom Projekttyp verwendet werden kann. Alle standard\-Designer müssen in der Registrierung ihrer Factory\-Editors Informationen eingeben. Die IDE kann dann den Designer instanziieren, bei jedem einer Datei mit einer bestimmten Erweiterung öffnen. Die Daten müssen in einer Datei gespeichert.  
  
 Standard\-editor  
 Editor, der unabhängig von jedem Projekttyp verwendet werden kann. Diese Editoren haben EditorFactories in der Registrierung registriert. Dadurch wird die IDE zu suchen, und rufen den Editor.  
  
 Standard\-OS\-editor  
 Ein einbetten, die kein Visual Studio\-spezifische. Er registriert ist, verwenden die bekannten Win32\-Schlüssel \(z. B. die Win32\-Explorer weiß, wie aufrufen\). Wenn solche Redakteur eingebettet werden kann, wird der Editor noch an seiner Stelle in der IDE angezeigt. Andernfalls wird ein separates Fenster oberster Ebene für diese Editoren erstellt.  
  
 Unterkontext Behälter  
 Ein `IVsUserContext` Objekt mit einem kontextbehälter verknüpft. Dieses Objekt enthält die Lookup\-Schlüsselwörter, F1\-Schlüsselwörter und Attribute für eine Auswahl in einem IDE\-Komponente. Unterkontext gehören einen Befehl in einem Toolfenster oder ein Schlüsselwort in einem Editor.  
  
 Aufgabenliste  
 Toolfenster, die von der IDE implementiert wird, und zeigt eine Liste der aktiven Aufgaben.  
  
 Textpuffer  
 Allgemeiner Name für das Objekt `VSTextBuffer`.  
  
 Anzeigen von Text  
 Allgemeiner Name für das Objekt `VSTextView`.  
  
 Tool\-Komponente der obersten Ebene  
 Eine Komponente, die als ein nicht modales Popup\-Fenster, koordinieren eng mit der Benutzeroberfläche der IDE ausgeführt wird. Wie unabhängige Komponenten der obersten Ebene müssen der obersten Ebene Toolkomponenten auch Modalität und Message Loop\-Dienste mit der IDE koordinieren.  
  
 Komponente der obersten Ebene  
 Ein VSPackage\-Objekt, das ein modales Fenster oberster Ebene statt den Clientbereich des IDE\-Fenster verwaltet. Implementieren Sie die Komponenten der obersten Ebene der `IOleComponent` Schnittstelle Message Loop Dienste wie z. B. Zugriff auf Leerlaufzeit nutzen.  
  
 UI aktiv  
 Ein VSPackage\-Objekt, das sichtbar ist und derzeit den Fokus besitzt.  
  
 Hierarchie der Benutzeroberfläche  
 Ein COM\-Objekt, das die `IVsUIHierarchy` Schnittstelle, um die Anzeige einer Hierarchie ermöglichen. Das Fenster des UI\-Hierarchie implementiert die `ISelectionContainer` \-Schnittstelle, um das Eigenschaftenfenster aktualisiert, andere Windows Projekttyp können bei Bedarf diese Implementierung verwenden.  
  
 VSCT  
 Visual Studio\-Befehl\-Tabelle. Die VSCT\-Datei enthält Informationen über die Platzierung und das Verhalten von Menüs, Symbolleisten und Befehle im XML\-Format.  
  
 VSPackage  
 Eine installierbare Softwarekomponente, die Visual Studio\-IDE erweitert wird, indem Sie eine oder mehrere der folgenden beitragen: Benutzeroberfläche, Dienste, Projekttypen oder Editor\-Designer. Ein VSPackage besteht ein COM\-Objekt, das die `IVsPackage` Schnittstelle und eine oder mehrere andere COM\-Objekte, die andere Schnittstellen zur Unterstützung von Auswahl und andere Funktionen zu implementieren. Darüber hinaus hat ein VSPackage bestimmten Registrierung.