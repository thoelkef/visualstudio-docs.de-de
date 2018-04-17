---
title: Glossar für Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a08985c4977896e35fa8cd94014385ac32dd8bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK-Glossar
In diesem Glossar enthält Definitionen für Begriffe, die in verwendet werden die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Dokumentation.  
  
## <a name="terms"></a>Begriffe  
 Add-In  
 Ein Hilfsprogramm-Anwendung, Treiber oder anderer Software zu einem primären Anwendung hinzugefügt wurden. In der Visual Studio integrierten Entwicklungsumgebung (IDE) ist ein Add-in ein Automation-basierte Anwendung, die die Funktionen der IDE erweitert.  
  
 Automatisierungsmodell  
 Das Automatisierungsmodell, die in früheren Versionen von Visual Studio als Erweiterbarkeitsmodell bekannt ist eine Programmierschnittstelle, die Ihnen sofortigen Zugriff auf die zugrunde liegenden Routinen der IDE. -Add-ins, Assistenten und Makros Objekte in das Automatisierungsmodell zum Steuerelement verwenden, oder die Funktionalität der IDE erweitern.  
  
 Befehl Benutzeroberflächenkontext  
 Die Zuordnung einer GUID mit der Sichtbarkeit einer UI-Befehl oder ein Element wie eine Symbolleiste. Befehl Benutzeroberflächenkontext besteht ein Unterschied zu Auswahlkontext insofern, dass er nicht in einem Fenster angefügt ist.  
  
 Befehl Benutzeroberflächenkontext verwendet werden kann:  
  
-   Weisen Sie eine GUID in eine Symbolleiste, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert ist.  
  
-   Weisen Sie eine GUID für die Verfügbarkeit eines Befehls, ohne zu laden, oder führen Sie eine VSPackage.  
  
-   Weisen Sie einen GUID, um aktive schlüsselbindung auswirken.  
  
-   Weisen Sie eine GUID zum Aufzeichnen von Makros zu aktivieren.  
  
-   Weisen Sie eine GUID, die zum Aktivieren des Debugmodus oder zwischen Entwurfs- und Ausführungsmodus in einem Editor zu wechseln.  
  
 component  
 Softwarekomponente, die Teil der Funktionalität einer Anwendung ohne die Anwendung alle bereits vorhandenen Informationen zur Implementierung der Software vorgenommen werden können. Kommunikation zwischen einer Komponente und einer Anwendung erfolgt ausschließlich über Schnittstellen für OLE-Stil.  
  
 Standortkomponenten-manager  
 Ein Dienst `SOleComponentManager`, stellt nichtbenutzer-Schnittstelle Koordinierung Services für die Komponenten der obersten Ebene. Die `SOleComponentManager` service implementiert die `IOleComponentManager` Schnittstelle.  
  
 UI-Standortkomponenten-manager  
 Ein Dienst `SOleComponentUIManager`, Benutzer Schnittstelle Koordinierung Dienste bietet. Die `SOleComponentUIManager` service implementiert die `IOleComponentUIManager` und `IOleInPlaceComponentUIManager` Schnittstellen.  
  
 Kontext Eigenschaftenbehälters.  
 Ein `IVsUserContext` (COM-Objekt) zu einer Umgebung Komponente angefügt. Dieses Objekt enthält die Lookup-Schlüsselwörter, F1-Schlüsselwörter und Attribute in Bezug auf die Komponente. Aus diesem Kontext zeigen Sie außerdem auf alle Unterkontext dienen, die mit ihnen verknüpft werden.  
  
 Kontextanbieter  
 Eine Komponente in der IDE, die einen Kontext Behälter zugeordnet wurde. Solche Komponenten zählen ein Toolfenster, Editor oder Projekthierarchie.  
  
 Designer  
 Eine Programmierschnittstelle, die Benutzern zum Bearbeiten von Elementen der Benutzeroberfläche (Formulare, Schaltflächen und anderen Steuerelementen) ermöglicht.  
  
 DocData  
 Ein COM-Objekt, das Kapseln von der zugrunde liegenden Daten eines Dokuments in einer Welt, in dem Dokument-/Ansichtarchitektur Trennung vorhanden ist (z. B. im Text-Editor Fall wäre dies den Textpuffer zugrunde liegenden alle Sichten der Text-Editor). Wenn dieses Objekt in der EditorFactory nicht angegeben wird, wird die IDE eine in dessen Auftrag aufzubauen produzieren. Die Zuständigkeit für dieses Objekt wird zum Verwalten der Dauerhaftigkeit von Daten und die Freigabe Semantik für mehrere Ansichten über diesen identisch `DocData`. Wenn die `DocData` -Objekt unterstützt die `IOleCommandTarget` -Schnittstelle, wird in der Befehlsrouting der UIShell aufgenommen.  
  
 DocObject  
 Technologie, die zum Hosten der Benutzeroberflächenautomatisierungs innerhalb eines Rahmens, der vom Host verwendet werden. Dieser Begriff bezieht sich genauer gesagt, um alle einbetten, die unterstützt die `IOleDocument` und Schnittstellen. Diese Technologie verfügt über viele mögliche Clientanwendungen wie z. B. ein Implementierungsdetail von COM-Dokumenten, Toolfenster in Visual Basic 5.0, ActiveX-Designer in Visual Basic 6.0, und So weiter.  
  
 Dokument  
 Auf das Dokument als Ganzes verwendet – sowohl die `DocData` und `DocView`. Eine DocumentFrame enthält z. B. eine `DocView`, aber auch behält einen Verweis auf die `DocData` Dauerhaftigkeit zu behandeln.  
  
 DocView  
 Die mit der Interaktion des Benutzers zum Anzeigen und Bearbeiten von den zugrunde liegenden DocObject/Embedding/Fensterbereichs `DocData`. Beachten Sie, dass Benutzer nicht die Vorteile der Dokument-/Ansichtarchitektur Trennung vorgehen, die Teil der `DocObject` Benutzeroberfläche entwerfen. Benutzer verwenden eine gesamte DocObject fungieren als Sicht anstelle von abstrakter (und weniger formalisierter) Konzept eines zugrunde liegenden Daten, die als bekannt `DocData`. `DocView` Objekte werden immer mit Frame-Dokumentobjekte (untergeordnete MDI-Fenster) der IDE eingebettet.  
  
 DTE  
 Die `DTE` (Development Tools Extensibility)-Objekt ist das oberste Zugriffspunkt in Visual Studio-Automatisierungsmodells, wodurch Sie programmgesteuert zu automatisieren und zu erweitern der IDE.  
  
 Dynamisches Hilfefenster  
 Toolfenster, die von der IDE implementiert wird, und zeigt eine Liste der Suche Schlüsselwort oder F1-Hilfethemen.  
  
 Editor  
 Code (Klassen, CLSID), implementiert die `DocView`. Es implementiert auch `DocData` , wenn die Ansichtsdaten/Trennung unterstützt wird.  
  
 Erweiterung  
 Eine Funktion, die geändert werden, passt, oder eine IDE hinzugefügt. Erstellen Sie mithilfe des Automatisierungsmodells oder VSPackages Erweiterungen.  
  
 externen editor  
 Ein Editor, der nicht für die IDE, z. B. Microsoft Word spezifisch ist. Es wurde durch eine eigene Mechanismen registriert und kann außerhalb der IDE verwendet werden. Wenn dieser Editor eingebettet werden kann, wird es in einem Fenster in der IDE angezeigt. Wenn er nicht eingebettet werden kann, wird ein separates Fenster oberster Ebene erstellt.  
  
 Hierarchie  
 Struktur der Knoten, jeden Knoten, die eine Reihe von Eigenschaften zugeordnet.  
  
 unabhängige Komponente der obersten Ebene  
 Eine Komponente, die ein nicht modales Fenster oberster Ebene verwendet und kann als eigenständige Anwendungsfenster effektiv arbeiten, aber als in-Process-Objekt implementiert wird. Aus diesem Grund muss eine unabhängige Komponente der obersten Ebene modalitäts- und Message-Schleife-Dienste mit der IDE koordinieren. Eigene Nachrichtenschleife keine in-Process-Objekte.  
  
 Informationsanbieter  
 Der Anbieter ist ein Modul, die Schlüsselwörter zu suchen und eine Liste mit Themen, in Form von zurückgeben kann `IVsUserContextItem` Objekte. Um F1 und Suchfunktionen Schlüsselwort-Elemente für den Informationsanbieter bereitzustellen, registrieren Sie die Hilfedatei (. HxS) mit dem System. Die Hilfethemen in diesen Dateien werden verwendet, um die Liste der Themen im dynamischen Hilfefenster angezeigt, und, ob ein Benutzer F1 drückt bereitstellen.  
  
 Direktes-Komponente  
 Ein VSPackage-Objekt, implementiert die `IOleInPlaceComponent` Schnittstelle, um ein Fenster zu verwalten, die visuell in einem Dokumentfenster der IDE Besitz enthalten ist. Direktes Komponenten am nicht in der standard OLE-Zusammenführungsfunktion; Stattdessen können sie ihre Elemente der Benutzeroberfläche in der IDE integrieren.  
  
 Es gibt zwei Arten von direkten-Komponenten: konfigurierbares direktes Komponenten und Komponentensteuerelementen.  
  
 Konfigurierbares direktes Komponenten haben, Menüs, Symbolleisten und Befehlen, die eng integriert sind, in die Benutzeroberfläche der IDE, als angezeigt werden, wenn sie direkt in die IDE erstellt wurden.  
  
 Komponentensteuerelemente müssen nicht ihre eigenen Elemente der Benutzeroberfläche in der IDE integriert. Verwenden sie stattdessen, Menüs, Befehle und Symbolleisten der IDE. Beispielsweise konnte der fett formatierten Befehl fett formatiert, ein markierten Worts in einem rich-Text-Steuerelement eingebettet in einem Formular verwendet werden. Allerdings können Komponentensteuerelemente anfordern, dynamisch installierten komponentenspezifische-Benutzeroberflächenelemente angezeigt werden.  
  
 -Sprachdienst  
 Ein Satz von Objekten, die VSPackage-Entwicklern zum Implementieren von Computer Sprache Code-Editoren, z. B. Text markieren und farbliche Kennzeichnung von Funktionen ermöglicht.  
  
 Sonstige Dateien-Projekt  
 Projekt öffnen Datendateien gespeichert, die nicht in jedem Projekt verwendet. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.  
  
 Projekt  
 Projekte bestehen aus Hierarchy-Objekten oder COM-Objekte implementiert, die `IVsHierarchy` Schnittstelle.  
  
 projektspezifische Designer oder editor  
 Ein Designer, der unabhängig von Projekttyp verwendet werden kann. Alle projektspezifische-Designer müssen in der Registrierung ihrer Editorfactory Informationen eingeben. Die IDE kann dann den Designer instanziieren, immer ein bestimmten Dateityp in einem bestimmten Projekt geöffnet wird.  
  
 Projekttyp Fenster  
 Ein Fenster, die ständig, die derzeit aktiven Projekthierarchie und das Element aus dem Kontext des globalen Auswahl verfolgt. Verwenden Sie die Windows Projekttyp die `SVsTrackSelectionEx` Dienst, um die IDE Änderungen zu informieren und Feedback für den Benutzer anzuzeigen. Projektmappen-Explorer ist ein Beispiel eines Projekttyp Fensters.  
  
 Eigenschaftenfenster  
 Früher Eigenschaftenbrowser.  
  
 verweisbasierten Projekten  
 Projekt, das die Dateien für das Projekt werden im selben Verzeichnis nicht benötigen. Stattdessen werden Verweise auf Dateien aus anderen unabhängigen Verzeichnissen gespeichert und vom das Projekt selbst verwaltet.  
  
 Dokumenttabelle der ausgeführten  
 Interne Struktur, die mit dem die IDE die Liste aller aktuell geöffneten Dokumente verwaltet werden. Diese Liste enthält alle geöffneten Dokumente im Arbeitsspeicher, unabhängig davon, ob die Dokumente derzeit bearbeitet wird. Ein Dokument ist jedes Element, das gespeichert wird, z. B. gespeicherte Prozeduren, die in einen Editor, Dateien in einem Projekt oder das Hauptprojekt-Datei (z. B. VCPROJ-Datei) geöffnet.  
  
 Auswahlkontext  
 Daten, die Teil des Details aller Fenster in der IDE und werden verwendet, um die aktive Auswahl zu verfolgen. Auswahlkontext besteht aus:  
  
-   Zeiger auf die `IVsHierarchy` Schnittstelle von der Projekthierarchie  
  
-   Element-ID des Projektelements.  
  
-   Zeiger auf die `ISelectionContainer` Schnittstelle und bietet Zugriff auf die Eigenschaften für die aktive Objekte.  
  
-   Ein Array von Elementwerten.  
  
 service  
 Ein Vertrag für einen Satz von COM-Schnittstellen, die in ein einzelnes COM-Objekt befinden. Wenn Sie einen Dienst, der durch eine GUID identifiziert wird erstellen, definieren Sie den Satz von COM-Schnittstellen, der den Dienst ausführt. COM-Objekte mithilfe Dienste miteinander kommunizieren.  
  
 Projektmappen  
 Eine Gruppe von verwandten Projekten, die mit denen Benutzer arbeitet.  
  
 Standard-designer  
 Ein Designer, der unabhängig von Projekttyp verwendet werden kann. Alle standard-Designer müssen in der Registrierung ihrer Editorfactory Informationen eingeben. Die IDE kann Designer dann instanziiert werden bei jedem von Dateien mit einer bestimmten Erweiterung öffnen. Der persistenten Speicherung der Daten müssen in eine Datei.  
  
 Standard-Editors  
 Editor, der unabhängig von einem bestimmten Projekttyp verwendet werden kann. Solche-Editoren weisen EditorFactories in der Registrierung registriert. Dadurch wird die IDE zum Suchen und Aufrufen von Editor.  
  
 Standard-OS-editor  
 Visual Studio ein einbetten, die kein bestimmtes. Verwenden die bekannten Schlüssel für die Win32-registriert ist (z. B. die Win32-Explorer weiß, wie aufrufen). Wenn solche ein Editors eingebettet werden kann, wird der Editor weiterhin an seiner Stelle in der IDE angezeigt. Andernfalls wird ein separates Fenster oberster Ebene für diese Editoren erstellt.  
  
 Unterkontext Eigenschaftenbehälters.  
 Ein `IVsUserContext` Objekt mit einem Kontext Behälter verknüpft. Dieses Objekt enthält die Lookup-Schlüsselwörter, F1-Schlüsselwörter und Attribute zur Auswahl mehrerer Zellen in einem IDE-Komponente. Beispiele für Unterkontext umfassen einen Befehl in einem Toolfenster oder ein Schlüsselwort in einem Editor.  
  
 Aufgabenliste  
 Toolfenster, die von der IDE implementiert wird, und zeigt eine Liste von aktiven Aufgaben.  
  
 Textpuffer  
 Der allgemeine Name für das Objekt `VSTextBuffer`.  
  
 Textansicht  
 Der allgemeine Name für das Objekt `VSTextView`.  
  
 auf der obersten Ebene Toolkomponente  
 Eine Komponente, die als ein nicht modales Popup-Fenster, koordinieren eng mit der Benutzeroberfläche der IDE ausgeführt wird. Wie unabhängige Komponenten der obersten Ebene müssen der obersten Ebene Toolkomponenten auch modalitäts- und Message-Schleife-Dienste mit der IDE koordiniert werden.  
  
 Komponente der obersten Ebene  
 Ein VSPackage-Objekt, das ein nicht modales Fenster oberster Ebene anstatt den Clientbereich eines Fensters IDE verwaltet. Implementieren Sie die Komponenten der obersten Ebene der `IOleComponent` Schnittstelle Message-Schleife-Dienste wie z. B. den Zugriff auf die Zeit im Leerlauf nutzen.  
  
 UI aktiv  
 Ein VSPackage-Objekt, das sichtbar ist und aktuell den Fokus hat.  
  
 Hierarchie der Benutzeroberfläche  
 Ein COM-Objekt, implementiert die `IVsUIHierarchy` Schnittstelle, um die Anzeige einer Hierarchie zu ermöglichen. Das Fenster des UI-Hierarchie implementiert die `ISelectionContainer` -Schnittstelle, um das Eigenschaftenfenster zu aktualisieren; die anderen Projekttyp Windows können Sie diese Implementierung verwenden, falls gewünscht.  
  
 VSCT  
 Visual Studio-Befehlstabelle. Die VSCT-Datei enthält Informationen über die Platzierung und das Verhalten von Menüs, Symbolleisten und Befehle im XML-Format.  
  
 VSPackage  
 Eine installierbare Softwarekomponente, die der Visual Studio-IDE erweitert wird, indem Sie eine oder mehrere der folgenden beitragen: Benutzeroberfläche, Dienste, -Projekttypen oder Editor-Designer. Eine VSPackage besteht aus einer COM-Objekt, das implementiert die `IVsPackage` Schnittstelle und eine oder mehrere andere COM-Objekten, die zur Unterstützung von Auswahl und andere Funktionen eine andere Schnittstelle implementiert. Darüber hinaus weist eine VSPackage spezifische registrierungsanforderungen.