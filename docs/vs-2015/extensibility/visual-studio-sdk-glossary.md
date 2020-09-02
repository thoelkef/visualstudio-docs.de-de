---
title: Visual Studio SDK-Glossar | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538706"
---
# <a name="visual-studio-sdk-glossary"></a>Glossar für das Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Glossar enthält Definitionen für Begriffe, die in der- [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Dokumentation verwendet werden.  
  
## <a name="terms"></a>Begriffe  
 Add-In  
 Eine hilfsprogrammanwendung, ein Treiber oder eine andere Software, die zu einer primären Anwendung hinzugefügt wurde. In der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio ist ein Add-in eine Automatisierungs basierte Anwendung, die die Funktionen der IDE erweitert.  
  
 Automatisierungsmodell  
 Das Automatisierungs Modell, das in früheren Versionen von Visual Studio als Erweiterbarkeits Modell bekannt ist, ist eine Programmierschnittstelle, die Ihnen den Zugriff auf die zugrunde liegenden Routinen ermöglicht, die die IDE steuern. Add-Ins, Assistenten und Makros verwenden Objekte im Automatisierungs Modell, um die Funktionalität der IDE zu steuern oder zu erweitern.  
  
 Befehls Benutzeroberflächen Kontext  
 Zuordnung einer GUID mit der Sichtbarkeit eines UI-Befehls oder-Elements, z. b. einer Symbolleiste. Der Kontext der Befehls Benutzeroberfläche ist anders als der Auswahl Kontext, da er nicht an ein Fenster angefügt ist.  
  
 Der Befehls Benutzeroberflächen Kontext kann für Folgendes verwendet werden:  
  
- Zuweisen einer GUID zu einer Symbolleiste, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert wird.  
  
- Weisen Sie der Verfügbarkeit eines Befehls eine GUID zu, ohne ein VSPackage laden oder ausführen zu müssen.  
  
- Weisen Sie eine GUID zu, um die aktive schlüsselbindung zu beeinflussen.  
  
- Weisen Sie eine GUID zu, um die Makro Aufzeichnung zu aktivieren.  
  
- Weisen Sie eine GUID zu, um den Debugmodus zu aktivieren oder zwischen dem Entwurfs-und dem Lauf Modus in einem Editor zu wechseln.  
  
  Komponente  
  Software, die Teil der Funktionalität einer Anwendung sein kann, ohne dass diese Anwendung bereits vorhandene Informationen zur Implementierung der Software hat. Die Kommunikation zwischen einer Komponente und einer Anwendung erfolgt ausschließlich über Schnittstellen im OLE-Stil.  
  
  Komponenten-Manager  
  Ein Dienst, `SOleComponentManager` , der Nichtbenutzer Oberflächen-Koordinationsdienste für Komponenten der obersten Ebene bereitstellt. Der `SOleComponentManager` Dienst implementiert die- `IOleComponentManager` Schnittstelle.  
  
  Komponenten-UI-Manager  
  Ein Dienst, `SOleComponentUIManager` , der Benutzeroberflächen-Koordinationsdienste bereitstellt. Der `SOleComponentUIManager` Dienst implementiert die `IOleComponentUIManager` -und- `IOleInPlaceComponentUIManager` Schnittstellen.  
  
  Kontext Behälter  
  Ein `IVsUserContext` Objekt (com-Objekt), das an eine Umgebungs Komponente angefügt ist. Dieses Objekt enthält Such Schlüsselwörter, F1-Schlüsselwörter und Attribute, die mit der Komponente in Beziehung stehen. Kontext Behälter zeigen zusätzlich auf alle unter Kontext Behälter, die mit Ihnen verknüpft sind.  
  
  Kontext Anbieter  
  Eine Komponente in der IDE, der ein Kontext Behälter zugeordnet ist. Zu diesen Komponenten gehören ein Tool Fenster, ein Editor oder eine Projekt Hierarchie.  
  
  Designer  
  Eine Programmierschnittstelle, die es Benutzern ermöglicht, Elemente der Benutzeroberfläche (Formulare, Schaltflächen und andere Steuerelemente) zu bearbeiten.  
  
  DocData  
  Ein COM-Objekt, das die zugrunde liegenden Daten eines Dokuments in einer Welt kapselt, in der die Dokument-/ansichttrennung vorliegt (z. b. im Text-Editor-Fall ist dies der Text Puffer, der allen Text-Editor-Sichten zugrunde liegt). Wenn die Editorfactory dieses Objekt nicht bereitstellt, wird Sie von der IDE in Ihrem Auftrag erstellt. Die Verantwortung für dieses Objekt besteht darin, die Daten Persistenz und die Freigabe Semantik für mehrere Ansichten zu verwalten `DocData` . Wenn das `DocData` Objekt die- `IOleCommandTarget` Schnittstelle unterstützt, wird es in das Befehls Routing von uiShell eingeschlossen.  
  
  DocObject  
  Technologie, mit der die Benutzeroberfläche in einem Frame gehostet wird, der vom Host bereitgestellt wird. Genauer gesagt bezieht sich dieser Begriff auf alle Einbettungen, die die `IOleDocument` und die zugehörigen Schnittstellen unterstützen. Diese Technologie verfügt über zahlreiche potenzielle Anwendungen, wie z. b. ein Implementierungsdetail von com-Dokumenten, Tool Fenster in Visual Basic 5,0, ActiveX-Designern in Visual Basic 6,0 usw.  
  
  Dokument  
  Wird verwendet, um generisch auf das Dokument als Ganzes zu verweisen – sowohl als `DocData` auch die `DocView` . Ein documentframe enthält z. b. einen `DocView` , behält aber auch einen Verweis auf, `DocData` um die Persistenz zu verarbeiten.  
  
  DocView  
  DocObject/Einbettungs-/Windows-Pane, mit dem der Benutzer interagiert, um den zugrunde liegenden anzuzeigen und zu bearbeiten `DocData` . Beachten Sie, dass die Benutzer die Trennung von Dokumenten/Sichten, die Teil des Schnittstellen Entwurfs ist, nicht nutzen `DocObject` . Benutzer verwenden ein gesamtes DocObject-Objekt, um als Ansicht zu fungieren, anstatt ein abstraktes (und weniger formalisiertes) Konzept der zugrunde liegenden Daten zu verwenden, die als bezeichnet werden `DocData` . `DocView` Objekte werden immer mit Dokument Rahmen Objekten (untergeordnete MDI-Fenster) der IDE eingebettet.  
  
  DTE  
  Das `DTE` -Objekt (Erweiterbarkeit der Entwicklungs Tools) ist der oberste Zugriffspunkt im Visual Studio-Automatisierungs Modell, mit dem Sie die IDE Programm gesteuert automatisieren und erweitern können.  
  
  Dynamisches Hilfefenster  
  Tool Fenster, das von der IDE implementiert wird und eine Liste mit Such Schlüsselwörtern oder F1-Hilfe Themen anzeigt.  
  
  Editor  
  Code (Klasse, CLSID), der implementiert `DocView` . Es implementiert auch, `DocData` Wenn die Unterscheidung zwischen Sicht und Daten unterstützt wird.  
  
  Erweiterung  
  Eine Funktion, mit der eine IDE geändert, angepasst oder einer IDE hinzugefügt wird. Sie erstellen Erweiterungen mit dem Automatisierungs Modell oder VSPackages.  
  
  externer Editor  
  Ein Editor, der nicht spezifisch für die IDE ist, z. b. Microsoft Word. Es wurde über seine eigenen Mechanismen registriert und kann außerhalb der IDE verwendet werden. Wenn dieser Editor eingebettet werden kann, wird er in einem Fenster in der IDE angezeigt. Wenn Sie nicht eingebettet werden kann, wird ein separates Fenster der obersten Ebene erstellt.  
  
  Hierarchie  
  Struktur von Knoten, jeder Knoten, der einem Satz von Eigenschaften zugeordnet ist.  
  
  unabhängige Komponente der obersten Ebene  
  Eine Komponente, die ein nicht modalem Fenster der obersten Ebene verwendet und effektiv als eigenständiges Anwendungsfenster fungieren kann, jedoch als in-Process-Objekt implementiert wird. Daher muss eine unabhängige Komponente der obersten Ebene die Modalität und Nachrichten Schleifen Dienste mit der IDE koordinieren. In-Process-Objekte haben keine eigene Nachrichten Schleife.  
  
  Informationsanbieter  
  Der Informationsanbieter ist ein Modul, das nach Schlüsselwörtern suchen und eine Liste von Themen in Form von-Objekten zurückgeben kann `IVsUserContextItem` . Um F1-und Suche-Schlüsselwort Elemente für den Informationsanbieter bereitzustellen, registrieren Sie die kompilierte Hilfedatei (. HxS) mit dem System. Die Hilfe Themen in diesen Dateien werden verwendet, um die Liste der Themen bereitzustellen, die im Fenster Dynamische Hilfe angezeigt werden, und es wird angezeigt, ob ein Benutzer F1 drückt.  
  
  direkte Komponente  
  Ein VSPackage-Objekt, das die- `IOleInPlaceComponent` Schnittstelle zum Verwalten eines Fensters implementiert, das sich visuell in einem Dokument Fenster befindet, das der IDE gehört. Direkte Komponenten nehmen nicht an der standardmäßigen OLE-Menü Zusammenführung Teil. Stattdessen integrieren Sie die Elemente der Benutzeroberfläche in die IDE.  
  
  Es gibt zwei Arten von direkten Komponenten: hart verdrahtete direkte Komponenten und Komponenten Steuerelemente.  
  
  Direkt verdrahtete direkte Komponenten verfügen über Menüs, Symbolleisten und Befehle, die eng in die Benutzeroberfläche der IDE integriert sind und so angezeigt werden, als würden Sie direkt in die IDE integriert.  
  
  Komponenten Steuerelemente verfügen nicht über eigene Benutzeroberflächen Elemente, die in die IDE integriert sind. Stattdessen verwenden Sie die Menüs, Befehle und Symbolleisten der IDE. Beispielsweise könnte mit dem Befehl Bold ein ausgewähltes Wort in einem Rich-Text-Steuerelement fett formatiert werden, das in ein Formular eingebettet ist. Komponenten Steuerelemente können jedoch anfordern, dass dynamisch installierte Komponenten spezifische UI-Elemente angezeigt werden.  
  
  Sprachdienst  
  Ein Satz von-Objekten, mit dem VSPackage-Entwickler Features von Computer Sprachcode-Editoren implementieren können, z. b. Textmarkierung und farbige Farbgebung.  
  
  Projekt "sonstige Dateien"  
  Projekt zum beherbergen offener Dateien, die nicht in einem Projekt vorhanden sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.  
  
  Projekt  
  Projekte bestehen aus Hierarchie Objekten oder COM-Objekten, die die- `IVsHierarchy` Schnittstelle implementieren.  
  
  projektspezifischer Designer oder Editor  
  Ein Designer, der nicht unabhängig vom Projekttyp verwendet werden kann. Alle projektspezifischen Designer müssen ihre Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann dann den Designer instanziieren, wenn ein bestimmter Dateityp in einem bestimmten Projekt geöffnet wird.  
  
  Projekttyp Fenster  
  Ein Fenster, in dem die derzeit aktive Projekt Hierarchie und das Element aus dem globalen Auswahl Kontext nachverfolgt werden. Projekttyp Windows verwenden `SVsTrackSelectionEx` Sie den-Dienst, um die IDE der Änderungen zu warnen und dem Benutzer Feedback anzuzeigen. Projektmappen-Explorer ist ein Beispiel für ein Fenster vom Typ Projekt.  
  
  Eigenschaftenfenster  
  Früher Eigenschaften Browser.  
  
  Verweis basierte Projekte  
  Projekt, bei dem sich die Dateien für das Projekt nicht im selben Verzeichnis befinden müssen. Stattdessen werden Verweise auf Dateien aus anderen nicht verknüpften Verzeichnissen gespeichert und durch das Projekt selbst verwaltet.  
  
  Ausführen der dokumententabelle  
  Interne Struktur, mit der die IDE die Liste aller gegenwärtig geöffneten Dokumente verwaltet. Diese Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob die Dokumente gerade bearbeitet werden. Ein Dokument ist ein beliebiges Element, das gespeichert wird, einschließlich gespeicherter Prozeduren, die in einem Editor geöffnet sind, Dateien in einem Projekt oder in der Hauptprojekt Datei (z. b. *. VCPROJ-Datei).  
  
  Auswahl Kontext  
  Daten, die Teil der Details jedes Fensters in der IDE sind und zum Nachverfolgen der aktiven Auswahl verwendet werden. Der Auswahl Kontext besteht aus folgendem:  
  
- Zeiger auf die- `IVsHierarchy` Schnittstelle der Projekt Hierarchie  
  
- Der Element Bezeichner des Projekt Elements.  
  
- Ein Zeiger auf die- `ISelectionContainer` Schnittstelle, die Zugriff auf die Eigenschaften der aktiven-Objekte bereitstellt  
  
- Array von Element Werten.  
  
  Dienst  
  Ein Vertrag für einen Satz von COM-Schnittstellen, die sich in einem einzelnen COM-Objekt befinden. Wenn Sie einen Dienst erstellen, der durch eine GUID identifiziert wird, definieren Sie den Satz von COM-Schnittstellen, der den Dienst ausführt. Für COM-Objekte werden Dienste verwendet, um miteinander zu kommunizieren.  
  
  Lösung  
  Gruppe verwandter Projekte, mit denen ein Benutzer arbeitet.  
  
  Standard-Designer  
  Ein Designer, der unabhängig vom Projekttyp verwendet werden kann. Alle Standard Designer müssen die Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann dann den Designer instanziieren, wenn eine Datei mit einer bestimmten Erweiterung geöffnet wird. Die Daten müssen in einer Datei gespeichert werden.  
  
  Standard-Editor  
  Editor, der unabhängig von einem bestimmten Projekttyp verwendet werden kann. Bei solchen Editoren sind editorfactorys in der Registrierung registriert. Dies ermöglicht der IDE, den Editor zu finden und aufzurufen.  
  
  Standard-OS-Editor  
  Eine Einbettung, die nicht Visual Studio-spezifisch ist. Sie wird mit den bekannten Win32-Schlüsseln registriert (z. b. kann der Win32-Explorer aufrufen). Wenn ein solcher Editor eingebettet werden kann, wird der Editor weiterhin in der IDE angezeigt. Andernfalls wird für solche Editoren ein separates Fenster der obersten Ebene erstellt.  
  
  unter Kontext Behälter  
  Ein- `IVsUserContext` Objekt, das mit einem Kontext Behälter verknüpft ist. Dieses Objekt enthält Such Schlüsselwörter, F1-Schlüsselwörter und Attribute für eine Auswahl innerhalb einer IDE-Komponente. Beispiele für unter Kontext sind ein Befehl in einem Tool Fenster oder ein Schlüsselwort in einem Editor.  
  
  Aufgabenliste  
  Tool Fenster, das von der IDE implementiert wird und eine Liste aktiver Aufgaben anzeigt.  
  
  Text Puffer  
  Der allgemeine Name für das Objekt `VSTextBuffer` .  
  
  Text Ansicht  
  Der allgemeine Name für das Objekt `VSTextView` .  
  
  Tool Komponente der obersten Ebene  
  Eine Komponente, die als nicht modalem Popup Fenster fungiert und eng mit der Benutzeroberfläche der IDE koordiniert wird. Wie unabhängige Komponenten der obersten Ebene müssen auch Tool Komponenten der obersten Ebene die Modalität und Nachrichten Schleifen Dienste mit der IDE koordinieren.  
  
  Komponente der obersten Ebene  
  Ein VSPackage-Objekt, das ein nicht modalem Fenster auf oberster Ebene anstelle des Client Bereichs eines IDE-Fensters verwaltet. Komponenten der obersten Ebene implementieren die- `IOleComponent` Schnittstelle, um Nachrichten Schleifen Dienste wie den Zugriff auf die Leerlaufzeit zu nutzen.  
  
  UI-aktiv  
  Ein VSPackage-Objekt, das sichtbar ist und derzeit den Fokus besitzt.  
  
  UI-Hierarchie  
  Ein COM-Objekt, das die- `IVsUIHierarchy` Schnittstelle implementiert, um die Anzeige einer Hierarchie zuzulassen. Das UI-Hierarchie Fenster implementiert die- `ISelectionContainer` Schnittstelle, um die Eigenschaftenfenster zu aktualisieren. andere Projekttyp Fenster können diese Implementierung verwenden, wenn gewünscht.  
  
  VSCT  
  Visual Studio-Befehls Tabelle. Die vsct-Datei enthält Informationen über die Platzierung und das Verhalten von Menüs, Symbolleisten und Befehlen im XML-Format.  
  
  VSPackage  
  Ein installier bares Softwareelement, das die Visual Studio-IDE erweitert, indem Sie eine oder mehrere der folgenden Aktionen beibringt: Benutzeroberfläche, Dienste, Projekttypen oder Editor/Designer. Ein VSPackage besteht aus einem COM-Objekt, das die `IVsPackage` -Schnittstelle implementiert, und einem oder mehreren anderen COM-Objekten, die andere Schnittstellen implementieren, um Auswahl und andere Funktionen zu unterstützen. Außerdem gelten für ein VSPackage bestimmte Registrierungsanforderungen.
