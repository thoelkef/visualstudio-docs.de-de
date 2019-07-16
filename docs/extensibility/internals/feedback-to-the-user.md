---
title: Feedback an den Benutzer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2255a972dd7a889713e77fa686b348500c03ea7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328981"
---
# <a name="feedback-to-the-user"></a>Feedback an den Benutzer
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), visuelles Feedback in Bezug auf verfügbare Funktionalität auf der aktuellen Auswahl und globale Auswahlkontext des Benutzers basiert. Die folgende Tabelle enthält die Funktionalität, die in andere Auswahl Kontexten verfügbar ist.

|Auswahlkontext|Verfügbaren Funktionen|
|-----------------------|-----------------------------|
|IDE|Global|
|Aktuelle Produktgruppe|Produktspezifisch|
|Aktive Hierarchie|Hierarchie Typ spezifische|
|Aktive Hierarchie-Element|Hierarchie Element Typ spezifische|
|Aktive Dokument|Dokument Typ spezifische|
|Fenster der obersten Multiple Document Interface (MDI)|Fenster Typ spezifische|
|Aktuellen Auswahlkontext|Bestimmte Auswahlkontext|

 Wenn Sie die Funktionalität nur Benutzer benötigen und kontinuierlich bereitstellen, konsistente Auswahl und Umgebung Kontext Feedback anzuzeigen, verringern Sie die Komplexität in der IDE. Die folgenden Regeln gelten immer, wenn ein Fenster in der IDE geöffnet wird:

- Wenn das Fenster seinen Auswahlkontext geändert wird, wird Auswahlfeedback eindeutig im Fenster angezeigt und die **dynamische Hilfe** Fenster angezeigt wird, wird den aktuellen Kontext entsprechend aktualisiert.

- Wenn das Fenster globale Auswahlkontext geändert wird, werden alle kontextspezifische Menüs, die aktive Hierarchie-Fenster und die Titelleiste der Anwendung entsprechend den aktuellen Kontext aktualisiert.

- Im Fenster sollten die Eigenschaften für die aktuelle Auswahl in Oberfläche der **Eigenschaften** Fenster und optional angezeigt, die **Eigenschaftenseiten** Dialogfeld.

- Wenn das Fenster nicht Eigenschaften Oberfläche oder globale Auswahlkontext ändern, sollten Auswahlfeedback nicht im Fenster bleiben, wenn er nicht mehr das aktive Fenster in der IDE ist.

- Alle für die spezifischen Toolfenster sollten kontinuierlich das aktive Dokument widerspiegeln.

- Menüs, Symbolleisten und die Titelleiste der Anwendung sollte das oberste Multiple Document Interface (MDI)-Clientfenster widerspiegeln.

  Z. B. wenn der HTML-Code anzeigen von einer **Webformular** innerhalb einer Web-Anwendung mit Visual Basic-Projekt wird geöffnet und der Benutzer auswählt eine `<td>` Tag, Feedback auf folgende Weise bereitgestellt:

- Auswahl in das aktive Fenster angegeben ist, und entsprechend in der **Eigenschaften** Fenster.

- Die Dokument-spezifischen **Toolbox** wird das aktive Dokument entsprechend aktualisiert.

- Die **Editor** Symbolleiste und **Tabelle** Menü angezeigt werden und der Titelleiste auf das Web Form-Fenster entsprechend aktualisiert.

- Die aktive Hierarchie-Fenster, in der Regel **Projektmappen-Explorer**, und das Title-Leiste Update entsprechend den aktuellen Kontext und dem kontextabhängigen **Projekt** Menübefehle jetzt anwenden, auf dem aktiven Web -Anwendungsprojekt.

## <a name="see-also"></a>Siehe auch
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)