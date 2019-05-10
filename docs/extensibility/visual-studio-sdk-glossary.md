---
title: Visual Studio SDK-Glossar | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6157b4bc3537a4f88feb91d512241451b8324ba7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838905"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK-Glossar
In diesem Glossar enthält Definitionen für Begriffe, die in dienen der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Dokumentation.

## <a name="terms"></a>Begriffe
 Add-in-ein Hilfsprogramm-Anwendung, Treiber oder andere Software zu einem primären Anwendung hinzugefügt wurden. In der Visual Studio integrierte Entwicklungsumgebung (IDE) ist ein Add-in eine Automation-basierte Anwendung, die die Funktionen der IDE erweitert.

 in früheren Versionen von Visual Studio als Erweiterbarkeitsmodell bekannt Automatisierungsmodell des Automatisierungsmodells ist eine Programmierschnittstelle, die Ihnen ermöglicht, Zugriff auf die zugrunde liegenden Routinen der IDE. -Add-ins, Assistenten und Makros verwenden die Objekte im Automatisierungsmodell steuern oder erweitern die Funktionalität der IDE.

 befehlsbenutzeroberflächenkontext Zuordnung einer GUID mit der Sichtbarkeit eines UI-Befehl oder ein Element wie eine Symbolleiste. Befehlsbenutzeroberflächenkontext ist im Gegensatz zu Auswahlkontext, da es in einem Fenster angefügt ist.

 Befehls-UI-Kontext verwendet werden kann:

- Weisen Sie eine GUID in eine Symbolleiste, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert wird.

- Weisen Sie eine GUID für die Verfügbarkeit eines Befehls, ohne zu laden, oder führen Sie eine VSPackage.

- Weisen Sie eine GUID, die Auswirkungen auf die aktive tastenzuordnung.

- Weisen Sie eine GUID zum Aufzeichnen von Makros zu aktivieren.

- Weisen Sie eine GUID, die zum Aktivieren der Debug-Modus oder zwischen dem Entwurfs- und Ausführungsmodus in einem Editor zu wechseln.

  Komponente Softwarekomponente, die Teil der Funktionalität einer Anwendung ohne die Anwendung, die alle bereits vorhandenen Informationen zur Implementierung von der Software vorgenommen werden können. Die Kommunikation zwischen einer Komponente und eine Anwendung ist ausschließlich über Schnittstellen für OLE-Stil.

  Dienst-Manager eine Komponente `SOleComponentManager`, die Benutzeroberfläche Koordination Services für die Komponenten der obersten Ebene bereitstellt. Die `SOleComponentManager` -Dienst implementiert die `IOleComponentManager` Schnittstelle.

  UI-Manager ein Komponentendienst, `SOleComponentUIManager`, die Koordination der Benutzeroberflächendienste bereitstellt. Die `SOleComponentUIManager` -Dienst implementiert die `IOleComponentUIManager` und `IOleInPlaceComponentUIManager` Schnittstellen.

  kontextbehälter ein `IVsUserContext` (COM-Objekt) zu einer Umgebung Komponente angefügt. Dieses Objekt enthält die Suche nach Schlüsselwörtern **F1** Schlüsselwörter und Attribute, die im Zusammenhang mit der Komponente. Kontext kontextbehälter zeigen Sie außerdem auf alle unterkontextbehälter, die auf diese verknüpft sind.

  Kontext-Anbieter eine Komponente in der IDE, die eine Kontextsammlung verknüpft ist. Solche Komponenten umfassen ein Toolfenster, Editor oder Projekthierarchie.

  der Designer eine Programmierschnittstelle, die Benutzern zum Bearbeiten von Elementen der Benutzeroberfläche (Formulare, Schaltflächen und andere Steuerelemente) ermöglicht.

  DocData-A-COM-Objekt, die die zugrunde liegenden Daten eines Dokuments in einer Welt kapseln, wenn die Trennung von Dokument/Ansicht vorhanden ist (z. B. im Text-Editor-Fall, wäre dies der Textpuffer, der zugrunde liegenden alle Text-Editor-Ansichten). Wenn der EditorFactory dieses Objekt nicht bereitstellt, stellt die IDE eine in dessen Auftrag aufzubauen. Die Verantwortung für dieses Objekt wird zum Verwalten von Datenpersistenz und die Freigabe Semantik für mehrere Ansichten auf diesem gleichen `DocData`. Wenn die `DocData` -Objekt unterstützt die `IOleCommandTarget` -Schnittstelle ab, die sie in das Befehlsrouting der UIShell enthalten ist.

  DocObject-Technologie, die zum Hosten der Benutzeroberflächenautomatisierungs innerhalb eines Rahmens, der vom Host verwendet werden. Genauer gesagt, dieser Begriff verweist auf eingebettet werden, die unterstützt die `IOleDocument` und entsprechende Schnittstellen. Diese Technologie hat viele Anwendungen wie z. B. ein Implementierungsdetail des COM-Dokumente, Toolfenster in Visual Basic 5.0, ActiveX-Designer in Visual Basic 6.0 und So weiter.

  wird verwendet, um generisch auf das Dokument als Ganzes verweisen zu dokumentieren – sowohl die `DocData` und `DocView`. Eine DocumentFrame enthält beispielsweise eine `DocView`, aber er behält auch einen Verweis auf die `DocData` Persistenz zu behandeln.

  DocView-die DocObject/Embedding/Fensterbereichs mit dem der Benutzer interagiert, zum Anzeigen und Bearbeiten der zugrunde liegende `DocData`. Benutzer nicht nutzen der Trennung von Dokument/Ansicht, die Teil der `DocObject` Benutzeroberfläche. Benutzer verwenden eine gesamte DocObject fungieren als Sicht anstelle von (und weniger formalisierte) eher abstrakte Konzept eines zugrunde liegenden Daten, die als bekannt `DocData`. `DocView` Objekte werden immer mit Dokument Keyframe-Objekte (untergeordnete MDI-Fenster) der IDE eingebettet.

  DTE der `DTE` Objekt (Development Tools Erweiterbarkeit) ist der oberste Zugriffspunkt in das Visual Studio-Automatisierungsmodell, wodurch Sie programmgesteuert automatisieren und erweitern die IDE.

  Dynamische Hilfe Fenster Toolfenster, das von der IDE implementiert wird, und zeigt eine Liste der suchenschlüsselwort oder **F1** Hilfethemen.

  Editor für Code (Klassen, CLSID), implementiert die `DocView`. Es implementiert auch `DocData` , wenn die Trennung von Ansicht und Daten unterstützt wird.

  Erweiterung A-Feature, das geändert werden, passt, oder eine IDE hinzugefügt. Erstellen Sie mithilfe des Automatisierungsmodells oder VSPackages Erweiterungen.

  externer Editor einen Editor, die spezifisch für die IDE, z. B. Microsoft Word nicht. Sie wurde durch eine eigene Mechanismen registriert und kann außerhalb der IDE verwendet werden. Wenn dieser Editor eingebettet werden kann, wird es in einem Fenster in der IDE angezeigt. Wenn er nicht eingebettet werden kann, wird ein separates Fenster für der obersten Ebene erstellt.

  Hierarchie Knotenstruktur, jeden Knoten, die einen Satz von Eigenschaften zugeordnet.

  unabhängige auf oberster Ebene eine Komponente, die ein nicht modales Fenster der obersten Ebene verwendet und kann als eigenständige Anwendungsfenster effektiv eingesetzt, aber als in-Process-Objekt implementiert wird. Aus diesem Grund muss eine unabhängige auf oberster Ebene Komponente modalitäts- und nachrichtenschleifendienste mit der IDE koordinieren. In-Process-Objekte haben keine eigene Meldungsschleife.

  Informationsanbieter der Informationsanbieter ist ein Modul, kann nach Schlüsselwörtern suchen und zurückgeben eine Liste der Themen, in Form von `IVsUserContextItem` Objekte. Zu **F1** und Nachschlage-Schlüsselwort Elemente, für den Informationsanbieter, registrieren Sie Ihre kompilierte Hilfedatei (*. HxS*) mit dem System. Geben Sie die Liste der Themen im dynamischen Hilfefenster angezeigt, und, ob ein Benutzer drückt die Hilfethemen in diesen Dateien **F1**.

  in-Place-Komponente eine VSPackage-Objekt, das implementiert die `IOleInPlaceComponent` Schnittstelle, um ein Fenster zu verwalten, die visuell in einem Dokumentfenster der IDE im Besitz befindet. Direktes Komponenten einbezogen nicht in der standard OLE-das Zusammenführen von Menüs; Stattdessen können sie die Elemente der Benutzeroberfläche in der IDE integrieren.

  Es gibt zwei Arten von Komponenten des direktes: herkömmliche direktes Komponenten und Komponentensteuerelementen.

  Flexibel konfigurierbares-in-Place-Komponenten verfügen über Menüs, Symbolleisten und Befehle, die eng integriert sind, in die Benutzeroberfläche der IDE, als angezeigt werden, wenn sie die IDE erstellt wurden.

  Komponenten-Benutzersteuerelemente wurde nicht für ihre eigenen Elemente der Benutzeroberfläche in die IDE integriert; Verwenden sie stattdessen, Menüs, Befehle und Symbolleisten der IDE. Der fett formatierten Befehl kann beispielsweise verwendet werden, ein markiertes Wort in einem rich-Text-Steuerelement in einem Formular eingebettet fett formatiert. Allerdings können Komponenten-Benutzersteuerelemente anfordern, dynamisch installierten komponentenspezifischen UI-Elemente angezeigt werden.

  Language-Dienst ein Satz von Objekten, die VSPackage-Entwicklern zum Implementieren von Funktionen der Computersprache Code-Editoren, z. B. Text markieren und die farbliche Kennzeichnung von ermöglicht.

  Verschiedene Projektdateien Projekt, das Haus von geöffneten Dateien, die nicht in jedem Projekt verwendet. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.

  Projekt-Projekten bestehen von Hierarchy-Objekten oder COM-Objekte, implementieren die `IVsHierarchy` Schnittstelle.

  projektspezifische-Designer oder Editor ein Designer, der unabhängig von Projekttyp nicht verwendet werden kann. Alle Designer eines projektspezifischen müssen ihre Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann dann den Designer instanziieren, immer ein bestimmten Dateityp in einem bestimmten Projekt geöffnet wird.

  Projekttyp Fenster ein Fenster überwacht, ständig die aktuellen Projekthierarchie und das Element aus dem Kontext der globalen Auswahl. Verwenden Sie den Projekttyp Windows die `SVsTrackSelectionEx` Dienst die IDE Änderungen benachrichtigt und Feedback für den Benutzer anzuzeigen. Projektmappen-Explorer ist ein Beispiel für ein Fenster Projekttyp.

  Fenster "Eigenschaften" früher Eigenschaftenbrowser.

  Referenz-basierte Projekte-Projekt, das die Dateien für das Projekt im gleichen Verzeichnis erforderlich ist. Stattdessen werden Verweise auf Dateien aus anderen Verzeichnissen unabhängigen gespeichert und vom das Projekt selbst verwaltet werden.

  Ausführen von interne Struktur des Dokuments-Tabelle mit dem die IDE die Liste aller aktuell geöffneten Dokumente verwaltet. Die Liste enthält alle geöffneten Dokumente im Arbeitsspeicher, unabhängig davon, ob die Dokumente derzeit bearbeitet wird. Ein Dokument ist jedes Element, das gespeichert wird, einschließlich gespeicherter Prozeduren, die in einem Editor, Dateien in einem Projekt oder der Hauptprojektdatei (z. B. *.VCPROJ-Datei) geöffnet.

  Auswahlkontext Daten, die Teil der Details aller Fenster in der IDE und zum Nachverfolgen der aktiven Auswahl. Auswahlkontext besteht aus:

- Zeiger auf die `IVsHierarchy` -Schnittstelle der Projekthierarchie

- Der Elementbezeichner des Projektelements.

- Zeiger auf die `ISelectionContainer` Schnittstelle, die Sie Zugriff auf Eigenschaften für die aktive Objekte bereitstellt.

- Ein Array von Elementwerten.

  Dienst einen Vertrag für einen Satz von COM-Schnittstellen, der sich in einem einzelnen COM-Objekt befindet. Wenn Sie einen Dienst, die von einer GUID identifiziert wird erstellen, definieren Sie den Satz von COM-Schnittstellen, der den Dienst ausführt. COM-Objekte mithilfe Dienste miteinander kommunizieren.

  Lösung Gruppieren von verwandten Projekten, die mit dem ein Benutzer arbeitet.

  Standard-Designer einen Designer, der unabhängig von Projekttyp verwendet werden kann. Alle standard-Designer müssen die Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann Klicken Sie dann den Designer instanziieren, wenn eine Datei mit einer bestimmten Erweiterung geöffnet ist. Die Daten müssen in einer Datei gespeichert.

  Standard-Editor-Editor, der unabhängig von einem bestimmten Projekttyp verwendet werden kann. Diese Editoren verfügen EditorFactories, die in der Registrierung registriert. Dadurch wird die IDE zu suchen und den Editor aufzurufen.

  Standard BS-Editor eine eingebettet werden, ist Visual Studio-spezifischer nicht. Mithilfe der bekannten Win32-Schlüssel registriert ist (z. B. die Win32-Explorer weiß, wie aufrufen). Wenn diese ein Editor eingebettet werden kann, wird der Editor immer noch an seiner Stelle in der IDE. Andernfalls wird ein separates Fenster für der obersten Ebene für diese Editoren erstellt.

  unterkontextbehälter ein `IVsUserContext` Objekt auf eine Kontextsammlung verknüpft. Das Objekt enthält die Suche nach Schlüsselwörtern **F1** Schlüsselwörter und Attribute für eine Auswahl in einer IDE-Komponente. Beispiele für unterkontextbehälter sind einen Befehl in einem Toolfenster oder ein Schlüsselwort in einem Editor.

  Aufgabenliste (Fenster)-Tool, das von der IDE implementiert wird, und zeigt eine Liste der aktiven Aufgaben.

  Text-Puffer, allgemeiner Name für das Objekt `VSTextBuffer`.

  Text anzeigen allgemeiner Name für das Objekt `VSTextView`.

  Tools der obersten Ebene eine Komponente, die als ein nicht modales Popupfenster, koordinieren eng mit der Benutzeroberfläche der IDE ausgeführt wird. Wie unabhängige Komponenten der obersten Ebene müssen der obersten Ebene Toolkomponenten modalitäts- und nachrichtenschleifendienste mit der IDE auch koordinieren.

  Komponente der obersten Ebene ein VSPackage-Objekt, das ein nicht modales Fenster oberster Ebene statt den Clientbereich eines Fensters IDE verwaltet. Implementieren Sie die Komponenten der obersten Ebene der `IOleComponent` Schnittstelle nachrichtenschleifendienste wie z. B. den Zugriff auf die Zeit im Leerlauf nutzen.

  Benutzeroberfläche active-ein VSPackage-Objekt, das sichtbar ist, und zurzeit den Fokus besitzt.

  UI-Hierarchie eine COM-Objekt, das implementiert die `IVsUIHierarchy` Schnittstelle, um die Anzeige einer Hierarchie zu ermöglichen. Die Benutzeroberfläche-hierarchienfenster implementiert die `ISelectionContainer` Schnittstelle, um das Fenster "Eigenschaften" zu aktualisieren; andere Fenster Projekttyp können bei Bedarf dieser Implementierung verwenden.

  VSCT-Visual Studio-Befehlstabelle. Die VSCT-Datei enthält Informationen über die Position und Verhalten des Menüs, Symbolleisten und Befehle im XML-Format.

  VSPackage eine installierbare Softwarekomponente, die Visual Studio-IDE erweitert, indem beitragen, eine oder mehrere der folgenden Elemente: Benutzeroberfläche, Dienste, Projekttypen oder Designer/Editor. Eine VSPackage besteht aus einer COM-Objekt, das implementiert die `IVsPackage` Schnittstelle und eine oder mehrere andere COM-Objekten, die andere Schnittstellen zur Unterstützung von Auswahl und andere Funktionen implementieren. Darüber hinaus weist eine VSPackage spezifische registrierungsanforderungen.