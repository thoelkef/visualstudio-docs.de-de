---
title: 'Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656620"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)
Beim Entwickeln einer Workflow Projekt Mappe mit der Vorgängerversion von, die [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] auf oder abzielt [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] , können benutzerdefinierte Aktivitäten dem Workflow Projekt und ihren Designern hinzugefügt werden, die in der **Toolbox** platziert werden, um den Zugriff zu vereinfachen. Sie können der **Toolbox** Aktivitäten auch direkt aus einer Dynamic Link Library (dll) hinzufügen.

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>So fügen Sie eine Aktivität aus einer DLL zur Toolbox hinzu

1. Klicken Sie mit der rechten Maustaste auf die Toolbox Fenster Oberfläche unter **Windows Workflow**, und klicken Sie dann auf **Elemente auswählen**.

2. Klicken Sie im Dialogfeld **Toolbox Elemente auswählen** auf die Registerkarte **System. Activities-Komponenten** , und klicken Sie dann auf der unteren rechten Seite des Fensters auf **Durchsuchen** .

3. Wählen Sie die dll aus dem Datei Verzeichnis aus, das die Implementierung der benutzerdefinierten Aktivität enthält, die der **Toolbox**hinzugefügt werden soll, und klicken Sie dann auf **Öffnen**.

4. Klicken Sie auf **OK** , um das Hinzufügen der Aktivität zur Toolbox abzuschließen.

## <a name="see-also"></a>Weitere Informationen
 [Verwenden der](../workflow-designer/using-the-legacy-activity-designer.md) [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md) des Legacy-Aktivitäts Designers