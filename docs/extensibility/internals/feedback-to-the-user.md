---
title: Feedback an den Benutzer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708410"
---
# <a name="feedback-to-the-user"></a>Feedback an den Benutzer
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der integrierten Entwicklungsumgebung (IDE) basiert das visuelle Feedback zur verfügbaren Funktionalität auf dem aktuellen Auswahl- und globalen Auswahlkontext des Benutzers. In der folgenden Tabelle sind die Funktionen aufgeführt, die in verschiedenen Auswahlkontexten verfügbar sind.

|Auswahlkontext|Verfügbare Funktionalität|
|-----------------------|-----------------------------|
|IDE|Global|
|Aktueller Produktsatz|Produktspezifisch|
|Aktive Hierarchie|Hierarchietypspezifisch|
|Aktives Hierarchieelement|Hierarchieelementtyp spezifisch|
|Aktives Dokument|Dokumenttypspezifisch|
|MDI-Fenster (Topmost Multiple-Document Interface)|Fenstertypspezifisch|
|Aktueller Auswahlkontext|Auswahlkontextspezifisch|

 Wenn Sie nur die Funktionen aufbringen, die Benutzer benötigen, und kontinuierlich konsistentes Auswahl- und Umgebungskontextfeedback bereitstellen, reduzieren Sie die Komplexität in der IDE. Die folgenden Regeln gelten immer dann, wenn ein Fenster in der IDE geöffnet wird:

- Wenn das Fenster seinen Auswahlkontext ändert, wird das Auswahlfeedback im Fenster deutlich angezeigt, und das Fenster **Dynamische Hilfe** wird, falls angezeigt, aktualisiert, um den aktuellen Kontext widerzuspiegeln.

- Wenn das Fenster den globalen Auswahlkontext ändert, werden alle kontextspezifischen Menüs, das aktive Hierarchiefenster und die Titelleiste der Anwendung aktualisiert, um den aktuellen Kontext widerzuspiegeln.

- Das Fenster sollte Eigenschaften für die aktuelle Auswahl im **Eigenschaftenfenster** und optional, falls angezeigt, das Dialogfeld **Eigenschaftenseiten** aufzeigen.

- Wenn das Fenster keine Eigenschaften anzeigt oder den globalen Auswahlkontext ändert, sollte das Auswahlfeedback nicht im Fenster verbleiben, wenn es sich nicht mehr um das aktive Fenster in der IDE handelt.

- Alle dokumentspezifischen Werkzeugfenster sollten das aktive Dokument kontinuierlich widerspiegeln.

- Menüs, Symbolleisten und die Titelleiste der Anwendung sollten das MDI-Clientfenster (Topmost Multiple Document Interface, MDI) widerspiegeln.

  Wenn z. B. die HTML-Ansicht eines **Webformulars** in einem Visual `<td>` Basic Web Application-Projekt geöffnet wird und der Benutzer ein Tag auswählt, wird Feedback wie folgt bereitgestellt:

- Die Auswahl wird im aktiven Fenster angezeigt und im **Eigenschaftenfenster** wiedergegeben.

- Die dokumentspezifische **Toolbox** wird aktualisiert, um das aktive Dokument widerzuspiegeln.

- Das Menü **"Editor-Symbolleiste"** und **"Tabelle"** werden angezeigt, und die Titelleiste wird aktualisiert, um das Fenster Webformular widerzuspiegeln.

- Das aktive Hierarchiefenster, das in der Regel **Projektmappen-Explorer**ist, und seine Titelleistenaktualisierung, um den aktuellen Kontext widerzuspiegeln, und die kontextsensitiven **Projektmenübefehle** gelten jetzt für das aktive Webanwendungsprojekt.

## <a name="see-also"></a>Weitere Informationen
- [Auswahl und Währung in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)
