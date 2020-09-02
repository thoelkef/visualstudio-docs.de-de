---
title: 'Gewusst wie: Hinzufügen von Kommentaren zu einem Workflow im Workflow-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663454"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Vorgehensweise: Hinzufügen von Kommentaren zu einem Workflow im Workflow-Designer
Um die Erstellung größerer, komplexerer Workflows zu erleichtern, bietet [!INCLUDE[net_v45](../includes/net-v45-md.md)] Entwicklern die Möglichkeit, den folgenden Elementtypen im Designer Anmerkungen hinzuzufügen:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Von <xref:System.Activities.Statements.FlowNode> abgeleitete Klassen

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Der Inhalt einer Anmerkung wird im Nur-Text-Format in der XAML-Datei gespeichert, die dem Workflow zugeordnet ist, und kann möglicherweise von anderen gelesen werden. Bedenken Sie diesen Umstand, wenn Sie vertrauliche Informationen in eine Anmerkung einfügen.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Hinzufügen einer Anmerkung zu einer Aktivität im Designer

1. Klicken Sie im Workflow-Designer mit der rechten Maustaste auf ein Element im Workflow-Designer, **und wählen Sie Anmerkungen,** Anmerkung **Hinzufügen**aus.

2. Fügen Sie den Text der Anmerkung im angegebenen Bereich ein.

3. Für das Element wird ein Anmerkungssymbol angezeigt. Wenn Sie mit dem Mauszeiger auf das Anmerkungssymbol zeigen, wird der Text der Anmerkung angezeigt.

     ![Sequenzaktivität mit Anmerkung](../workflow-designer/media/annotation.png "Anmerkung")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Anzeigen einer Anmerkung im Designer einer Aktivität

1. Klicken Sie bei einem Aktivitäts Designer, der eine Anmerkung außerhalb der Aktivität anzeigt, auf das **Pin** -Symbol im Funktions Indikator "Anmerkung".

2. Die Anmerkung wird im Aktivitäts-Designer angezeigt. Im unten stehenden Screenshot wird eine Anmerkung für die Startaktivität im Workflow im Aktivitäts-Designer angezeigt.

     ![Im Aktivitäts-Designer angezeigte Anmerkung](../workflow-designer/media/annotationindesigner.png "Annotationindesigner")

3. Um die Anmerkung außerhalb des Aktivitäts Designers anzuzeigen, bewegen Sie den Mauszeiger über den Bereich Anmerkung im Aktivitäts Designer, und klicken Sie auf das Symbol zum **lösen** .

     ![Außerhalb eines Aktivitäts-Designers angezeigte Anmerkung](../workflow-designer/media/annotationoutsidedesigner.png "Annotationoutsidedesigner")

### <a name="showing-or-hiding-all-annotations"></a>Ein- oder Ausblenden aller Anmerkungen

1. Klicken Sie mit der rechten Maustaste auf eine Aktivität, die eine Anmerkung enthält. Wählen Sie **Anmerkungen**und dann **alle Anmerkungen anzeigen**aus.

2. In den Aktivitäts-Designern werden alle Anmerkungen angezeigt.

3. Wenn Sie alle Anmerkungen außerhalb der Aktivitäts Designer anzeigen möchten, klicken Sie mit der rechten Maustaste auf die Aktivität, **und wählen Sie Anmerkungen aus**, und **blenden Sie alle Anmerkungen**aus.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Bearbeiten oder Löschen einer Anmerkung für eine Aktivität

1. Klicken Sie mit der rechten Maustaste auf eine Aktivität, die eine Anmerkung enthält.

2. Wählen Sie **Anmerkungen**, Anmerkung **Bearbeiten** oder **Anmerkung löschen**aus.

3. Die Anmerkung wird zur Bearbeitung geöffnet oder gelöscht.

4. Wenn Sie alle Anmerkungen gleichzeitig löschen möchten, klicken Sie mit der rechten Maustaste auf den Workflow-Designer, **und wählen Sie Anmerkung,** **alle Anmerkungen löschen**aus.

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Hinzufügen, Bearbeiten und Löschen einer Anmerkung für eine Variable oder ein Argument

1. Klicken Sie mit der rechten Maustaste auf eine Variable oder ein Argument, und wählen Sie Anmerkung hinzufügen.

2. Geben Sie den Text der Anmerkung ein. Für die Variable oder das Argument wird ein Anmerkungssymbol angezeigt.

3. Klicken Sie mit der rechten Maustaste auf eine Variable oder ein Argument, die bzw. das eine Anmerkung enthält. Wählen Sie Anmerkung bearbeiten aus.

4. Die Anmerkung wird zur Bearbeitung geöffnet.

5. Klicken Sie mit der rechten Maustaste auf eine Variable oder ein Argument, die bzw. das eine Anmerkung enthält. Wählen Sie Anmerkung löschen aus.

6. Die Anmerkung wird gelöscht.