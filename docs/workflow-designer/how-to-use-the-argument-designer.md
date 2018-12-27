---
title: 'Workflow-Designer – Vorgehensweise: Verwenden des Argument-Designers'
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
ms.openlocfilehash: 88d9d568a115680c545a32a0d5f533fcab51da1f
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684599"
---
# <a name="how-to-use-the-argument-designer"></a>Vorgehensweise: Verwenden des Argument-Designers

Im Vergleich zu früheren Versionen von .NET Framework, erleichtert der Argument-Designer Daten in und aus einer Aktivität fließen zu ermöglichen. Der Designer erfolgt durch Klicken auf die **Argumente** -Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Designer enthält eine Liste von Argumenten, die in Tabellenform angezeigt und können nach jedem die Spaltenüberschriften sortiert werden, mit Ausnahme der **Standardwert** Spalte. Für jedes Argument werden der Name, die Richtung (ein/aus/ein/aus/Eigenschaft), der Typ und ein Standardausdruckswert (sofern vorhanden) angegeben. Der Name und der Standardausdruckswert sind bearbeitbare Textfelder, und der Typ und die Richtung sind Dropdownlisten. Weitere Informationen finden Sie unter [Variablen und Argumente (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>So erstellen Sie ein neues Argument

1.  Öffnen Sie eine Lösung Workflow bzw. eine Aktivität in Visual Studio.

2.  Öffnen Sie den Argument-Designer, indem Sie auf die **Argumente** -Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Argument-Designer wird angezeigt.

3.  Klicken Sie auf die leere Zeile, die mit der Bezeichnung **Argument erstellen**. Dadurch wird eine neue Zeile hinzugefügt, mit einem neuen Argument mit den folgenden Standardwerten: Argumentx für den **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1, die automatisch inkrementiert wird ist, um eindeutige Argumentnamen, erstellen **In**  für die **Richtung**, und **Zeichenfolge** für die **Argumenttyp**. Wird kein Wert hinzugefügt, für die **Standardwert**. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.

    > [!NOTE]
    > Um ein Argument zu löschen, wählen Sie das Argument, indem Sie darauf klicken, und drücken Sie dann die **löschen** Schlüssel.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Workflow-Designers](developing-applications-with-the-workflow-designer.md)
- [Variablen und Argumente](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)