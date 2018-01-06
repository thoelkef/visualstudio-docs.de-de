---
title: Befehl Flag Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ff9458eed7f9c77a964240f81017d27d95d9622
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="command-flag-element"></a>Command-Flag-Element
Ändert das übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 Der folgende Abschnitt beschreibt die gültige Element-Werte.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|AllowParams|Gibt an, dass Benutzer Befehlsparameter in eingeben, können die **Befehl** Fenster, wenn sie den kanonischen Namen des Befehls eingeben.<br /><br /> Gültig für:`Button`|  
|AlwaysCreate|Menü wird erstellt, selbst wenn er keine Gruppen oder Schaltflächen enthält.<br /><br /> Gültig für:`Menu`|  
|CaseSensitive|Benutzereinträge auf Groß-/Kleinschreibung beachtet.<br /><br /> Gültig für:`Combo`|  
|CommandWellOnly|Wenden Sie dieses Flag an, wenn der Befehl nicht auf das Menü der obersten Ebene angezeigt, und es zusätzliche Shell Anpassung, z. B. für das Binden an eine Tastenkombination verfügbar machen möchten. Nachdem das VSPackage installiert ist, können Sie diese Befehle anpassen, indem Sie öffnen die **Optionen** (Dialogfeld), und bearbeiten Sie dann die Platzierung der Befehl unter dem **Tastatur Umgebung** Kategorie. Diese Kennzeichnung wirkt sich nicht bei der Platzierung in Kontextmenüs, Symbolleisten, Menücontroller oder Untermenüs.<br /><br /> Gültig für: `Button`,`Combo`|  
|DefaultDisabled|Der Befehl ist standardmäßig deaktiviert, wenn das VSPackage, die ihn implementiert nicht geladen wurde oder die `QueryStatus` Methode nicht aufgerufen wurde.<br /><br /> Gültig für: `Button`,`Combo`|  
|DefaultDocked|Standardmäßig angedockt. Diese Einstellung nicht mehr gilt für Symbolleisten, da sie immer angedockt sind.|  
|DefaultInvisible|Der Befehl ist standardmäßig nicht sichtbar, wenn das VSPackage, die ihn implementiert nicht geladen wurde oder die `QueryStatus` Methode nicht aufgerufen wurde.<br /><br /> Es wird empfohlen, dass Sie dies mit Zusammenfassen der `DynamicVisibility` Flag.<br /><br /> Gültig für: `Button`, `Combo`,`Menu`|  
|DontCache|Die Entwicklungsumgebung ist nicht im cache der `QueryStatus` Methodenergebnisse für diesen Befehl.<br /><br /> Für ein Menü weist dies ein Menücontroller nicht, um den Text der Menüelemente zwischenzuspeichern. Verwenden Sie dieses Flag an, wenn das Menü enthält dynamische Elemente oder Elemente mit dynamischen Text.<br /><br /> Gültig für: `Button`,`Menu`|  
|DynamicItemStart|Gibt den Anfang einer dynamischen Liste. Dadurch können die Umgebung, um eine Liste zu erstellen, indem Sie nach und nach Aufrufen der `QueryStatus` -Methode für Listenelemente, bis das Flag OLECMDERR_E_UNSUPPORTED zurückgegeben wird. Dies funktioniert gut für Elemente, z. B. die meisten vor kurzem (MRU) und Fensterlisten verwendet.<br /><br /> Gültig für:`Button`|  
|DynamicVisibility|Die Sichtbarkeit des Befehls kann geändert werden, über die `QueryStatus` Methode oder durch einen Kontext GUID, die in enthalten ist das `VisibilityConstraints` Abschnitt.<br /><br /> Gilt für Befehle, die angezeigt werden, auf die Menüs und Symbolleisten des Toolfensters, jedoch nicht auf der obersten Ebene Symbolleisten, die auf das Hauptfenster angezeigt werden. Der obersten Ebene Symbolleistenelemente können deaktiviert, jedoch nicht ausgeblendet, wenn das Flag OLECMDF_INVISIBLE zurückgegeben wird, aus der `QueryStatus` Methode. Befehle, die auf Symbolleisten des Toolfensters angezeigt werden, können ausgeblendet werden.<br /><br /> In einem Menü gibt dieses Flag auch an, dass er automatisch ausgeblendet werden soll, wenn alle ihre Elemente ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da dieses Verhalten bereits über Menüs der obersten Ebene verfügen.<br /><br /> Dieses Flag sollte kombiniert werden, mit der `DefaultInvisible` Flag.<br /><br /> Gültig für: `Button`, `Combo`,`Menu`|  
|Durch Drücken|Finden Sie im Thema filtern Schlüssel unter [Kombinationsfeld Element](../extensibility/combo-element.md).<br /><br /> Gültig für:`Combo`|  
|FixMenuController|Wenn Sie diesen Befehl auf einem Domänencontroller im Menü positioniert ist, ist der Befehl immer die Standardeinstellung; Dies bedeutet, ist der Befehl ausgewählt, wenn die Controller-Menüschaltfläche selbst ausgewählt ist. Wenn der Menücontroller im ist die `TextIsAnchorCommand` -flag festgelegt, und klicken Sie dann die Menücontroller auch den Text des Befehls ausgeführt wird, die hat die `FixMenuController` Flag.<br /><br /> Nur ein Befehl für ein Menücontroller müssen die `FixMenuController` Flag. Wenn mehr als ein Befehl so gekennzeichnet ist, wird mit dem letzte Befehl im Menü den Standardbefehl an.<br /><br /> Gültig für:`Button`|  
|IconAndText|Ein Symbol und Text in Menüs und Symbolleisten anzeigen<br /><br /> Gültig für: `Button`, `Combo`,`Menu`|  
|NoAutoComplete|Die AutoVervollständigen Funktion ist deaktiviert.<br /><br /> Gültig für:`Combo`|  
|NoButtonCustomize|Lassen Sie nicht des Benutzers diese Schaltfläche anpassen.<br /><br /> Gültig für: `Button`,`Combo`|  
|NoKeyCustomize|Aktivieren Sie die Anpassung der Tastatur nicht.<br /><br /> Gültig für: `Button`,`Combo`|  
|NoShowOnMenuController|Wenn Sie diesen Befehl auf einem Domänencontroller im Menü positioniert ist, wird der Befehl nicht in der Dropdown-Liste angezeigt.<br /><br /> Gültig für:`Button`|  
|NotInTBList|Wird nicht in der Liste der verfügbaren Symbolleisten angezeigt werden. Dies gilt nur für Menütypen Symbolleiste.<br /><br /> Gültig für:`Menu`|  
|NoToolbarClose|Benutzer kann die Symbolleiste nicht schließen. Dies gilt nur für Menütypen Symbolleiste.<br /><br /> Gültig für:`Menu`|  
|PICT|Zeigen Sie nur ein Symbol auf einer Symbolleiste, aber nur Text in einem Menü an "". Wenn kein Symbol angegeben wird, zeigt ein durch Klicken aktivierbaren Leerzeichen auf einer Symbolleiste.<br /><br /> Gültig für:`Button`|  
|PostExec|Wird der Befehl nicht blockierend. Die Entwicklungsumgebung verzögert Ausführung, bis alle vorab verarbeitete Abfragen abgeschlossen sind.<br /><br /> Gültig für:`Button`|  
|RouteToDocs|Der Befehl wird an das aktive Dokument weitergeleitet.<br /><br /> Gültig für:`Button`|  
|StretchHorizontally|Wenn dieses Flag festgelegt ist, wird die Breite die minimale Breite für das Kombinationsfeld, und wenn auf der Symbolleiste Platz verfügbar ist, im Kombinationsfeld wird gestreckt, um den verfügbaren Platz auszufüllen. Dies geschieht nur, wenn die Symbolleiste horizontal angedockt ist, und nur ein Kombinationsfeld auf der Symbolleiste kann das Flag (das Flag wird auf allen Seiten mit Ausnahme der ersten Kombinationsfeld ignoriert).<br /><br /> Gültig für:`Combo`|  
|TextMenuUseButton|Verwenden der `ButtonText` für Menüs. Standardfeldsatz ist `MenuText` wenn er angegeben wird.<br /><br /> Gültig für:`Button`|  
|TextChanges|Der Befehl oder im Menü Text kann über in der Regel zur Laufzeit geändert werden die `QueryStatus` Methode.<br /><br /> Gültig für: `Button`,`Menu`|  
|TextChangesButton|Gültig für:`Button`|  
|TextIsAnchorCommand|Für ein Menücontroller ist der Text des Menüs aus den Standardbefehl (Anchor) verwendet. Ein Premium-Befehl ist mit dem letzten Befehl ausgewählt oder als ausgewählt markiert. Wenn dieses Flag nicht festgelegt ist, die im Menü wird verwendet, das einen eigenen `MenuText` Feld. Klicken auf das Menücontroller ermöglicht jedoch weiterhin mit dem letzten ausgewählten Befehl von diesem Controller.<br /><br /> Es wird empfohlen, dass Sie dieses Flag mit Zusammenfassen der `TextChanges` Flag.<br /><br /> Dieses Flag gilt nur für Menüs des Typs, MenuController oder MenuControllerLatched.<br /><br /> Gültig für:`Menu`|  
|TextMenuCtrlUseMenu|Verwenden der `MenuText` Menücontroller Feld. Standardfeldsatz ist `ButtonText`.<br /><br /> Gültig für:`Button`|  
|TextMenuUseButton|Verwenden der `ButtonText` für Menüs. Standardfeldsatz ist `MenuText` wenn er angegeben wird.<br /><br /> Gültig für:`Button`|  
|TextOnly|Zeigen Sie nur-Text auf einer Symbolleiste oder ein Menü, jedoch kein Symbol an, auch wenn das Symbol "angegeben wird.<br /><br /> Gültig für:`Button`|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Buttons-Element](../extensibility/buttons-element.md)|Stellt eine Gruppe für [Schaltflächenelement](../extensibility/button-element.md) Elemente.|  
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die eine VSPackage implementiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)