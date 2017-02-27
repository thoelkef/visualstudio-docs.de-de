---
title: "Befehl Design | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle"
  - "Befehle, die Implementierung"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Befehl Design
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie einen Befehl VSPackage hinzufügen, müssen Sie angeben, wo sie angezeigt werden soll, wenn es verfügbar ist, und wie er behandelt werden soll.  
  
## Befehle definieren  
 Um neue Befehle zu definieren, fügen Sie eine Visual Studio\-Befehls\-Tabelle .vsct \(\) im VSPackage\-Projekt ein.  Wenn Sie ein VSPackage erstellen, indem Sie die Visual Studio\-Paket\-Vorlage verwendet haben, enthält das Projekt eine dieser Dateien.  Weitere Informationen finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio führt alle gefundenen zusammen .vsct\-Dateien, dass die Befehle anzeigen kann.  Da diese Dateien von der VSPackage\-Binärdatei unterschiedlich sind, muss Visual Studio das Paket nicht laden, um die Befehle zu ermitteln.  Weitere Informationen finden Sie unter [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio verwendet das Attribut <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Registrierungsdaten, um Menüressourcen und Befehle zu definieren.  Weitere Informationen finden Sie unter [Implementierung](../../extensibility/internals/command-implementation.md).  
  
 Befehle können auf mehrere verschiedene Möglichkeiten zur Laufzeit geändert werden.  Sie können angezeigt oder ausgeblendet werden, aktiviert oder deaktiviert werden.  Sie können verschiedene Text oder Symbolen angezeigt werden, oder andere Werte enthalten.  Ein Großteil Anpassung ist ausgeführt werden, bevor Visual Studio VSPackages geladen werden.  Weitere Informationen finden Sie unter [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## Befehls\-Handler  
 Wenn Sie einen Befehl erstellen, müssen Sie einen Ereignishandler bereitstellen, um den Befehl auszuführen.  Wenn der Benutzer den Befehl auswählt, muss er entsprechend weitergeleitet werden.  Weiterleiten eines Befehls für das Senden dieser in richtigen VSPackages ausblenden, um es zu aktivieren bzw. zu deaktivieren oder es anzuzeigen und führt sie aus, wenn der Benutzer beschließt.  Weitere Informationen finden Sie unter [Routing\-Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
## Die Visual Studio\-Befehls\-Umgebung  
 Visual Studio kann der Host eine beliebige Anzahl von VSPackages und jedes kann seinen eigenen Befehls Gruppe beitragen.  Die Umgebung wird nur die Befehle an, die auf die aktuelle Aufgabe geeignet sind.  Weitere Informationen finden Sie unter [Verfügbarkeit](../../extensibility/internals/command-availability.md) und [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md).  
  
 VSPackage, das die neue Befehle definiert, Menüs, Symbolleisten oder Kontextmenüs stellt die Befehlsinformationen für Visual Studio bei der Installation von Registrierungseinträgen dass Bezugshilfsmittel im systemeigenen oder verwalteten Assemblys bereit.  Jede Ressource verweist auf eine Datei der Binärdaten Ressource \(.cto\), die angezeigt wird, wenn Sie eine Visual Studio\-Befehls\-Tabelle \(.vsct\) kompilieren.  Dies kann Visual Studio, um zusammengeführte Befehls legt bereitzustellen, Menüs und Symbolleisten, ohne jedes installierte VSPackages geladen werden soll.  
  
### Befehls\-Organisation  
 Die Befehle positions Umgebung von Gruppe, Priorität und Menüs.  
  
-   Gruppen sind logische Auflistung verwandter Befehlen bereit, z. B. von **Ausschneiden**, **Kopieren**und **Einfügen** Befehlsgruppe.  Gruppen sind die Befehle in Menüs angezeigt werden.  
  
-   Priorität bestimmt die Reihenfolge, in der einzelne Befehle in einer Gruppe im Menü angezeigt werden.  
  
-   Menüs fungieren als Container für Gruppen auf.  
  
 Die Umgebung definiert mehrere Befehle, Gruppen und Menüs vor.  Weitere Informationen finden Sie unter [Standardbefehl, Gruppen\- und Platzierung der Symbolleiste](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Ein Befehl eine primäre Gruppe zugewiesen werden kann.  Die wichtigsten Steuerelemente die Position des Befehls in der Struktur des Hauptmenüs und im Dialogfeld **Anpassen** .  Ein Befehl kann in mehreren Gruppen werden. Beispielsweise kann ein Befehl für das Hauptmenü angezeigt, und in einem Kontextmenü auf einer Symbolleiste sein.  Weitere Informationen finden Sie unter [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### Befehls\-Routing  
 Der Prozess des Aufrufs und des Weiterleitens von Befehlen für VSPackages unterscheidet sich vom Prozess des Aufrufs von Methoden für Objektinstanzen.  
  
 Die Umgebung führt Befehle sequenziell aus dem innersten \(lokalen\) \- Befehls auf Grundlage der aktuellen Auswahl ist, zum äußersten \(globale\) Kontext wechselt.  Im ersten Kontext, der den Befehl auszuführen, ist der, der diesen behandelt.  Weitere Informationen finden Sie unter [Routing\-Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
 In den meisten Instanzen behandelt die Umgebung Befehle, indem sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Schnittstelle verwendet.  Da das Befehlsobjekt routing Schema für viele verschiedene Objekte zum Behandeln von Befehlen ermöglicht, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kann eine beliebige Anzahl von Objekten implementiert werden. Im Folgenden werden einige dieser ActiveX\-Steuerelemente Microsoft Windows Implementierungen, die Dokumentobjekte hierarchien Projekt, und VSPackage\-Objekte selbst \(für globale Befehle\).  In einigen speziellen Fällen, z. B. Befehle in einer Hierarchie weiterleitend, muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>\-Schnittstelle implementiert werden.  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Implementierung](../../extensibility/internals/command-implementation.md)|Beschreibt, wie Befehle in einem VSPackage implementieren.|  
|[Verfügbarkeit](../../extensibility/internals/command-availability.md)|Beschreibt, wie Visual Studio\-Kontext bestimmt, welche Befehle verfügbar sind.|  
|[Routing\-Algorithmus](../../extensibility/internals/command-routing-algorithm.md)|Beschreibt, wie Visual Studio\-Befehls\-Routing können Befehle Architektur der durch ein anderes VSPackages behandelt werden sollen.|  
|[Richtlinien zur Platzierung](../../extensibility/internals/command-placement-guidelines.md)|Schlägt vor, wie Befehle in der Visual Studio\-Umgebung positioniert.|  
|[Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Beschreibt, wie gut die VSPackages Visual Architektur der Studio\-Befehls verwenden kann.|  
|[Standardbefehl, Gruppen\- und Platzierung der Symbolleiste](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Beschreibt, wie VSPackages beste Verwendung der Befehle können, die in Visual Studio enthalten sind.|  
|[Verwalten von VSPackages](../../extensibility/managing-vspackages.md)|Beschreibt, wie Visual Studio VSPackages geladen werden.|  
|[Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Stellt Informationen über XML\-basierte .vsct\-Dateien bereit, mit denen das Lay\-out und die Darstellung von Befehlen in VSPackages zu beschreiben.|