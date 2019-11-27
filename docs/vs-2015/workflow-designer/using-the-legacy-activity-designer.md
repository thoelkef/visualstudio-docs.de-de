---
title: Verwenden des Legacy-Aktivitäts Designers | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302823"
---
# <a name="using-the-legacy-activity-designer"></a>Verwenden des Aktivitätsdesigners der Vorgängerversion
In diesem Thema wird beschrieben, wie der Aktivitätsdesigner in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwendet wird. Verwenden Sie den Designer der Vorgängerversion, wenn Sie auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Mit dem Aktivitätsdesigner können Sie benutzerdefinierte Aktivitäten erstellen.

## <a name="creating-a-custom-activity"></a>Erstellen einer benutzerdefinierten Aktivität
 Führen Sie die nachstehenden Schritte aus, um mit dem Aktivitätsdesigner eine benutzerdefinierte Aktivität zu erstellen:

1. Klicken Sie im Menü **Projekt** auf **Aktivität hinzufügen**.

2. Wählen Sie die Vorlage **Aktivität** oder **Aktivität (mit Code Trennung)** aus.

   1. Verwenden Sie die **Aktivitäts** Vorlage, um eine Aktivität mit der Aktivitäts Definition und dem Benutzercode in derselben Codedatei zu erstellen.

   2. Verwenden Sie die Vorlage " **Aktivität (mit Code Trennung)** ", um eine Aktivität mit der Aktivitäts Definition zu erstellen, die als Workflow Markup ausgedrückt wird, und den Benutzercode in einer separaten Codedatei.

3. Geben Sie einen Aktivitäts Namen ein, oder behalten Sie den Standardnamen bei, und klicken Sie auf **Hinzufügen**.

   Sie können auch eine Reihe von benutzerdefinierten Aktivitäten erstellen, indem Sie ein neues Projekt des Typs **Workflow Aktivitäts Bibliothek**erstellen. Weitere Informationen zu diesem Projekttyp finden [Sie unter Vorgehensweise: Erstellen einer Workflow Aktivitäts Bibliothek (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Konfigurieren einer Aktivität
 Wenn der Aktivitätsdesigner aktiv ist, können Sie mit dem Eigenschaftenbrowser die in der folgenden Tabelle aufgeführten Eigenschaften konfigurieren.

|Eigenschaft|Comments|
|--------------|--------------|
|**Name**|Der Name der Aktivität.|
|**Basisklasse**|Die Basisklasse, von der die Aktivität abgeleitet wird. Die Standardbasis Klasse ist [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). Klicken Sie im **Eigenschaften** Fenster auf die Auslassungs Punkte **[...]** der **Basisklasse** , um eine andere Basisklasse im [Dialog Feld .NET-Typ suchen und auswählen (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)auszuwählen.|
|**Beschreibung**|Die benutzerdefinierte Beschreibung der Aktivität.|
|**Aktiviert**|Standardmäßig auf **true** festgelegt, um die Aktivitäts Ausführung und die Validierung zu aktivieren. Legen Sie diese Einstellung auf **false** fest, um die Aktivitäts Ausführung und die Validierung Weitere Informationen zur Aktivitäts Ausführung und-Validierung finden Sie unter [entwickeln von Workflow Aktivitäten](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Hinzufügen von untergeordneten Aktivitäten
 Sie können untergeordnete Aktivitäten von der Toolbox zu der Aktivität ziehen, die Sie entwerfen. Sie können anschließend jede untergeordnete Aktivität mit dem Eigenschaftenbrowser konfigurieren.

## <a name="see-also"></a>Siehe auch
 [Entwickeln von Workflow Aktivitäten](https://go.microsoft.com/fwlink?LinkID=65024) [Erstellen von benutzerdefinierten Aktivitäten](https://go.microsoft.com/fwlink?LinkID=65021) [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md) [benutzerdefinierte Aktivitäten Beispiele](https://go.microsoft.com/fwlink?LinkID=65022) Gewusst [wie: Erstellen einer Workflow Aktivitäts Bibliothek (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [mit dem Legacy-Workflow-Designer](../workflow-designer/using-the-legacy-workflow-designer.md)