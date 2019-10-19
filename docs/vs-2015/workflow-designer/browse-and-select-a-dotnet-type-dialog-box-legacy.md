---
title: Dialog Feld ' .NET-Typ suchen und auswählen ' (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668987"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Dialogfeld '.NET-Typ suchen und auswählen' (Vorgängerversion)
In diesem Thema wird beschrieben, wie Sie das Dialogfeld **.NET-Typ suchen und auswählen** in der Legacy-[!INCLUDE[wfd1](../includes/wfd1-md.md)] verwenden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Wenn Sie im **Eigenschaften** Fenster Eigenschaften auswählen, die einen .NET Framework Typ in einer referenzierten Assembly annehmen, wird am Ende des Textfelds der Eigenschaft ein Ellipsen **[...]** angezeigt. Wenn Sie auf **[...]** klicken, wird das Dialogfeld **.NET-Typ suchen und auswählen** geöffnet. In diesem Dialogfeld können Sie einen Typ aus der Strukturansicht der referenzierten Assemblys auswählen. Wenn Sie z. b. den Aktivitäts Designer verwenden, klicken Sie im **Eigenschaften** Fenster auf die Auslassungs Punkte **[...]** der **Basisklasse** , um eine andere Basisklasse für eine Aktivität aus der Struktur der referenzierten Assemblys auszuwählen.

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **.NET-Typ suchen und auswählen** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Typname:**|Der Name des aktuell ausgewählten Typs.|
|**Type**|Der linke Bereich enthält eine Strukturansicht der Assemblys, auf die verwiesen wird. Im rechten Bereich werden die Typen angezeigt, die für die Auswahl aus der im linken Bereich ausgewählten Assembly, auf die verwiesen wird, zur Verfügung stehen.|

## <a name="see-also"></a>Siehe auch
 [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md)