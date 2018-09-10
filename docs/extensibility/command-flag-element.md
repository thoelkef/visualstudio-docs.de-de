---
title: Befehl Commandflag-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c963592fd286273e18a0bdf15905693f9f9cf1ce
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233177"
---
# <a name="command-flag-eelement"></a>Befehlsflag Eelement
Ändert das übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 Der folgende Abschnitt beschreibt die gültigen Werten.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|AllowParams|Gibt an, dass Benutzer in Parametern eingeben, können die **Befehl** Fenster, wenn sie den kanonischen Namen des Befehls eingeben.<br /><br /> Gültig für: `Button`|  
|AlwaysCreate|Menü "wird erstellt, auch wenn keine Gruppen oder Schaltflächen verfügbar sind.<br /><br /> Gültig für: `Menu`|  
|CaseSensitive|Benutzereinträge beachtet werden.<br /><br /> Gültig für: `Combo`|  
|CommandWellOnly|Wenden Sie dieses Flag an, wenn der Befehl nicht auf das Menü der obersten Ebene angezeigt, und Sie es zusätzliche Shell Anpassung, z. B. für das Binden an eine Tastenkombination zur Verfügung stellen möchten. Nach der Installation von VSPackages können Sie mit diesen Befehlen anpassen, indem Sie öffnen die **Optionen** Dialogfeld und bearbeiten Sie dann die Platzierung der Befehl unter der **Tastatur Umgebung** Kategorie. Dieses Flag hat keine Auswirkungen auf die Platzierung in Kontextmenüs, Symbolleisten, Menücontroller oder Untermenüs.<br /><br /> Gültig für: `Button`, `Combo`|  
|DefaultDisabled|Der Befehl ist standardmäßig deaktiviert, wenn das VSPackage, das sie implementiert nicht geladen wurde oder die `QueryStatus` Methode nicht aufgerufen wurde.<br /><br /> Gültig für: `Button`, `Combo`|  
|DefaultDocked|Standardmäßig angedockt. Diese Einstellung nicht mehr gilt in Symbolleisten, da diese immer angedockt sind.|  
|DefaultInvisible|Der Befehl ist standardmäßig nicht sichtbar, wenn das VSPackage, das sie implementiert nicht geladen wurde oder die `QueryStatus` Methode nicht aufgerufen wurde.<br /><br /> Es wird empfohlen, dass Sie dies mit kombinieren die `DynamicVisibility` Flag.<br /><br /> Gültig für: `Button`, `Combo`, `Menu`|  
|DontCache|Die Entwicklungsumgebung ist keine Zwischenspeicherung der `QueryStatus` Methodenergebnisse für diesen Befehl.<br /><br /> Für ein Menü wird hier ein Menücontroller nicht auf den Text der Einträge im cache. Verwenden Sie dieses Flag an, wenn das Menü enthält dynamische Elemente oder Elemente, die dynamischen Text enthalten.<br /><br /> Gültig für: `Button`, `Menu`|  
|DynamicItemStart|Gibt den Anfang einer dynamischen Liste. Dies ermöglicht die Umgebung, die eine Liste erstellen, indem Sie nacheinander Aufrufen der `QueryStatus` Methode für Listenelemente, bis das Flag OLECMDERR_E_UNSUPPORTED zurückgegeben wird. Dies funktioniert gut für Elemente, z. B. die meisten vor kurzem (MRU) und Fensterlisten verwendet.<br /><br /> Gültig für: `Button`|  
|DynamicVisibility|Die Sichtbarkeit des Befehls kann geändert werden, über die `QueryStatus` Methode oder über eine Kontext-GUID, der Bestandteil der `VisibilityConstraints` Abschnitt.<br /><br /> Gilt für Befehle, die angezeigt werden, in Menüs und Symbolleisten des Toolfensters, jedoch nicht auf der obersten Ebene Symbolleisten, die auf das Hauptfenster angezeigt werden. Auf oberster Ebene Symbolleistenelemente können deaktiviert, jedoch nicht ausgeblendet werden, wenn das Flag OLECMDF_INVISIBLE zurückgegeben wird, aus der `QueryStatus` Methode. Symbolleistenbefehle, die Symbolleisten des Toolfensters angezeigt werden, können ausgeblendet werden.<br /><br /> In einem Menü gibt dieses Flag auch, dass es automatisch ausgeblendet werden soll, wenn alle seine Member ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da dies bereits über Menüs der obersten Ebene verfügen.<br /><br /> Dieses Flag kombiniert werden soll, mit der `DefaultInvisible` Flag.<br /><br /> Gültig für: `Button`, `Combo`, `Menu`|  
|Filter-Schlüssel|Finden Sie im Thema "Filtern von Schlüssel" unter [Combo-Element](../extensibility/combo-element.md).<br /><br /> Gültig für: `Combo`|  
|FixMenuController|Wenn Sie diesen Befehl auf ein Menücontroller positioniert ist, ist der Befehl immer die Standardeinstellung; Dies bedeutet, ist der Befehl ausgewählt, wenn die Controller-Menüschaltfläche selbst ausgewählt ist. Wenn der Menücontroller verfügt die `TextIsAnchorCommand` flag so festgelegt, und klicken Sie dann die Menücontroller nimmt auch den Text des Befehls, die die `FixMenuController` Flag.<br /><br /> Nur ein Befehl für ein Menücontroller müssen die `FixMenuController` Flag. Wenn mehr als einen Befehl so gekennzeichnet ist, wird mit dem letzte Befehl im Menü der Standardbefehl.<br /><br /> Gültig für: `Button`|  
|IconAndText|Zeigen Sie im Menü und Symbolleiste ein Symbol und Text.<br /><br /> Gültig für: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Automatische Vervollständigung ist deaktiviert.<br /><br /> Gültig für: `Combo`|  
|NoButtonCustomize|Lassen Sie nicht des Benutzers diese Schaltfläche anpassen.<br /><br /> Gültig für: `Button`, `Combo`|  
|NoKeyCustomize|Aktivieren Sie die Anpassung der Tastatur nicht.<br /><br /> Gültig für: `Button`, `Combo`|  
|NoShowOnMenuController|Wenn Sie diesen Befehl auf ein Menücontroller positioniert ist, wird der Befehl nicht in der Dropdown-Liste angezeigt.<br /><br /> Gültig für: `Button`|  
|NotInTBList|Wird nicht in der Liste der verfügbaren Symbolleisten angezeigt werden. Dies gilt nur für die Symbolleiste im Menü-Typen.<br /><br /> Gültig für: `Menu`|  
|NoToolbarClose|Benutzer kann die Symbolleiste nicht schließen. Dies gilt nur für die Symbolleiste im Menü-Typen.<br /><br /> Gültig für: `Menu`|  
|PICT|Zeigen Sie nur ein Symbol auf einer Symbolleiste, aber nur Text in einem Menü an. Wenn kein Symbol angegeben ist, wird eine leere durch Klicken aktivierbare Fläche auf einer Symbolleiste gezeigt.<br /><br /> Gültig für: `Button`|  
|PostExec|Wird der Befehl nicht blockierend. Die Entwicklungsumgebung verzögert Ausführung, bis alle vorab verarbeitete Abfragen abgeschlossen sind.<br /><br /> Gültig für: `Button`|  
|RouteToDocs|Der Befehl wird an das aktive Dokument weitergeleitet.<br /><br /> Gültig für: `Button`|  
|StretchHorizontally|Wenn dieses Flag festgelegt ist, wird die Breite die minimale Breite für das Kombinationsfeld, und wenn der Speicherplatz auf der Symbolleiste vorhanden ist, im Kombinationsfeld wird gestreckt, um den verfügbaren Platz auszufüllen. Dies geschieht nur, wenn die Symbolleiste horizontal angedockt ist, und nur ein Kombinationsfeld auf der Symbolleiste kann das Flag (das Flag wird auf allen außer den ersten Kombinationsfeld ignoriert).<br /><br /> Gültig für: `Combo`|  
|TextMenuUseButton|Verwenden der `ButtonText` Feld für Menüs. Ist das Standardfeld `MenuText` wenn er angegeben wird.<br /><br /> Gültig für: `Button`|  
|TextChanges|Der Befehl oder Menü Text kann über in der Regel zur Laufzeit geändert werden die `QueryStatus` Methode.<br /><br /> Gültig für: `Button`, `Menu`|  
|TextChangesButton|Gültig für: `Button`|  
|TextIsAnchorCommand|Für ein Menücontroller wird der Text des Menüs von den Standardbefehl (Anker) verwendet. Ein Anchor-Befehl ist mit dem letzten Befehl ausgewählt oder ein Latchtyp zugeordnet werden. Wenn dieses Flag nicht festgelegt ist, der Menücontroller verwendet einen eigenen `MenuText` Feld. Klicken Sie auf dem Menücontroller im kann jedoch weiterhin mit dem letzten ausgewählten Befehl von diesem Controller.<br /><br /> Es wird empfohlen, dass Sie dieses Flag mit kombinieren die `TextChanges` Flag.<br /><br /> Dieses Flag gilt nur für Menüs des Typs, MenuController oder MenuControllerLatched.<br /><br /> Gültig für: `Menu`|  
|TextMenuCtrlUseMenu|Verwenden der `MenuText` Menücontroller Feld. Ist das Standardfeld `ButtonText`.<br /><br /> Gültig für: `Button`|  
|TextMenuUseButton|Verwenden der `ButtonText` Feld für Menüs. Ist das Standardfeld `MenuText` wenn er angegeben wird.<br /><br /> Gültig für: `Button`|  
|TextOnly|Zeigen Sie nur-Text auf einer Symbolleiste oder ein Menü, aber kein Symbol an, auch wenn das Symbol angegeben wird.<br /><br /> Gültig für: `Button`|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Buttons-element](../extensibility/buttons-element.md)|Stellt eine Gruppe für [Schaltflächenelement](../extensibility/button-element.md) Elemente.|  
|[Menus-element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)