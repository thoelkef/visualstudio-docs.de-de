---
title: 'Workflow-Designer - Vorgehensweise: verwenden den Importe-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de974ebba6fbe746a4d7acb4c1a20fefa5488a8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970647"
---
# <a name="how-to-use-the-imports-designer"></a>Vorgehensweise: Verwenden des Imports-Designers

Der Importe-Designer ermöglicht es Ihnen, Namespaces für die Typen einzugeben, die Sie in den Ausdrücken verwenden. Ähnlich wie die **importiert** oder **mit** Schlüsselwörter in Visual Basic und C#-, Angeben von Namespaces im Importe-Designer ermöglichen es Ihnen, einfach einen Typnamen in Ihrem Ausdruck anstatt einen vollständig qualifizierten eingeben Version-Typname.

Der Importe-Designer reagiert sowohl auf Änderungen, die in der Benutzeroberfläche vorgenommen werden, als auch auf Änderungen, die beim Speichern des Workflows gespeichert werden. Wenn der Workflow gespeichert wird, können dem Importe-Designer automatisch Namespaces hinzugefügt werden. Hierzu gehört Folgendes:

-   Namespaces für alle Typen, die in Variablen- und Argumentdeklarationen verwendet werden.

-   Namespaces für alle Typen, die in Ausdrücken verwendet werden.

-   Beliebige andere Namespaces, die zum Serialisieren des Workflows erforderlich sind (z. B., Namespaces, die von benutzerdefinierten Aktivitäten im Workflow verwendet werden).

 Wenn der Workflow gespeichert wird, wird Ihnen möglicherweise auffallen, dass einige Namespaces, die Sie manuell gelöscht haben, wegen der in der vorangehenden Liste beschriebenen Logik automatisch wieder dem Importe-Designer hinzugefügt werden.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>So fügen Sie der Liste der importierten Namespaces einen Namespace hinzu

1.  Öffnen Sie eine WCF-workflowdienstanwendung, Konsolenanwendung für Workflows oder Workflow-aktivitätsbibliothekprojekt in Visual Studio 2010 oder einer neu gehosteten workflowanwendung.

2.  Klicken Sie auf **Importe** am unteren Rand der hauptarbeitsfläche. Der Import-Designer wird angezeigt.

3.  Geben Sie einen Namespace ein, oder wählen Sie einen Namespace im Dropdownlisten-Steuerelement am oberen Rand des Import-Designers aus.

     Während der Eingabe wird eine Liste gültiger Namespaces angezeigt, die mit den eingegebenen Zeichen übereinstimmen.

4.  Drücken Sie **EINGABETASTE** die Liste der Namespace hinzu.

5.  Wenn Sie einen Namespace aus der Liste entfernen möchten, wählen Sie den Namespace, und drücken Sie dann die **löschen** auf der Tastatur die Taste. Beachten Sie, dass ein Namespace nur gelöscht werden kann, wenn er nicht gültig ist, z. B., wenn das Projekt nicht mehr auf die Assembly verweist, die den Namespace enthält.