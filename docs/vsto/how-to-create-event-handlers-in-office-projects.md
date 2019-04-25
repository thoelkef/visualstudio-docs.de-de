---
title: 'Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 577b12be220e2a695609db6c508d7aaf69c79f92
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054520"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten
  Es gibt verschiedene Möglichkeiten zum Erstellen von Ereignishandlern in Visual Basic und c#. In der Entwurfsansicht können Sie den Ereignishandler für Steuerelemente erstellen, indem Sie auf das Steuerelement doppelklicken oder Ereignisse im Bereich von der **Eigenschaften** Fenster aus, um Handler für alle Ereignisse für das Steuerelement zu erstellen. Wenn Sie in der Codeansicht sind, kann nicht beliebig So wechseln Sie zur Entwurfsansicht, um einen Ereignishandler zu erstellen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Zum Erstellen eines ereignishandlers in Visual Basic

1. Von der **Klassenname** Dropdownliste am oberen Rand des Code-Editor, wählen Sie das Objekt, das möchten Sie erstellen einen Ereignishandler für.

    > [!NOTE]
    >  Wenn Sie Ereignishandler für erstellen möchten `ThisDocument` oder `ThisWorkbook`, wählen Sie **(ThisDocument-Ereignisse)** oder **(ThisWorkbook-Ereignisse)** in die **Klassenname**Dropdown-Liste

2. Von der **Methodenname** Dropdown-Listenfeld oben im Code-Editor, wählen Sie das Ereignis.

     Visual Studio erstellt den Ereignishandler und verschiebt die Einfügemarke an den neu erstellten Ereignishandler. Wenn der Ereignishandler bereits vorhanden ist, verschiebt die Einfügemarke, mit dem vorhandenen Ereignishandler.

### <a name="to-create-an-event-handler-in-c"></a>So erstellen einen Ereignishandler in C\#

1. Erstellen der Ereignisdelegat in die **Start** -Ereignis der Klasse durch den vollqualifizierten Namen des Ereignisses gefolgt von einem Leerzeichen, und geben dann **+=** anschließend ohne Leerzeichen. Zum Beispiel:

     `this.<object name>.<event name> +=`

2. Am Ende der Zeile des Codes drücken Sie zweimal die TAB-Taste aus.

     Visual Studio automatisch abgeschlossen wird die Zeile des Codes, den Ereignishandler erstellt, und verschiebt die Einfügemarke an den neu erstellten Ereignishandler.

## <a name="see-also"></a>Siehe auch
- [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)
- [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)
