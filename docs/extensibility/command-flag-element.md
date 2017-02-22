---
title: "Command-Flag-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandFlag-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, CommandFlag"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Command-Flag-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ändert das übergeordnete Element.  
  
## Syntax  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## Attribute und Elemente  
 Der folgende Abschnitt beschreibt die gültige Element\-Werte.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Wert|Beschreibung|  
|----------|------------------|  
|AllowParams|Gibt an, dass Benutzer, die Parameter des Befehls in eingeben können die **Befehl** Fenster, wenn sie den kanonischen Namen des Befehls eingeben.<br /><br /> Gültig für: `Button`|  
|AlwaysCreate|Menü wird erstellt, auch wenn es keine Gruppen und Schaltflächen aufweist.<br /><br /> Gültig für: `Menu`|  
|CaseSensitive|Benutzereingaben werden Groß\-und Kleinschreibung berücksichtigt.<br /><br /> Gültig für: `Combo`|  
|CommandWellOnly|Wenden Sie dieses Flag an, wenn der Befehl nicht auf das Menü der obersten Ebene angezeigt und soll für zusätzliche Shell angepasst werden, z. B. für das Binden an eine Tastenkombination verfügbar zu machen. Nach der Installation des VSPackages können Sie mit diesen Befehlen anpassen, indem Sie öffnen die **Optionen** \(Dialogfeld\), und bearbeiten Sie anschließend den Befehl Platzierung unter der **Tastatur Umgebung** Kategorie. Dieses Flag hat keine Auswirkungen auf die Platzierung auf Kontextmenüs, Symbolleisten, Menüs oder Untermenüs.<br /><br /> Gültig für: `Button`, `Combo`|  
|DefaultDisabled|Der Befehl ist standardmäßig deaktiviert, wenn das VSPackage, das sie implementiert nicht geladen wird oder die `QueryStatus` \-Methode nicht aufgerufen wurde.<br /><br /> Gültig für: `Button`, `Combo`|  
|DefaultDocked|Standardmäßig verankert. Diese Einstellung nicht mehr gilt für Symbolleisten, da diese immer angedockt sind.|  
|DefaultInvisible|Der Befehl ist standardmäßig nicht sichtbar, wenn das VSPackage, das sie implementiert nicht geladen wird oder die `QueryStatus` \-Methode nicht aufgerufen wurde.<br /><br /> Es wird empfohlen, dass Sie dies durch Kombinieren der `DynamicVisibility` Flag.<br /><br /> Gültig für: `Button`, `Combo`, `Menu`|  
|DontCache|Die Development Environment zwischenspeichert, die `QueryStatus` Methodenergebnisse für diesen Befehl.<br /><br /> Ein Menü gibt dies einen Menü\-Controller nicht, der den Text der Einträge im cache. Verwenden Sie dieses Flag an, wenn das Menü enthält die dynamischen Elemente oder Elemente mit dynamischen Text.<br /><br /> Gültig für: `Button`, `Menu`|  
|DynamicItemStart|Gibt den Anfang einer dynamischen Liste. Dadurch können die Umgebung, um eine Liste zu erstellen, indem Sie nacheinander Aufrufen der `QueryStatus` \-Methode für Listenelemente, bis das Flag OLECMDERR\_E\_UNSUPPORTED zurückgegeben wird. Dies funktioniert gut für Elemente, wie z. B. zuletzt Fensterlisten und Listen der zuletzt verwendeten.<br /><br /> Gültig für: `Button`|  
|DynamicVisibility|Die Sichtbarkeit des Befehls geändert werden kann, bis die `QueryStatus` Methode oder durch eine Kontext\-GUID, die in enthalten ist die `VisibilityConstraints` Abschnitt.<br /><br /> Gilt für Befehle in Menüs und Symbolleisten von Toolfenstern, aber nicht auf der obersten Ebene Symbolleisten, die im Hauptfenster angezeigt werden. Elemente der obersten Ebene können deaktiviert, jedoch nicht ausgeblendet, wenn das Flag OLECMDF\_INVISIBLE, von zurückgegeben wird der `QueryStatus` Methode. Symbolleistenbefehle auf Symbolleisten von Toolfenstern können ausgeblendet werden.<br /><br /> In einem Menü gibt dieses Flag auch, dass es automatisch ausgeblendet werden soll, wenn alle seine Member ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da dieses Verhalten bereits über Menüs der obersten Ebene verfügen.<br /><br /> Dieses Flag kombiniert werden soll, mit der `DefaultInvisible` Flag.<br /><br /> Gültig für: `Button`, `Combo`, `Menu`|  
|Filter\-Schlüssel|Finden Sie unter Filtern von Schlüsseln [Kombinationsfeld\-Element](../extensibility/combo-element.md).<br /><br /> Gültig für: `Combo`|  
|FixMenuController|Wenn dieser Befehl auf einem Domänencontroller im Menü positioniert ist, ist der Befehl immer die Standardeinstellung. also ist mit dem Befehl ausgewählt, wenn die Schaltfläche selbst Controller ausgewählt ist. Wenn der Menü\-Controller verfügt die `TextIsAnchorCommand` \-flag festgelegt ist, und klicken Sie dann im Menü Controller nimmt auch den Text des Befehls, die die `FixMenuController` Flag.<br /><br /> Nur ein Befehl auf einem Domänencontroller im Menü müsste die `FixMenuController` Flag. Wenn mehr als einen Befehl so gekennzeichnet ist, wird mit dem letzte Befehl im Menü der Standardbefehl.<br /><br /> Gültig für: `Button`|  
|IconAndText|Zeigen Sie im Menü und Symbolleiste ein Symbol und Text.<br /><br /> Gültig für: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Die AutoVervollständigen Funktion ist deaktiviert.<br /><br /> Gültig für: `Combo`|  
|NoButtonCustomize|Lassen Sie nicht des Benutzers diese Schaltfläche anpassen.<br /><br /> Gültig für: `Button`, `Combo`|  
|NoKeyCustomize|Aktivieren Sie die Anpassung der Tastatur nicht.<br /><br /> Gültig für: `Button`, `Combo`|  
|NoShowOnMenuController|Wenn Sie diesen Befehl auf einem Domänencontroller im Menü positioniert ist, wird der Befehl nicht in der Dropdown\-Liste angezeigt.<br /><br /> Gültig für: `Button`|  
|NotInTBList|Wird nicht in der Liste der verfügbaren Symbolleisten angezeigt werden. Dies ist nur für die Symbolleiste Menütypen gültig.<br /><br /> Gültig für: `Menu`|  
|NoToolbarClose|Benutzer kann die Symbolleiste nicht schließen. Dies ist nur für die Symbolleiste Menütypen gültig.<br /><br /> Gültig für: `Menu`|  
|PICT|Zeigen Sie nur ein Symbol auf einer Symbolleiste, aber nur Text in einem Menü. Wenn kein Symbol angegeben wird, zeigt ein durch Klicken aktivierbaren Leerzeichen auf einer Symbolleiste.<br /><br /> Gültig für: `Button`|  
|PostExec|Wird der Befehl nicht blockierend. Die Development Environment verzögert Ausführung, bis alle vorab verarbeitete Abfragen abgeschlossen sind.<br /><br /> Gültig für: `Button`|  
|RouteToDocs|Der Befehl wird an das aktive Dokument weitergeleitet.<br /><br /> Gültig für: `Button`|  
|StretchHorizontally|Wenn dieses Flag festgelegt ist, wird die Breite die minimale Breite für das Kombinationsfeld, und wenn auf der Symbolleiste Platz vorhanden ist, im Kombinationsfeld wird gestreckt, um den verfügbaren Platz ausfüllen. Dies geschieht nur, wenn die Symbolleiste horizontal angedockt ist, und nur ein Kombinationsfeld auf der Symbolleiste kann das Flag \(das Flag wird auf allen außer den ersten Kombinationsfeld ignoriert\).<br /><br /> Gültig für: `Combo`|  
|TextMenuUseButton|Verwenden der `ButtonText` für Menüs. Das Feld `MenuText` Wenn es angegeben wird.<br /><br /> Gültig für: `Button`|  
|TextÄndert|Der Befehl oder Menü Text kann über in der Regel zur Laufzeit geändert werden die `QueryStatus` Methode.<br /><br /> Gültig für: `Button`, `Menu`|  
|TextChangesButton|Gültig für: `Button`|  
|TextIsAnchorCommand|Bei einem Domänencontroller im Menü wird der Text im Menü den Standardbefehl \(Anker\) entnommen. Ein Premium\-Befehl ist mit dem letzten Befehl ausgewählt oder aktiviert. Wenn dieses Flag nicht festgelegt ist, der im Menü Controller verwendet eine eigene `MenuText` Feld. Auf dem Controller im Menü kann jedoch weiterhin mit dem letzten ausgewählten Befehl aus diesem Controller.<br /><br /> Es wird empfohlen, dass Sie dieses Flag mit Kombinieren der `TextChanges` Flag.<br /><br /> Dieses Flag gilt nur für Menüs des Typs, MenuController oder MenuControllerLatched.<br /><br /> Gültig für: `Menu`|  
|TextMenuCtrlUseMenu|Verwenden der `MenuText` Feld Menücontroller. Das Feld `ButtonText`.<br /><br /> Gültig für: `Button`|  
|TextMenuUseButton|Verwenden der `ButtonText` für Menüs. Das Feld `MenuText` Wenn es angegeben wird.<br /><br /> Gültig für: `Button`|  
|TextOnly|Nur Text auf einer Symbolleiste oder einem Menü jedoch kein Symbol angezeigt, auch wenn das Symbol angegeben wird.<br /><br /> Gültig für: `Button`|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Schaltflächen\-Element](../extensibility/buttons-element.md)|Stellt eine Gruppe für [Button\-Element](../extensibility/button-element.md) Elemente.|  
|[Menüs\-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)