---
title: "IDE-definierte Befehle f&#252;r die Erweiterung Projektsysteme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, Projektsysteme"
  - "Projektsysteme, Umgebung benutzerdefinierte Befehle"
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# IDE-definierte Befehle f&#252;r die Erweiterung Projektsysteme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie Projektsysteme erweitern möchten, können Sie die Befehle und Befehlsgruppen verwenden, die vom [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bereitgestellt werden.  
  
 In den folgenden Abschnitten sind die Elemente aufgeführt, die zum Erweitern von Projektsystemen besonders nützlich sind.  
  
## Befehls\-Menüs  
 In der folgenden Tabelle werden die Menüs Befehls an, die nützliche Speicherorte befinden, damit Sie Befehle auf hoher Ebene einfügen, die einem Projekt extender aufrufen.  
  
|Klicken Sie im Menü Befehle|Beschreibung|  
|---------------------------------|------------------|  
|IDM\_VS\_MENU\_PROJECT|Das Menü **Projekt** der obersten Ebene.|  
|IDM\_VS\_TOOL\_PROJWIN|Die **Projektmappen\-Explorer** Symbolleiste.|  
  
## Kontextmenüs  
 In der folgenden Tabelle sind die Kontextmenüs an, die gelten für die ein einzelner Knoten in **Projektmappen\-Explorer**ausgewählt wird oder wenn es mehrere homogene Auswahl in **Projektmappen\-Explorer**vorhanden ist, wenn alle ausgewählten Knoten vom selben Typ sind.  
  
|Kontextmenü|Beschreibung|  
|-----------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Gilt, wenn der Knoten ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Gilt, wenn eine Datei ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Gilt, wenn ein Ordner ausgewählt wird.|  
|IDM\_VS\_CTXT\_WEBREFFOLDER|Gilt, wenn der Ordner Webverweise ausgewählt ist.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Gilt, wenn der Stammknoten " Verweise „Verweise“ aufgerufen wird, ausgewählt ist.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Gilt, wenn Verweisknoten ausgewählt werden. Diese schließen nur Assembly, COM\- und Projektverweise ein.  Schließt keine Webverweise ein.|  
  
 In der folgenden Tabelle sind die Kontextmenüs an, die anwenden, wenn die Auswahl in **Projektmappen\-Explorer** mehrere Hierarchien umfassen.  
  
|Kontextmenü|Beschreibung|  
|-----------------|------------------|  
|IDM\_VS\_CTXT\_XPROJ\_SLNPROJ|Gilt, wenn die aktuelle Auswahl knoten\- Stammprojekt und Projektmappen Knoten enthält.|  
|IDM\_VS\_CTXT\_XPROJ\_SLNITEM|Gilt, wenn die aktuelle Auswahl den Projektmappenknoten und \- Projektelemente enthält.|  
|IDM\_VS\_CTXT\_XPROJ\_MULTIPROJ|Gilt nur, wenn sich die aktuelle Auswahl aus mehreren Knoten Stammprojekt besteht.|  
|IDM\_VS\_CTXT\_XPROJ\_PROJITEM|Gilt, wenn die aktuelle Auswahl einer Mischung von Knoten Stammprojekt und \- Projektelemente enthält.  Darüber hinaus enthält die Auswahl möglicherweise den Projektmappenknoten.|  
|IDM\_VS\_CTXT\_XPROJ\_MULTIITEM|Gilt, wenn die aktuelle Auswahl von Projektelementen mehrere Projekte in der Projektmappe enthält, oder wenn Elemente unterschiedlicher Typen im gleichen Projekt ausgewählt werden.|  
  
## Befehlsgruppen  
 In der folgenden Tabelle sind die Befehlsgruppen an, die Sie verwenden können, wenn Sie Projekte erweitern, und das Sie über das <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> Kontextmenü zugreifen können.  
  
|Befehlsgruppe|Beschreibung|  
|-------------------|------------------|  
|IDG\_VS\_CTXT\_PROJECT\_BUILD|Befehle für das Erstellen, Neuerstellen und Bereitstellen des Projekts.|  
|IDG\_VS\_CTXT\_COMPILELINK|Befehle für das Kompilieren und Verknüpfen des Projekts.|  
|IDG\_VS\_CTXT\_PROJECT\_CONFIG|Befehle, die Projektkonfigurations\- und Buildreihenfolge festlegen.|  
|IDG\_VS\_CTXT\_PROJECT\_ADD|Befehle, die dem Projekt Elemente hinzufügen.|  
|IDG\_VS\_CTXT\_PROJECT\_START|Befehle, die das Startprojekt festlegen, mit der die F5\-Taste zugeordnet wurde.|  
|IDG\_VS\_CTXT\_PROJECT\_SAVE|Befehle zum Speichern von Projektelementen.|  
|IDG\_VS\_CTXT\_PROJECT\_DEBUG|Befehle für das Debuggen.|  
|IDG\_VS\_CTXT\_PROJECT\_SCC|Befehle für die Quellcodeverwaltung.|  
|IDG\_VS\_CTXT\_PROJECT\_TRANSFER|Befehle Kopieren und Ausschneiden und für Einfügevorgänge.|  
|IDG\_VS\_CTXT\_PROJECT\_PROPERTIES|Befehle, die den Zugriff auf das Dialogfeld **Projekteigenschaften** ermöglichen.|  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand\- und OleMenuCommand\-Objekte](../../misc/menucommands-vs-olemenucommands.md)   
 [Erstellen von wieder verwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md)