---
title: 'Workflow-Designer – Vorgehensweise: Hinzufügen von Kommentaren zu einem workflow'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c7eb15c6d19ab40df6913dd67466dc20012492b7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60058588"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Vorgehensweise: Hinzufügen von Kommentaren zu einem Workflow im Workflow-Designer

Um zu ermöglichen, größerer, komplexerer Workflows zu erstellen, kann .NET Framework 4.5 der Entwickler auf die folgenden Elementtypen im Designer Anmerkungen hinzuzufügen:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Von <xref:System.Activities.Statements.FlowNode> abgeleitete Klassen

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Der Inhalt einer Anmerkung wird im Nur-Text-Format in der XAML-Datei gespeichert, die dem Workflow zugeordnet ist, und kann möglicherweise von anderen gelesen werden. Bedenken Sie diesen Umstand, wenn Sie vertrauliche Informationen in eine Anmerkung einfügen.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Hinzufügen einer Anmerkung zu einer Aktivität im Designer

1. Der Workflow-Designer mit der Maustaste auf ein Element im Workflow Designer, und wählen **Anmerkungen**, **Anmerkung hinzufügen**.

1. Fügen Sie den Text der Anmerkung im angegebenen Bereich ein.

   Das Element wird ein Anmerkungssymbol gezeigt. Mit dem Mauszeiger auf das Anmerkungssymbol zeigt den Text der Anmerkung.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Anzeigen einer Anmerkung im Designer einer Aktivität

1. Ein Aktivitäts-Designer mit einer Anmerkung, die außerhalb der Aktivität angezeigt, und klicken Sie auf die **Pin** Symbol im anmerkungsadorner.

   Die Anmerkung wird im Aktivitäts Designer angezeigt. Im unten stehenden Screenshot wird eine Anmerkung für die Startaktivität im Workflow im Aktivitäts-Designer angezeigt.

   ![Im Aktivitäts-Designer angezeigte Anmerkung](../workflow-designer/media/annotationindesigner.png)

2. Wenn die Anmerkung außerhalb der Aktivitäts Designer anzeigen möchten, zeigen Sie auf den anmerkungsbereich im Aktivitäts Designer, und klicken Sie auf die **Unpin** Symbol

   ![Außerhalb einer Aktivitäts Designer angezeigte Anmerkung](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Ein- oder Ausblenden aller Anmerkungen

1. Klicken Sie mit der rechten Maustaste auf eine Aktivität, die eine Anmerkung enthält. Wählen Sie **Anmerkungen**, **alle Anmerkungen anzeigen**.

   Alle Anmerkungen werden in der Aktivitäts Designer angezeigt.

1. Um alle Anmerkungen außerhalb der Aktivitäts Designer anzuzeigen, mit der Maustaste, auf die Aktivität, und wählen **Anmerkungen**, **alle Anmerkungen ausblenden**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Bearbeiten oder Löschen einer Anmerkung für eine Aktivität

1. Klicken Sie mit der rechten Maustaste auf eine Aktivität, die eine Anmerkung enthält.

1. Wählen Sie **Anmerkungen**, **Anmerkung bearbeiten** oder **Anmerkung löschen**.

   Die Anmerkung wird zur Bearbeitung geöffnet oder gelöscht.

1. Um alle Anmerkungen gleichzeitig zu löschen, Maustaste den Workflow aus, und wählen **Anmerkung**, **alle Anmerkungen löschen**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Hinzufügen, Bearbeiten und Löschen einer Anmerkung für eine Variable oder ein Argument

1. Klicken Sie mit der rechten Maustaste auf eine Variable oder ein Argument, und wählen Sie Anmerkung hinzufügen.

1. Geben Sie den Text der Anmerkung ein. Die Variable oder das Argument wird ein Anmerkungssymbol angezeigt.

1. Klicken Sie mit der rechten Maustaste auf eine Variable oder ein Argument, die bzw. das eine Anmerkung enthält. Wählen Sie Anmerkung bearbeiten aus.

   Die Anmerkung wird zur Bearbeitung geöffnet.

1. Klicken Sie mit der rechten Maustaste auf eine Variable oder ein Argument, die bzw. das eine Anmerkung enthält. Wählen Sie Anmerkung löschen aus.

   Die Anmerkung wird gelöscht.