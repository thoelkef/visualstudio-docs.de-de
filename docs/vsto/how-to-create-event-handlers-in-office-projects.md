---
title: 'Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8b7e55ee7f094ad104d9c8eb6ef3057621bcccee
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254243"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten
  Es gibt verschiedene Möglichkeiten zum Erstellen von Ereignishandlern in Visual Basic und c#. In der Entwurfsansicht können Sie den Ereignishandler für Steuerelemente erstellen, indem Sie auf das Steuerelement doppelklicken oder Ereignisse im Bereich von der **Eigenschaften** Fenster aus, um Handler für alle Ereignisse für das Steuerelement zu erstellen. Wenn Sie in der Codeansicht sind, kann nicht beliebig So wechseln Sie zur Entwurfsansicht, um einen Ereignishandler zu erstellen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Zum Erstellen eines ereignishandlers in Visual Basic  
  
1.  Von der **Klassenname** Dropdownliste am oberen Rand des Code-Editor, wählen Sie das Objekt, das möchten Sie erstellen einen Ereignishandler für.  
  
    > [!NOTE]  
    >  Wenn Sie Ereignishandler für erstellen möchten `ThisDocument` oder `ThisWorkbook`, wählen Sie **(ThisDocument-Ereignisse)** oder **(ThisWorkbook-Ereignisse)** in die **Klassenname**Dropdown-Liste  
  
2.  Von der **Methodenname** Dropdown-Listenfeld oben im Code-Editor, wählen Sie das Ereignis.  
  
     Visual Studio erstellt den Ereignishandler und verschiebt die Einfügemarke an den neu erstellten Ereignishandler. Wenn der Ereignishandler bereits vorhanden ist, verschiebt die Einfügemarke, mit dem vorhandenen Ereignishandler.  
  
### <a name="to-create-an-event-handler-in-c"></a>Zum Erstellen eines ereignishandlers in c#  
  
1.  Erstellen der Ereignisdelegat in die **Start** -Ereignis der Klasse durch den vollqualifizierten Namen des Ereignisses gefolgt von einem Leerzeichen, und geben dann **+=** anschließend ohne Leerzeichen. Zum Beispiel:  
  
     `this.<object name>.<event name> +=`  
  
2.  Am Ende der Zeile des Codes drücken Sie zweimal die TAB-Taste aus.  
  
     Visual Studio automatisch abgeschlossen wird die Zeile des Codes, den Ereignishandler erstellt, und verschiebt die Einfügemarke an den neu erstellten Ereignishandler.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)  
  
  