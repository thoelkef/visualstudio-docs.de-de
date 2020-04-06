---
title: Glossar des Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698170"
---
# <a name="visual-studio-sdk-glossary"></a>Glossar des Visual Studio SDK
Dieses Glossar enthält Definitionen für Begriffe, die in der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Dokumentation verwendet werden.

## <a name="terms"></a>Begriffe
 Add-In Eine Dienstprogrammanwendung, ein Treiber oder eine andere Software, die einer primären Anwendung hinzugefügt wurde. In der integrierten Visual Studio-Entwicklungsumgebung (IDE) ist ein Add-In eine Automatisierungs-basierte Anwendung, die die Funktionen der IDE erweitert.

 Automatisierungsmodell Das Automatisierungsmodell, das in früheren Versionen von Visual Studio als Erweiterbarkeitsmodell bezeichnet wird, ist eine Programmierschnittstelle, die Ihnen Zugriff auf die zugrunde liegenden Routinen gibt, die die IDE antreiben. Add-Ins, Assistenten und Makros verwenden Objekte im Automatisierungsmodell, um die Funktionalität der IDE zu steuern oder zu erweitern.

 Befehl UI-Kontext Zuordnung einer GUID mit der Sichtbarkeit eines UI-Befehls oder Elements, z. B. einer Symbolleiste. Der Kontext der Befehlsbenutzeroberfläche unterscheidet sich im Gegensatz zum Auswahlkontext, da er nicht an ein Fenster angefügt ist.

 Der Kontext der Befehlsbenutzeroberfläche kann verwendet werden, um:

- Weisen Sie einer Symbolleiste eine GUID zu, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert wird.

- Weisen Sie der Verfügbarkeit eines Befehls eine GUID zu, ohne ein VSPackage laden oder ausführen zu müssen.

- Weisen Sie eine GUID zu, um die aktive Schlüsselbindung zu beeinflussen.

- Weisen Sie eine GUID zu, um die Makroaufzeichnung zu aktivieren.

- Weisen Sie eine GUID zu, um den Debugmodus zu aktivieren oder zwischen Entwurf und Ausführungsmodus in einem Editor umzuschalten.

  Komponente Software, die Teil der Funktionalität einer Anwendung werden kann, ohne dass diese Anwendung bereits vorhandene Informationen über die Implementierung der Software enthält. Die Kommunikation zwischen einer Komponente und einer Anwendung erfolgt ausschließlich über Schnittstellen im OLE-Stil.

  Komponentenmanager Ein `SOleComponentManager`Dienst , der Nicht-Benutzerschnittstellenkoordinationsdienste für Komponenten der obersten Ebene bereitstellt. Der `SOleComponentManager` Dienst implementiert `IOleComponentManager` die Schnittstelle.

  Component UI Manager `SOleComponentUIManager`Ein Dienst, der Benutzeroberflächenkoordinationsdienste bereitstellt. Der `SOleComponentUIManager` Dienst implementiert `IOleComponentUIManager` `IOleInPlaceComponentUIManager` die und Schnittstellen.

  Kontextbeutel `IVsUserContext` Ein Objekt (COM-Objekt), das an eine Umgebungskomponente angefügt ist. Dieses Objekt enthält Suchschlüsselwörter, **F1-Schlüsselwörter** und Attribute, die sich auf die Komponente beziehen. Kontextbeutel weisen zusätzlich auf alle Subkontextbeutel hin, die mit ihnen verknüpft sind.

  Kontextanbieter Eine Komponente in der IDE, der eine Kontexttüte zugeordnet ist. Zu diesen Komponenten gehören ein Werkzeugfenster, ein Editor oder eine Projekthierarchie.

  Designer Eine Programmierschnittstelle, mit der Benutzer Elemente der Benutzeroberfläche (Formulare, Schaltflächen und andere Steuerelemente) bearbeiten können.

  DocData Ein COM-Objekt, das die zugrunde liegenden Daten eines Dokuments in einer Welt kapselt, in der dokument-/ansichtstrennung besteht (z. B. im Fall des Texteditors wäre dies der Textpuffer, der allen Texteditoransichten zugrunde liegt). Wenn die EditorFactory dieses Objekt nicht liefert, stellt die IDE ein Objekt in ihrem Namen her. Die Verantwortung dieses Objekts liegt in der Verwaltung der Datenpersistenz `DocData`und der Freigabesemantik für mehrere Ansichten über diese . Wenn `DocData` das Objekt `IOleCommandTarget` die Schnittstelle unterstützt, ist es im Befehlsrouting der UIShell enthalten.

  DocObject-Technologie, die zum Hostieren der Benutzeroberfläche in einem vom Host bereitgestellten Frame verwendet wird. Genauer gesagt bezieht sich dieser Begriff auf `IOleDocument` jede Einbettung, die die und verwandte Schnittstellen unterstützt. Diese Technologie verfügt über viele potenzielle Anwendungen, z. B. implementierungsdetails COM-Dokumente, Toolfenster in Visual Basic 5.0, ActiveX-Designer in Visual Basic 6.0 usw.

  Dokument Verwendet, um allgemein auf das Dokument `DocData` als `DocView`Ganzes zu verweisen – sowohl die als auch die . Ein DocumentFrame enthält z. B. eine `DocView`, aber `DocData` es behält auch einen Verweis auf die Persistenz, die persistenz behandelt wird.

  DocView Das DocObject/Embedding/WindowPane, mit dem der Benutzer `DocData`interagiert, um den zugrunde liegenden anzuzeigen und zu bearbeiten. Benutzer nutzen die Dokument-/Ansichtstrennung, die Teil `DocObject` des Schnittstellenentwurfs ist, nicht. Benutzer verwenden ein gesamtes DocObject, um als Ansicht zu fungieren, anstatt einen abstrakteren (und weniger formalisierten) Begriff der zugrunde liegenden Daten zu verwenden, der als bezeichnet wird. `DocData` `DocView`Objekte werden immer mit Document Frame-Objekten (MDI-untergeordneten Fenstern) der IDE eingebettet.

  DTE `DTE` Das Objekt (Development Tools Extensibility) ist der oberste Zugriffspunkt im Visual Studio-Automatisierungsmodell, mit dem Sie die IDE programmgesteuert automatisieren und erweitern können.

  Dynamisches Hilfefenster Toolfenster, das von der IDE implementiert wird und eine Liste der Suchbegriffe oder **F1-Hilfethemen** anzeigt.

  Editorcode (Klasse, CLSID), der `DocView`die implementiert. Es wird `DocData` auch implementiert, wenn die Ansicht und die Datentrennung unterstützt werden.

  Erweiterung Ein Feature, das eine IDE ändert, anpasst oder hinzufügt. Sie erstellen Erweiterungen mit dem Automatisierungsmodell oder VSPackages.

  Externer Editor Ein Editor, der nicht spezifisch für die IDE ist, z. B. Microsoft Word. Es wurde über eigene Mechanismen registriert und kann außerhalb der IDE verwendet werden. Wenn dieser Editor eingebettet werden kann, wird er in einem Fenster in der IDE angezeigt. Wenn es nicht eingebettet werden kann, wird ein separates Fenster der obersten Ebene erstellt.

  HierarchieStruktur der Knoten, jedem Knoten, der einem Satz von Eigenschaften zugeordnet ist.

  unabhängige Komponente der obersten Ebene Eine Komponente, die ein modusloses Fenster der obersten Ebene verwendet und effektiv als eigenständiges Anwendungsfenster arbeiten kann, aber als In-Process-Objekt implementiert wird. Daher muss eine unabhängige Komponente der obersten Ebene Modalitäts- und Nachrichtenschleifendienste mit der IDE koordinieren. In-Process-Objekte haben keine eigene Nachrichtenschleife.

  Informationsanbieter Der Informationsanbieter ist ein Modul, das Keywords suchen und eine `IVsUserContextItem` Themenliste in Form von Objekten zurückgeben kann. Um **F1-** und Suchschlüsselelemente für den Informationsanbieter bereitzustellen, registrieren Sie Ihre kompilierte Hilfedatei (*. HxS*) mit dem System. Die Hilfethemen in diesen Dateien enthalten die Liste der Themen, die im Fenster Dynamische Hilfe angezeigt werden und angezeigt werden, ob ein Benutzer **F1**drückt.

  In-Place-Komponente Ein VSPackage-Objekt, das die `IOleInPlaceComponent` Schnittstelle implementiert, um ein Fenster zu verwalten, das visuell in einem Dokumentfenster enthalten ist, das der IDE gehört. Direkte Komponenten nehmen nicht an der standardmäßigen OLE-Menüzusammenführung teil. stattdessen integrieren sie ihre Benutzeroberflächenelemente in die IDE.

  Es gibt zwei Arten von ortsgebundenen Komponenten: fest verdrahtete an Ort und Stelle Komponentensteuerungen.

  Fest verdrahtete direkte Komponenten verfügen über Menüs, Symbolleisten und Befehle, die eng in die Benutzeroberfläche der IDE integriert sind und so erscheinen, als wären sie direkt in die IDE integriert.

  Komponentensteuerelemente verfügen nicht über eigene Benutzeroberflächenelemente, die in die IDE integriert sind. Stattdessen verwenden sie die Menüs, Befehle und Symbolleisten der IDE. Der Befehl Fett kann beispielsweise verwendet werden, um ein ausgewähltes Wort innerhalb eines in ein Formular eingebetteten Rich-Text-Steuerelements fett zu formatieren. Komponentensteuerelemente können jedoch anfordern, dass dynamisch installierte komponentenspezifische UI-Elemente angezeigt werden.

  Sprachdienst Eine Gruppe von Objekten, mit denen VSPackage-Entwickler Features von Code-Editoren für Computersprachen implementieren können, z. B. Textmarkierung und Farbtumung.

  Verschiedene Dateien Projekt Projekt verwendet, um offene Dateien zu hause, die nicht in einem Projekt sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.

  Projektprojekte bestehen aus Hierarchieobjekten oder COM-Objekten, die die `IVsHierarchy` Schnittstelle implementieren.

  projektspezifischer Designer oder Editor Ein Designer, der nicht unabhängig vom Projekttyp verwendet werden kann. Alle projektspezifischen Designer müssen ihre Editor Factory-Informationen in die Registrierung eingeben. Die IDE kann dann den Designer instanziieren, wenn ein bestimmter Dateityp in einem bestimmten Projekt geöffnet wird.

  Projekttypfenster Ein Fenster, das die aktuell aktive Projekthierarchie und das Element ständig aus dem globalen Auswahlkontext nachverfolgt. Fenster vom Projekttyp `SVsTrackSelectionEx` verwenden den Dienst, um die IDE über Änderungen zu warnen und dem Benutzer Feedback anzuzeigen. Der Projektmappen-Explorer ist ein Beispiel für ein Projektfenster.

  Eigenschaftenfenster Früher Eigenschaftenbrowser.

  Referenzbasierte Projekte Projekt, bei dem sich die Dateien für das Projekt nicht im selben Verzeichnis befinden müssen. Stattdessen werden Verweise auf Dateien aus anderen nicht verwandten Verzeichnissen gespeichert und vom Projekt selbst verwaltet.

  Laufende Dokumenttabelle Interne Struktur, mit der die IDE die Liste aller derzeit geöffneten Dokumente verwaltet. Die Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob die Dokumente gerade bearbeitet werden. Ein Dokument ist ein beliebiges Element, das gespeichert wird, einschließlich gespeicherter Prozeduren, die in einem Editor geöffnet werden, Dateien in einem Projekt oder der Hauptprojektdatei (z. B. *.vcproj-Datei).

  Auswahlkontext Daten, die Teil des Details jedes Fensters in der IDE sind und zum Nachverfolgen aktiver Auswahlen verwendet werden. Der Auswahlkontext besteht aus:

- Zeiger auf `IVsHierarchy` die Schnittstelle der Projekthierarchie

- Elementkennung des Projektelements.

- Zeiger auf `ISelectionContainer` die Schnittstelle, die Zugriff auf Eigenschaften für die aktiven Objekte bietet.

- Array von Elementwerten.

  service Ein Vertrag für eine Gruppe von COM-Schnittstellen, die sich in einem einzelnen COM-Objekt befinden. Wenn Sie einen Dienst erstellen, der durch eine GUID identifiziert wird, definieren Sie den Satz von COM-Schnittstellen, die den Dienst ausführt. COM-Objekte verwenden Dienste, um miteinander zu kommunizieren.

  Lösung Gruppe verwandter Projekte, mit denen ein Benutzer arbeitet.

  Standarddesigner Ein Designer, der unabhängig vom Projekttyp verwendet werden kann. Alle Standarddesigner müssen ihre Editor Factory-Informationen in die Registrierung eingeben. Die IDE kann dann den Designer instanziieren, wenn eine Datei mit einer bestimmten Erweiterung geöffnet wird. Die Daten müssen in einer Datei beibehalten werden.

  Standard-Editor-Editor, der unabhängig von einem bestimmten Projekttyp verwendet werden kann. Solche Editoren haben EditorFactories in der Registrierung registriert. Dadurch kann die IDE den Editor suchen und aufrufen.

  Standard-Betriebssystem-Editor Eine Einbettung, die nicht Visual Studio-spezifisch ist. Es wird mit den bekannten Win32-Schlüsseln registriert (z. B. weiß der Win32 Explorer, wie man ihn aufruft). Wenn ein solcher Editor eingebettet werden kann, wird der Editor immer noch an seiner Stelle in der IDE angezeigt. Andernfalls wird ein separates Fenster der obersten Ebene für solche Editoren erstellt.

  Subkontextbeutel `IVsUserContext` Ein Objekt, das mit einer Kontexttasche verknüpft ist. Das Objekt enthält Suchschlüsselwörter, **F1-Schlüsselwörter** und Attribute für eine Auswahl innerhalb einer IDE-Komponente. Beispiele für Subkontext sind ein Befehl in einem Toolfenster oder ein Schlüsselwort in einem Editor.

  Aufgabenliste Werkzeugfenster, das von der IDE implementiert wird und eine Liste der aktiven Aufgaben anzeigt.

  Textpuffer Allgemeiner Name `VSTextBuffer`für das Objekt .

  Textansicht Allgemeiner Name `VSTextView`für das Objekt .

  Werkzeugkomponente der obersten Ebene Eine Komponente, die als modusloses Popupfenster arbeitet und eng mit der Benutzeroberfläche der IDE koordiniert wird. Wie unabhängige Komponenten der obersten Ebene müssen Komponenten der werkzeugobersten Ebene auch Modalitäts- und Nachrichtenschleifendienste mit der IDE koordinieren.

  Top-Level-Komponente Ein VSPackage-Objekt, das ein modusloses Fenster der obersten Ebene anstelle des Clientbereichs eines IDE-Fensters verwaltet. Komponenten der obersten `IOleComponent` Ebene implementieren die Schnittstelle, um Nachrichtenschleifendienste wie den Zugriff auf Leerlaufzeiten zu nutzen.

  UI aktiv Ein VSPackage-Objekt, das sichtbar ist und derzeit den Fokus hat.

  UI-Hierarchie Ein COM-Objekt, das die `IVsUIHierarchy` Schnittstelle implementiert, um die Anzeige einer Hierarchie zu ermöglichen. Das UI-Hierarchiefenster `ISelectionContainer` implementiert die Schnittstelle zum Aktualisieren des Eigenschaftenfensters. andere Projektfenster können diese Implementierung bei Bedarf verwenden.

  VSCT Visual Studio-Befehlstabelle. Die .vsct-Datei enthält Informationen über die Platzierung und das Verhalten von Menüs, Symbolleisten und Befehlen im XML-Format.

  VSPackage Eine installierbare Software, die die Visual Studio-IDE erweitert, indem sie eines oder mehrere der folgenden Elemente beisteuert: Benutzeroberfläche, Dienste, Projekttypen oder Editor/Designer. Ein VSPackage besteht aus einem COM-Objekt, das die Schnittstelle implementiert, und einem oder mehreren anderen COM-Objekten, die `IVsPackage` andere Schnittstellen implementieren, um die Auswahl und andere Features zu unterstützen. Darüber hinaus hat ein VSPackage spezifische Registrierungsanforderungen.
