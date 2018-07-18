---
title: 'Workflow-Designer - Vorgehensweise: Verwenden des Argument-Designers'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94656c7242c4bc6bc1dd1430230dac62a5322f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971871"
---
# <a name="how-to-use-the-argument-designer"></a>Vorgehensweise: Verwenden des Argument-Designers

Im Vergleich zu früheren Versionen von .NET Framework, erleichtert die Argument-Designer Daten in eine und aus einer Aktivität fließen zu lassen. Der Designer zugegriffen wird, indem Sie auf die **Argumente** Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Designer enthält eine Liste von Argumenten, die in einer Tabelle angezeigt und können nach jedem Spaltenkopf, sortiert werden, mit Ausnahme von der **Standardwert** Spalte. Für jedes Argument werden der Name, die Richtung (ein/aus/ein/aus/Eigenschaft), der Typ und ein Standardausdruckswert (sofern vorhanden) angegeben. Der Name und der Standardausdruckswert sind bearbeitbare Textfelder, und der Typ und die Richtung sind Dropdownlisten. Weitere Informationen finden Sie unter [Variablen und Argumente (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>So erstellen Sie ein neues Argument

1.  Öffnen Sie eine Workflow- oder aktivitätsprojektmappe-Projektmappe in Visual Studio 2010.

2.  Öffnen Sie den Argument-Designer, indem Sie auf die **Argumente** Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Argument-Designer wird angezeigt.

3.  Klicken Sie auf die leere Zeile, die mit der Bezeichnung **Argument erstellen**. Dadurch wird eine neue Zeile mit einem neuen Argument mit den folgenden Standardwerten hinzugefügt: Argumentx für den **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1 ist, die automatisch, zum Erstellen von eindeutigen Argumentnamen inkrementiert wird, **In**  für die **Richtung**, und **Zeichenfolge** für die **Argumenttyp**. Wird kein Wert für hinzugefügt **Standardwert**. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.

    > [!NOTE]
    > Um ein Argument zu löschen, wählen Sie das Argument, indem Sie darauf klicken, und drücken Sie dann die **löschen** Schlüssel.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Workflow-Designers](../workflow-designer/using-the-workflow-designer.md)
- [Variablen und Argumente](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)