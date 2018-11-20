---
title: Visual Studio SDK-Glossar | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ec2300e8bf700deacd50a4a980e02aa4b903bae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758958"
---
# <a name="visual-studio-sdk-glossary"></a>Glossar für das Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Glossar enthält Definitionen für Begriffe, die in dienen der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Dokumentation.  
  
## <a name="terms"></a>Begriffe  
 Add-In  
 Ein Hilfsprogramm-Anwendung, Treiber oder andere Software zu einem primären Anwendung hinzugefügt wurden. In der Visual Studio integrierte Entwicklungsumgebung (IDE) ist ein Add-in eine Automation-basierte Anwendung, die die Funktionen der IDE erweitert.  
  
 Automatisierungsmodell  
 Das Automatisierungsmodell, die in früheren Versionen von Visual Studio als Erweiterbarkeitsmodell bekannt ist eine Programmierschnittstelle, die Ihnen ermöglicht, Zugriff auf die zugrunde liegenden Routinen der IDE. -Add-ins, Assistenten und Makros verwenden die Objekte im Automatisierungsmodell steuern oder erweitern die Funktionalität der IDE.  
  
 Befehls-UI-Kontext  
 Die Zuordnung einer GUID mit der Sichtbarkeit eines UI-Befehl oder ein Element wie eine Symbolleiste. Befehlsbenutzeroberflächenkontext ist im Gegensatz zu Auswahlkontext, da diese nicht in einem Fenster angefügt ist.  
  
 Befehls-UI-Kontext verwendet werden kann:  
  
- Weisen Sie eine GUID in eine Symbolleiste, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert wird.  
  
- Weisen Sie eine GUID für die Verfügbarkeit eines Befehls, ohne zu laden, oder führen Sie eine VSPackage.  
  
- Weisen Sie eine GUID, die Auswirkungen auf die aktive tastenzuordnung.  
  
- Weisen Sie eine GUID zum Aufzeichnen von Makros zu aktivieren.  
  
- Weisen Sie eine GUID, die zum Aktivieren der Debug-Modus oder zwischen dem Entwurfs- und Ausführungsmodus in einem Editor zu wechseln.  
  
  component  
  Softwarekomponente, die Teil der Funktionalität einer Anwendung ohne die Anwendung, die alle bereits vorhandenen Informationen zur Implementierung von der Software vorgenommen werden können. Die Kommunikation zwischen einer Komponente und eine Anwendung ist ausschließlich über Schnittstellen für OLE-Stil.  
  
  Standortkomponenten-manager  
  Ein Dienst `SOleComponentManager`, die Benutzeroberfläche Koordination Services für die Komponenten der obersten Ebene bereitstellt. Die `SOleComponentManager` -Dienst implementiert die `IOleComponentManager` Schnittstelle.  
  
  UI-Standortkomponenten-manager  
  Ein Dienst `SOleComponentUIManager`, die Koordination der Benutzeroberflächendienste bereitstellt. Die `SOleComponentUIManager` -Dienst implementiert die `IOleComponentUIManager` und `IOleInPlaceComponentUIManager` Schnittstellen.  
  
  kontextbehälter  
  Ein `IVsUserContext` (COM-Objekt) zu einer Umgebung Komponente angefügt. Dieses Objekt enthält die Suche nach Schlüsselwörtern, F1-Schlüsselwörter und Attribute, die im Zusammenhang mit der Komponente. Kontext kontextbehälter zeigen Sie außerdem auf alle unterkontextbehälter, die auf diese verknüpft sind.  
  
  Kontextanbieter  
  Eine Komponente in der IDE, die eine Kontextsammlung verknüpft ist. Solche Komponenten umfassen ein Toolfenster, Editor oder Projekthierarchie.  
  
  Designer  
  Eine Programmierschnittstelle, die Benutzern zum Bearbeiten von Elementen der Benutzeroberfläche (Formulare, Schaltflächen und andere Steuerelemente) ermöglicht.  
  
  Docdata-Objekt  
  Ein COM-Objekt, das die zugrunde liegenden Daten eines Dokuments in einer Welt kapseln, wenn die Trennung von Dokument/Ansicht vorhanden ist (z. B. im Text-Editor-Fall, wäre dies der Textpuffer, der zugrunde liegenden alle Text-Editor-Ansichten). Wenn dieses Objekt nicht von EditorFactory bereitstellt werden, wird die IDE eine Webauthentifizierung produzieren. Die Verantwortung für dieses Objekt wird zum Verwalten von Datenpersistenz und die Freigabe Semantik für mehrere Ansichten auf diesem gleichen `DocData`. Wenn die `DocData` -Objekt unterstützt die `IOleCommandTarget` -Schnittstelle, wird es in das Befehlsrouting der UIShell enthalten sein.  
  
  DocObject  
  Technologie, die zum Hosten der Benutzeroberflächenautomatisierungs innerhalb eines Rahmens, der vom Host verwendet werden. Genauer gesagt, dieser Begriff verweist auf eingebettet werden, die unterstützt die `IOleDocument` und entsprechende Schnittstellen. Diese Technologie hat viele Anwendungen wie z. B. ein Implementierungsdetail des COM-Dokumente, Toolfenster in Visual Basic 5.0, ActiveX-Designer in Visual Basic 6.0 und So weiter.  
  
  Dokument  
  Der Oberbegriff für das Dokument als Ganzes verwendet – sowohl die `DocData` und `DocView`. Eine DocumentFrame enthält beispielsweise eine `DocView`, aber er behält auch einen Verweis auf die `DocData` Persistenz zu behandeln.  
  
  DocView  
  Die mit dem der Benutzer interagiert, zum Anzeigen und Bearbeiten der zugrunde liegende DocObject/Embedding/Fensterbereichs `DocData`. Beachten Sie, dass Benutzer nicht die Trennung von Dokument/Ansicht nutzen werden, die Teil der `DocObject` Benutzeroberfläche. Benutzer verwenden eine gesamte DocObject fungieren als Sicht anstelle von (und weniger formalisierte) eher abstrakte Konzept eines zugrunde liegenden Daten, die als bekannt `DocData`. `DocView` Objekte werden immer mit Dokument Keyframe-Objekte (untergeordnete MDI-Fenster) der IDE eingebettet.  
  
  DTE  
  Die `DTE` Objekt (Development Tools Erweiterbarkeit) ist der oberste Zugriffspunkt in das Visual Studio-Automatisierungsmodell, wodurch Sie programmgesteuert automatisieren und erweitern die IDE.  
  
  Dynamisches Hilfefenster  
  Toolfenster, die von der IDE implementiert wird, und zeigt eine Liste der suchenschlüsselwort oder die F1-Hilfethemen.  
  
  Editor  
  Code (Klassen, CLSID), implementiert die `DocView`. Es implementiert auch `DocData` , wenn die Trennung von Ansicht/Daten unterstützt wird.  
  
  Erweiterung  
  Eine Funktion, die geändert werden, passt, oder eine IDE hinzugefügt. Erstellen Sie mithilfe des Automatisierungsmodells oder VSPackages Erweiterungen.  
  
  externer editor  
  Ein Editor, der nicht spezifisch für die IDE, z. B. Microsoft Word ist. Sie wurde durch eine eigene Mechanismen registriert und kann außerhalb der IDE verwendet werden. Wenn dieser Editor eingebettet werden kann, wird es in einem Fenster in der IDE angezeigt. Wenn er nicht eingebettet werden kann, wird ein separates Fenster für der obersten Ebene erstellt.  
  
  Hierarchie  
  Struktur der Knoten, jeden Knoten, die einen Satz von Eigenschaften zugeordnet.  
  
  unabhängig von der obersten Ebene Komponente  
  Eine Komponente, die ein nicht modales Fenster der obersten Ebene verwendet und kann als eigenständige Anwendungsfenster effektiv eingesetzt, aber als in-Process-Objekt implementiert wird. Aus diesem Grund muss eine unabhängige auf oberster Ebene Komponente modalitäts- und nachrichtenschleifendienste mit der IDE koordinieren. In-Process-Objekte keine eigene Meldungsschleife.  
  
  Informationsanbieter  
  Der Informationsanbieter ist ein Modul, Suchschlüsselwörter und eine Liste der Themen, in Form von zurückgeben kann `IVsUserContextItem` Objekte. Um F1 und Lookup-Schlüsselwort Elemente für den Informationsanbieter bereitzustellen, registrieren Sie Ihre kompilierte Hilfedatei (. HxS) mit dem System. Die Hilfethemen in diesen Dateien werden verwendet, um die Liste der Themen im dynamischen Hilfefenster angezeigt, und, ob ein Benutzer F1 drückt bereitzustellen.  
  
  in-Place-Komponente  
  Ein VSPackage-Objekt, implementiert die `IOleInPlaceComponent` Schnittstelle, um ein Fenster zu verwalten, die visuell in einem Dokumentfenster der IDE im Besitz befindet. In-Place-Komponenten nicht an der standard OLE-das Zusammenführen von Menüs beteiligt; Stattdessen können sie die Elemente der Benutzeroberfläche in der IDE integrieren.  
  
  Es gibt zwei Arten von Komponenten des direktes: herkömmliche direktes Komponenten und Komponentensteuerelementen.  
  
  Flexibel konfigurierbares-in-Place-Komponenten verfügen über Menüs, Symbolleisten und Befehle, die eng integriert sind, in die Benutzeroberfläche der IDE, als angezeigt werden, wenn sie die IDE erstellt wurden.  
  
  Komponenten-Benutzersteuerelemente weisen keine eigenen Elemente der Benutzeroberfläche in die IDE integriert. Verwenden sie stattdessen, Menüs, Befehle und Symbolleisten der IDE. Der fett formatierten Befehl kann beispielsweise verwendet werden, ein markiertes Wort in einem rich-Text-Steuerelement in einem Formular eingebettet fett formatiert. Allerdings können Komponenten-Benutzersteuerelemente anfordern, dynamisch installierten komponentenspezifischen UI-Elemente angezeigt werden.  
  
  Sprachdienst  
  Ein Satz von Objekten, die VSPackage-Entwickler Funktionen Computer Sprache Code-Editoren, z. B. Text markieren und die farbliche Kennzeichnung von implementieren kann.  
  
  Projekt "Sonstige Dateien"  
  Das Projekt verwendet, um Haus geöffneten Dateien, die nicht in jedem Projekt vorhanden sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.  
  
  Projekt  
  Projekte bestehen von Hierarchy-Objekten oder COM-Objekte, implementieren die `IVsHierarchy` Schnittstelle.  
  
  projektspezifische-Designer oder editor  
  Ein Designer, der unabhängig von Projekttyp nicht verwendet werden kann. Alle Designer eines projektspezifischen müssen ihre Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann dann den Designer instanziieren, immer ein bestimmten Dateityp in einem bestimmten Projekt geöffnet wird.  
  
  Projekttyp Fenster  
  Ein Fenster, die ständig die aktuellen Projekthierarchie und das Element aus dem globalen Auswahlkontext nachverfolgt. Verwenden Sie den Projekttyp Windows die `SVsTrackSelectionEx` Dienst die IDE Änderungen benachrichtigt und Feedback für den Benutzer anzuzeigen. Projektmappen-Explorer ist ein Beispiel für ein Fenster Projekttyp.  
  
  Eigenschaftenfenster  
  Früher Eigenschaftenbrowser.  
  
  Referenz-basierte Projekte  
  Projekt, das die Dateien für das Projekt im selben Verzeichnis nicht benötigen. Stattdessen werden Verweise auf Dateien aus anderen Verzeichnissen unabhängigen gespeichert und vom das Projekt selbst verwaltet werden.  
  
  aktive Dokumenttabelle  
  Interne Struktur, die mit dem die IDE die Liste aller aktuell geöffneten Dokumente verwaltet werden. Diese Liste enthält alle geöffneten Dokumente im Arbeitsspeicher, unabhängig davon, ob die Dokumente derzeit bearbeitet wird. Ein Dokument ist jedes Element, das gespeichert wird, einschließlich gespeicherter Prozeduren, die in einem Editor, Dateien in einem Projekt oder der Hauptprojektdatei (z. B. *.VCPROJ-Datei) geöffnet.  
  
  Auswahlkontext  
  Daten, die Teil der Details aller Fenster in der IDE und zum Nachverfolgen der aktiven Auswahl. Auswahlkontext besteht aus:  
  
- Zeiger auf die `IVsHierarchy` -Schnittstelle der Projekthierarchie  
  
- Der Elementbezeichner des Projektelements.  
  
- Zeiger auf die `ISelectionContainer` Schnittstelle, die Sie Zugriff auf Eigenschaften für die aktive Objekte bereitstellt.  
  
- Ein Array von Elementwerten.  
  
  service  
  Ein Vertrag für einen Satz von COM-Schnittstellen, die sich in einem einzelnen COM-Objekt befinden. Wenn Sie einen Dienst, die von einer GUID identifiziert wird erstellen, definieren Sie den Satz von COM-Schnittstellen, der den Dienst ausführt. COM-Objekte mithilfe Dienste miteinander kommunizieren.  
  
  Lösung  
  Die Gruppe von verwandten Projekten, die mit denen ein Benutzer arbeitet.  
  
  Standard-designer  
  Ein Designer, der unabhängig von Projekttyp verwendet werden kann. Alle standard-Designer müssen die Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann Klicken Sie dann den Designer instanziieren, wenn eine Datei mit einer bestimmten Erweiterung geöffnet ist. Die Daten müssen in einer Datei gespeichert.  
  
  Standard-editor  
  Editor, der unabhängig von einem bestimmten Projekttyp verwendet werden kann. Diese Editoren verfügen EditorFactories, die in der Registrierung registriert. Dadurch wird die IDE zu suchen und den Editor aufzurufen.  
  
  Standard-OS-editor  
  Ein eingebettet werden, ist kein Visual Studio-spezifische. Mithilfe der bekannten Win32-Schlüssel registriert ist (z. B. die Win32-Explorer weiß, wie aufrufen). Wenn diese ein Editor eingebettet werden kann, wird der Editor immer noch an seiner Stelle in der IDE angezeigt. Andernfalls wird ein separates Fenster für der obersten Ebene für diese Editoren erstellt.  
  
  unterkontextbehälter  
  Ein `IVsUserContext` Objekt auf eine Kontextsammlung verknüpft. Dieses Objekt enthält die Suche nach Schlüsselwörtern, F1-Schlüsselwörter und Attribute für eine Auswahl innerhalb einer IDE-Komponente. Beispiele für unterkontextbehälter sind einen Befehl in einem Toolfenster oder ein Schlüsselwort in einem Editor.  
  
  Aufgabenliste  
  Toolfenster, die von der IDE implementiert wird, und zeigt eine Liste der aktiven Aufgaben.  
  
  Textpuffer  
  Allgemeiner Name für das Objekt `VSTextBuffer`.  
  
  Textansicht  
  Allgemeiner Name für das Objekt `VSTextView`.  
  
  der obersten Ebene Toolkomponente  
  Eine Komponente, die als ein nicht modales Popupfenster, koordinieren eng mit der Benutzeroberfläche der IDE ausgeführt wird. Wie unabhängige Komponenten der obersten Ebene müssen der obersten Ebene Toolkomponenten modalitäts- und nachrichtenschleifendienste mit der IDE auch koordinieren.  
  
  Komponente der obersten Ebene  
  Ein VSPackage-Objekt, das ein nicht modales Fenster oberster Ebene statt den Clientbereich eines Fensters IDE verwaltet. Implementieren Sie die Komponenten der obersten Ebene der `IOleComponent` Schnittstelle nachrichtenschleifendienste wie z. B. den Zugriff auf die Zeit im Leerlauf nutzen.  
  
  Aktive Benutzeroberfläche  
  Ein VSPackage-Objekt, das sichtbar ist, und zurzeit den Fokus besitzt.  
  
  Hierarchie der Benutzeroberfläche  
  Ein COM-Objekt, implementiert die `IVsUIHierarchy` Schnittstelle, um die Anzeige einer Hierarchie zu ermöglichen. Die Benutzeroberfläche-hierarchienfenster implementiert die `ISelectionContainer` Schnittstelle, um das Fenster "Eigenschaften" zu aktualisieren; andere Fenster Projekttyp können bei Bedarf dieser Implementierung verwenden.  
  
  VSCT  
  Visual Studio-Befehlstabelle. Die VSCT-Datei enthält Informationen über die Position und Verhalten des Menüs, Symbolleisten und Befehle im XML-Format.  
  
  VSPackage  
  Eine installierbare Softwarekomponente, die Visual Studio-IDE erweitert, indem beitragen, eine oder mehrere der folgenden:-Benutzeroberfläche, Dienste, Projekttypen oder Designer/Editor. Eine VSPackage besteht aus einer COM-Objekt, das implementiert die `IVsPackage` Schnittstelle und eine oder mehrere andere COM-Objekten, die andere Schnittstellen zur Unterstützung von Auswahl und andere Funktionen implementieren. Darüber hinaus weist eine VSPackage spezifische registrierungsanforderungen.

