---
title: 'Gewusst wie: Verwenden des Argument-Designers | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659116"
---
# <a name="how-to-use-the-argument-designer"></a>Vorgehensweise: Verwenden des Argument-Designers
Verglichen mit früheren Versionen von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], ist es mit dem Argument-Designer einfach, Daten in eine und aus einer Aktivität fließen zu lassen. Der Zugriff auf den Designer erfolgt durch Klicken auf die Schaltfläche **Argumente** in der linken unteren Ecke der Entwurfs Canvas. Der Designer enthält eine Liste von Argumenten, die in tabellarischer Form angezeigt werden und nach den einzelnen Spaltenüberschriften sortiert werden können, mit Ausnahme der **Standardwert** Spalte. Für jedes Argument werden der Name, die Richtung (ein/aus/ein/aus/Eigenschaft), der Typ und ein Standardausdruckswert (sofern vorhanden) angegeben. Der Name und der Standardausdruckswert sind bearbeitbare Textfelder, und der Typ und die Richtung sind Dropdownlisten. [!INCLUDE[crabout](../includes/crabout-md.md)] Argumente finden Sie unter [Variablen und Argumente](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>So erstellen Sie ein neues Argument

1. Öffnen Sie in [!INCLUDE[vs2010](../includes/vs2010-md.md)] eine Workflow- oder Aktivitätsprojektmappe.

2. Öffnen Sie den Argument-Designer, indem Sie auf die Schaltfläche **Argumente** in der linken unteren Ecke der Entwurfs Canvas klicken. Der Argument-Designer wird angezeigt.

3. Klicken Sie auf die leere Zeile mit der Bezeichnung **Create Argument**. Dadurch wird eine neue Zeile mit einem neuen Argument mit den folgenden Standardwerten hinzugefügt: argumentx für den **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1 ist, der automatisch erhöht wird, um eindeutige Argument Namen zu erstellen, **in** für die **Richtung**. und die **Zeichenfolge** für den **Argumenttyp**. Für den **Standardwert**wird kein Wert hinzugefügt. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.

    > [!NOTE]
    > Wählen Sie zum Löschen eines Arguments das Argument aus, indem Sie darauf klicken, und drücken Sie dann die ENTF **-Taste.**

## <a name="see-also"></a>Siehe auch
 [Verwenden der Workflow-Designer](../workflow-designer/using-the-workflow-designer.md) [Variablen und Argumente](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)