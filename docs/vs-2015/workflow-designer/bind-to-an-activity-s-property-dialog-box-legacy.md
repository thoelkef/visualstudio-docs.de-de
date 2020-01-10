---
title: Dialog Feld "an&#39;eine Aktivität binden" (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f88d7ebe714fcdc9bf404e1cf58c4c86cf37047d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851467"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Dialog Feld "an&#39;eine Aktivität binden" (Legacy)
In diesem Thema wird beschrieben, wie Sie das Dialogfeld **an die Eigenschaft einer Aktivität binden** in der Legacy-[!INCLUDE[wfd1](../includes/wfd1-md.md)]verwenden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Ein Instanztyp der Abhängigkeitseigenschaft kann an die öffentliche Eigenschaft oder das Ereignis einer anderen Aktivität gebunden werden. Weitere Informationen zur Aktivitäts Bindung finden Sie unter [Verwenden von Abhängigkeits Eigenschaften](https://msdn2.microsoft.com/library/bb675255.aspx).

 Sie wählen eine Eigenschaft aus, an die gebunden werden soll, indem Sie das Dialogfeld **an die Eigenschaft einer Aktivität binden** . Öffnen Sie dieses Dialogfeld, indem Sie im Eigenschaften Fenster am Ende des Textfelds der ausgewählten Eigenschaft auf die Auslassungs Punkte **[...]** klicken, oder indem Sie auf das blaue Ausrufezeichen Symbol klicken, das neben dem Eigenschaftsnamen im **Eigenschaften** Browser angezeigt wird.

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog **Felds binden an die Eigenschaft einer Aktivität** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Binden an einen vorhandenen Member**|Wählen Sie einen Member aus, an den Sie im Strukturansichtsbereich binden möchten. Im Bereich unterhalb der Struktur wird eine Meldung angezeigt, ob es sich bei dem Member um einen gültigen Typ handelt, an den gebunden werden kann, oder nicht. Klicken Sie auf **OK** , um eine Bindung mit dem ausgewählten gültigen Member herzustellen.|
|**Binden an einen neuen Member**|Erstellen Sie ein neues Memberfeld oder eine Eigenschaft, an das bzw. die gebunden werden kann. Geben Sie einen **neuen Elementnamen**ein. Wählen Sie aus, ob Sie eine Abhängigkeits Eigenschaft oder ein öffentliches Feld erstellen möchten, indem Sie **Create Field** oder **Create Property**auswählen. Klicken Sie auf **OK** , um das neue Mitglied zu erstellen.|

## <a name="see-also"></a>Siehe auch
 [Verwenden von Aktivitäts Eigenschaften](https://msdn2.microsoft.com/library/bb628510.aspx) [mithilfe von Abhängigkeits Eigenschaften](https://msdn2.microsoft.com/library/bb675255.aspx) [Legacy-Designer für Windows Workflow Foundation UI-Hilfe](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
