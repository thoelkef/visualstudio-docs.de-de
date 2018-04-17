---
title: 'Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten | Microsoft Docs'
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
ms.openlocfilehash: 833e41979d1dac9def7e647b396161d0ac5e2b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten
  Es gibt mehrere Möglichkeiten, Ereignishandler in Visual Basic und c# zu erstellen. In der Entwurfsansicht können Sie die Ereignishandler für Steuerelemente erstellen, indem Sie auf das Steuerelement doppelklicken oder verwenden Sie den Ereignisbereich "von der **Eigenschaften** Fenster Handler für jedes Ereignis auf das Steuerelement zu erstellen. Jedoch, wenn Sie in der Codeansicht sind, nicht empfiehlt, wechseln Sie zur Entwurfsansicht, um einen Ereignishandler zu erstellen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>So erstellen Sie einen Ereignishandler in Visual Basic  
  
1.  Aus der **Klassenname** -Dropdownliste am oberen Rand des Code-Editor, wählen Sie das Objekt, das Sie möchten einen Ereignishandler für erstellen.  
  
    > [!NOTE]  
    >  Wenn Sie Ereignishandler für erstellen möchten `ThisDocument` oder `ThisWorkbook`, müssen Sie auswählen, **(ThisDocument-Ereignisse)** oder **(ThisWorkbook-Ereignisse)** in die **Klassenname**Dropdown-Liste  
  
2.  Aus der **Methodennamen** Dropdown-Liste im oberen Bereich des Code-Editor wählen Sie das Ereignis.  
  
     Visual Studio erstellt den Ereignishandler und verschiebt die Einfügemarke an den neu erstellten Ereignishandler. Wenn der Ereignishandler bereits vorhanden ist, verschiebt die Einfügemarke an den vorhandenen Ereignishandler.  
  
### <a name="to-create-an-event-handler-in-c"></a>So erstellen Sie einen Ereignishandler in c#  
  
1.  Erstellen Sie den Ereignisdelegaten in der **Start** -Ereignis für die Klasse durch den qualifizierten Namen gefolgt von einem Leerzeichen eingeben, und geben dann **+=** ohne Leerzeichen im Anschluss. Zum Beispiel:  
  
     `this.<object name>.<event name> +=`  
  
2.  Drücken Sie die TAB-Taste zweimal am Ende der Zeile des Codes.  
  
     Visual Studio automatisch abgeschlossen wird die Codezeile, erstellt den Ereignishandler und verschiebt die Einfügemarke an den neu erstellten Ereignishandler.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)  
  
  