---
title: Befehls-Flag-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7173bc1ebc5507eadf319c0374f4c878dea62857
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739778"
---
# <a name="command-flag-eelement"></a>Befehlsflag Eelement
Ändert das übergeordnete Element.

## <a name="syntax"></a>Syntax

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 Im folgenden Abschnitt werden gültige Elementwerte beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|AllowParams|Gibt an, dass Benutzer Befehlsparameter im **Befehlsfenster** eingeben können, wenn sie den kanonischen Namen des Befehls eingeben.<br /><br /> Gültig für:`Button`|
|Alwayscreate|Menü wird erstellt, auch wenn es keine Gruppen oder Schaltflächen hat.<br /><br /> Gültig für:`Menu`|
|CaseSensitive|Bei Benutzereinträgen wird die Groß-/Kleinschreibung beachtet.<br /><br /> Gültig für:`Combo`|
|CommandWellOnly|Wenden Sie dieses Flag an, wenn der Befehl nicht im Menü der obersten Ebene angezeigt wird und Sie es für eine zusätzliche Shellanpassung verfügbar machen möchten, z. B. zum Binden an eine Tastenkombination. Nachdem das VSPackage installiert wurde, können Sie diese Befehle anpassen, indem Sie das Dialogfeld **Optionen** öffnen und dann die Befehlsplatzierung unter der Kategorie **Tastaturumgebung** bearbeiten. Dieses Flag wirkt sich nicht auf die Platzierung in Kontextmenüs, Symbolleisten, Menücontrollern oder Untermenüs aus.<br /><br /> Gültig für: `Button`,`Combo`|
|DefaultDisabled|Standardmäßig ist der Befehl deaktiviert, wenn das VSPackage, das `QueryStatus` ihn implementiert, nicht geladen oder die Methode nicht aufgerufen wurde.<br /><br /> Gültig für: `Button`,`Combo`|
|DefaultDocked|Standardmäßig angedockt. Diese Einstellung gilt nicht mehr für Symbolleisten, da sie immer angedockt sind.|
|DefaultInvisible|Standardmäßig ist der Befehl unsichtbar, wenn das VSPackage, das `QueryStatus` ihn implementiert, nicht geladen oder die Methode nicht aufgerufen wurde.<br /><br /> Es wird empfohlen, dies mit dem `DynamicVisibility` Flag zu kombinieren.<br /><br /> Gültig `Button`für: `Combo`, ,`Menu`|
|DontCache|Die Entwicklungsumgebung speichert `QueryStatus` die Methodenergebnisse für diesen Befehl nicht zwischen.<br /><br /> Bei einem Menü wird ein Menücontroller aufgefordert, den Text seiner Menüelemente nicht zwischenzuspeichern. Verwenden Sie dieses Flag, wenn das Menü dynamische Elemente oder Elemente mit dynamischem Text enthält.<br /><br /> Gültig für: `Button`,`Menu`|
|DynamicItemStart|Gibt den Anfang einer dynamischen Liste an. Dadurch kann die Umgebung eine Liste erstellen, indem die `QueryStatus` Methode sukzessive für Listenelemente aufgerufen wird, bis das OLECMDERR_E_UNSUPPORTED-Flag zurückgegeben wird. Dies funktioniert gut für Elemente wie zuletzt verwendete (MRU) Listen und Fensterlisten.<br /><br /> Gültig für:`Button`|
|DynamicVisibility|Die Sichtbarkeit des Befehls kann `QueryStatus` durch die Methode oder durch eine `VisibilityConstraints` Kontext-GUID geändert werden, die im Abschnitt enthalten ist.<br /><br /> Gilt für Befehle, die in Menüs und Symbolleisten für das Werkzeugfenster des Werkzeugs des Werkzeugs des Werkzeugs der obersten Ebene angezeigt werden. Symbolleistenelemente der obersten Ebene können deaktiviert, aber nicht ausgeblendet `QueryStatus` werden, wenn das OLECMDF_INVISIBLE-Flag von der Methode zurückgegeben wird. Symbolleistenbefehle, die auf Symbolleisten des Werkzeugfensters angezeigt werden, können ausgeblendet werden.<br /><br /> In einem Menü zeigt dieses Flag auch an, dass es automatisch ausgeblendet werden sollte, wenn alle mitglieder ausgeblendet sind. Dieses Flag wird in der Regel Untermenüs zugewiesen, da Menüs der obersten Ebene dieses Verhalten bereits aufweisen.<br /><br /> Dieses Flag sollte mit `DefaultInvisible` der Flagge kombiniert werden.<br /><br /> Gültig `Button`für: `Combo`, ,`Menu`|
|FilterKeys|Siehe das Thema Filterschlüssel unter [Combo Element](../extensibility/combo-element.md).<br /><br /> Gültig für:`Combo`|
|FixMenuController|Wenn dieser Befehl auf einem Menücontroller positioniert ist, ist der Befehl immer der Standard. Das heißt, der Befehl wird immer dann ausgewählt, wenn die Menücontrollerschaltfläche selbst ausgewählt ist. Wenn auf dem `TextIsAnchorCommand` Menücontroller das Flag gesetzt ist, nimmt der Menücontroller seinen Text auch von dem Befehl mit dem `FixMenuController` Flag.<br /><br /> Nur ein Befehl auf einem `FixMenuController` Menücontroller sollte das Flag haben. Wenn mehr als ein Befehl so markiert ist, wird der letzte Befehl im Menü zum Standardbefehl.<br /><br /> Gültig für:`Button`|
|IconAndText|Zeigen Sie ein Symbol und Einen Text im Menü und auf der Symbolleiste an.<br /><br /> Gültig `Button`für: `Combo`, ,`Menu`|
|NoAutoVervollständigen|Die Funktion "Auto-Vervollständigung" ist deaktiviert.<br /><br /> Gültig für:`Combo`|
|NoButtonCustomize|Lassen Sie den Benutzer diese Schaltfläche nicht anpassen.<br /><br /> Gültig für: `Button`,`Combo`|
|NoKeyCustomize|Aktivieren Sie die Tastaturanpassung nicht.<br /><br /> Gültig für: `Button`,`Combo`|
|NoShowOnMenuController|Wenn dieser Befehl auf einem Menücontroller positioniert ist, wird der Befehl nicht in der Dropdownliste angezeigt.<br /><br /> Gültig für:`Button`|
|NotInTBList|Wird nicht in der Liste der verfügbaren Symbolleisten angezeigt. Dies gilt nur für Toolbar-Menütypen.<br /><br /> Gültig für:`Menu`|
|NoToolbarClose|Der Benutzer kann die Symbolleiste nicht schließen. Dies gilt nur für Toolbar-Menütypen.<br /><br /> Gültig für:`Menu`|
|Pict|Zeigt nur ein Symbol auf einer Symbolleiste, aber nur Text in einem Menü an. Wenn kein Symbol angegeben ist, wird ein anklickbares Leerzeichen auf einer Symbolleiste angezeigt.<br /><br /> Gültig für:`Button`|
|PostExec|Macht den Befehl nicht blockierend. Die Entwicklungsumgebung verschiebt die Ausführung, bis alle Vorverarbeitungsabfragen abgeschlossen sind.<br /><br /> Gültig für:`Button`|
|RouteToDocs|Der Befehl wird an das aktive Dokument weitergeleitet.<br /><br /> Gültig für:`Button`|
|StretchHorizontally|Wenn dieses Flag festgelegt ist, wird die Breite zur minimalen Breite für das Kombinationsfeld, und wenn auf der Symbolleiste Platz vorhanden ist, wird das Kombinationsfeld dehnt sich aus, um den verfügbaren Platz zu füllen. Dies tritt nur auf, wenn die Symbolleiste horizontal angedockt ist und nur ein Kombinationsfeld auf der Symbolleiste das Flag verwenden kann (das Flag wird auf allen außer dem ersten Kombinationsfeld ignoriert).<br /><br /> Gültig für:`Combo`|
|TextMenuUseButton|Verwenden `ButtonText` Sie das Feld für Menüs. Das Standardfeld `MenuText` ist, wenn es angegeben ist.<br /><br /> Gültig für:`Button`|
|TextÄnderungen|Der Befehl summiert sich zur Laufzeit, `QueryStatus` in der Regel über die Methode.<br /><br /> Gültig für: `Button`,`Menu`|
|TextChangesButton|Gültig für:`Button`|
|TextIsAnchorCommand|Bei einem Menücontroller wird der Text des Menüs dem Standardbefehl (Anker) entnommen. Ein Ankerbefehl ist der letzte ausgewählte oder gesperrte Befehl. Wenn dieses Flag nicht gesetzt ist, `MenuText` verwendet der Menücontroller ein eigenes Feld. Wenn Sie jedoch auf den Menücontroller klicken, wird weiterhin der zuletzt ausgewählte Befehl von diesem Controller aus aktiviert.<br /><br /> Es wird empfohlen, dieses `TextChanges` Flag mit dem Flag zu kombinieren.<br /><br /> Dieses Flag gilt nur für Menüs vom Typ MenuController oder MenuControllerLatched.<br /><br /> Gültig für:`Menu`|
|TextMenuCtrlUseMenu|Verwenden `MenuText` Sie das Feld auf Menücontrollern. Das Standardfeld `ButtonText`ist .<br /><br /> Gültig für:`Button`|
|TextMenuUseButton|Verwenden `ButtonText` Sie das Feld für Menüs. Das Standardfeld `MenuText` ist, wenn es angegeben ist.<br /><br /> Gültig für:`Button`|
|TextOnly|Zeigt nur Text auf einer Symbolleiste oder einem Menü, aber kein Symbol an, auch wenn das Symbol angegeben ist.<br /><br /> Gültig für:`Button`|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Buttons-Element](../extensibility/buttons-element.md)|Stellt eine Gruppe für [Button-Elementelemente](../extensibility/button-element.md) bereit.|
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabelle (. Vsct) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
